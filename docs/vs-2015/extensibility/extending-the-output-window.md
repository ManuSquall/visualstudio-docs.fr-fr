---
title: Extension du Fenêtre Sortie | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Output window, about Output window
ms.assetid: b02fa88c-f92a-4ff6-ba5f-2eb4d48a643a
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2788903c60564d501770616fbe3ad2335e60a250
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204426"
---
# <a name="extending-the-output-window"></a>Extension de la fenêtre Sortie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La fenêtre **sortie** est un ensemble de volets de texte en lecture/écriture. Visual Studio contient les volets intégrés suivants : la **génération**, dans laquelle les projets communiquent des messages sur les builds, et **général**, dans lequel [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] communique les messages relatifs à l’IDE. Les projets obtiennent une référence au volet de **génération** automatiquement via les <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> méthodes d’interface, et Visual Studio offre un accès direct au volet **général** par le biais du <xref:Microsoft.VisualStudio.Shell.Interop.SVsGeneralOutputWindowPane> service. Outre les volets intégrés, vous pouvez créer et gérer vos propres volets personnalisés.  
  
 Vous pouvez contrôler la fenêtre de **sortie** directement par le biais des <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> interfaces et. L' <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> interface, qui est proposée par le <xref:Microsoft.VisualStudio.Shell.Interop.SVsOutputWindow> service, définit des méthodes pour la création, la récupération et la destruction des volets de la fenêtre **sortie** . L' <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> interface définit des méthodes pour l’indication des volets, le masquage des volets et la manipulation de leur texte. Une autre façon de contrôler la fenêtre de **sortie** consiste à utiliser les <xref:EnvDTE.OutputWindow> <xref:EnvDTE.OutputWindowPane> objets et dans le modèle objet Automation de Visual Studio. Ces objets encapsulent presque toutes les fonctionnalités des <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> interfaces et <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> . En outre, les <xref:EnvDTE.OutputWindow> <xref:EnvDTE.OutputWindowPane> objets et ajoutent des fonctionnalités de niveau supérieur pour faciliter l’énumération des volets de la fenêtre **sortie** et l’extraction de texte à partir des volets.  
  
## <a name="creating-an-extension-that-uses-the-output-pane"></a>Création d’une extension qui utilise le volet de sortie  
 Vous pouvez créer une extension qui exerce différents aspects du volet de sortie.  
  
1. Créez un projet VSIX nommé `TestOutput` à l’aide d’une commande de menu nommée **TestOutput**. Pour plus d’informations, consultez [création d’une extension à l’aide d’une commande de menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2. Ajoutez les références suivantes :  
  
    1. EnvDTE  
  
    2. EnvDTE80  
  
3. Dans TestOutput.cs, ajoutez l’instruction using suivante :  
  
    ```f#  
    using EnvDTE;  
    using EnvDTE80;  
    ```  
  
4. Dans TestOutput.cs, supprimez la méthode méthode ShowMessageBox. Ajoutez le stub de méthode suivant :  
  
    ```csharp  
    private void OutputCommandHandler(object sender, EventArgs e)  
    {  
    }  
    ```  
  
5. Dans le constructeur TestOutput, remplacez le gestionnaire de commandes par OutputCommandHandler. Voici la partie qui ajoute les commandes :  
  
    ```csharp  
    OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
    if (commandService != null)  
    {  
        CommandID menuCommandID = new CommandID(MenuGroup, CommandId);  
        EventHandler eventHandler = OutputCommandHandler;  
        MenuCommand menuItem = new MenuCommand(eventHandler, menuCommandID);  
        commandService.AddCommand(menuItem);  
    }  
    ```  
  
6. Les sections ci-dessous ont des méthodes différentes qui illustrent les différentes façons de gérer le volet de sortie. Vous pouvez appeler ces méthodes dans le corps de la méthode OutputCommandHandler (). Par exemple, le code suivant ajoute la méthode CreatePane () indiquée dans la section suivante.  
  
    ```csharp  
    private void OutputCommandHandler(object sender, EventArgs e)  
    {  
        CreatePane(new Guid(), "Created Pane", true, false);  
    }  
    ```  
  
## <a name="creating-an-output-window-with-ivsoutputwindow"></a>Création d’un Fenêtre Sortie avec IVsOutputWindow  
 Cet exemple montre comment créer un nouveau volet de fenêtre **sortie** à l’aide de l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> interface.  
  
```csharp  
void CreatePane(Guid paneGuid, string title,   
    bool visible, bool clearWithSolution)  
{  
    IVsOutputWindow output =   
        (IVsOutputWindow)GetService(typeof(SVsOutputWindow));  
    IVsOutputWindowPane pane;  
  
    // Create a new pane.  
    output.CreatePane(  
        ref paneGuid,   
        title,   
        Convert.ToInt32(visible),   
        Convert.ToInt32(clearWithSolution));  
  
    // Retrieve the new pane.  
    output.GetPane(ref paneGuid, out pane);  
  
     pane.OutputString("This is the Created Pane \n");  
}  
```  
  
 Si vous ajoutez cette méthode à l’extension indiquée dans la section précédente, lorsque vous cliquez sur la commande **Invoke TestOutput** , vous devez voir la fenêtre **sortie** avec un en-tête qui indique **afficher la sortie de : CreatedPane** et les mots **le volet créé** dans le volet lui-même.  
  
## <a name="creating-an-output-window-with-outputwindow"></a>Création d’un Fenêtre Sortie avec OutputWindow  
 Cet exemple montre comment créer un volet de fenêtre **sortie** à l’aide de l' <xref:EnvDTE.OutputWindow> objet.  
  
```csharp  
void CreatePane(string title)  
{  
    DTE2 dte = (DTE2)GetService(typeof(DTE));  
    OutputWindowPanes panes =  
        dte.ToolWindows.OutputWindow.OutputWindowPanes;  
  
    try  
    {  
        // If the pane exists already, write to it.  
        panes.Item(title);  
    }  
    catch (ArgumentException)  
    {  
        // Create a new pane and write to it.  
        return panes.Add(title);  
    }  
}  
```  
  
 Bien que la <xref:EnvDTE.OutputWindowPanes> collection vous permette de récupérer un volet de fenêtre **sortie** en fonction de son titre, il n’est pas garanti que les titres des volets soient uniques. Si vous doutez de l’unicité d’un titre, utilisez la <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow.GetPane%2A> méthode pour récupérer le volet approprié par son GUID.  
  
 Si vous ajoutez cette méthode à l’extension indiquée dans la section précédente, lorsque vous cliquez sur la commande **Invoke TestOutput** , vous devez voir la fenêtre sortie avec un en-tête qui indique **afficher la sortie de : DTEPane** et le **volet DTE ajouté** dans le volet lui-même.  
  
## <a name="deleting-an-output-window"></a>Suppression d’un Fenêtre Sortie  
 Cet exemple montre comment supprimer un volet de la fenêtre **sortie** .  
  
```csharp  
void DeletePane(Guid paneGuid)  
{  
    IVsOutputWindow output =  
    (IVsOutputWindow)ServiceProvider.GetService(typeof(SVsOutputWindow));  
  
    IVsOutputWindowPane pane;  
    output.GetPane(ref paneGuid, out pane);  
  
    if (pane == null)  
    {  
        CreatePane(paneGuid, "New Pane\n", true, true);  
    }  
     else  
    {  
        output.DeletePane(ref paneGuid);  
    }  
}  
```  
  
 Si vous ajoutez cette méthode à l’extension indiquée dans la section précédente, lorsque vous cliquez sur la commande **Invoke TestOutput** , vous devez voir la fenêtre sortie avec un en-tête indiquant **afficher la sortie de : nouveau volet** et le **volet mots ajoutés créés** dans le volet lui-même. Si vous cliquez à nouveau sur la commande **Invoke TestOutput** , le volet est supprimé.  
  
## <a name="getting-the-general-pane-of-the-output-window"></a>Obtention du volet général de l’Fenêtre Sortie  
 Cet exemple montre comment obtenir le volet **général** intégré de la fenêtre **sortie** .  
  
```csharp  
void GetGeneralPane()  
{  
    return (IVsOutputWindowPane)GetService(  
        typeof(SVsGeneralOutputWindowPane));  
}  
```  
  
 Si vous ajoutez cette méthode à l’extension indiquée dans la section précédente, lorsque vous cliquez sur la commande **Invoke TestOutput** , vous devez voir que la fenêtre **sortie** affiche le **volet général trouvé** dans le volet.  
  
## <a name="getting-the-build-pane-of-the-output-window"></a>Obtention du volet de génération du Fenêtre Sortie  
 Cet exemple montre comment rechercher le volet Build et y écrire. Étant donné que le volet de génération n’est pas activé par défaut, il l’active également.  
  
```csharp  
void OutputTaskItemStringExExample(string buildMessage)  
{  
    EnvDTE80.DTE2 dte = (EnvDTE80.DTE2)ServiceProvider.GetService(typeof(EnvDTE.DTE));  
  
    EnvDTE.OutputWindowPanes panes =  
        dte.ToolWindows.OutputWindow.OutputWindowPanes;  
    foreach (EnvDTE.OutputWindowPane pane in panes)  
        {  
            if (pane.Name.Contains("Build"))  
            {  
                pane.OutputString(buildMessage + "\n");  
                pane.Activate();  
                return;  
             }  
        }  
}  
```
