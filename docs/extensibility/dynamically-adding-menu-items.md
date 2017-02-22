---
title: "Ajouter dynamiquement des &#233;l&#233;ments de Menu | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "DYNAMICITEMSTART"
  - "ajouter dynamiquement des éléments de menu"
  - "menus, ajouter des éléments dynamiques"
ms.assetid: d281e9c9-b289-4d64-8d0a-094bac6c333c
caps.latest.revision: 37
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 37
---
# Ajouter dynamiquement des &#233;l&#233;ments de Menu
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vous pouvez ajouter des éléments de menu au moment de l’exécution en spécifiant le `DynamicItemStart` commande indicateur sur une définition de bouton d’espace réservé dans le fichier de table de commande \(.vsct\) de Visual Studio, puis définir \(dans le code\), le nombre de menu d’éléments à afficher et gérer les commandes. Lorsque le VSPackage est chargé, l’espace réservé est remplacé par les éléments de menu dynamique.  
  
 Visual Studio utilise les listes dynamiques dans le **récents** liste \(MRU\), qui affiche les noms des documents récemment ouverts, et le **Windows** liste qui affiche les noms de windows qui sont actuellement ouverts. Le `DynamicItemStart` indicateur sur une définition de commande indique que la commande est un espace réservé jusqu'à ce que le VSPackage est ouvert. Lorsque le VSPackage est ouvert, l’espace réservé est remplacé par 0 ou plus de commandes qui sont créés au moment de l’exécution et ajoutés à la liste dynamique. Vous n’êtes peut\-être pas en mesure de voir la position dans le menu dans lequel la liste dynamique s’affiche jusqu'à ce que le VSPackage est ouvert. Pour remplir la liste dynamique, Visual Studio vous demande le VSPackage pour rechercher une commande avec un ID dont les premiers caractères sont identiques à l’ID de l’espace réservé. Lorsque Visual Studio détecte une commande, il ajoute le nom de la commande à la liste dynamique. Ensuite, elle incrémente l’ID et recherche d’une autre commande correspondante à ajouter à la liste dynamique jusqu'à ce que les commandes ne plus dynamique.  
  
 Cette procédure pas à pas montre comment définir le projet de démarrage dans une solution Visual Studio avec une commande sur le **l’Explorateur de solutions** barre d’outils. Elle utilise un contrôleur de menu est une liste dynamique des projets de la solution active. Pour conserver cette commande lorsque aucune solution n’est ouverte ou lorsque la solution ouverte n'a qu’un seul projet, le VSPackage est chargé uniquement lorsqu’une solution comporte plusieurs projets.  
  
 Pour plus d’informations sur les fichiers .vsct, consultez la page [Table de commandes de Visual Studio \(. Fichiers VSCT\)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
## Création d’une Extension avec une commande de Menu  
  
1.  Créez un projet VSIX nommé `DynamicMenuItems`.  
  
2.  Lors de l’ouverture du projet, ajouter un modèle d’élément commande personnalisée et nommez\-le **DynamicMenu**. Pour plus d'informations, consultez [Création d'une Extension avec une commande de Menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
## Les éléments de configuration dans le fichier .vsct  
 Pour créer un contrôleur de menu avec des éléments de menu dynamiques dans une barre d’outils, vous spécifiez les éléments suivants :  
  
-   Deux groupes, celui qui contient le contrôleur de menu et une autre qui contient les éléments de menu dans la liste déroulante de commande  
  
-   Un élément de menu de type `MenuController`  
  
-   Deux boutons, qui agit comme un espace réservé pour les éléments de menu et l’autre qui fournit l’icône et l’info\-bulle dans la barre d’outils.  
  
1.  Dans DynamicMenuPackage.vsct, définissez les ID de commande. Accédez à la section Symbols et remplacez les éléments IDSymbol dans les **guidDynamicMenuPackageCmdSet** GuidSymbol bloc. Vous devez définir les éléments IDSymbol pour les deux groupes, le contrôleur de menu, la commande de l’espace réservé et la commande d’ancre.  
  
    ```c#  
    <GuidSymbol name="guidDynamicMenuPackageCmdSet" value="{ your GUID here }">  
        <IDSymbol name="MyToolbarItemGroup" value="0x1020" />  
        <IDSymbol name="MyMenuControllerGroup" value="0x1025" />  
        <IDSymbol name="MyMenuController" value ="0x1030"/>  
        <IDSymbol name="cmdidMyAnchorCommand" value="0x0103" />  
        <!-- NOTE: The following command expands at run time to some number of ids.  
         Try not to place command ids after it (e.g. 0x0105, 0x0106).  
         If you must add a command id after it, make the gap very large (e.g. 0x200) -->  
        <IDSymbol name="cmdidMyDynamicStartCommand" value="0x0104" />  
    </GuidSymbol>    
    ```  
  
2.  Dans la section groupes, supprimez les groupes existants et ajouter les deux groupes que vous venez de définir :  
  
    ```  
    <Groups>  
        <!-- The group that adds the MenuController on the Solution Explorer toolbar.   
             The 0x4000 priority adds this group after the group that contains the  
             Preview Selected Items button, which is normally at the far right of the toolbar. -->  
        <Group guid="guidDynamicMenuPackageCmdSet" id="MyToolbarItemGroup" priority="0x4000" >  
            <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_PROJWIN" />  
        </Group>  
        <!-- The group for the items on the MenuController drop-down. It is added to the MenuController submenu. -->  
        <Group guid="guidDynamicMenuPackageCmdSet" id="MyMenuControllerGroup" priority="0x4000" >  
            <Parent guid="guidDynamicMenuPackageCmdSet" id="MyMenuController" />  
        </Group>  
    </Groups>  
    ```  
  
     Ajoutez le MenuController. Définissez l’indicateur de commande DynamicVisibility, car il n’est pas toujours visible. Le ButtonText n’est pas affichée.  
  
    ```  
    <Menus>  
        <!-- The MenuController to display on the Solution Explorer toolbar.  
             Place it in the ToolbarItemGroup.-->  
        <Menu guid="guidDynamicMenuPackageCmdSet" id="MyMenuController" priority="0x1000" type="MenuController">  
            <Parent guid="guidDynamicMenuPackageCmdSet" id="MyToolbarItemGroup" />  
            <CommandFlag>DynamicVisibility</CommandFlag>  
            <Strings>  
               <ButtonText></ButtonText>  
           </Strings>  
        </Menu>  
    </Menus>  
    ```  
  
3.  Ajoutez deux boutons, comme un espace réservé pour les éléments de menu dynamiques et comme point d’ancrage pour le MenuController.  
  
     Le parent du bouton espace réservé est la **MyMenuControllerGroup**. Ajoutez les indicateurs de commande texteModifie DynamicItemStart et DynamicVisibility sur le bouton de l’espace réservé. Le ButtonText n’est pas affichée.  
  
     Le bouton d’ancrage conserve l’icône et le texte d’info\-bulle. Le parent du bouton d’ancrage est également le **MyMenuControllerGroup**. Vous ajoutez l’indicateur de commande NoShowOnMenuController pour vous assurer que le bouton n’apparaît pas réellement dans le menu déroulant de contrôleur et l’indicateur de commande FixMenuController afin de faciliter l’ancre permanente.  
  
    ```  
    <!-- The placeholder for the dynamic items that expand to N items at runtime. -->  
    <Buttons>  
        <Button guid="guidDynamicMenuPackageCmdSet" id="cmdidMyDynamicStartCommand" priority="0x1000" >  
          <Parent guid="guidDynamicMenuPackageCmdSet" id="MyMenuControllerGroup" />  
          <CommandFlag>DynamicItemStart</CommandFlag>  
          <CommandFlag>DynamicVisibility</CommandFlag>  
          <CommandFlag>TextChanges</CommandFlag>  
          <!-- This text does not appear. -->  
          <Strings>  
            <ButtonText>Project</ButtonText>  
          </Strings>  
        </Button>  
  
        <!-- The anchor item to supply the icon/tooltip for the MenuController -->  
        <Button guid="guidDynamicMenuPackageCmdSet" id="cmdidMyAnchorCommand" priority="0x0000" >  
          <Parent guid="guidDynamicMenuPackageCmdSet" id="MyMenuControllerGroup" />  
          <!-- This is the icon that appears on the Solution Explorer toolbar. -->  
          <Icon guid="guidImages" id="bmpPicArrows"/>  
          <!-- Do not show on the menu controller's drop down list-->  
          <CommandFlag>NoShowOnMenuController</CommandFlag>  
          <!-- Become the permanent anchor item for the menu controller -->  
          <CommandFlag>FixMenuController</CommandFlag>  
          <!-- The text that appears in the tooltip.-->  
          <Strings>  
            <ButtonText>Set Startup Project</ButtonText>  
          </Strings>  
        </Button>  
    </Buttons>  
    ```  
  
4.  Ajouter une icône au projet \(dans le dossier de ressources\), puis ajoutez la référence à celle\-ci dans le fichier .vsct. Dans cette procédure pas à pas, nous utilisons l’icône de flèches qui est inclus dans le modèle de projet.  
  
5.  Ajoutez une section VisibilityConstraints en dehors de la section commandes juste avant la section de symboles. \(Vous pouvez obtenir un avertissement si vous l’ajoutez après les symboles\). Cette section s’assure que le contrôleur de menu apparaît uniquement lorsqu’une solution avec plusieurs projets est chargée.  
  
    ```  
    <VisibilityConstraints>  
         <!--Make the MenuController show up only when there is a solution with more than one project loaded-->  
        <VisibilityItem guid="guidDynamicMenuPackageCmdSet" id="MyMenuController" context="UICONTEXT_SolutionHasMultipleProjects"/>  
    </VisibilityConstraints>  
    ```  
  
## Implémentation de la commande de menu dynamique  
 Vous créez une classe de commande de menu dynamique qui hérite de <xref:Microsoft.VisualStudio.Shell.OleMenuCommand>. Dans cette implémentation, le constructeur spécifie un prédicat à utiliser pour la correspondance des commandes. Vous devez substituer la <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.DynamicItemMatch%2A> méthode à utiliser ce prédicat pour définir le <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.MatchedCommandId%2A> propriété, qui identifie la commande à appeler.  
  
1.  Créer un nouveau fichier de classe c\# nommé DynamicItemMenuCommand.cs et ajoutez une classe nommée **DynamicItemMenuCommand** qui hérite de <xref:Microsoft.VisualStudio.Shell.OleMenuCommand>:  
  
    ```c#  
    class DynamicItemMenuCommand : OleMenuCommand  
    {  
  
    }  
  
    ```  
  
2.  Ajoutez le code suivant à l’aide des instructions :  
  
    ```c#  
    using Microsoft.VisualStudio.Shell;  
    using Microsoft.VisualStudio.Shell.Interop;  
    using System.ComponentModel.Design;  
    ```  
  
3.  Ajoutez un champ privé pour stocker le prédicat de correspondance :  
  
    ```c#  
    private Predicate<int> matches;  
  
    ```  
  
4.  Ajoutez un constructeur qui hérite de la <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> constructeur et spécifie un gestionnaire de commandes et une <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> Gestionnaire. Ajoutez un prédicat pour la correspondance de la commande :  
  
    ```c#  
    public DynamicItemMenuCommand(CommandID rootId, Predicate<int> matches, EventHandler invokeHandler, EventHandler beforeQueryStatusHandler)  
        : base(invokeHandler, null /*changeHandler*/, beforeQueryStatusHandler, rootId)  
    {  
        if (matches == null)  
        {  
            throw new ArgumentNullException("matches");  
        }  
  
        this.matches = matches;  
    }  
    ```  
  
5.  Remplacer la <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.DynamicItemMatch%2A> méthode afin qu’il appelle les correspondances prédicat et définit le <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.MatchedCommandId%2A> propriété :  
  
    ```c#  
    public override bool DynamicItemMatch(int cmdId)  
    {  
        // Call the supplied predicate to test whether the given cmdId is a match.  
        // If it is, store the command id in MatchedCommandid   
        // for use by any BeforeQueryStatus handlers, and then return that it is a match.  
        // Otherwise clear any previously stored matched cmdId and return that it is not a match.  
        if (this.matches(cmdId))  
        {  
            this.MatchedCommandId = cmdId;  
            return true;  
        }  
  
        this.MatchedCommandId = 0;  
        return false;  
    }  
    ```  
  
## Ajout de la commande  
 Le constructeur DynamicMenu est lorsque vous configurez des commandes de menu, y compris les menus dynamiques et des éléments de menu.  
  
1.  Dans DynamicMenuPackageGuids.cs, ajoutez le GUID de l’ensemble de commandes et l’ID de commande :  
  
    ```c#  
    public const string guidDynamicMenuPackageCmdSet = "00000000-0000-0000-0000-00000000";  // get the GUID from the .vsct file  
    public const uint cmdidMyCommand = 0x104;  
    ```  
  
2.  Dans le fichier DynamicMenu.cs, ajoutez le code suivant à l’aide des instructions :  
  
    ```c#  
    using EnvDTE;  
    using EnvDTE80;  
    using System.ComponentModel.Design;  
    ```  
  
3.  Dans la classe DynamicMenu, ajoutez un champ privé **dte2**.  
  
    ```c#  
    private DTE2 dte2;  
    ```  
  
4.  Ajoutez un champ privé rootItemId :  
  
    ```c#  
    private int rootItemId = 0;  
    ```  
  
5.  Dans le constructeur DynamicMenu, ajoutez la commande de menu. Dans la section suivante, nous définirons le Gestionnaire de commandes, la `BeforeQueryStatus` Gestionnaire d’événements et le prédicat de correspondance.  
  
    ```c#  
    private DynamicMenu(Package package)  
    {  
        if (package == null)  
        {  
            throw new ArgumentNullException(nameof(package));  
        }  
  
        this.package = package;  
  
        OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
        if (commandService != null)  
        {  
            // Add the DynamicItemMenuCommand for the expansion of the root item into N items at run time.   
            CommandID dynamicItemRootId = new CommandID(new Guid(DynamicMenuPackageGuids.guidDynamicMenuPackageCmdSet), (int)DynamicMenuPackageGuids.cmdidMyCommand);  
            DynamicItemMenuCommand dynamicMenuCommand = new DynamicItemMenuCommand(dynamicItemRootId,  
                IsValidDynamicItem,  
                OnInvokedDynamicItem,  
                OnBeforeQueryStatusDynamicItem);  
                commandService.AddCommand(dynamicMenuCommand);  
                }  
  
        dte2 = (DTE2)this.ServiceProvider.GetService(typeof(DTE));  
    }  
    ```  
  
## L’implémentation de gestionnaires  
 Pour implémenter des éléments de menu dynamiques sur un contrôleur de menu, vous devez traiter la commande lorsque vous cliquez sur un élément dynamique. Vous devez également implémenter la logique qui définit l’état de l’élément de menu. Ajoutez les gestionnaires à la classe DynamicMenu.  
  
1.  Pour implémenter le **définir un projet de démarrage** de commande, ajoutez le **OnInvokedDynamicItem** Gestionnaire d’événements. Il recherche le projet dont le nom est le même que le texte de la commande qui a été appelée et le définit comme projet de démarrage en définissant son chemin d’accès absolu dans le <xref:EnvDTE.SolutionBuild.StartupProjects%2A> propriété.  
  
    ```c#  
    private void OnInvokedDynamicItem(object sender, EventArgs args)  
    {  
        DynamicItemMenuCommand invokedCommand = (DynamicItemMenuCommand)sender;  
        // If the command is already checked, we don’t need to do anything  
        if (invokedCommand.Checked)  
            return;  
  
        // Find the project that corresponds to the command text and set it as the startup project  
        var projects = dte2.Solution.Projects;  
        foreach (Project proj in projects)  
        {  
            if (invokedCommand.Text.Equals(proj.Name))  
            {  
                dte2.Solution.SolutionBuild.StartupProjects = proj.FullName;  
                return;  
            }  
        }  
    }  
    ```  
  
2.  Ajouter la `OnBeforeQueryStatusDynamicItem` Gestionnaire d’événements. C’est le gestionnaire appelé avant une `QueryStatus` événement. Il détermine si l’élément de menu est un élément de « vraie », autrement dit, pas l’élément d’espace réservé, et indique si l’élément est déjà activé \(ce qui signifie que le projet est déjà défini comme projet de démarrage\).  
  
    ```c#  
    private void OnBeforeQueryStatusDynamicItem(object sender, EventArgs args)  
    {  
        DynamicItemMenuCommand matchedCommand = (DynamicItemMenuCommand)sender;  
        matchedCommand.Enabled = true;  
        matchedCommand.Visible = true;  
  
        // Find out whether the command ID is 0, which is the ID of the root item.  
        // If it is the root item, it matches the constructed DynamicItemMenuCommand,  
         // and IsValidDynamicItem won't be called.  
        bool isRootItem = (matchedCommand.MatchedCommandId == 0);  
  
        // The index is set to 1 rather than 0 because the Solution.Projects collection is 1-based.  
        int indexForDisplay = (isRootItem ? 1 : (matchedCommand.MatchedCommandId - (int) DynamicMenuPackageGuids.cmdidMyCommand) + 1);  
  
        matchedCommand.Text = dte2.Solution.Projects.Item(indexForDisplay).Name;  
  
        Array startupProjects = (Array)dte2.Solution.SolutionBuild.StartupProjects;  
        string startupProject = System.IO.Path.GetFileNameWithoutExtension((string)startupProjects.GetValue(0));  
  
        // Check the command if it isn't checked already selected  
        matchedCommand.Checked = (matchedCommand.Text == startupProject);  
  
        // Clear the ID because we are done with this item.  
        matchedCommand.MatchedCommandId = 0;  
    }  
    ```  
  
## L’implémentation du prédicat de correspondance d’ID commande  
  
1.  À présent implémenter le prédicat de correspondance. Nous devons déterminer deux choses : tout d’abord, si l’ID de commande est valide \(il est supérieur ou égal à l’ID de commande déclaré\) et la deuxième, si elle spécifie un projet \(il est inférieur au nombre de projets dans la solution\).  
  
    ```c#  
    private bool IsValidDynamicItem(int commandId)  
    {  
        // The match is valid if the command ID is >= the id of our root dynamic start item   
        // and the command ID minus the ID of our root dynamic start item  
        // is less than or equal to the number of projects in the solution.  
        return (commandId >= (int)DynamicMenuPackageGuids.cmdidMyCommand) && ((commandId - (int)DynamicMenuPackageGuids.cmdidMyCommand) < dte2.Solution.Projects.Count);  
    }  
    ```  
  
## Définir le VSPackage charger uniquement lorsqu’une solution comporte plusieurs projets  
 Étant donné que la **définir un projet de démarrage** commande est inutile, sauf si la solution active comporte plusieurs projets, vous pouvez définir votre VSPackage pour charger automatiquement que dans ce cas. Vous utilisez <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> avec le contexte de l’interface utilisateur <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids.SolutionHasMultipleProjects>. Dans le fichier DynamicMenuPackage.cs ajouter les attributs suivants à la classe DynamicMenuPackage :  
  
```c#  
[PackageRegistration(UseManagedResourcesOnly = true)]  
[InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]  
[ProvideMenuResource("Menus.ctmenu", 1)]  
[ProvideAutoLoad(UIContextGuids.SolutionHasMultipleProjects)]  
[Guid(DynamicMenuPackageGuids.PackageGuidString)]  
public sealed class DynamicMenuItemsPackage : Package  
{}  
```  
  
## Test de la commande de définir un projet de démarrage  
 Vous pouvez maintenant tester votre code.  
  
1.  Générez le projet et commencez le débogage. L’instance expérimentale doit apparaître.  
  
2.  Dans l’instance expérimentale, ouvrez une solution qui contient plusieurs projets.  
  
     Vous devez voir l’icône de flèche sur la **l’Explorateur de solutions** barre d’outils. Lorsque vous le développerez, éléments de menu qui représentent les différents projets de la solution doivent apparaître.  
  
3.  Lorsque vous activez un des projets, il devient le projet de démarrage.  
  
4.  Lorsque vous fermez la solution, ou ouvrez une solution qui contient un seul projet, la barre d’outils disparaisse.  
  
## Voir aussi  
 [Commandes, Menus et barres d'outils](../extensibility/internals/commands-menus-and-toolbars.md)   
 [Comment ajouter des éléments d'Interface utilisateur dans les packages VS](../extensibility/internals/how-vspackages-add-user-interface-elements.md)