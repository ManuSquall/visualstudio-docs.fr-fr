---
title: Créer et gérer des boîtes de dialogue modales | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dialog boxes, managing in Visual Studio
ms.assetid: 491bc0de-7dba-478c-a76b-923440e090f3
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dfd0fb71aaca9cb3de2d7cc6d3b6229042a4e7fa
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62926404"
---
# <a name="create-and-manage-modal-dialog-boxes"></a>Créer et gérer des boîtes de dialogue modales
Lorsque vous créez une boîte de dialogue modale dans Visual Studio, vous devez vous assurer que la fenêtre parente de la boîte de dialogue est désactivée lorsque la boîte de dialogue s’affiche, puis réactiver la fenêtre parente après la fermeture de la boîte de dialogue. Si vous ne le faites pas, vous pouvez recevoir l’erreur : *Microsoft Visual Studio ne peut pas arrêter, car une boîte de dialogue modale est active. Fermez la boîte de dialogue et réessayez.*

Il existe deux façons d’effectuer cette opération. Si vous avez une boîte de dialogue WPF, il est recommandé de dériver à partir <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>, puis appelez <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow.ShowModal%2A> pour afficher la boîte de dialogue. Si vous procédez ainsi, il est inutile de gérer l’état modal de la fenêtre parente.

Si votre boîte de dialogue n’est pas WPF, ou pour une autre raison, vous ne pouvez pas dériver votre boîte de dialogue classe <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>, vous devez obtenir le parent de la boîte de dialogue en appelant <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.GetDialogOwnerHwnd%2A> et gérer l’état modal vous-même, en appelant le <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.EnableModeless%2A> méthode avec un paramètre de 0 (false) avant d’afficher la boîte de dialogue et en appelant la méthode avec un paramètre de 1 (true) après la fermeture de la boîte de dialogue.

## <a name="create-a-dialog-box-derived-from-dialogwindow"></a>Créer une boîte de dialogue dérivée de DialogWindow

1. Créez un projet VSIX nommé **OpenDialogTest** et ajoutez une commande de menu nommée **OpenDialog**. Pour plus d’informations sur la procédure à suivre, consultez [créer une extension avec une commande de menu](../extensibility/creating-an-extension-with-a-menu-command.md).

2. Pour utiliser le <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> (classe), vous devez ajouter des références aux assemblys suivants (dans l’onglet Framework de la **ajouter une référence** boîte de dialogue) :

    - *PresentationCore*

    - *PresentationFramework*

    - *WindowsBase*

    - *System.Xaml*

3. Dans *OpenDialog.cs*, ajoutez le code suivant `using` instruction :

    ```csharp
    using Microsoft.VisualStudio.PlatformUI;
    ```

4. Déclarez une classe nommée `TestDialogWindow` qui dérive de <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>:

    ```csharp
    class TestDialogWindow : DialogWindow
    {. . .}
    ```

5. Pour être en mesure de réduire ou agrandir la boîte de dialogue, définissez <xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasMaximizeButton%2A> et <xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasMinimizeButton%2A> sur true :

    ```csharp
    internal TestDialogWindow()
    {
        this.HasMaximizeButton = true;
        this.HasMinimizeButton = true;
    }
    ```

6. Dans le `OpenDialog.ShowMessageBox` (méthode), remplacez le code existant par le code suivant :

    ```csharp
    TestDialogWindow testDialog = new TestDialogWindow();
    testDialog.ShowModal();
    ```

7. Générez et exécutez l’application. L’instance expérimentale de Visual Studio doit apparaître. Sur le **outils** menu de l’instance expérimentale, vous devez voir une commande nommée **OpenDialog appeler**. Lorsque vous cliquez sur cette commande, vous devez voir la boîte de dialogue. Vous pourrez réduire et agrandir la fenêtre.

## <a name="create-and-manage-a-dialog-box-not-derived-from-dialogwindow"></a>Créer et gérer une boîte de dialogue non dérivée de DialogWindow

1. Pour cette procédure, vous pouvez utiliser la **OpenDialogTest** solution que vous avez créé dans la procédure précédente, avec les mêmes références d’assembly.

2. Ajoutez le code suivant `using` déclarations :

    ```csharp
    using System.Windows;
    using Microsoft.Internal.VisualStudio.PlatformUI;
    ```

3. Créez une classe nommée `TestDialogWindow2` qui dérive de <xref:System.Windows.Window>:

    ```csharp
    class TestDialogWindow2 : Window
    {. . .}
    ```

4. Ajouter une référence privée à <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>:

    ```
    private IVsUIShell shell;
    ```

5. Ajoutez un constructeur qui définit la référence à <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>:

    ```csharp
    public TestDialogWindow2(IVsUIShell uiShell)
    {
        shell = uiShell;
    }
    ```

6. Dans le `OpenDialog.ShowMessageBox` (méthode), remplacez le code existant par le code suivant :

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

7. Générez et exécutez l’application. Sur le **outils** menu, vous devez voir une commande nommée **OpenDialog appeler**. Lorsque vous cliquez sur cette commande, vous devez voir la boîte de dialogue.
