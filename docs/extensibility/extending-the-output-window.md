---
title: Extension du Fenêtre Sortie | Microsoft Docs
description: Découvrez comment étendre la fenêtre de sortie dans le kit de développement logiciel (SDK) Visual Studio et créer et gérer vos propres volets personnalisés.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Output window, about Output window
ms.assetid: b02fa88c-f92a-4ff6-ba5f-2eb4d48a643a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 402c53691525530171edafd6a0751dfc72c9798d
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900211"
---
# <a name="extend-the-output-window"></a>Étendre la fenêtre sortie
La fenêtre **sortie** est un ensemble de volets de texte en lecture/écriture. Visual Studio contient les volets intégrés suivants : la **génération**, dans laquelle les projets communiquent des messages sur les builds, et **général**, dans lequel [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] communique les messages relatifs à l’IDE. Les projets obtiennent une référence au volet de **génération** automatiquement via les <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> méthodes d’interface, et Visual Studio offre un accès direct au volet **général** par le biais du <xref:Microsoft.VisualStudio.Shell.Interop.SVsGeneralOutputWindowPane> service. Outre les volets intégrés, vous pouvez créer et gérer vos propres volets personnalisés.

 Vous pouvez contrôler la fenêtre de **sortie** directement par le biais des <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> interfaces et. L' <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> interface, qui est proposée par le <xref:Microsoft.VisualStudio.Shell.Interop.SVsOutputWindow> service, définit des méthodes pour la création, la récupération et la destruction des volets de la fenêtre **sortie** . L' <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> interface définit des méthodes pour l’indication des volets, le masquage des volets et la manipulation de leur texte. Une autre façon de contrôler la fenêtre de **sortie** consiste à utiliser les <xref:EnvDTE.OutputWindow> <xref:EnvDTE.OutputWindowPane> objets et dans le modèle objet Automation de Visual Studio. Ces objets encapsulent presque toutes les fonctionnalités des <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> interfaces et <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> . En outre, les <xref:EnvDTE.OutputWindow> <xref:EnvDTE.OutputWindowPane> objets et ajoutent des fonctionnalités de niveau supérieur pour faciliter l’énumération des volets de la fenêtre **sortie** et l’extraction de texte à partir des volets.

## <a name="create-an-extension-that-uses-the-output-pane"></a>Créer une extension qui utilise le volet de sortie
 Vous pouvez créer une extension qui exerce différents aspects du volet de sortie.

1. Créez un projet VSIX nommé `TestOutput` à l’aide d’une commande de menu nommée **TestOutput**. Pour plus d’informations, consultez [créer une extension à l’aide d’une commande de menu](../extensibility/creating-an-extension-with-a-menu-command.md).

2. Ajoutez les références suivantes :

    1. EnvDTE

    2. EnvDTE80

3. Dans *TestOutput. cs*, ajoutez l’instruction using suivante :

    ```f#
    using EnvDTE;
    using EnvDTE80;
    ```

4. Dans *TestOutput. cs*, supprimez la `ShowMessageBox` méthode. Ajoutez le stub de méthode suivant :

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

6. Les sections ci-dessous ont des méthodes différentes qui illustrent les différentes façons de gérer le volet de sortie. Vous pouvez appeler ces méthodes dans le corps de la `OutputCommandHandler()` méthode. Par exemple, le code suivant ajoute la `CreatePane()` méthode indiquée dans la section suivante.

    ```csharp
    private void OutputCommandHandler(object sender, EventArgs e)
    {
        CreatePane(new Guid(), "Created Pane", true, false);
    }
    ```

## <a name="create-an-output-window-with-ivsoutputwindow"></a>Créer une fenêtre de sortie avec IVsOutputWindow
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

## <a name="create-an-output-window-with-outputwindow"></a>Créer une fenêtre sortie avec OutputWindow
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
        panes.Add(title);
    }
}
```

 Bien que la <xref:EnvDTE.OutputWindowPanes> collection vous permette de récupérer un volet de fenêtre **sortie** en fonction de son titre, il n’est pas garanti que les titres des volets soient uniques. Si vous doutez de l’unicité d’un titre, utilisez la <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow.GetPane%2A> méthode pour récupérer le volet approprié par son GUID.

 Si vous ajoutez cette méthode à l’extension indiquée dans la section précédente, lorsque vous cliquez sur la commande **Invoke TestOutput** , vous devez voir la fenêtre sortie avec un en-tête qui indique **afficher la sortie de : DTEPane** et le **volet DTE ajouté** dans le volet lui-même.

## <a name="delete-an-output-window"></a>Supprimer une fenêtre sortie
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

## <a name="get-the-general-pane-of-the-output-window"></a>Obtenir le volet général de la fenêtre sortie
 Cet exemple montre comment obtenir le volet **général** intégré de la fenêtre **sortie** .

```csharp
IVsOutputWindowPane GetGeneralPane()
{
    return (IVsOutputWindowPane)GetService(
        typeof(SVsGeneralOutputWindowPane));
}
```

 Si vous ajoutez cette méthode à l’extension indiquée dans la section précédente, lorsque vous cliquez sur la commande **Invoke TestOutput** , vous devez voir que la fenêtre **sortie** affiche le **volet général trouvé** dans le volet.

## <a name="get-the-build-pane-of-the-output-window"></a>Obtient le volet de génération de la fenêtre sortie
 Cet exemple montre comment rechercher le volet **Build** et y écrire. Étant donné que le volet de **génération** n’est pas activé par défaut, il l’active également.

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
