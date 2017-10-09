---
title: "Working with C++ and Python in Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: 9/28/2017
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-python"
ms.devlang: python
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
ms.assetid: f7dbda92-21bf-4af0-bb34-29b8bf231f32
description: The process amd steps to write a C++ extension or module for Python in Visual Studio
caps.latest.revision: 1
author: "kraigb"
ms.author: "kraigb"
manager: "ghogen"
---

# Creating a C++ extension for Python

Modules written in C++ (or C) are commonly used to extend the capabilities of a Python interpreter as well as to enable access to low-level operating system capabilities. There are three primary types of modules:

- Accelerator modules: because Python is an interpreted language, certain pieces of code can be written in C++ for higher performance. 
- Wrapper modules: wrappers expose existing C/C++ interfaces to Python code or expose a more "Pythonic" API that's easy to use from Python.
- Low-level system access modules: created to access lower-level features of the CPython runtime, the operating system, or the underlying hardware. 

This topic walks through building a C++ extension module for CPython that computes a hyperbolic tangent and calls it from Python code. The routine is implemented first in Python to demonstrate the performance gain of implementing the same routine in C++.

The approach taken here is that for standard CPython extensions as described in the [Python documentation](https://docs.python.org/3/c-api/). A comparison between this and other means is described under [alternative approaches](#alternative-approaches) at the end of this topic.

## Prerequisites

- Visual Studio 2017 with both the **Desktop Development with C++** and **Python Development** workloads installed with default options. 
- In the **Python Development** workload, also check the box on the right for **Python native development tools**, which sets up most of the options described in this topic. (This option also includes the C++ workload automatically.) 

![Selecting the Python native development tools option](media/cpp-install-native.png)

- Installing the **Data science and analytical applications** workload also includes Python and the **Python native development tools** option by default.

For more information, see [Installing Python Support for Visual Studio](installation.md), including using other versions of Visual Studio. If you install Python separately, be sure to select **Download debugging symbols** and **Download debug binaries** under **Advanced Options** in the installer. This option ensures that you have the necessary debug libraries available if you choose to do a debug build.

## Create the Python application

1. Create a new Python project in Visual Studio by selecting **File > New > Project**. Search for "Python", select the **Python Application** template, give it a suitable name and location, and select **OK**.

1. In the project's `.py` file, paste the following code that benchmarks the computation of a hyperbolic tangent (implemented without using the math library for easier comparison). Feel free to enter the code manually to experience some of the [Python editing features](code-editing.md).

    ```python
    from itertools import islice
    from random import random
    from time import perf_counter

    COUNT = 500000  # Change this value depending on the speed of your computer
    DATA = list(islice(iter(lambda: (random() - 0.5) * 3.0, None), COUNT))

    e = 2.7182818284590452353602874713527

    def sinh(x):
        return (1 - (e ** (-2 * x))) / (2 * (e ** -x))

    def cosh(x):
        return (1 + (e ** (-2 * x))) / (2 * (e ** -x))

    def tanh(x):
        tanh_x = sinh(x) / cosh(x)
        return tanh_x

    def sequence_tanh(data):
        '''Applies the hyperbolic tangent function to map all values in
        the sequence to a value between -1.0 and 1.0.
        '''
        result = []
        for x in data:
            result.append(tanh(x))
        return result

    def test(fn, name):
        start = perf_counter()
        result = fn(DATA)
        duration = perf_counter() - start
        print('{} took {:.3f} seconds\n\n'.format(name, duration))

        for d in result:
            assert -1 <= d <=1, " incorrect values"

    if __name__ == "__main__":
        print('Running benchmarks with COUNT = {}'.format(COUNT))
        test(sequence_tanh, 'sequence_tanh')

        test(lambda d: [tanh(x) for x in d], '[tanh(x) for x in d]')
    ```

1. Run the program using **Debug > Start without Debugging** (Ctrl+F5) to see the results. You can adjust the `COUNT` variable to change how long the benchmarks take to run. For the purposes of this walkthrough, set the count so that each benchmark takes around two seconds.

## Create the core C++ project

1. Right-click the solution in Solution Explorer and select **Add > New Project...**. A Visual Studio solution can contain both Python and C++ projects together.

1. Search on "C++", select **Empty project**, specify a name (such as TanhBenchmark), and select **OK**. Note: if you've installed the **Python native development tools** with Visual Studio 2017, you can start with the **Python Extension Module** template, which has much of what's described here already in place. For this walkthrough, though, starting with an empty project demonstrates building the extension module step by step.

1. Create a C++ file in the new project by right-clicking the **Source Files** node, then select **Add > New Item..."**, select **C++ File**, give it a name (like `module.cpp`), and select **OK**. This step is necessary to turn on the C++ property pages in the next steps.

1. Right-click the new project and select **Properties**, then at the top of the **Property Pages** dialog that appears, set **Configuration** to **All Configurations**.

1. Set the specific properties as described below, then select **OK**.

    | Tab | Property | Value | 
    | --- | --- | --- |
    | General | General > Target Name | Set this field to exactly match the name of the module as Python sees it. |
    | | General > Target Extension | .pyd |
    | | Project Defaults > Configuration Type | Dynamic Library (.dll) |
    | C/C++ > General | Additional Include Directories | Add the Python `include` folder as appropriate for your installation, for example, `c:\Python36\include` |     
    | C/C++ > Preprocessor | Preprocessor Definitions | Add `Py_LIMITED_API;` to the beginning of the string, which restricts some of the functions you can call from Python and makes the code more portable between different versions of Python. |
    | C/C++ > Code Generation | Runtime Library | Multi-threaded DLL (/MD) (see Warning below) |
    | Linker > General | Additional Library Directories | Add the Python `libs` folder containing `.lib` files as appropriate for your installation, for example, `c:\Python36\libs`. (Be sure to point to the `libs` folder that contains `.lib` files, and *not* the `Lib` folder that contains `.py` files.) | 

    > [!Tip]
    > If you don't see the C/C++ tab, it's because the project doesn't contain any files that it identifies as C/C++ source files. This condition can occur if you create a source file without a `.c` or `.cpp` extension. For example, if you accidentally entered `module.coo` instead of `module.cpp` in the new item dialog earlier, then Visual Studio creates the file but doesn't set the file type to "C/C+ Code," which is what activates the C/C++ properties tab. This misidentification remains the case even if you rename the file with `.cpp`. To set the file type properly, right-click the file in Solution Explorer, select **Properties**, then set  **File Type** to **C/C++ Code**.

    > [!Warning]
    > Don't set the **C/C++ > Code Generation > Runtime Library** option to "Multi-threaded Debug DLL (/MDd)" even for a Debug configuration. Select the "Multi-threaded DLL (/MD)" runtime because that's what the non-debug Python binaries are built with. If you happen to set the /MDd option, you see error *C1189: Py_LIMITED_API is incompatible with Py_DEBUG, Py_TRACE_REFS, and Py_REF_DEBUG* when building a Debug configuration of your DLL. Furthermore, if you remove `Py_LIMITED_API` to avoid the build error, Python crashes when attempting to import the module. (The crash happens within the DLL's call to `PyModule_Create` as described later, with the output message of *Fatal Python error: PyThreadState_Get: no current thread*.)
    >
    > Note that the /MDd option is what's used to build the Python debug binaries (such as python_d.exe), but selecting it for an extension DLL still causes the build error with `Py_LIMITED_API`.
   
1. Right-click the C++ project and select **Build** to test your configurations (both Debug and Release). The `.pyd` files are located in the *solution* folder under **Debug** and **Release**, not the C++ project folder itself.

1. Add the following code to the C++ project's main `.cpp` file:

    ```cpp
    #include <Windows.h>
    #include <cmath>    

    const double e = 2.7182818284590452353602874713527;

    double sinh_impl(double x) {
        return (1 - pow(e, (-2 * x))) / (2 * pow(e, -x));
    }

    double cosh_impl(double x) {
        return (1 + pow(e, (-2 * x))) / (2 * pow(e, -x));
    }

    double tanh_impl(double x) {
        return sinh_impl(x) / cosh_impl(x);
    }
    ```

1. Build the C++ project again to confirm that your code is correct.


## Convert the C++ project to an extension for Python

To make the C++ DLL into an extension for Python, you need to modify the exported methods to interact with Python types. Then you need to add a function that exports the module, along with definitions of the module's methods. For background on what's shown here, refer to the [Python/C API Reference Manual](https://docs.python.org/3/c-api/index.html) and especially [Module Objects](https://docs.python.org/3/c-api/module.html) on python.org. (Remember to select your version of Python from the drop-down control on the upper right.)

1. In the C++ file, include `Python.h` at the top:

    ```cpp
    #include <Python.h>
    ```

1. Modify the `tanh_impl` method to accept and return Python types:

    ```cpp
    PyObject* tanh_impl(PyObject *, PyObject* o) {
        double x = PyFloat_AsDouble(o);
        double tanh_x = sinh_impl(x) / cosh_impl(x);
        return PyFloat_FromDouble(tanh_x);
    }
    ```

1. Add a structure that defines how the C++ `tanh` function is presented to Python:

    ```cpp
    static PyMethodDef superfastcode_methods[] = {
        // The first property is the name exposed to python, the second is the C++ function name        
        { "fast_tanh", (PyCFunction)tanh_impl, METH_O, nullptr },

        // Terminate the array with an object containing nulls.
        { nullptr, nullptr, 0, nullptr }
    };
    ```

1. Add a structure that defines the module as Python sees it:

    ```cpp
    static PyModuleDef superfastcode_module = {
        PyModuleDef_HEAD_INIT,
        "superfastcode",						// Module name
        "Provides some functions, but faster",  // Module description
        0,
        superfastcode_methods                   // Structure that defines the methods
    };
    ```

1. Add a method that Python calls when it loads the module, which must be named `PyInit_<module-name>`, where *&lt;module_name&gt;* exactly matches the C++ Project's **General > Target Name** property (that is, it matches the filename of the `.pyd` built by the project).

    ```cpp
    PyMODINIT_FUNC PyInit_superfastcode() {    
        return PyModule_Create(&superfastcode_module);
    }
    ```

1. Build the C++ project again to verify your code.

## Test the code and compare the results

Now that you have the DLL structured as a Python extension, you can refer to it from the Python project, import the module, and use its methods.

### Make the DLL available to Python

There are two ways to make the DLL available to Python.

First, you can add a reference from the Python project to the C++ project, provided that they're in the same Visual Studio solution:

1. In Solution Explorer, right-click the **References** node in your Python project and select **Add Reference**. In the dialog that appears, select the **Projects** tab, select the **superfastcode** project (or whatever name you're using), and then **OK**.

Second, you can install the module in the global Python environment, making it available to other Python projects as well. Doing so typically requires that you refresh the IntelliSense completion database for that environment. Refreshing is also necessary when removing the module from the environment.

1. If you're using Visual Studio 2017, run the Visual Studio installer, select **Modify**, select **Individual Components > Compilers, build tools, and runtimes > Visual C++ 2015.3 v140 toolset**. This step is necessary because Python (for Windows) is itself built with Visual Studio 2015 (version 14.0) and expects that those tools are available when building an extension through the method described here.

1. Create a file named `setup.py` in your C++ project by right-clicking the project and selecting **Add > New Item...**. Then select "C++ File (.cpp)", name the file `setup.py`, and selecting **OK** (naming the file with the `.py` extension makes Visual Studio recognize it as Python despite using the C++ file template). When the file appears in the editor, paste the following code into it:

    ```python
    from distutils.core import setup, Extension, DEBUG

    sfc_module = Extension('superfastcode', sources = ['module.cpp'])

    setup(name = 'superfastcode', version = '1.0',
        description = 'Python Package with superfastcode C++ Extension',
        ext_modules = [sfc_module]
        )
    ```

    See [Building C and C++ Extensions](https://docs.python.org/3/extending/building.html) (python.org) for documentation on this script.

1. The `setup.py` code instructs Python to build the extension using the Visual Studio 2015 C++ toolset when used from the command line. Open an elevated command prompt, navigate to the folder containing the C++ project (and `setup.py`), and enter the following command:

    ```
    pip install .
    ```

### Call the DLL from Python

After you've completed either of the methods above, you can now call the `fast_tanh` function and compare its performance to the Python implementation:

1. Add the following lines in your `.py` file to call the `fast_tanh` method exported from the DLL and display its output. If you type the `from s` statement manually, you'll see `superfastcode` come up in the completion list, and after typing `import` the `fast_tanh` method appears.

    ```python
    from superfastcode import fast_tanh    
    test(lambda d: [fast_tanh(x) for x in d], '[fast_tanh(x) for x in d]')
    ```

1. Run the Python program and see that the C++ routine runs 5 to 20 times faster than the Python implementation. Again, try increasing the `COUNT` variable so that the differences are more pronounced. Also note that a Release build of the C++ module runs faster than a Debug build because the Debug build is less optimized and contains various error checks. Feel free to switch between those configurations for comparison.

## Debug the C++ code

Visual Studio supports debugging Python and C++ code together.

1. Right-click the Python project in Solution Explorer, select **Properties**, select the **Debug** tab, and then select the **Debug > Enable native code debugging** option.

    > [!Tip]
    > When you enable native code debugging, the Python output window may disappear immediately when the program has completed without giving you the usual "Press any key to continue..." pause. To force a pause, add the `-i` option to the **Run > Interpreter Arguments** field on the **Debug** tab when you enable native code debugging. This argument puts the Python interpreter into interactive mode after the code finishes, at which point it waits for you to press Ctrl+Z, Enter to exit. (Alternately, if you don't mind modifying your Python code, you can add `import os` and `os.system("pause")` statements at the end of your program. This code duplicates the original pause prompt.)

1. Select **File > Save** to save the property changes.

1. Set the build configuration to Debug in the Visual Studio toolbar. 

    ![Setting the build configuration to Debug](media/cpp-set-debug.png)

1. Because code generally takes longer to run in the debugger, you may want to change the `COUNT` variable in your `.py` file to a value that's about 5 times smaller (for example, change it from `500000` to `100000`).

1. In your C++ code, set a breakpoint on the first line of the `tanh_impl` method, then start the debugger (F5 or **Debug > Start Debugging**). The debugger stops when that code is called. If the breakpoint is not hit, check that the configuration is set to Debug and that you've saved the project (which does not happen automatically when starting the debugger).

    ![Stopping at a breakpoint in C++ code](media/cpp-debugging.png)

1. At this point you can step through the C++ code, examine variables, and so on. These features are detailed in [Debugging C++ and Python Together](debugging-mixed-mode.md).

## Alternative approaches 

There are a variety of means to create Python extensions as described in the table below. The first entry for CPython is what's been discussed in this topic already.

| Approach | Vintage | Representative User(s) | Pro(s) | Con(s) |
| --- | --- | --- | --- | --- |
| C/C++ extension modules for CPython | 1991 | Standard Library | [Extensive documentation and tutorials](https://docs.python.org/3/c-api/). Total control. | Compilation, portability, reference management. High C knowledge. |
| SWIG | 1996 | [crfsuite](http://www.chokkan.org/software/crfsuite/) | Generate bindings for many languages at once. | Excessive overhead if Python is the only target. |
| ctypes | 2003 | [oscrypto](https://github.com/wbond/oscrypto) | No compilation, wide availability. | Accessing and mutating C structures cumbersome and error prone. |
| Cython | 2007 | [gevent](http://www.gevent.org/), [kivy](https://kivy.org/) | Python-like. Highly mature. High performance. | Compilation, new syntax and toolchain. |
| cffi | 2013 | [cryptography](https://cryptography.io/en/latest/), [pypy](http://pypy.org/) | Ease of integration, PyPy compatibility. | New, less mature. |
