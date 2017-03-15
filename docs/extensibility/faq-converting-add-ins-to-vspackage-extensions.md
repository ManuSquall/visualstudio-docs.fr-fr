---
title: "Forum aux questions : Conversion des compléments en extensions VSPackage | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3a01d333-6e31-423f-ae06-5091a4fcb7a9
caps.latest.revision: 22
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: dd7451b090cb9f25f85d08341b6d38130a13942b
ms.lasthandoff: 02/22/2017

---
# <a name="faq-converting-add-ins-to-vspackage-extensions"></a>FAQ : conversion de compléments en extensions VSPackage
Les compléments sont désormais déconseillés. Pour effectuer une nouvelle extension de Visual Studio, vous devez créer une extension VSIX. Voici les réponses aux questions fréquemment posées sur la façon de convertir un complément Visual Studio à une extension VSIX.  
  
> [!WARNING]
>  À compter de Visual Studio 2015, pour les projets c# et Visual Basic, vous pouvez utiliser le projet VSIX et ajouter des modèles d’élément pour les commandes de menu, fenêtres Outil et des VSPackages. Pour plus d’informations, consultez [Nouveautés dans le Kit de développement logiciel Visual Studio 2015](../extensibility/what-s-new-in-the-visual-studio-2015-sdk.md).  
  
> [!IMPORTANT]
>  Dans de nombreux cas, vous pouvez simplement transférer votre code de complément à un projet VSIX avec un élément de projet VSPackage. Vous pouvez obtenir l’objet automation DTE en appelant <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A>dans le <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>méthode.</xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> </xref:Microsoft.VisualStudio.Shell.Package.GetService%2A>  
>   
>  `DTE2 dte = (DTE2)GetService(typeof(DTE));`  
>   
>  Pour plus d’informations, consultez [comment exécuter le code de mon complément dans un VSPackage ?](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md#BKMK_RunAddin) ci-dessous.  
  
## <a name="what-software-do-i-need-to-develop-vsix-extensions"></a>Quel logiciel ai-je besoin développer des extensions VSIX ?  
 À partir de Visual Studio 2015, vous n’installez pas Visual Studio SDK à partir du centre de téléchargement. Il est inclus comme fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le Kit de développement logiciel Visual Studio plus tard. Pour plus d’informations, consultez [l’installation du Kit de développement logiciel Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="wheres-the-extension-documentation"></a>Où se trouve la documentation de l’extension ?  
 Démarrer avec [commencer à développer des Extensions Visual Studio](../extensibility/starting-to-develop-visual-studio-extensions.md). Autres articles sur le développement d’extensions VSSDK sur MSDN sont situés sous ce.  
  
## <a name="can-i-convert-my-add-in-project-to-a-vsix-project"></a>Puis-je convertir mon projet de complément à un projet VSIX ?  
 Impossible de convertir un projet de complément directement à un projet VSIX, car les mécanismes utilisés dans des projets VSIX ne sont pas les mêmes que celles dans les projets de complément. Le modèle de projet VSIX, ainsi que les modèles d’élément de projet appropriés ont beaucoup de code qui rend relativement facile à la création et en cours d’exécution comme une extension VSIX.  
  
##  <a name="a-namebkmkstartdevelopinga-how-do-i-start-developing-vsix-extensions"></a><a name="BKMK_StartDeveloping"></a>Comment commencer à développer des extensions VSIX ?  
 Voici comment procéder à une extension VSIX qui contient une commande :  
  
#### <a name="to-make-a-vsix-extension-that-has-a-menu-command"></a>Pour créer une extension VSIX qui dispose d’une commande de menu  
  
1.  Créez un projet VSIX. (**Fichier**, **nouveau**, **projet**, ou de type **projet** dans les **lancement rapide** fenêtre). Dans le **nouveau projet** boîte de dialogue, développez **Visual C# / extensibilité** ou **Visual Basic / extensibilité** et sélectionnez **projet VSIX**.) Nommez le projet **TestExtension** et spécifier un emplacement pour celui-ci.  
  
2.  Ajouter un **personnalisée** modèle d’élément de projet. (Cliquez sur le nœud de projet dans le **l’Explorateur de solutions** et sélectionnez **Ajouter / nouvel élément**. Dans le **nouveau projet** boîte de dialogue pour Visual c# ou Visual Basic, sélectionnez le **extensibilité** nœud et sélectionnez **personnalisée**.)  
  
3.  Appuyez sur la touche F5 pour exécuter le projet en mode débogage.  
  
     Une seconde instance de Visual Studio apparaît. Celle-ci est appelée instance expérimentale. Ses paramètres peuvent différer de ceux de l'instance de Visual Studio qui vous sert à écrire du code. À la première exécution de l'instance expérimentale, vous êtes invité à vous connecter à VS en ligne et à spécifier vos thème et profil.  
  
     Sur le **outils** menu (dans l’instance expérimentale), vous devez voir un bouton nommé **mon nom de commande**. Lorsque vous cliquez sur ce bouton, un message doit apparaître : **dans testvspackagepackage.MenuItemCallback ()**.  
  
##  <a name="a-namebkmkrunaddina-how-can-i-run-my-add-in-code-in-a-vspackage"></a><a name="BKMK_RunAddin"></a>Comment puis-je exécuter mon code de complément dans un VSPackage ?  
 Un code de complément s'exécute généralement de l'une des deux façons suivantes :  
  
-   déclenché par une commande de menu (le code se trouve dans la méthode `IDTCommandTarget.Exec`) ;  
  
-   automatiquement au démarrage (le code se trouve dans le gestionnaire d'événements `OnConnection`.).  
  
 Vous pouvez procéder de la même façon dans un VSPackage. Voici comment ajouter du code de complément dans une méthode de rappel :  
  
#### <a name="to-implement-a-menu-command-in-a-vspackage"></a>Pour implémenter une commande de menu dans un VSPackage  
  
1.  Créez un VSPackage comportant une commande de menu. (Pour plus d’informations, consultez [avec une commande de Menu pour créer une Extension](../extensibility/creating-an-extension-with-a-menu-command.md).)  
  
2.  Ouvrez le fichier contenant la définition du VSPackage. (Dans un projet c#, il a * \<nom de votre projet >*Package.cs.)  
  
3.  Ajoutez les instructions `using` suivantes au fichier :  
  
    ```c#  
    using EnvDTE;  
    using EnvDTE80;  
    ```  
  
4.  Recherchez la méthode `MenuItemCallback`. Ajoutez un appel à <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A>pour obtenir le <xref:EnvDTE80.DTE2>objet :</xref:EnvDTE80.DTE2> </xref:Microsoft.VisualStudio.Shell.Package.GetService%2A>  
  
    ```c#  
    DTE2 dte = (DTE2)GetService(typeof(DTE));  
    ```  
  
5.  Ajoutez le code de votre complément qui se trouve dans sa méthode `IDTCommandTarget.Exec`. Par exemple, voici du code qui ajoute un nouveau volet à la **sortie** fenêtre et imprime « Texte » dans le volet Nouveau.  
  
    ```c#  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        DTE2 dte = (DTE2) GetService(typeof(DTE));  
        OutputWindow outputWindow = dte.ToolWindows.OutputWindow;  
  
        OutputWindowPane outputWindowPane = outputWindow.OutputWindowPanes.Add("A New Pane");  
        outputWindowPane.OutputString("Some Text");  
    }  
  
    ```  
  
6.  Générez et exécutez ce projet. Appuyez sur F5 ou sélectionnez **Démarrer** sur la **Debug** barre d’outils. Dans l’instance expérimentale de Visual Studio, le **outils** menu doit avoir un bouton nommé **mon nom de commande**. Lorsque vous cliquez sur ce bouton, la mention **texte** doit apparaître dans un **sortie** volet de fenêtre. (Vous devrez peut-être ouvrir le **sortie** fenêtre.)  
  
 Votre code peut également s'exécuter au démarrage. Toutefois, cette approche est généralement déconseillée dans le cas des extensions VSPackage. Si un nombre trop élevé d'extensions sont chargées au démarrage de Visual Studio, le démarrage peut durer plus longtemps. Une meilleure pratique consiste à charger automatiquement le VSPackage uniquement quand une condition spécifique est satisfaite (comme l'ouverture d'une solution).  
  
 Cette procédure montre comment exécuter du code de complément dans un VSPackage qui est automatiquement chargé à l'ouverture d'une solution :  
  
#### <a name="to-autoload-a-vspackage"></a>Pour charger automatiquement un VSPackage  
  
1.  Avec un élément de projet de Package Visual Studio, créez un projet VSIX. (Pour connaître les étapes à suivre, consultez [comment démarrer le développement d’extensions VSIX ?](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md#BKMK_StartDeveloping). Il suffit d’ajouter le **Package Visual Studio** d’élément de projet à la place.) Nommez le projet VSIX **TestAutoload**.  
  
2.  Ouvrez TestAutoloadPackage.cs. Recherchez la ligne où la classe de package est déclarée :  
  
    ```c#  
    public sealed class <name of your package>Package : Package  
    ```  
  
3.  Un ensemble d'attributs se trouve au-dessus de cette ligne. Ajoutez cet attribut :  
  
    ```c#  
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]  
    ```  
  
4.  Définissez un point d'arrêt dans la méthode `Initialize()` et démarrez le débogage (F5).  
  
5.  Dans l'instance expérimentale, ouvrez un projet. Le VSPackage doit se charger et votre point d'arrêt doit être atteint.  
  
 Vous pouvez spécifier d’autres contextes dans lesquels charger votre VSPackage en utilisant les champs de <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80>.</xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> Pour plus d’informations, consultez [le chargement de packages VS](../extensibility/loading-vspackages.md).  
  
## <a name="how-can-i-get-the-dte-object"></a>Comment obtenir l'objet DTE ?  
 Si votre complément n'affiche pas des éléments d'interface utilisateur, tels que des commandes de menu, des boutons de barre d'outils ou des fenêtres Outil, vous devez pouvoir utiliser votre code tel quel, tant que vous obtenez l'objet d'automation DTE du VSPackage. Voici comment :  
  
#### <a name="to-get-the-dte-object-from-a-vspackage"></a>Pour obtenir l'objet DTE d'un VSPackage  
  
1.  Dans un projet VSIX, avec un modèle d’élément de Package Visual Studio, recherchez le * \<le nom du projet >*fichier Package.cs. C’est la classe qui dérive de <xref:Microsoft.VisualStudio.Shell.Package>; il peut vous aider à interagir avec Visual Studio.</xref:Microsoft.VisualStudio.Shell.Package> Dans ce cas, vous utilisez ses <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A>pour obtenir le <xref:EnvDTE80.DTE2>objet.</xref:EnvDTE80.DTE2> </xref:Microsoft.VisualStudio.Shell.Package.GetService%2A>  
  
2.  Ajoutez ces instructions `using` :  
  
    ```c#  
    using EnvDTE;  
    using EnvDTE80;  
    ```  
  
3.  Recherchez la méthode `Initialize`. Cette méthode gère la commande que vous avez spécifiée dans l'Assistant Package. Ajoutez un appel à <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A>pour obtenir l’objet DTE :</xref:Microsoft.VisualStudio.Shell.Package.GetService%2A>  
  
    ```c#  
    DTE dte = (DTE)GetService(typeof(DTE));  
    ```  
  
 Après avoir configuré le <xref:EnvDTE.DTE>d’objet automation, vous pouvez ajouter le reste de votre code de complément au projet.</xref:EnvDTE.DTE> Si vous avez besoin du <xref:EnvDTE80.DTE2>de l’objet, vous pouvez faire la même chose.</xref:EnvDTE80.DTE2>  
  
## <a name="how-do-i-change-menu-commands-and-toolbar-buttons-in-my-add-in-to-the-vspackage-style"></a>Comment attribuer le style de mon complément VSPackage aux commandes de menu et aux boutons de barre d'outils ?  
 Les extensions VSPackage utilisent le fichier .vsct pour créer la plupart des commandes de menu, les barres d'outils et autres éléments d'interface utilisateur. Le **personnalisée** modèle de projet vous donne la possibilité de créer une commande sur le **outils** menu. Pour plus d’informations, consultez [avec une commande de Menu pour créer une Extension](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
 Pour plus d’informations sur les fichiers .vsct, consultez [comment VSPackages ajouter des éléments d’Interface utilisateur](../extensibility/internals/how-vspackages-add-user-interface-elements.md). Pour les procédures pas à pas qui montrent comment utiliser le fichier .vsct pour ajouter des éléments de menu, les barres d’outils et les boutons de barre d’outils, consultez [extension des Menus et des commandes](../extensibility/extending-menus-and-commands.md).  
  
## <a name="how-do-i-add-custom-tool-windows-in-the-vspackage-way"></a>Comment ajouter des fenêtres Outil personnalisées à la façon d'un VSPackage ?  
 Le modèle de projet de fenêtre de l’outil personnalisé vous permet de créer une fenêtre outil. Pour plus d’informations sur ce modèle de projet, consultez [création d’une Extension avec une fenêtre outil](../extensibility/creating-an-extension-with-a-tool-window.md). Pour plus d’informations sur les fenêtres Outil, consultez [extension et personnalisation des fenêtres Outil](../extensibility/extending-and-customizing-tool-windows.md) et les articles, en particulier [Ajout d’une fenêtre outil](../extensibility/adding-a-tool-window.md).  
  
## <a name="how-do-i-manage-visual-studio-windows-in-the-vspackage-way"></a>Comment gérer des fenêtres Visual Studio à la façon d'un VSPackage ?  
 Si votre complément gère des fenêtres Visual Studio, le code de complément doit fonctionner dans un VSPackage. Par exemple, cette procédure montre comment ajouter du code qui gère la **liste des tâches** à la `MenuItemCallback` méthode du VSPackage.  
  
#### <a name="to-insert-window-management-code-from-an-add-in-into-a-vspackage"></a>Pour insérer du code de gestion de fenêtres à partir d'un complément dans un VSPackage  
  
1.  Créer un VSPackage doté d’une commande de menu, comme dans le [comment démarrer le développement d’extensions VSIX ?](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md#BKMK_StartDeveloping) section.  
  
2.  Ouvrez le fichier contenant la définition du VSPackage. (Dans un projet c#, il a * \<nom de votre projet >*Package.cs.)  
  
3.  Ajoutez ces instructions `using` :  
  
    ```c#  
    using EnvDTE;  
    using EnvDTE80;  
    ```  
  
4.  Recherchez la méthode `MenuItemCallback`. Ajoutez un appel à <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A>pour obtenir le <xref:EnvDTE80.DTE2>objet :</xref:EnvDTE80.DTE2> </xref:Microsoft.VisualStudio.Shell.Package.GetService%2A>  
  
    ```c#  
    DTE2 dte = (DTE2)GetService(typeof(DTE));  
    ```  
  
5.  Ajoutez le code à partir de votre complément. Par exemple, voici du code qui ajoute de nouvelles tâches à la **liste des tâches**indique le nombre de tâches et supprimer une tâche.  
  
    ```c#  
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
  
1.  Créer un VSPackage doté d’une commande de menu, comme dans le [comment démarrer le développement d’extensions VSIX ?](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md#BKMK_StartDeveloping) section.  
  
2.  Ouvrez le fichier contenant la définition du VSPackage. (Dans un projet c#, il a * \<nom de votre projet >*Package.cs.)  
  
3.  Ajoutez ces instructions `using` :  
  
    ```c#  
    using EnvDTE;  
    using EnvDTE80;  
    ```  
  
4.  Recherchez la méthode `MenuItemCallback`. Ajoutez un appel à <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A>pour obtenir le <xref:EnvDTE80.DTE2>objet :</xref:EnvDTE80.DTE2> </xref:Microsoft.VisualStudio.Shell.Package.GetService%2A>  
  
    ```c#  
    DTE2 dte = (DTE2)GetService(typeof(DTE));  
    ```  
  
5.  Ajoutez le code à partir de votre complément. Par exemple, le code suivant vous permet d'obtenir le nom du projet de démarrage dans une solution. (Une solution comprenant plusieurs projets doit être ouverte quand ce package est exécuté.)  
  
    ```c#  
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
  
```c#  
Events2 dteEvents = (Events2)dte.Events;  
dteEvents.ProjectItemsEvents.ItemRenamed += listener1.OnItemRenamed;   
. . .  
public void OnItemRenamed(EnvDTE.ProjectItem projItem, string oldName)   
{  
    string s = "[Event] Renamed " + oldName + " to " + Path.GetFileName(projItem.get_FileNames(1) + " in project " + projItem.ContainingProject.Name;   
}  
```
