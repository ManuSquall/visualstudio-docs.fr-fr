---
title: Extension de la fenêtre de sortie | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Output window, about Output window
ms.assetid: b02fa88c-f92a-4ff6-ba5f-2eb4d48a643a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 03e7cb1a462c79f498687296afd8c64accfc1458
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56706208"
---
# <a name="extend-the-output-window"></a>Étendre la fenêtre Sortie
Le **sortie** fenêtre est un ensemble de volets de texte en lecture/écriture. Visual Studio propose ces volets intégrés : **Build**, dans les projets qui communiquent sur les builds, les messages et **général**, dans lequel [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] communique les messages sur l’IDE. Projets obtenir une référence à la **générer** automatiquement par le biais du volet le <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> méthodes d’interface et Visual Studio offre un accès direct à la **général** volet via le <xref:Microsoft.VisualStudio.Shell.Interop.SVsGeneralOutputWindowPane> service. Outre les volets intégrés, vous pouvez créer et gérer vos propres volets personnalisés.

 Vous pouvez contrôler le **sortie** fenêtre directement via le <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> et <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> interfaces. Le <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> interface, ce qui vous est offerte par le <xref:Microsoft.VisualStudio.Shell.Interop.SVsOutputWindow> de service, définit des méthodes pour la création, la récupération et la destruction **sortie** volets de fenêtre. Le <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> interface définit les méthodes d’affichage de volets, de masquage des volets et de manipuler leur texte. Une autre façon de contrôler la **sortie** fenêtre consiste à utiliser le <xref:EnvDTE.OutputWindow> et <xref:EnvDTE.OutputWindowPane> objets dans le modèle d’objet Automation Visual Studio. Ces objets encapsulent presque toutes les fonctionnalités de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> et <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> interfaces. En outre, le <xref:EnvDTE.OutputWindow> et <xref:EnvDTE.OutputWindowPane> objets ajoutent certaines fonctionnalités de niveau supérieur pour le rendre plus facile à énumérer les **sortie** volets de fenêtre et à récupérer du texte dans les volets.

## <a name="create-an-extension-that-uses-the-output-pane"></a>Créer une extension qui utilise le volet de sortie
 Vous pouvez créer une extension qui exécute les différents aspects du volet sortie.

1.  Créez un projet VSIX nommé `TestOutput` avec une commande de menu nommée **Testouput**. Pour plus d’informations, consultez [créer une extension avec une commande de menu](../extensibility/creating-an-extension-with-a-menu-command.md).

2.  Ajoutez les références suivantes :

    1.  EnvDTE

    2.  EnvDTE80

3.  Dans *TestOutput.cs*, ajoutez le code suivant à l’aide d’instruction :

    ```f#
    using EnvDTE;
    using EnvDTE80;
    ```

4.  Dans *TestOutput.cs*, supprimez le `ShowMessageBox` (méthode). Ajoutez le stub de méthode suivant :

    ```csharp
    private void OutputCommandHandler(object sender, EventArgs e)
    {
    }
    ```

5.  Dans le constructeur Testouput, modifiez le Gestionnaire de commandes à OutputCommandHandler. Voici la partie qui ajoute les commandes :

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

6.  Les sections ci-dessous proposent des méthodes qui montrent différentes manières de traiter avec le volet de sortie. Vous pouvez appeler ces méthodes au corps de la `OutputCommandHandler()` (méthode). Par exemple, le code suivant ajoute le `CreatePane()` méthode donnée en fonction de la section suivante.

    ```csharp
    private void OutputCommandHandler(object sender, EventArgs e)
    {
        CreatePane(new Guid(), "Created Pane", true, false);
    }
    ```

## <a name="create-an-output-window-with-ivsoutputwindow"></a>Créer une fenêtre de sortie avec IVsOutputWindow
 Cet exemple montre comment créer un nouveau **sortie** volet de fenêtre à l’aide de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> interface.

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

 Si vous ajoutez cette méthode à l’extension donnée dans la section précédente, lorsque vous cliquez sur le **Testouput appeler** commande que vous devez voir le **sortie** fenêtre avec un en-tête indiquant **afficher la sortie De : CreatedPane** et les mots **il s’agit du volet créé** dans le volet de lui-même.

## <a name="create-an-output-window-with-outputwindow"></a>Créer une fenêtre de sortie avec OutputWindow
 Cet exemple montre comment créer un **sortie** volet de fenêtre à l’aide de la <xref:EnvDTE.OutputWindow> objet.

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

 Bien que le <xref:EnvDTE.OutputWindowPanes> collection vous permet de récupérer un **sortie** volet de fenêtre par son titre, des titres de volet ne sont pas garantis pour être unique. Lorsque vous douter de l’unicité d’un titre, utilisez la <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow.GetPane%2A> méthode pour récupérer le volet correct par son GUID.

 Si vous ajoutez cette méthode à l’extension donnée dans la section précédente, lorsque vous cliquez sur le **Testouput appeler** commande, vous devez voir la fenêtre de sortie avec un en-tête indiquant **afficher la sortie à partir de : DTEPane** et les mots **ajouté le volet DTE** dans le volet de lui-même.

## <a name="delete-an-output-window"></a>Supprimer une fenêtre de sortie
 Cet exemple montre comment supprimer un **sortie** volet de fenêtre.

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

 Si vous ajoutez cette méthode à l’extension donnée dans la section précédente, lorsque vous cliquez sur le **Testouput appeler** commande, vous devez voir la fenêtre de sortie avec un en-tête indiquant **afficher la sortie à partir de : Nouveau volet** et les mots **ajouté le volet Création** dans le volet de lui-même. Si vous cliquez sur le **Testouput appeler** commande là encore, le volet est supprimé.

## <a name="get-the-general-pane-of-the-output-window"></a>Obtenir le volet Général de la fenêtre Sortie
 Cet exemple montre comment obtenir l’intégrée **général** volet de la **sortie** fenêtre.

```csharp
IVsOutputWindowPane GetGeneralPane()
{
    return (IVsOutputWindowPane)GetService(
        typeof(SVsGeneralOutputWindowPane));
}
```

 Si vous ajoutez cette méthode à l’extension donnée dans la section précédente, lorsque vous cliquez sur le **Testouput appeler** commande, vous devez voir que la **sortie** fenêtre affiche les mots **trouvé général volet** dans le volet.

## <a name="get-the-build-pane-of-the-output-window"></a>Obtenir le volet de la génération de la fenêtre Sortie
 Cet exemple montre comment rechercher le **Build** volet et en écriture à ce dernier. Dans la mesure où le **Build** volet n’est pas activé par défaut, il l’active également.

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
