---
title: "Command Handling | Microsoft Docs"
ms.date: "11/04/2016"
ms.topic: "conceptual"
helpviewer_keywords:
  - "editors [Visual Studio SDK], legacy - command handling"
ms.assetid: 78f67d92-77f7-45cb-ad75-6e3346379cc3
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
  - "vssdk"
---
# Command handling
Your editor can define new commands. Commands are typically displayed in a menu, on a toolbar, or in a context menu.

 For more information about defining commands and menus, see [Commands, menus, and toolbars](../extensibility/internals/commands-menus-and-toolbars.md).

 A language service can control what context menus are shown in the editor, by intercepting the <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> enumeration. Alternately, you can control the context menu on a per-marker basis. For more information, see [Important commands for Language Service filters](../extensibility/internals/important-commands-for-language-service-filters.md).

## Add commands to the editor context menu
 To add a command to the context menu, you must first define a set of menu commands belonging to a specific group. The following example is taken from the *.vsct* file generated as a part of the walkthrough [Walkthrough: Add features to a custom editor](../extensibility/walkthrough-adding-features-to-a-custom-editor.md):

 \<Menu guid="guidCustomEditorCmdSet" id="IDMX_RTF" priority="0x0000" type="Context">

 \<Parent guid="guidCustomEditorCmdSet" id="0"/>

 \<Strings>

 \<ButtonText>CustomEditor Context Menu\</ButtonText>

 \<CommandName>CustomEditorContextMenu\</CommandName>

 \</Strings>

 \</Menu>

 \</Menus>

 The above text adds a context menu command with the text **CustomEditor Context Menu**. The Menu GUID is part of the command set that is created with this editor. The type is "Context".

 You can also use predefined commands that don't need to be defined in the *.vsct* file. For example, examine the *EditorPane.cs* file generated by the Visual Studio Package template. You will find that a set of predefined commands, such as <xref:Microsoft.VisualStudio.VSConstants.VSStd97CmdID> defined by <xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>, are handled in command handlers such as the `onSelectAll` method.

## See also
- [Commands, menus, and toolbars](../extensibility/internals/commands-menus-and-toolbars.md)