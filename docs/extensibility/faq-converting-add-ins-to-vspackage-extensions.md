---
title: 'FAQ : Conversion des compléments en extensions VSPackage | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 3a01d333-6e31-423f-ae06-5091a4fcb7a9
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d1abb79bc8d982ba36091bfcbc6ec4c84c5df4a2
ms.sourcegitcommit: d4bea2867a4f0c3b044fd334a54407c0fe87f9e8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58789528"
---
# <a name="faq-converting-add-ins-to-vspackage-extensions"></a>FAQ : Conversion des compléments en extensions VSPackage
Les compléments sont désormais déconseillés. Pour effectuer une nouvelle extension de Visual Studio, vous devez créer une extension VSIX. Voici les réponses à certaines questions fréquemment posées sur la façon de convertir un complément Visual Studio pour une extension VSIX.

> [!WARNING]
>  À compter de Visual Studio 2015, pour les projets c# et Visual Basic, vous pouvez utiliser le projet VSIX et ajouter des modèles d’élément pour les commandes de menu, les fenêtres Outil et les VSPackages. Pour plus d’informations, consultez [quelles sont les nouveautés dans le Kit de développement logiciel Visual Studio 2015](../extensibility/what-s-new-in-the-visual-studio-2015-sdk.md).

> [!IMPORTANT]
>  Dans de nombreux cas, vous pouvez simplement transférer votre code de complément à un projet VSIX avec un élément de projet VSPackage. Vous pouvez obtenir l'objet automation DTE en appelant <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> dans la méthode <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>.
>
>  `DTE2 dte = (DTE2)GetService(typeof(DTE));`
>
>  Pour plus d’informations, consultez [comment puis-je exécuter mon code de complément dans un VSPackage ?](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md#BKMK_RunAddin) ci-dessous.

## <a name="what-software-do-i-need-to-develop-vsix-extensions"></a>Quel logiciel besoin développer des extensions VSIX
 À partir de Visual Studio 2015, vous n’installez pas le Kit de développement logiciel Visual Studio à partir du centre de téléchargement. Il est inclus comme fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit SDK VS par la suite. Pour plus d’informations, consultez [installer le SDK Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="wheres-the-extension-documentation"></a>Où se trouve la documentation de l’extension ?
 Démarrer avec [commencer à développer des extensions Visual Studio](../extensibility/starting-to-develop-visual-studio-extensions.md). Autres articles sur le développement d’extension extensibilité Visual Studio sur MSDN sont ci-dessous celui-là.

## <a name="can-i-convert-my-add-in-project-to-a-vsix-project"></a>Puis-je convertir mon projet de complément à un projet VSIX ?
 Impossible de convertir un projet de complément directement à un projet VSIX, car les mécanismes utilisés dans des projets VSIX ne sont pas les mêmes que celles dans les projets de complément. Le modèle de projet VSIX, ainsi que les modèles d’élément de projet approprié ont beaucoup de code qui rend relativement simple être opérationnel et en cours d’exécution comme extension VSIX.

##  <a name="BKMK_StartDeveloping"></a> Comment commencer à développer des extensions VSIX ?
 Voici comment procéder à une extension VSIX qui comporte une commande de menu :

### <a name="to-make-a-vsix-extension-that-has-a-menu-command"></a>Pour créer une extension VSIX qui dispose d’une commande de menu

1. Créez un projet VSIX. (**Fichier** > **New** > **projet**, ou type **projet** dans la zone de recherche). Dans le **nouveau projet** boîte de dialogue, développez **Visual C#**   >  **extensibilité** ou **Visual Basic**  >  **Extensibilité** et sélectionnez **projet VSIX**. Nommez le projet **TestExtension** et spécifiez un emplacement pour celui-ci.

2. Ajouter un **commande personnalisée** modèle d’élément. (Cliquez sur le nœud de projet dans le **l’Explorateur de solutions** et sélectionnez **ajouter** > **un nouvel élément**. Dans le **ajouter un nouvel élément** boîte de dialogue pour soit Visual C# ou Visual Basic, sélectionnez le **extensibilité** nœud et sélectionnez **commande personnalisée**.)

3. Appuyez sur **F5** pour générer et exécuter le projet en mode débogage.

   Une seconde instance de Visual Studio apparaît. Celle-ci est appelée instance expérimentale. Ses paramètres peuvent différer de ceux de l'instance de Visual Studio qui vous sert à écrire du code. À la première exécution de l'instance expérimentale, vous êtes invité à vous connecter à VS en ligne et à spécifier vos thème et profil.

   Sur le **outils** menu (dans l’instance expérimentale), vous devez voir un bouton nommé **mon nom de commande**. Lorsque vous choisissez ce bouton, un message doit apparaître : **Inside TestVSPackagePackage.MenuItemCallback()**.

##  <a name="BKMK_RunAddin"></a> Comment puis-je exécuter mon code de complément dans un VSPackage ?

Un code de complément s'exécute généralement de l'une des deux façons suivantes :

- Déclenché par une commande de menu (le code se trouve dans le `IDTCommandTarget.Exec` méthode.)

- automatiquement au démarrage (le code se trouve dans le gestionnaire d'événements `OnConnection`.).

Vous pouvez procéder de la même façon dans un VSPackage. Voici comment ajouter du code de complément dans une méthode de rappel :

### <a name="to-implement-a-menu-command-in-a-vspackage"></a>Pour implémenter une commande de menu dans un VSPackage

1. Créez un VSPackage comportant une commande de menu. (Pour plus d’informations, consultez [créer une extension avec une commande de menu](../extensibility/creating-an-extension-with-a-menu-command.md).)

2. Ouvrez le fichier contenant la définition du VSPackage. (Dans un projet c#, il a  *\<nom de votre projet > Package.cs*.)

3. Ajoutez les instructions `using` suivantes au fichier :

   ```csharp
   using EnvDTE;
   using EnvDTE80;
   ```

4. Recherchez la méthode `MenuItemCallback`. Ajoutez un appel à <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> pour obtenir l'objet <xref:EnvDTE80.DTE2> :

   ```csharp
   DTE2 dte = (DTE2)GetService(typeof(DTE));
   ```

5. Ajoutez le code de votre complément qui se trouve dans sa méthode `IDTCommandTarget.Exec`. Par exemple, voici du code qui ajoute un nouveau volet à la **sortie** fenêtre et imprime du « Texte » dans le nouveau volet.

   ```csharp
   private void MenuItemCallback(object sender, EventArgs e)
   {
       DTE2 dte = (DTE2) GetService(typeof(DTE));
       OutputWindow outputWindow = dte.ToolWindows.OutputWindow;

       OutputWindowPane outputWindowPane = outputWindow.OutputWindowPanes.Add("A New Pane");
       outputWindowPane.OutputString("Some Text");
   }

   ```

6. Générez et exécutez ce projet. Appuyez sur **F5** ou sélectionnez **Démarrer** sur le **déboguer** barre d’outils. Dans l’instance expérimentale de Visual Studio, le **outils** menu doit avoir un bouton nommé **mon nom de commande**. Lorsque vous cliquez sur ce bouton, les mots **texte** doit apparaître dans un **sortie** volet de fenêtre. (Vous devrez peut-être ouvrir le **sortie** fenêtre.)

   Votre code peut également s'exécuter au démarrage. Toutefois, cette approche est généralement déconseillée dans le cas des extensions VSPackage. Si un nombre trop élevé d'extensions sont chargées au démarrage de Visual Studio, le démarrage peut durer plus longtemps. Une meilleure pratique consiste à charger automatiquement le VSPackage uniquement quand une condition spécifique est satisfaite (comme l'ouverture d'une solution).

   Cette procédure montre comment exécuter du code de complément dans un VSPackage qui est automatiquement chargé à l'ouverture d'une solution :

### <a name="to-autoload-a-vspackage"></a>Pour charger automatiquement un VSPackage

1. Créez un projet VSIX avec un élément de projet de Package Visual Studio. (Pour savoir comment procéder, consultez [comment démarrer le développement d’extensions VSIX ?](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md#BKMK_StartDeveloping). Il suffit d’ajouter le **Package Visual Studio** l’élément de projet à la place.) Nommez le projet VSIX **TestAutoload**.

2. Ouvrez *TestAutoloadPackage.cs*. Recherchez la ligne où la classe de package est déclarée :

   ```csharp
   public sealed class <name of your package>Package : Package
   ```

3. Un ensemble d'attributs se trouve au-dessus de cette ligne. Ajoutez cet attribut :

   ```csharp
   [ProvideAutoLoad(UIContextGuids80.SolutionExists)]
   ```

4. Définir un point d’arrêt dans le `Initialize()` (méthode) et démarrer le débogage (**F5**).

5. Dans l'instance expérimentale, ouvrez un projet. Le VSPackage doit se charger et votre point d'arrêt doit être atteint.

   Vous pouvez spécifier d'autres contextes dans lesquels charger votre VSPackage en utilisant les champs de <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80>. Pour plus d’informations, consultez [charge VSPackages](../extensibility/loading-vspackages.md).

## <a name="how-can-i-get-the-dte-object"></a>Comment obtenir l'objet DTE ?
 Si votre complément n'affiche pas des éléments d'interface utilisateur, tels que des commandes de menu, des boutons de barre d'outils ou des fenêtres Outil, vous devez pouvoir utiliser votre code tel quel, tant que vous obtenez l'objet d'automation DTE du VSPackage. Voici comment :

### <a name="to-get-the-dte-object-from-a-vspackage"></a>Pour obtenir l'objet DTE d'un VSPackage

1. Dans un projet VSIX avec un modèle d’élément de Package Visual Studio, recherchez le  *\<nom du projet > Package.cs* fichier. Il s'agit de la classe dérivée de <xref:Microsoft.VisualStudio.Shell.Package> ; elle peut vous permettre d'interagir avec Visual Studio. Dans ce cas, vous utilisez sa méthode <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> pour obtenir l'objet <xref:EnvDTE80.DTE2>.

2. Ajoutez ces instructions `using` :

   ```csharp
   using EnvDTE;
   using EnvDTE80;
   ```

3. Recherchez la méthode `Initialize`. Cette méthode gère la commande que vous avez spécifiée dans l'Assistant Package. Ajoutez un appel à <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> pour obtenir l'objet DTE :

   ```csharp
   DTE dte = (DTE)GetService(typeof(DTE));
   ```

   Une fois obtenu l'objet d'automation <xref:EnvDTE.DTE>, vous pouvez ajouter le reste votre code de complément au projet. Si vous avez besoin de l'objet <xref:EnvDTE80.DTE2>, vous pouvez procéder de la même façon.

## <a name="how-do-i-change-menu-commands-and-toolbar-buttons-in-my-add-in-to-the-vspackage-style"></a>Comment attribuer le style de mon complément VSPackage aux commandes de menu et aux boutons de barre d'outils ?
 Utilisation d’extensions VSPackage le *.vsct* fichier pour créer la plupart des commandes de menu, barres d’outils, des boutons de barre d’outils et toute autre interface utilisateur. Le **commande personnalisée** modèle d’élément de projet vous donne la possibilité pour créer une commande sur le **outils** menu. Pour plus d’informations, consultez [créer une extension avec une commande de menu](../extensibility/creating-an-extension-with-a-menu-command.md).

 Pour plus d’informations sur *.vsct* de fichiers, consultez [comment VSPackages ajoute des éléments d’interface utilisateur](../extensibility/internals/how-vspackages-add-user-interface-elements.md). Pour les procédures pas à pas qui montrent comment utiliser le *.vsct* fichier à ajouter des éléments de menu, les barres d’outils et les boutons de barre d’outils, consultez [étendre des menus et commandes](../extensibility/extending-menus-and-commands.md).

## <a name="how-do-i-add-custom-tool-windows-in-the-vspackage-way"></a>Comment ajouter des fenêtres Outil personnalisées à la façon d'un VSPackage ?
 Le modèle d’élément de projet fenêtre d’outil personnalisé vous permet de créer une fenêtre outil. Pour plus d’informations sur ce modèle d’élément de projet, consultez [créer une extension avec une fenêtre outil](../extensibility/creating-an-extension-with-a-tool-window.md). Pour plus d’informations sur les fenêtres Outil, consultez [étendre et personnaliser les fenêtres d’outil](../extensibility/extending-and-customizing-tool-windows.md) et les articles dans cette section, particulièrement [ajouter une fenêtre outil](../extensibility/adding-a-tool-window.md).

## <a name="how-do-i-manage-visual-studio-windows-in-the-vspackage-way"></a>Comment gérer des fenêtres Visual Studio à la façon d'un VSPackage ?
 Si votre complément gère des fenêtres Visual Studio, le code de complément doit fonctionner dans un VSPackage. Par exemple, cette procédure montre comment ajouter du code qui gère la **liste des tâches** à la `MenuItemCallback` méthode du VSPackage.

#### <a name="to-insert-window-management-code-from-an-add-in-into-a-vspackage"></a>Pour insérer du code de gestion de fenêtres à partir d'un complément dans un VSPackage

1.  Créer un VSPackage ayant une commande de menu, comme dans le [comment démarrer le développement d’extensions VSIX ?](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md#BKMK_StartDeveloping) section.

2.  Ouvrez le fichier contenant la définition du VSPackage. (Dans un projet c#, il a  *\<nom de votre projet > Package.cs*.)

3.  Ajoutez ces instructions `using` :

    ```csharp
    using EnvDTE;
    using EnvDTE80;
    ```

4.  Recherchez la méthode `MenuItemCallback`. Ajoutez un appel à <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> pour obtenir l'objet <xref:EnvDTE80.DTE2> :

    ```csharp
    DTE2 dte = (DTE2)GetService(typeof(DTE));
    ```

5.  Ajoutez le code à partir de votre complément. Par exemple, voici du code qui ajoute de nouvelles tâches à la **liste des tâches**, répertorie le nombre de tâches, puis supprime une tâche.

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        DTE2 dte = (DTE2) GetService(typeof(DTE));

        TaskList tl = (TaskList)dte.ToolWindows.TaskList;
        askItem tlItem;

        // Add a couple of tasks to the Task List.
        tlItem = tl.TaskItems.Add(" ", " ", "Test task 1.",
            vsTaskPriority.vsTaskPriorityHigh, vsTaskIcon.vsTaskIconUser,
            true, "", 10, true, true);
        tlItem = tl.TaskItems.Add(" ", " ", "Test task 2.",
            vsTaskPriority.vsTaskPriorityLow, vsTaskIcon.vsTaskIconComment, true, "", 20, true,true);

        // List the total number of task list items after adding the new task items.
        System.Windows.Forms.MessageBox.Show("Task Item 1 description: "+tl.TaskItems.Item(2).Description);
        System.Windows.Forms.MessageBox.Show("Total number of task items: "+tl.TaskItems.Count);

        // Remove the second task item. The items list in reverse numeric order.
        System.Windows.Forms.MessageBox.Show("Deleting the second task item");
        tl.TaskItems.Item(2).Delete();
        System.Windows.Forms.MessageBox.Show("Total number of task items: "+tl.TaskItems.Count);
    }
    ```

## <a name="how-do-i-manage-projects-and-solutions-in-a-vspackage"></a>Comment gérer des projets et des solutions dans un VSPackage ?
 Si votre complément gère des projets et des solutions, le code de complément doit fonctionner dans un VSPackage. Par exemple, cette procédure décrit l'ajout de code qui permet d'obtenir le projet de démarrage.

1.  Créer un VSPackage ayant une commande de menu, comme dans le [comment démarrer le développement d’extensions VSIX ?](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md#BKMK_StartDeveloping) section.

2.  Ouvrez le fichier contenant la définition du VSPackage. (Dans un projet c#, il a  *\<nom de votre projet > Package.cs*.)

3.  Ajoutez ces instructions `using` :

    ```csharp
    using EnvDTE;
    using EnvDTE80;
    ```

4.  Recherchez la méthode `MenuItemCallback`. Ajoutez un appel à <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> pour obtenir l'objet <xref:EnvDTE80.DTE2> :

    ```csharp
    DTE2 dte = (DTE2)GetService(typeof(DTE));
    ```

5.  Ajoutez le code à partir de votre complément. Par exemple, le code suivant vous permet d'obtenir le nom du projet de démarrage dans une solution. (Une solution comprenant plusieurs projets doit être ouverte quand ce package est exécuté.)

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        DTE2 dte = (DTE2) GetService(typeof(DTE));

        SolutionBuild2 sb = (SolutionBuild2)dte.Solution.SolutionBuild;
        Project startupProj;
        string msg = "";

        foreach (String item in (Array)sb.StartupProjects)
        {
            msg += item;
        }
        System.Windows.Forms.MessageBox.Show("Solution startup Project: "+msg);
        startupProj = dte.Solution.Item(msg);
        System.Windows.Forms.MessageBox.Show("Full name of solution's startup project: "+"/n"+startupProj.FullName);
    }
    ```

## <a name="how-do-i-set-keyboard-shortcuts-in-a-vspackage"></a>Comment définir des raccourcis clavier dans un VSPackage ?
 Vous utilisez le `<KeyBindings>` élément de la *.vsct* fichier. Dans l’exemple suivant, le raccourci clavier de la commande `idCommand1` est **Alt**+**A**et le raccourci clavier de la commande `idCommand2` est **Alt**  + **Ctrl**+**A**. Notez la syntaxe des noms de touches.

```xml
<KeyBindings>
    <KeyBinding guid="MyProjectCmdSet" id="idCommand1" editor="guidVSStd97" key1="A" mod1="ALT" />
    <KeyBinding guid="MyProjectCmdSet" id="idCommand2" editor="guidVSStd97" key1="A" mod1="CONTROL" mod2="ALT" />
</KeyBindings>
```

## <a name="how-do-i-handle-automation-events-in-a-vspackage"></a>Comment gérer des événements d'automation dans un VSPackage ?
 Vous gérez des événements d'automation dans un VSPackage de la même façon que dans votre complément. Le code suivant illustre la gestion de l'événement `OnItemRenamed`. (Cet exemple suppose que vous avez déjà obtenu l'objet DTE.)

```csharp
Events2 dteEvents = (Events2)dte.Events;
dteEvents.ProjectItemsEvents.ItemRenamed += listener1.OnItemRenamed;
. . .
public void OnItemRenamed(EnvDTE.ProjectItem projItem, string oldName)
{
    string s = "[Event] Renamed " + oldName + " to " + Path.GetFileName(projItem.get_FileNames(1) + " in project " + projItem.ContainingProject.Name;
}
```