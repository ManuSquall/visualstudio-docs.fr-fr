---
title: "Créer et gérer des boîtes de dialogue modales | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dialog boxes, managing in Visual Studio
ms.assetid: 491bc0de-7dba-478c-a76b-923440e090f3
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 1bb0372ab217847f91b1cdeeb8cf2915379e2f66
ms.lasthandoff: 02/22/2017

---
# <a name="creating-and-managing-modal-dialog-boxes"></a>Créer et gérer des boîtes de dialogue modales
Lorsque vous créez une boîte de dialogue modale à l’intérieur de Visual Studio, vous devez vous assurer que la fenêtre parente de la boîte de dialogue est désactivée lorsque la boîte de dialogue est affichée, puis réactiver la fenêtre parente après la fermeture de la boîte de dialogue. Si vous ne le faites pas, vous pouvez recevoir l’erreur : « Microsoft Visual Studio ne peut pas s’est arrêté, car une boîte de dialogue modale est active. Fermez la boîte de dialogue et réessayez. »  
  
 Il existe deux façons de procéder. La méthode recommandée, si vous disposez d’une boîte de dialogue WPF doit dériver de <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>, puis appelez <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow.ShowModal%2A>pour afficher la boîte de dialogue.</xref:Microsoft.VisualStudio.PlatformUI.DialogWindow.ShowModal%2A> </xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> Si vous le faites, il est inutile de gérer l’état modal de la fenêtre parente.  
  
 Si votre boîte de dialogue n’est pas WPF, ou pour une autre raison, vous ne pouvez pas dériver votre boîte de dialogue classe <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>, vous devez obtenir le parent de la boîte de dialogue en appelant <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.GetDialogOwnerHwnd%2A>et gérer l’état modal vous-même, en appelant le <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.EnableModeless%2A>méthode avec un paramètre de 0 (false) avant d’afficher la boîte de dialogue et en appelant la méthode avec un paramètre de 1 (true) après la fermeture de la boîte de dialogue.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.EnableModeless%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.GetDialogOwnerHwnd%2A> </xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>  
  
## <a name="creating-a-dialog-box-derived-from-dialogwindow"></a>Création d’une boîte de dialogue dérivée de DialogWindow  
  
1.  Créez un projet VSIX nommé **OpenDialogTest** et ajoutez une commande de menu nommée **OpenDialog**. Pour plus d’informations, consultez [avec une commande de Menu pour créer une Extension](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2.  Pour utiliser le <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>(classe), vous devez ajouter des références aux assemblys suivants (dans l’onglet cadre de la **ajouter une référence** boîte de dialogue) :</xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>  
  
    -   PresentationCore  
  
    -   PresentationFramework  
  
    -   WindowsBase  
  
    -   System.Xaml  
  
3.  Dans OpenDialog.cs, ajoutez le code suivant `using` instruction :  
  
    ```c#  
    using Microsoft.VisualStudio.PlatformUI;  
    ```  
  
4.  Déclarez une classe nommée **TestDialogWindow** qui dérive de <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>:</xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>  
  
    ```c#  
    class TestDialogWindow : DialogWindow  
    {. . .}  
    ```  
  
5.  Pour pouvoir réduire ou agrandir la boîte de dialogue, définissez <xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasMaximizeButton%2A>et <xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasMinimizeButton%2A>sur true :</xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasMinimizeButton%2A> </xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasMaximizeButton%2A>  
  
    ```c#  
    internal TestDialogWindow()  
    {  
        this.HasMaximizeButton = true;  
        this.HasMinimizeButton = true;  
    }  
    ```  
  
6.  Dans le **OpenDialog.ShowMessageBox** (méthode), remplacez le code existant par le code suivant :  
  
    ```c#  
    TestDialogWindow testDialog = new TestDialogWindow();  
    testDialog.ShowModal();  
    ```  
  
7.  Générez et exécutez l’application. L’instance expérimentale de Visual Studio doit s’afficher. Sur le **outils** menu de l’instance expérimentale, vous devez voir une commande nommée **OpenDialog appeler**. Lorsque vous cliquez sur cette commande, vous devez voir la boîte de dialogue. Vous devez pouvoir réduire ou agrandir la fenêtre.  
  
## <a name="creating-and-managing-a-dialog-box-not-derived-from-dialogwindow"></a>Création et gestion d’une boîte de dialogue non dérivée DialogWindow  
  
1.  Pour cette procédure, vous pouvez utiliser la **OpenDialogTest** solution que vous avez créé dans la procédure précédente, avec les mêmes références d’assembly.  
  
2.  Ajoutez le code suivant `using` déclarations :  
  
    ```c#  
    using System.Windows;  
    using Microsoft.Internal.VisualStudio.PlatformUI;  
    ```  
  
3.  Créez une classe nommée **TestDialogWindow2** qui dérive de <xref:System.Windows.Window>:</xref:System.Windows.Window>  
  
    ```c#  
    class TestDialogWindow2 : Window  
    {. . .}  
    ```  
  
4.  Ajoutez une référence privée à <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>:</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>  
  
    ```  
    private IVsUIShell shell;  
    ```  
  
5.  Ajoutez un constructeur qui définit la référence à <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>:</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>  
  
    ```c#  
    public TestDialogWindow2(IVsUIShell uiShell)  
    {  
        shell = uiShell;  
    }  
    ```  
  
6.  Dans le **OpenDialog.ShowMessageBox** (méthode), remplacez le code existant par le code suivant :  
  
    ```c#  
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
  
7.  Générez et exécutez l’application. Sur le **outils** menu, vous devez voir une commande nommée **OpenDialog appeler**. Lorsque vous cliquez sur cette commande, vous devez voir la boîte de dialogue.
