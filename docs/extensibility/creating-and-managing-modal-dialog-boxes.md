---
title: Création et gestion de boîtes de dialogue modales | Microsoft Docs
description: Découvrez comment créer une boîte de dialogue modale dans Visual Studio à l’aide de DialogWindow et sans utiliser DialogWindow.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- dialog boxes, managing in Visual Studio
ms.assetid: 491bc0de-7dba-478c-a76b-923440e090f3
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 96ac3c9ee92cd9124485dde29814f4a1e5c942c8
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105055750"
---
# <a name="create-and-manage-modal-dialog-boxes"></a>Créer et gérer des boîtes de dialogue modales
Quand vous créez une boîte de dialogue modale dans Visual Studio, vous devez vous assurer que la fenêtre parente de la boîte de dialogue est désactivée pendant que la boîte de dialogue est affichée, puis réactiver la fenêtre parente après la fermeture de la boîte de dialogue. Si vous ne le faites pas, vous risquez de recevoir le message d’erreur : *Microsoft Visual Studio ne peut pas s’arrêter, car une boîte de dialogue modale est active. Fermez la boîte de dialogue active, puis réessayez.*

Il existe deux façons de procéder. La méthode recommandée, si vous avez une boîte de dialogue WPF, est de la dériver de <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> , puis <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow.ShowModal%2A> d’appeler pour afficher la boîte de dialogue. Dans ce cas, vous n’avez pas besoin de gérer l’État modal de la fenêtre parente.

Si votre boîte de dialogue n’est pas WPF ou si vous ne pouvez pas dériver votre classe de boîte de dialogue à partir de <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> , vous devez obtenir le parent de la boîte de dialogue en appelant <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.GetDialogOwnerHwnd%2A> et gérer vous-même l’État modal, en appelant la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.EnableModeless%2A> méthode avec un paramètre de 0 (false) avant d’afficher la boîte de dialogue et en appelant à nouveau la méthode avec un paramètre de 1

## <a name="create-a-dialog-box-derived-from-dialogwindow"></a>Créer une boîte de dialogue dérivée de DialogWindow

1. Créez un projet VSIX nommé **OpenDialogTest** et ajoutez une commande de menu nommée **OpenDialog**. Pour plus d’informations sur la façon de procéder, consultez [créer une extension à l’aide d’une commande de menu](../extensibility/creating-an-extension-with-a-menu-command.md).

2. Pour utiliser la <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> classe, vous devez ajouter des références aux assemblys suivants (sous l’onglet Framework de la boîte de dialogue **Ajouter une référence** ) :

    - *PresentationCore*

    - *PresentationFramework*

    - *WindowsBase*

    - *System.Xaml*

3. Dans *OpenDialog. cs*, ajoutez l' `using` instruction suivante :

    ```csharp
    using Microsoft.VisualStudio.PlatformUI;
    ```

4. Déclarez une classe nommée `TestDialogWindow` qui dérive de <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> :

    ```csharp
    class TestDialogWindow : DialogWindow
    {. . .}
    ```

5. Pour pouvoir réduire et agrandir la boîte de dialogue, définissez <xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasMaximizeButton%2A> et <xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasMinimizeButton%2A> sur true :

    ```csharp
    internal TestDialogWindow()
    {
        this.HasMaximizeButton = true;
        this.HasMinimizeButton = true;
    }
    ```

6. Dans la `OpenDialog.ShowMessageBox` méthode, remplacez le code existant par ce qui suit :

    ```csharp
    TestDialogWindow testDialog = new TestDialogWindow();
    testDialog.ShowModal();
    ```

7. Générez et exécutez l’application. L’instance expérimentale de Visual Studio doit apparaître. Dans le menu **Outils** de l’instance expérimentale, vous devez voir une commande appelée **appeler OpenDialog**. Lorsque vous cliquez sur cette commande, la fenêtre de dialogue doit s’afficher. Vous devez être en mesure de réduire et d’agrandir la fenêtre.

## <a name="create-and-manage-a-dialog-box-not-derived-from-dialogwindow"></a>Créer et gérer une boîte de dialogue non dérivée de DialogWindow

1. Pour cette procédure, vous pouvez utiliser la solution **OpenDialogTest** que vous avez créée dans la procédure précédente, avec les mêmes références d’assembly.

2. Ajoutez les `using` déclarations suivantes :

    ```csharp
    using System.Windows;
    using Microsoft.Internal.VisualStudio.PlatformUI;
    ```

3. Créez une classe nommée `TestDialogWindow2` qui dérive de <xref:System.Windows.Window> :

    ```csharp
    class TestDialogWindow2 : Window
    {. . .}
    ```

4. Ajoutez une référence privée à <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> :

    ```
    private IVsUIShell shell;
    ```

5. Ajoutez un constructeur qui définit la référence à <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> :

    ```csharp
    public TestDialogWindow2(IVsUIShell uiShell)
    {
        shell = uiShell;
    }
    ```

6. Dans la `OpenDialog.ShowMessageBox` méthode, remplacez le code existant par ce qui suit :

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

7. Générez et exécutez l’application. Dans le menu **Outils** , vous devez voir une commande appelée **appeler OpenDialog**. Lorsque vous cliquez sur cette commande, la fenêtre de dialogue doit s’afficher.
