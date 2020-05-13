---
title: Obtenir des propriétés de projets (fr) Microsoft Docs
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- project properties, displaying in tool window
- tool windows, displaying project properties
ms.assetid: 96ba07ca-0811-4013-8602-12550ac4ba79
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9ddfd48827bc762c9189f9b7600cfe9200e5c866
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711410"
---
# <a name="get-project-properties"></a>Obtenir des propriétés du projet

Cette procédure pas à pas montre comment afficher les propriétés du projet dans une fenêtre d’outils.

## <a name="prerequisites"></a>Prérequis

A partir de Visual Studio 2015, vous n’installez pas le Visual Studio SDK à partir du centre de téléchargement. Il est inclus comme une fonctionnalité facultative dans la configuration Visual Studio. Vous pouvez également installer le VS SDK plus tard. Pour plus d’informations, voir [Installer le Studio Visuel SDK](../extensibility/installing-the-visual-studio-sdk.md).

### <a name="to-create-a-vsix-project-and-add-a-tool-window"></a>Créer un projet VSIX et ajouter une fenêtre d’outils

1. Chaque extension Visual Studio commence par un projet de déploiement VSIX, qui contiendra les actifs d’extension. Créer [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] un projet `ProjectPropertiesExtension`VSIX nommé . Vous pouvez trouver le modèle de projet VSIX dans le dialogue **du nouveau projet** en recherchant "vsix".

2. Ajoutez une fenêtre d’outil en ajoutant `ProjectPropertiesToolWindow`un modèle d’élément de fenêtre d’outil personnalisé nommé . Dans la **Solution Explorer**, cliquez à droite sur le nœud du projet et sélectionnez **Ajouter** > **un nouvel article**. Dans le **dialogue Add New Item**, rendez-vous sur Visual **C’Items** > **Extensibility** et **sélectionnez Custom Tool Window**. Dans le champ **Nom** au bas du dialogue, `ProjectPropertiesToolWindow.cs`changer le nom du fichier à . Pour plus d’informations sur la façon de créer une fenêtre d’outil personnalisée, voir [Créer une extension avec une fenêtre d’outil](../extensibility/creating-an-extension-with-a-tool-window.md).

3. Générez la solution et vérifiez qu’elle est compilée sans erreur.

### <a name="to-display-project-properties-in-a-tool-window"></a>Afficher les propriétés du projet dans une fenêtre d’outils

1. Dans le fichier ProjectPropertiesToolWindowCommand.cs, ajoutez ce qui suit à l’aide de directives.

    ```csharp
    using EnvDTE;
    using System.Windows.Controls;

    ```

2. Dans *ProjectPropertiesToolWindowControl.xaml*, retirez le bouton existant et ajoutez un TreeView de la boîte à outils. Vous pouvez également supprimer le gestionnaire d’événements de clic du fichier *ProjectPropertiesToolWindowControl.xaml.cs.*

3. Dans *ProjectPropertiesToolWindowCommand.cs*, utilisez `ShowToolWindow()` la méthode pour ouvrir le projet et lire ses propriétés, puis ajoutez les propriétés à l’TreeView. Le code de ShowToolWindow devrait ressembler à ce qui suit:

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

4. Générez le projet et commencez le débogage. L’instance expérimentale devrait apparaître.

5. Dans l'instance expérimentale, ouvrez un projet.

6. Dans la **vue** > **d’autres Windows** cliquez sur **ProjectPropertiesToolWindow**.

  Vous devriez voir le contrôle de l’arbre dans la fenêtre d’outil avec le nom du premier projet et de toutes ses propriétés de projet.
