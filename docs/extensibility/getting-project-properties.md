---
title: Obtention des propriétés du projet | Microsoft Docs
description: Découvrez comment afficher les propriétés d’un projet dans une fenêtre outil. Cet exemple montre le contrôle d’arborescence dans la fenêtre outil.
ms.custom: SEO-VS-2020
ms.date: 3/16/2019
ms.topic: how-to
helpviewer_keywords:
- project properties, displaying in tool window
- tool windows, displaying project properties
ms.assetid: 96ba07ca-0811-4013-8602-12550ac4ba79
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d3f7f6cc788e693ae143b288c589fc868c59d531
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900666"
---
# <a name="get-project-properties"></a>Obtient les propriétés du projet

Cette procédure pas à pas montre comment afficher les propriétés d’un projet dans une fenêtre outil.

## <a name="prerequisites"></a>Prérequis

À compter de Visual Studio 2015, vous n’installez pas le kit de développement logiciel (SDK) Visual Studio à partir du centre de téléchargement. Il est inclus en tant que fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit de développement logiciel (SDK) Visual Studio plus tard. Pour plus d’informations, consultez [installer le kit de développement logiciel (SDK) Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

### <a name="to-create-a-vsix-project-and-add-a-tool-window"></a>Pour créer un projet VSIX et ajouter une fenêtre outil

1. Chaque extension Visual Studio commence par un projet de déploiement VSIX, qui contient les composants d’extension. Créez un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projet VSIX nommé `ProjectPropertiesExtension` . Vous pouvez trouver le modèle de projet VSIX dans la boîte de dialogue **nouveau projet** en recherchant « VSIX ».

2. Ajoutez une fenêtre outil en ajoutant un modèle d’élément de fenêtre outil personnalisé nommé `ProjectPropertiesToolWindow` . Dans le **Explorateur de solutions**, cliquez avec le bouton droit sur le nœud du projet et sélectionnez **Ajouter**  >  **un nouvel élément**. Dans la **boîte de dialogue Ajouter un nouvel élément**, accédez à extensibilité des **éléments Visual C#**  >   et sélectionnez **fenêtre outil personnalisée**. Dans le champ **nom** en bas de la boîte de dialogue, remplacez le nom de fichier par `ProjectPropertiesToolWindow.cs` . Pour plus d’informations sur la création d’une fenêtre outil personnalisée, consultez [créer une extension avec une fenêtre outil](../extensibility/creating-an-extension-with-a-tool-window.md).

3. Générez la solution et vérifiez qu’elle est compilée sans erreur.

### <a name="to-display-project-properties-in-a-tool-window"></a>Pour afficher les propriétés d’un projet dans une fenêtre outil

1. Dans le fichier ProjectPropertiesToolWindowCommand. cs, ajoutez les directives using suivantes.

    ```csharp
    using EnvDTE;
    using System.Windows.Controls;

    ```

2. Dans *ProjectPropertiesToolWindowControl. Xaml*, supprimez le bouton existant et ajoutez un TreeView à partir de la boîte à outils. Vous pouvez également supprimer le gestionnaire d’événements Click du fichier *ProjectPropertiesToolWindowControl. Xaml. cs* .

3. Dans *ProjectPropertiesToolWindowCommand. cs*, utilisez la `ShowToolWindow()` méthode pour ouvrir le projet et lire ses propriétés, puis ajoutez les propriétés à l’arborescence. Le code de ShowToolWindow doit ressembler à ce qui suit :

    ```csharp
    private void ShowToolWindow(object sender, EventArgs e)
    {
        ToolWindowPane window = this.package.FindToolWindow(typeof(ProjectPropertiesToolWindow), 0, true);
        if ((null == window) || (null == window.Frame))
        {
            throw new NotSupportedException("Cannot create window.");
        }
        IVsWindowFrame windowFrame = (IVsWindowFrame)window.Frame;
        Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(windowFrame.Show());

        // Get the tree view and populate it if there is a project open.
        ProjectPropertiesToolWindowControl control = (ProjectPropertiesToolWindowControl)window.Content;
        TreeView treeView = control.treeView;

        // Reset the TreeView to 0 items.
        treeView.Items.Clear();

        DTE dte = (DTE)this.ServiceProvider.GetService(typeof(DTE));
        Projects projects = dte.Solution.Projects;
        if (projects.Count == 0)   // no project is open
        {
            TreeViewItem item = new TreeViewItem();
            item.Name = "Projects";
            item.ItemsSource = new string[]{ "no projects are open." };
            item.IsExpanded = true;
            treeView.Items.Add(item);
            return;
        }

        Project project = projects.Item(1);
        TreeViewItem item1 = new TreeViewItem();
        item1.Header = project.Name + "Properties";
        treeView.Items.Add(item1);

        foreach (Property property in project.Properties)
        {
            TreeViewItem item = new TreeViewItem();
            item.ItemsSource = new string[] { property.Name };
            item.IsExpanded = true;
            treeView.Items.Add(item);
        }
    }
    ```

4. Générez le projet et commencez le débogage. L’instance expérimentale doit apparaître.

5. Dans l'instance expérimentale, ouvrez un projet.

6. Dans la **vue**  >  **autres fenêtres** , cliquez sur **ProjectPropertiesToolWindow**.

  Vous devez voir le contrôle d’arborescence dans la fenêtre outil, ainsi que le nom du premier projet et de toutes ses propriétés de projet.
