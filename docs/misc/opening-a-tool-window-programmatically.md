---
title: "Ouverture d’une fen&#234;tre Outil par programmation | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "fenêtres Outil, créer par programmation"
ms.assetid: 0017441e-7aa3-4a61-9939-57af11d90d97
caps.latest.revision: 16
caps.handback.revision: 16
manager: "douge"
---
# Ouverture d’une fen&#234;tre Outil par programmation
Pour ouvrir les fenêtres Outil, il suffit généralement de cliquer sur une commande d’un menu ou d’appuyer sur un raccourci clavier équivalent. Toutefois, vous devrez peut\-être ouvrir une fenêtre Outil par programmation, comme le fait le gestionnaire de commandes.  
  
 Pour ouvrir une fenêtre Outil dans le package géré Visual Studio qui la fournit, utilisez <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A>. Pour ouvrir une fenêtre Outil dans un autre package Visual Studio, utilisez <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.FindToolWindow%2A>. Dans les deux cas, la fenêtre Outil est créée en fonction des besoins.  
  
 Le code suivant provient de l’exemple C\# Reference.ToolWindow.  
  
### Pour ouvrir une fenêtre Outil par programmation  
  
1.  Créez le volet de fenêtre Outil, le frame et le package Visual Studio qui les implémente. Pour plus d'informations, consultez [Ajout d’une fenêtre outil](../extensibility/adding-a-tool-window.md).  
  
2.  Ajoutez le <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> au package Visual Studio qui le fournit.  
  
    ```c#  
    [ProvideToolWindow(typeof(PersistedWindowPane), Style = VsDockStyle.Tabbed, Window = "3ae79031-e1bc-11d0-8f78-00a0c9110057")] [ProvideMenuResource(1000, 1)] [MsVsShell.DefaultRegistryRoot(@"Software\Microsoft\VisualStudio\8.0Exp")] [PackageRegistration(UseManagedResourcesOnly = true)] [Guid("01069CDD-95CE-4620-AC21-DDFF6C57F012")] // your package will have a different GUID public class PackageToolWindow : Package {  
    ```  
  
     Cela inscrit le PersistedWindowPane de la fenêtre Outil à ouvrir comme ancré à l’**Explorateur de solutions**. Pour plus d'informations, consultez [L’inscription d’une fenêtre outil](../extensibility/registering-a-tool-window.md).  
  
3.  Utilisez <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> pour trouver le volet de fenêtre Outil ou le créer s’il n’existe pas déjà.  
  
    ```vb#  
    ' Get the 1 (index 0) and only instance of our tool window. ' If it does not already exist it will get created. Dim pane As MsVsShell.ToolWindowPane = Me.FindToolWindow(GetType(PersistedWindowPane), 0, True) If pane Is Nothing Then End If  
  
    ```  
  
    ```c#  
    // Get the 1 (index 0) and only instance of our tool window. // If it does not already exist it will get created. MsVsShell.ToolWindowPane pane =     this.FindToolWindow(typeof(PersistedWindowPane), 0, true); if (pane == null) {  
    ```  
  
4.  Obtenez le frame de la fenêtre Outil à partir du volet de la fenêtre Outil.  
  
    ```vb#  
    Dim frame As IVsWindowFrame = TryCast(pane.Frame, IVsWindowFrame) If frame Is Nothing Then End If  
  
    ```  
  
    ```c#  
    IVsWindowFrame frame = pane.Frame as IVsWindowFrame; if (frame == null) {  
    ```  
  
5.  Affichez la fenêtre Outil.  
  
    ```vb#  
    ' Bring the tool window to the front and give it focus ErrorHandler.ThrowOnFailure(frame.Show())  
  
    ```  
  
    ```c#  
    // Bring the tool window to the front and give it focus ErrorHandler.ThrowOnFailure(frame.Show());  
    ```