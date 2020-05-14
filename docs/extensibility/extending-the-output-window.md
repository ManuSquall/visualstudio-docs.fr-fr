---
title: Extension de la fenêtre de sortie (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Output window, about Output window
ms.assetid: b02fa88c-f92a-4ff6-ba5f-2eb4d48a643a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 800b443b079111d1d09fffdd900b246a020578f4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711640"
---
# <a name="extend-the-output-window"></a>Étendre la fenêtre de sortie
La fenêtre **de sortie** est un ensemble de volets texte de lecture/écriture. Visual Studio a ces volets intégrés: **Construire**, dans lequel les projets de communiquer des messages sur les constructions, et **Général**, dans lequel [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] communique des messages sur l’IDE. Les projets obtiennent **Build** automatiquement une référence <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> à la vitre Build à travers les méthodes <xref:Microsoft.VisualStudio.Shell.Interop.SVsGeneralOutputWindowPane> d’interface, et Visual Studio offre un accès direct à la vitre **générale** grâce au service. En plus des vitres intégrées, vous pouvez créer et gérer vos propres vitres personnalisées.

 Vous pouvez contrôler la fenêtre <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> **de sortie** directement à travers les interfaces et les interfaces. L’interface, <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> qui est <xref:Microsoft.VisualStudio.Shell.Interop.SVsOutputWindow> offerte par le service, définit les méthodes pour créer, récupérer et détruire les vitres **de sortie.** L’interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> définit des méthodes pour montrer les vitres, cacher les vitres et manipuler leur texte. Une autre façon de contrôler la <xref:EnvDTE.OutputWindow> fenêtre <xref:EnvDTE.OutputWindowPane> **de sortie** est à travers le modèle d’objet Visual Studio Automation. Ces objets encapsulent presque toutes <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> les <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> fonctionnalités et les interfaces. En outre, <xref:EnvDTE.OutputWindow> <xref:EnvDTE.OutputWindowPane> les objets et les objets ajoutent une fonctionnalité de niveau supérieur pour faciliter l’énumération des vitres **de sortie** et pour récupérer le texte des vitres.

## <a name="create-an-extension-that-uses-the-output-pane"></a>Créer une extension qui utilise le volet Output
 Vous pouvez faire une extension qui exerce différents aspects de la vitre de sortie.

1. Créez un projet `TestOutput` VSIX nommé avec une commande de menu nommée **TestOutput**. Pour plus d’informations, voir [Créer une extension avec une commande de menu](../extensibility/creating-an-extension-with-a-menu-command.md).

2. Ajoutez les références suivantes :

    1. EnvDTE

    2. EnvDTE80

3. Dans *TestOutput.cs*, ajouter l’instruction suivante en utilisant:

    ```f#
    using EnvDTE;
    using EnvDTE80;
    ```

4. Dans *TestOutput.cs*, supprimer `ShowMessageBox` la méthode. Ajouter le talon de méthode suivant :

    ```csharp
    private void OutputCommandHandler(object sender, EventArgs e)
    {
    }
    ```

5. Dans le constructeur TestOutput, changez le gestionnaire de commande en OutputCommandHandler. Voici la partie qui ajoute les commandes:

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

6. Les sections ci-dessous ont différentes méthodes qui montrent différentes façons de traiter le volet output. Vous pouvez appeler ces méthodes `OutputCommandHandler()` au corps de la méthode. Par exemple, le code `CreatePane()` suivant ajoute la méthode donnée dans la section suivante.

    ```csharp
    private void OutputCommandHandler(object sender, EventArgs e)
    {
        CreatePane(new Guid(), "Created Pane", true, false);
    }
    ```

## <a name="create-an-output-window-with-ivsoutputwindow"></a>Créez une fenêtre de sortie avec IVsOutputWindow
 Cet exemple montre comment créer un nouveau volet <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> de fenêtre de **sortie** en utilisant l’interface.

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

 Si vous ajoutez cette méthode à l’extension donnée dans la section précédente, lorsque vous cliquez sur la commande **Invoke TestOutput,** vous devriez voir la fenêtre **de sortie** avec un en-tête qui indique Afficher la **sortie de: CreatedPane** et les mots **C’est le volet créé** dans le volet lui-même.

## <a name="create-an-output-window-with-outputwindow"></a>Créer une fenêtre de sortie avec OutputWindow
 Cet exemple montre comment créer une vitre <xref:EnvDTE.OutputWindow> de **sortie** en utilisant l’objet.

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

 Bien <xref:EnvDTE.OutputWindowPanes> que la collection vous permete de récupérer une vitre **de sortie** par son titre, les titres de volet ne sont pas garantis pour être uniques. Lorsque vous doutez de l’unicité d’un titre, utilisez la <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow.GetPane%2A> méthode pour récupérer le volet correct par son GUID.

 Si vous ajoutez cette méthode à l’extension donnée dans la section précédente, lorsque vous cliquez sur la commande **Invoke TestOutput,** vous devriez voir la fenêtre de sortie avec un en-tête qui dit Afficher la **sortie de: DTEPane** et les mots **ajoutés DTE Pane** dans la vitre elle-même.

## <a name="delete-an-output-window"></a>Supprimer une fenêtre de sortie
 Cet exemple montre comment supprimer une vitre **de sortie.**

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

 Si vous ajoutez cette méthode à l’extension donnée dans la section précédente, lorsque vous cliquez sur la commande **Invoke TestOutput,** vous devriez voir la fenêtre de sortie avec un en-tête qui indique Afficher la **sortie de: New Pane** et les mots **ajoutés Créé Pane** dans la vitre elle-même. Si vous cliquez à nouveau sur la commande **Invoke TestOutput,** le volet est supprimé.

## <a name="get-the-general-pane-of-the-output-window"></a>Obtenez la vitre générale de la fenêtre Output
 Cet exemple montre comment obtenir la vitre **générale** intégrée de la fenêtre **output.**

```csharp
IVsOutputWindowPane GetGeneralPane()
{
    return (IVsOutputWindowPane)GetService(
        typeof(SVsGeneralOutputWindowPane));
}
```

 Si vous ajoutez cette méthode à l’extension donnée dans la section précédente, lorsque vous cliquez sur la commande **Invoke TestOutput,** vous devez voir que la fenêtre **de sortie** affiche les mots Found **General pane** dans la vitre.

## <a name="get-the-build-pane-of-the-output-window"></a>Obtenez la vitre Build de la fenêtre Output
 Cet exemple montre comment trouver la vitre **Build** et y écrire. Étant donné que le volet **Build** n’est pas activé par défaut, il l’active également.

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
