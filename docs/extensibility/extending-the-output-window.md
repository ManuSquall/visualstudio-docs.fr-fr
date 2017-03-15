---
title: "Extension de la fen&#234;tre Sortie | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Fenêtre Sortie, à propos de la fenêtre Sortie"
ms.assetid: b02fa88c-f92a-4ff6-ba5f-2eb4d48a643a
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# Extension de la fen&#234;tre Sortie
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le **sortie** fenêtre est un ensemble de volets de texte en lecture\/écriture. Visual Studio propose ces volets intégrés : **Build**, dans les projets de communication des messages sur les builds, et **Général**, dans lequel [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] communique les messages de l'IDE. Projets d'obtenir une référence à la **Générer** automatiquement par le biais du volet le <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> méthodes d'interface et Visual Studio offre un accès direct à la **Général** volet via le <xref:Microsoft.VisualStudio.Shell.Interop.SVsGeneralOutputWindowPane> service. Outre les volets intégrés, vous pouvez créer et gérer vos propres volets personnalisés.  
  
 Vous pouvez contrôler le **sortie** directement par le biais de la fenêtre du <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> et <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> interfaces. Le <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> interface, ce qui est proposé par le <xref:Microsoft.VisualStudio.Shell.Interop.SVsOutputWindow> service, définit des méthodes pour la création, la récupération et la destruction **sortie** volets de fenêtre. Le <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> interface définit des méthodes pour afficher des volets, masquer des volets et la manipulation de leur texte. Une autre façon de contrôler les **sortie** fenêtre s'effectue via le <xref:EnvDTE.OutputWindow> et <xref:EnvDTE.OutputWindowPane> objets dans le modèle d'objet Automation Visual Studio. Ces objets encapsulent presque toutes les fonctionnalités de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> et <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> interfaces. En outre, le <xref:EnvDTE.OutputWindow> et <xref:EnvDTE.OutputWindowPane> objets ajoutent des fonctionnalités de niveau supérieur pour le rendre plus facile à énumérer les **sortie** volets de fenêtre et de récupérer du texte dans les volets.  
  
## Création d'une Extension qui utilise le volet de sortie  
 Vous pouvez créer une extension qui utilise différents aspects du volet de sortie.  
  
1.  Créez un projet VSIX nommé `TestOutput` avec une commande de menu nommé **RésultatTest**. Pour plus d'informations, consultez [Création d'une Extension avec une commande de Menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2.  Ajoutez les références suivantes :  
  
    1.  EnvDTE  
  
    2.  EnvDTE80  
  
3.  Dans TestOutput.cs, ajoutez l'instruction using :  
  
    ```f#  
    using EnvDTE; using EnvDTE80;  
    ```  
  
4.  Dans TestOutput.cs, supprimez la méthode ShowMessageBox. Ajoutez le stub de méthode suivantes :  
  
    ```c#  
    private void OutputCommandHandler(object sender, EventArgs e) { }  
    ```  
  
5.  Dans le constructeur de RésultatTest, modifiez le Gestionnaire de commandes à OutputCommandHandler. Voici la partie qui ajoute les commandes :  
  
    ```c#  
    OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService; if (commandService != null) { CommandID menuCommandID = new CommandID(MenuGroup, CommandId); EventHandler eventHandler = OutputCommandHandler; MenuCommand menuItem = new MenuCommand(eventHandler, menuCommandID); commandService.AddCommand(menuItem); }  
    ```  
  
6.  Les sections ci\-dessous proposent des méthodes qui montrent différentes manières de traiter avec le volet de sortie. Vous pouvez appeler ces méthodes au corps de la méthode OutputCommandHandler\(\). Par exemple, le code suivant ajoute la méthode CreatePane\(\) donnée dans la section suivante.  
  
    ```c#  
    private void OutputCommandHandler(object sender, EventArgs e) { CreatePane(new Guid(), "Created Pane", true, false); }  
    ```  
  
## Création d'une fenêtre de sortie avec IVsOutputWindow  
 Cet exemple montre comment créer un nouveau **sortie** volet de fenêtre à l'aide de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> interface.  
  
```c#  
void CreatePane(Guid paneGuid, string title, bool visible, bool clearWithSolution) { IVsOutputWindow output = (IVsOutputWindow)GetService(typeof(SVsOutputWindow)); IVsOutputWindowPane pane; // Create a new pane. output.CreatePane( ref paneGuid, title, Convert.ToInt32(visible), Convert.ToInt32(clearWithSolution)); // Retrieve the new pane. output.GetPane(ref paneGuid, out pane); pane.OutputString("This is the Created Pane \n"); }  
```  
  
 Si vous ajoutez cette méthode à l'extension indiquée dans la section précédente, lorsque vous cliquez sur le **RésultatTest appeler** commande doit s'afficher le **sortie** fenêtre avec un en\-tête indiquant **Afficher la sortie à partir de : CreatedPane** et les mots **il s'agit du volet Création** dans le volet de lui\-même.  
  
## Création d'une fenêtre de sortie avec OutputWindow  
 Cet exemple montre comment créer un **sortie** volet de fenêtre à l'aide de la <xref:EnvDTE.OutputWindow> objet.  
  
```c#  
void CreatePane(string title) { DTE2 dte = (DTE2)GetService(typeof(DTE)); OutputWindowPanes panes = dte.ToolWindows.OutputWindow.OutputWindowPanes; try { // If the pane exists already, write to it. panes.Item(title); } catch (ArgumentException) { // Create a new pane and write to it. return panes.Add(title); } }  
```  
  
 Bien que le <xref:EnvDTE.OutputWindowPanes> collection vous permet de récupérer un **sortie** volet de fenêtre par son titre, le titre des volets n'est pas garanti pour être unique. Lorsque vous douter de l'unicité d'un titre, utilisez la <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow.GetPane%2A> méthode pour récupérer le volet correct par son GUID.  
  
 Si vous ajoutez cette méthode à l'extension indiquée dans la section précédente, lorsque vous cliquez sur le **RésultatTest appeler** commande, vous devez voir la fenêtre de sortie avec un en\-tête indiquant **Afficher la sortie à partir de : DTEPane** et les mots **ajouté le volet DTE** dans le volet de lui\-même.  
  
## Suppression d'une fenêtre de sortie  
 Cet exemple montre comment supprimer une **sortie** volet de fenêtre.  
  
```c#  
void DeletePane(Guid paneGuid) { IVsOutputWindow output = (IVsOutputWindow)ServiceProvider.GetService(typeof(SVsOutputWindow)); IVsOutputWindowPane pane; output.GetPane(ref paneGuid, out pane); if (pane == null) { CreatePane(paneGuid, "New Pane\n", true, true); } else { output.DeletePane(ref paneGuid); } }  
```  
  
 Si vous ajoutez cette méthode à l'extension indiquée dans la section précédente, lorsque vous cliquez sur le **RésultatTest appeler** commande, vous devez voir la fenêtre de sortie avec un en\-tête indiquant **Afficher la sortie à partir de : nouveau volet** et les mots **ajouté le volet Création** dans le volet de lui\-même. Si vous cliquez sur le **RésultatTest appeler** de commande, celui\-ci est supprimé.  
  
## Mise en route le volet Général de la fenêtre Sortie  
 Cet exemple montre comment obtenir l'intégrée **Général** volet de la **sortie** fenêtre.  
  
```c#  
void GetGeneralPane() { return (IVsOutputWindowPane)GetService( typeof(SVsGeneralOutputWindowPane)); }  
```  
  
 Si vous ajoutez cette méthode à l'extension indiquée dans la section précédente, lorsque vous cliquez sur le **RésultatTest appeler** commande, vous devez voir que la **sortie** fenêtre montre les mots **volet trouvé général** dans le volet.  
  
## Mise en route au volet Build de la fenêtre Sortie  
 Cet exemple montre comment rechercher le volet Création et d'écriture. Étant donné que le volet de la Build n'est pas activé par défaut, il l'active d'également.  
  
```c#  
void OutputTaskItemStringExExample(string buildMessage) { EnvDTE80.DTE2 dte = (EnvDTE80.DTE2)ServiceProvider.GetService(typeof(EnvDTE.DTE)); EnvDTE.OutputWindowPanes panes = dte.ToolWindows.OutputWindow.OutputWindowPanes; foreach (EnvDTE.OutputWindowPane pane in panes) { if (pane.Name.Contains("Build")) { pane.OutputString(buildMessage + "\n"); pane.Activate(); return; } } }  
```