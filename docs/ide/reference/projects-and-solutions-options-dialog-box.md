---
title: "Projects and Solutions, Options Dialog Box | Microsoft Docs"
ms.custom: ""
ms.date: 7/14/2017
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.ToolsOptionsPages.Projects.General"
  - "VS.ToolsOptionsPages.Projects.Locations"
helpviewer_keywords: 
  - "Projects and Solutions Options dialog box"
  - "Options dialog box, Projects and Solutions"
ms.assetid: 2801f24e-a138-488a-ae3c-e1f99a678ac0
caps.latest.revision: 12
author: "gewarren"
ms.author: "gewarren"
manager: "ghogen"
---
# Projects and Solutions, Options Dialog Box

Sets [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] behavior related to projects and solutions. To access these options, select **Tools > Options** expand **Projects and Solutions**, and click **General**.

The default paths for project and template folders are set through the **Locations** tab in the same dialog box.
  
> [!NOTE]
>  The options available in dialog boxes, and the names and locations of menu commands you see, might differ from what is described in Help depending on your active settings or edition. This Help page was written with the **General Development settings** in mind. To view or change your settings, choose **Import and Export Settings** on the **Tools** menu. For more information, see [Personalize the Visual Studio IDE](../../ide/personalizing-the-visual-studio-ide.md).  
  
## General tab options  
 
**Lightweight Solution Load**
Reduces the amount of time and memory required to load large solutions in the IDE. Large solutions containing many C#, Visual Basic, or C++ projects are likely to see a substantial performance benefit using lightweight solution load.

- **Let Visual Studio choose what's best for my solution**: Lets Visual Studio automatically determine whether to apply Lightweight solution load based on the characteristics of the solution.
- **Enabled**: Always applies Lightweight solution load when loading solutions.
- **Disabled**: Never applies Lightweight solution load.

For more information, see [Optimize Visual Studio Startup Time](../optimize-visual-studio-startup-time.md#speed_up_solution_load)

**Always show Error List if build finishes with errors**  
Opens the **Error List** window on build completion, only if a project failed to build. Errors that occur during the build process are displayed. When this option is cleared, the errors still occur but the window does not open when the build is complete. This option is enabled by default.  

**Track Active Item in Solution Explorer**  
When selected, **Solution Explorer** automatically opens and the active item is selected. The selected item changes as you work with different files in a project or solution, or different components in a designer. When this option is cleared, the selection in **Solution Explorer** does not change automatically. This option is enabled by default.  

**Show advanced build configurations**  
When selected, the build configuration options appear on the **Project Property Pages** dialog box and the **Solution Property Pages** dialog box. When cleared, the build configuration options do not appear on the **Project Property Pages** dialog box and the **Solution Property Pages** dialog box for [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] and [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] projects that contain one configuration or the two configurations debug and release. If a project has a user-defined configuration, the build configuration options are shown.  

When unselected, the commands on the **Build** menu, such as **Build Solution**, **Rebuild Solution**, and **Clean Solution**, are performed on the Release configuration and the commands on the **Debug** menu, such as **Start Debugging** and **Start Without Debugging**, are performed on the Debug configuration.  

**Always show solution**  
When selected, the solution and all commands that act on solutions are always shown in the IDE. When cleared, all projects are created as stand-alone projects and you do not see the solution in Solution Explorer or commands that act on solutions in the IDE if the solution contains only one project.  

**Save new projects when created**  
When selected, you can specify a location for your project in the **New Project** dialog box. When cleared, all new projects are created as temporary projects. When you are working with temporary projects, you can create and experiment with a project without having to specify a disk location.  

**Warn user when the project location is not trusted**  
If you attempt to create a new project or open an existing project in a location that is not fully trusted (for example, on a UNC path or an HTTP path), a message is displayed. Use this option to specify whether the message is displayed each time that you attempt to create or open a project in a location that is not fully trusted.  

**Show Output window when build starts**  
Automatically displays the Output Window in the IDE at the outset of solution builds. For more information, see [How to: Control the Output Window](http://msdn.microsoft.com/Library/91aebd15-8854-4a7a-9f7d-57376fb4e858).

**Prompt for symbolic renaming when renaming files**  
When selected, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] displays a message box asking whether or not it should also rename all references in the project to the code element.  

**Prompt before moving files to a new location**  
When selected, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] displays a confirmation message box before the locations of files are changed by actions in Solution Explorer. 

## Locations tab options

**Projects location**  
Specifies the default location where [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] creates new projects and solution folders. Several dialog boxes also use the location set in this option for folder starting points. For example, the Open Project dialog box uses this location for the My Projects shortcut.  

**User project templates location**  
Specifies the default location that the **New Project** dialog box uses to create the list of **My Templates**. For more information, see [How to: Locate and Organize Templates](../../ide/how-to-locate-and-organize-project-and-item-templates.md).  

**User item templates location**  
Specifies the default location that the **Add New Item** dialog box uses to create the list of **My Templates**. For more information, see [How to: Locate and Organize Templates](../../ide/how-to-locate-and-organize-project-and-item-templates.md). 

## See Also  
- [Options Dialog Box,  Projects and Solutions, Build and Run](../../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md)
- - [Options Dialog Box,  Projects and Solutions, Web Projects](../../ide/reference/options-dialog-box-projects-and-solutions-web-projects.md)