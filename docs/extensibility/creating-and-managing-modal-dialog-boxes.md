---
title: Création et gestion des boîtes de dialogue modal (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dialog boxes, managing in Visual Studio
ms.assetid: 491bc0de-7dba-478c-a76b-923440e090f3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 786a2fbe2b75c51420668eb1ab6f596213d3da9b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739498"
---
# <a name="create-and-manage-modal-dialog-boxes"></a>Créer et gérer des boîtes de dialogue modal
Lorsque vous créez une boîte de dialogue modal à l’intérieur de Visual Studio, vous devez vous assurer que la fenêtre parente de la boîte de dialogue est désactivée pendant que la boîte de dialogue est affichée, puis ré-activer la fenêtre parente après la boîte de dialogue est fermée. Si vous ne le faites pas, vous pouvez recevoir l’erreur: *Microsoft Visual Studio ne peut pas s’arrêter parce qu’un dialogue modal est actif. Fermez le dialogue actif et réessayez.*

Il y a deux façons de le faire. La façon recommandée, si vous avez une boîte de <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>dialogue WPF, est de le tirer de , puis appeler <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow.ShowModal%2A> pour afficher la boîte de dialogue. Si vous faites cela, vous n’avez pas besoin de gérer l’état modal de la fenêtre parente.

Si votre boîte de dialogue n’est pas WPF, ou pour <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>une autre raison que vous ne pouvez <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.GetDialogOwnerHwnd%2A> pas tirer votre classe boîte de <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.EnableModeless%2A> dialogue de , alors vous devez obtenir le parent de la boîte de dialogue en appelant et gérer l’état modal vous-même, en appelant la méthode avec un paramètre de 0 (faux) avant d’afficher la boîte de dialogue et d’appeler la méthode à nouveau avec un paramètre de 1 (vrai) après la fermeture de la boîte de dialogue.

## <a name="create-a-dialog-box-derived-from-dialogwindow"></a>Créer une boîte de dialogue dérivée de DialogWindow

1. Créez un projet VSIX nommé **OpenDialogTest** et ajoutez une commande de menu nommée **OpenDialog**. Pour plus d’informations sur la façon de le faire, voir [Créer une extension avec une commande de menu](../extensibility/creating-an-extension-with-a-menu-command.md).

2. Pour utiliser <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> la classe, vous devez ajouter des références aux assemblages suivants (dans l’onglet Cadre de la boîte de dialogue **Add Reference):**

    - *PresentationCore*

    - *PresentationFramework*

    - *WindowsBase*

    - *System.Xaml*

3. Dans *OpenDialog.cs*, ajouter la `using` déclaration suivante:

    ```csharp
    using Microsoft.VisualStudio.PlatformUI;
    ```

4. Déclarez une `TestDialogWindow` classe nommée <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>qui dérive de :

    ```csharp
    class TestDialogWindow : DialogWindow
    {. . .}
    ```

5. Pour être en mesure de minimiser et <xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasMaximizeButton%2A> <xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasMinimizeButton%2A> de maximiser la boîte de dialogue, ensemble et à vrai:

    ```csharp
    internal TestDialogWindow()
    {
        this.HasMaximizeButton = true;
        this.HasMinimizeButton = true;
    }
    ```

6. Dans `OpenDialog.ShowMessageBox` la méthode, remplacez le code existant par les éléments suivants :

    ```csharp
    TestDialogWindow testDialog = new TestDialogWindow();
    testDialog.ShowModal();
    ```

7. Générez et exécutez l’application. L’exemple expérimental de Visual Studio devrait apparaître. Sur le menu **Outils** de l’instance expérimentale, vous devriez voir une commande nommée **Invoke OpenDialog**. Lorsque vous cliquez sur cette commande, vous devriez voir la fenêtre de dialogue. Vous devriez être en mesure de minimiser et de maximiser la fenêtre.

## <a name="create-and-manage-a-dialog-box-not-derived-from-dialogwindow"></a>Créer et gérer une boîte de dialogue non dérivée de DialogWindow

1. Pour cette procédure, vous pouvez utiliser la solution **OpenDialogTest** que vous avez créée dans la procédure précédente, avec les mêmes références d’assemblage.

2. Ajouter les `using` déclarations suivantes :

    ```csharp
    using System.Windows;
    using Microsoft.Internal.VisualStudio.PlatformUI;
    ```

3. Créer une `TestDialogWindow2` classe nommée <xref:System.Windows.Window>qui dérive de :

    ```csharp
    class TestDialogWindow2 : Window
    {. . .}
    ```

4. Ajoutez une référence <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>privée à :

    ```
    private IVsUIShell shell;
    ```

5. Ajouter un constructeur qui définit <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>la référence à :

    ```csharp
    public TestDialogWindow2(IVsUIShell uiShell)
    {
        shell = uiShell;
    }
    ```

6. Dans `OpenDialog.ShowMessageBox` la méthode, remplacez le code existant par les éléments suivants :

    ```csharp
    IVsUIShell uiShell = (IVsUIShell)ServiceProvider.GetService(typeof(SVsUIShell));

    TestDialogWindow2 testDialog2 = new TestDialogWindow2(uiShell);
    //get the owner of this dialog
    IntPtr hwnd;
    uiShell.GetDialogOwnerHwnd(out hwnd);
    testDialog2.WindowStartupLocation = System.Windows.WindowStartupLocation.CenterOwner;
    uiShell.EnableModeless(0);
    try
    {
        WindowHelper.ShowModal(testDialog2, hwnd);
    }
    finally
    {
        // This will take place after the window is closed.
        uiShell.EnableModeless(1);
    }
    ```

7. Générez et exécutez l’application. Sur le menu **Tools,** vous devriez voir une commande nommée **Invoke OpenDialog**. Lorsque vous cliquez sur cette commande, vous devriez voir la fenêtre de dialogue.
