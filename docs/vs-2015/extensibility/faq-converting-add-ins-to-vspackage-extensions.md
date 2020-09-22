---
title: 'FAQ : conversion des compléments en extensions VSPackage | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 3a01d333-6e31-423f-ae06-5091a4fcb7a9
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bc6ed31f96fc2021d0d9e104692f0440cfb78a5e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839986"
---
# <a name="faq-converting-add-ins-to-vspackage-extensions"></a>FAQ : conversion de compléments en extensions VSPackage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les compléments sont désormais déconseillés. Pour créer une nouvelle extension Visual Studio, vous devez créer une extension VSIX. Voici les réponses à certaines questions fréquemment posées sur la conversion d’un complément Visual Studio en extension VSIX.  
  
> [!WARNING]
> À compter de Visual Studio 2015, pour les projets C# et Visual Basic, vous pouvez utiliser le projet VSIX et ajouter des modèles d’élément pour les commandes de menu, les fenêtres outil et les VSPackages. Pour plus d’informations, consultez [Nouveautés du kit de développement logiciel (SDK) Visual Studio 2015](../extensibility/what-s-new-in-the-visual-studio-2015-sdk.md).  
  
> [!IMPORTANT]
> Dans de nombreux cas, vous pouvez simplement transférer votre code de complément vers un projet VSIX à l’aide d’un élément de projet VSPackage. Vous pouvez obtenir l'objet automation DTE en appelant <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> dans la méthode <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>.  
>   
> `DTE2 dte = (DTE2)GetService(typeof(DTE));`  
>   
> Pour plus d’informations, consultez [Comment puis-je exécuter mon code de complément dans un VSPackage ?](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md#BKMK_RunAddin) ci-dessous.  
  
## <a name="what-software-do-i-need-to-develop-vsix-extensions"></a>De quel logiciel ai-je besoin pour développer des extensions VSIX ?  
 À compter de Visual Studio 2015, vous n’installez pas le kit de développement logiciel (SDK) Visual Studio à partir du centre de téléchargement. Il est inclus en tant que fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit de développement logiciel (SDK) Visual Studio plus tard. Pour plus d’informations, consultez [installation du kit de développement logiciel (SDK) Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="wheres-the-extension-documentation"></a>Où se trouve la documentation de l’extension ?  
 Commencez par commencer [à développer des extensions Visual Studio](../extensibility/starting-to-develop-visual-studio-extensions.md). D’autres articles sur le développement d’extensions VSSDK sur MSDN sont en dessous de celui-ci.  
  
## <a name="can-i-convert-my-add-in-project-to-a-vsix-project"></a>Puis-je convertir mon projet de complément en projet VSIX ?  
 Un projet de complément ne peut pas être converti directement en projet VSIX, car les mécanismes utilisés dans les projets VSIX ne sont pas les mêmes que ceux des projets de complément. Le modèle de projet VSIX, ainsi que les modèles d’élément de projet appropriés, comportent beaucoup de code qui facilite l’installation et l’exécution en tant qu’extension VSIX.  
  
## <a name="how-do-i-start-developing-vsix-extensions"></a><a name="BKMK_StartDeveloping"></a> Comment faire commencer à développer des extensions VSIX ?  
 Voici comment créer un VSIX qui a une commande de menu :  
  
#### <a name="to-make-a-vsix-extension-that-has-a-menu-command"></a>Pour créer une extension VSIX qui a une commande de menu  
  
1. Créez un projet VSIX. (**Fichier**, **nouveau**, **projet**ou type **projet** dans la fenêtre **lancement rapide** ). Dans la boîte de dialogue **nouveau projet** , développez **Visual C#/Extensibility** ou **Visual Basic/extensibilité** , puis sélectionnez **projet VSIX**.) Nommez le projet **TestExtension** et spécifiez un emplacement pour celui-ci.  
  
2. Ajoutez un modèle d’élément de projet de **commande personnalisé** . (Cliquez avec le bouton droit sur le nœud du projet dans le **Explorateur de solutions** puis sélectionnez **Ajouter/nouvel élément**. Dans la boîte de dialogue **nouveau projet** pour Visual C# ou Visual Basic, sélectionnez le nœud **extensibilité** et sélectionnez **commande personnalisée**.)  
  
3. Appuyez sur la touche F5 pour exécuter le projet en mode débogage.  
  
     Une seconde instance de Visual Studio apparaît. Celle-ci est appelée instance expérimentale. Ses paramètres peuvent différer de ceux de l'instance de Visual Studio qui vous sert à écrire du code. À la première exécution de l'instance expérimentale, vous êtes invité à vous connecter à VS en ligne et à spécifier vos thème et profil.  
  
     Dans le menu **Outils** (dans l’instance expérimentale), vous devez voir un bouton nommé **mon nom de commande**. Quand vous choisissez ce bouton, un message doit s’afficher : **dans TestVSPackagePackage. MenuItemCallback ()**.  
  
## <a name="how-can-i-run-my-add-in-code-in-a-vspackage"></a><a name="BKMK_RunAddin"></a> Comment puis-je exécuter le code de mon complément dans un VSPackage ?  
 Un code de complément s'exécute généralement de l'une des deux façons suivantes :  
  
- déclenché par une commande de menu (le code se trouve dans la méthode `IDTCommandTarget.Exec`) ;  
  
- automatiquement au démarrage (le code se trouve dans le gestionnaire d'événements `OnConnection`.).  
  
  Vous pouvez procéder de la même façon dans un VSPackage. Voici comment ajouter du code de complément dans une méthode de rappel :  
  
#### <a name="to-implement-a-menu-command-in-a-vspackage"></a>Pour implémenter une commande de menu dans un VSPackage  
  
1. Créez un VSPackage comportant une commande de menu. (Pour plus d’informations, consultez [création d’une extension à l’aide d’une commande de menu](../extensibility/creating-an-extension-with-a-menu-command.md).)  
  
2. Ouvrez le fichier contenant la définition du VSPackage. (Dans un projet C#, il s’agit <em>\<your project name></em> de Package.cs.)  
  
3. Ajoutez les instructions `using` suivantes au fichier :  
  
   ```csharp  
   using EnvDTE;  
   using EnvDTE80;  
   ```  
  
4. Recherchez la méthode `MenuItemCallback`. Ajoutez un appel à <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> pour obtenir l'objet <xref:EnvDTE80.DTE2> :  
  
   ```csharp  
   DTE2 dte = (DTE2)GetService(typeof(DTE));  
   ```  
  
5. Ajoutez le code de votre complément qui se trouve dans sa méthode `IDTCommandTarget.Exec`. Par exemple, voici du code qui ajoute un nouveau volet à la fenêtre **sortie** et imprime un texte dans le nouveau volet.  
  
   ```csharp  
   private void MenuItemCallback(object sender, EventArgs e)  
   {  
       DTE2 dte = (DTE2) GetService(typeof(DTE));  
       OutputWindow outputWindow = dte.ToolWindows.OutputWindow;  
  
       OutputWindowPane outputWindowPane = outputWindow.OutputWindowPanes.Add("A New Pane");  
       outputWindowPane.OutputString("Some Text");  
   }  
  
   ```  
  
6. Générez et exécutez ce projet. Appuyez sur F5 ou sélectionnez **Démarrer** dans la barre d’outils **Déboguer** . Dans l’instance expérimentale de Visual Studio, le menu **Outils** doit avoir un bouton nommé **mon nom de commande**. Quand vous choisissez ce bouton, les mots du **texte** doivent apparaître dans un volet de la fenêtre **sortie** . (Vous devrez peut-être ouvrir la fenêtre **sortie** .)  
  
   Votre code peut également s'exécuter au démarrage. Toutefois, cette approche est généralement déconseillée dans le cas des extensions VSPackage. Si un nombre trop élevé d'extensions sont chargées au démarrage de Visual Studio, le démarrage peut durer plus longtemps. Une meilleure pratique consiste à charger automatiquement le VSPackage uniquement quand une condition spécifique est satisfaite (comme l'ouverture d'une solution).  
  
   Cette procédure montre comment exécuter du code de complément dans un VSPackage qui est automatiquement chargé à l'ouverture d'une solution :  
  
#### <a name="to-autoload-a-vspackage"></a>Pour charger automatiquement un VSPackage  
  
1. Créez un projet VSIX avec un élément de projet de package Visual Studio. (Pour connaître les étapes à suivre, consultez [Comment faire commencer à développer des extensions VSIX ?](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md#BKMK_StartDeveloping). Il vous suffit d’ajouter l’élément de projet de **package Visual Studio** .) Nommez le projet VSIX **TestAutoload**.  
  
2. Ouvrez TestAutoloadPackage.cs. Recherchez la ligne où la classe de package est déclarée :  
  
   ```csharp  
   public sealed class <name of your package>Package : Package  
   ```  
  
3. Un ensemble d'attributs se trouve au-dessus de cette ligne. Ajoutez cet attribut :  
  
   ```csharp  
   [ProvideAutoLoad(UIContextGuids80.SolutionExists)]  
   ```  
  
4. Définissez un point d'arrêt dans la méthode `Initialize()` et démarrez le débogage (F5).  
  
5. Dans l'instance expérimentale, ouvrez un projet. Le VSPackage doit se charger et votre point d'arrêt doit être atteint.  
  
   Vous pouvez spécifier d'autres contextes dans lesquels charger votre VSPackage en utilisant les champs de <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80>. Pour plus d’informations, consultez [chargement des VSPackages](../extensibility/loading-vspackages.md).  
  
## <a name="how-can-i-get-the-dte-object"></a>Comment obtenir l'objet DTE ?  
 Si votre complément n'affiche pas des éléments d'interface utilisateur, tels que des commandes de menu, des boutons de barre d'outils ou des fenêtres Outil, vous devez pouvoir utiliser votre code tel quel, tant que vous obtenez l'objet d'automation DTE du VSPackage. Voici comment procéder :  
  
#### <a name="to-get-the-dte-object-from-a-vspackage"></a>Pour obtenir l'objet DTE d'un VSPackage  
  
1. Dans un projet VSIX avec un modèle d’élément de package Visual Studio, recherchez le <em>\<project name></em> fichier Package.cs. Il s'agit de la classe dérivée de <xref:Microsoft.VisualStudio.Shell.Package> ; elle peut vous permettre d'interagir avec Visual Studio. Dans ce cas, vous utilisez sa méthode <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> pour obtenir l'objet <xref:EnvDTE80.DTE2>.  
  
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
 Les extensions VSPackage utilisent le fichier .vsct pour créer la plupart des commandes de menu, les barres d'outils et autres éléments d'interface utilisateur. Le modèle d’élément de projet de **commande personnalisée** vous donne la possibilité de créer une commande dans le menu **Outils** . Pour plus d’informations, consultez [création d’une extension à l’aide d’une commande de menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
 Pour plus d’informations sur les fichiers. vsct, consultez [Comment les VSPackages ajoutent des éléments d’interface utilisateur](../extensibility/internals/how-vspackages-add-user-interface-elements.md). Pour obtenir des procédures pas à pas qui montrent comment utiliser le fichier. vsct pour ajouter des éléments de menu, des barres d’outils et des boutons de barre d’outils, consultez [extension des menus et des commandes](../extensibility/extending-menus-and-commands.md).  
  
## <a name="how-do-i-add-custom-tool-windows-in-the-vspackage-way"></a>Comment ajouter des fenêtres Outil personnalisées à la façon d'un VSPackage ?  
 Le modèle d’élément de projet de fenêtre outil personnalisée vous donne la possibilité de créer une fenêtre outil. Pour plus d’informations sur ce modèle d’élément de projet, consultez [création d’une extension avec une fenêtre outil](../extensibility/creating-an-extension-with-a-tool-window.md). Pour plus d’informations sur les fenêtres outil, consultez [extension et personnalisation des fenêtres outil](../extensibility/extending-and-customizing-tool-windows.md) et des articles qui la composent, en particulier l' [Ajout d’une fenêtre outil](../extensibility/adding-a-tool-window.md).  
  
## <a name="how-do-i-manage-visual-studio-windows-in-the-vspackage-way"></a>Comment gérer des fenêtres Visual Studio à la façon d'un VSPackage ?  
 Si votre complément gère des fenêtres Visual Studio, le code de complément doit fonctionner dans un VSPackage. Par exemple, cette procédure montre comment ajouter du code qui gère le **liste des tâches** à la `MenuItemCallback` méthode du VSPackage.  
  
#### <a name="to-insert-window-management-code-from-an-add-in-into-a-vspackage"></a>Pour insérer du code de gestion de fenêtres à partir d'un complément dans un VSPackage  
  
1. Créez un VSPackage qui a une commande de menu, comme dans la section [Comment faire démarrer le développement d’extensions VSIX ?](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md#BKMK_StartDeveloping) .  
  
2. Ouvrez le fichier contenant la définition du VSPackage. (Dans un projet C#, il s’agit <em>\<your project name></em> de Package.cs.)  
  
3. Ajoutez ces instructions `using` :  
  
   ```csharp  
   using EnvDTE;  
   using EnvDTE80;  
   ```  
  
4. Recherchez la méthode `MenuItemCallback`. Ajoutez un appel à <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> pour obtenir l'objet <xref:EnvDTE80.DTE2> :  
  
   ```csharp  
   DTE2 dte = (DTE2)GetService(typeof(DTE));  
   ```  
  
5. Ajoutez le code à partir de votre complément. Par exemple, voici du code qui ajoute de nouvelles tâches au **liste des tâches**, répertorie le nombre de tâches, puis supprime une tâche.  
  
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
  
1. Créez un VSPackage qui a une commande de menu, comme dans la section [Comment faire démarrer le développement d’extensions VSIX ?](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md#BKMK_StartDeveloping) .  
  
2. Ouvrez le fichier contenant la définition du VSPackage. (Dans un projet C#, il s’agit <em>\<your project name></em> de Package.cs.)  
  
3. Ajoutez ces instructions `using` :  
  
   ```csharp  
   using EnvDTE;  
   using EnvDTE80;  
   ```  
  
4. Recherchez la méthode `MenuItemCallback`. Ajoutez un appel à <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> pour obtenir l'objet <xref:EnvDTE80.DTE2> :  
  
   ```csharp  
   DTE2 dte = (DTE2)GetService(typeof(DTE));  
   ```  
  
5. Ajoutez le code à partir de votre complément. Par exemple, le code suivant vous permet d'obtenir le nom du projet de démarrage dans une solution. (Une solution comprenant plusieurs projets doit être ouverte quand ce package est exécuté.)  
  
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
 Vous utilisez l'élément `<KeyBindings>` du ficher .vsct. Dans l'exemple suivant, le raccourci clavier de la commande `idCommand1` est Alt+A, et celui de la commande `idCommand2` est Alt+Ctrl+A. Notez la syntaxe des noms de touches.  
  
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
