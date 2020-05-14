---
title: Ajout dynamique des éléments de menu (en anglais seulement) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- DYNAMICITEMSTART
- menu items, adding dynamically
- menus, adding dynamic items
ms.assetid: d281e9c9-b289-4d64-8d0a-094bac6c333c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4387c1930e09e49c0ec5c36ccedc1bb83dc273f3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712065"
---
# <a name="dynamically-add-menu-items"></a>Ajouter dynamiquement les éléments de menu
Vous pouvez ajouter des éléments de `DynamicItemStart` menu au moment de l’exécution en spécifiant le drapeau de commande sur une définition de bouton de pointage dans le fichier Visual Studio command-table *(.vsct*), puis en définissant (en code) le nombre d’éléments de menu à afficher et en manipulant la commande(s). Lorsque le VSPackage est chargé, le placeholder est remplacé par les éléments de menu dynamique.

 Visual Studio utilise des listes dynamiques dans la liste **most Recently Used** (MRU), qui affiche les noms des documents qui ont été ouverts récemment, et la liste **Windows,** qui affiche les noms des fenêtres qui sont actuellement ouvertes.   Le `DynamicItemStart` drapeau sur une définition de commande spécifie que la commande est un espace réservé jusqu’à ce que le VSPackage soit ouvert. Lorsque le VSPackage est ouvert, le propriétaire de place est remplacé par 0 commandes ou plus qui sont créées au moment de l’exécution et ajoutées à la liste dynamique. Vous ne pouvez pas être en mesure de voir la position sur le menu où la liste dynamique apparaît jusqu’à ce que le VSPackage est ouvert.  Pour remplir la liste dynamique, Visual Studio demande au VSPackage de rechercher une commande avec une pièce d’identité dont les premiers caractères sont les mêmes que l’ID du placeholder. Lorsque Visual Studio trouve une commande assortie, il ajoute le nom de la commande à la liste dynamique. Ensuite, il incrémente l’ID et cherche une autre commande correspondante à ajouter à la liste dynamique jusqu’à ce qu’il n’y ait plus de commandes dynamiques.

 Ce pas-là montre comment définir le projet de démarrage dans une solution Visual Studio avec une commande sur la barre d’outils **Solution Explorer.** Il utilise un contrôleur de menu qui a une liste de décrochage dynamique des projets dans la solution active. Pour éviter que cette commande n’apparaisse lorsqu’aucune solution n’est ouverte ou lorsque la solution ouverte n’a qu’un seul projet, le VSPackage n’est chargé que lorsqu’une solution a plusieurs projets.

 Pour plus d’informations sur les fichiers *.vsct,* voir [Visual Studio table de commande (.vsct) fichiers](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).

## <a name="create-an-extension-with-a-menu-command"></a>Créer une extension avec une commande de menu

1. Créer un projet `DynamicMenuItems`VSIX nommé .

2. Lorsque le projet s’ouvre, ajoutez un modèle d’élément de commande personnalisé et nommez-le **DynamicMenu**. Pour plus d’informations, voir [Créer une extension avec une commande de menu](../extensibility/creating-an-extension-with-a-menu-command.md).

## <a name="setting-up-the-elements-in-the-vsct-file"></a>Mise en place des éléments dans le fichier *.vsct*
 Pour créer un contrôleur de menu avec des éléments de menu dynamiques sur une barre d’outils, vous spécifiez les éléments suivants :

- Deux groupes de commande, l’un qui contient le contrôleur de menu et l’autre qui contient les éléments du menu dans le dropdown

- Un élément de menu de type`MenuController`

- Deux boutons, l’un qui agit comme le placeholder pour les éléments du menu et l’autre qui fournit l’icône et la pointe d’outils sur la barre d’outils.

1. Dans *DynamicMenuPackage.vsct*, définissez les ED de commande. Rendez-vous à la section Symboles et remplacez les éléments IDSymbol dans le bloc **guidDynamicMenuPackageCmdSet** GuidSymbol. Vous devez définir les éléments IDSymbol pour les deux groupes, le contrôleur de menu, la commande de placeholder, et la commande d’ancrage.

    ```xml
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

2. Dans la section Groupes, supprimez les groupes existants et ajoutez les deux groupes que vous venez de définir :

    ```xml
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

     Ajouter le MenuController. Réglez le drapeau de commande DynamicVisibility, car il n’est pas toujours visible. Le BoutonText n’est pas affiché.

    ```xml
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

3. Ajoutez deux boutons, l’un en tant que placeholder pour les éléments de menu dynamique et l’autre comme point d’ancrage pour le MenuController.

     Le parent du bouton placeholder est le **MyMenuControllerGroup**. Ajoutez les drapeaux de commande DynamicItemStart, DynamicVisibility et TextChanges au bouton du porte-avions. Le BoutonText n’est pas affiché.

     Le bouton d’ancrage contient l’icône et le texte de l’outil. Le parent du bouton d’ancrage est également le **MyMenuControllerGroup**. Vous ajoutez le drapeau de commande NoShowOnMenuController pour vous assurer que le bouton n’apparaît pas réellement dans le décrochage du contrôleur de menu, et le drapeau de commande FixMenuController pour en faire l’ancre permanente.

    ```xml
    <!-- The placeholder for the dynamic items that expand to N items at run time. -->
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

4. Ajoutez une icône au projet (dans le dossier *Ressources),* puis ajoutez la référence dans le fichier *.vsct.* Dans cette procédure pas à pas, nous utilisons l’icône Arrows qui est incluse dans le modèle de projet.

5. Ajoutez une section VisibilityConstraints à l’extérieur de la section Commandes juste avant la section Symboles. (Vous pouvez obtenir un avertissement si vous l’ajoutez après les symboles.) Cette section permet de s’assurer que le contrôleur de menu n’apparaît que lorsqu’une solution avec plusieurs projets est chargée.

    ```xml
    <VisibilityConstraints>
         <!--Make the MenuController show up only when there is a solution with more than one project loaded-->
        <VisibilityItem guid="guidDynamicMenuPackageCmdSet" id="MyMenuController" context="UICONTEXT_SolutionHasMultipleProjects"/>
    </VisibilityConstraints>
    ```

## <a name="implement-the-dynamic-menu-command"></a>Mettre en œuvre la commande dynamique du menu
 Vous créez un cours de commande <xref:Microsoft.VisualStudio.Shell.OleMenuCommand>de menu dynamique qui hérite de . Dans cette implémentation, le constructeur précise un prédicat à utiliser pour l’appariement des commandes. Vous devez passer <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.DynamicItemMatch%2A> outre à la méthode d’utilisation de ce prédicat pour définir la <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.MatchedCommandId%2A> propriété, qui identifie la commande à invoquer.

1. Créez un nouveau fichier de classe Cmd nommé *DynamicItemMenuCommand.cs*, et ajoutez une classe <xref:Microsoft.VisualStudio.Shell.OleMenuCommand>nommée **DynamicItemMenuCommand** qui hérite de :

    ```csharp
    class DynamicItemMenuCommand : OleMenuCommand
    {

    }

    ```

2. Ajoutez les directives using suivantes :

    ```csharp
    using Microsoft.VisualStudio.Shell;
    using Microsoft.VisualStudio.Shell.Interop;
    using System.ComponentModel.Design;
    ```

3. Ajouter un champ privé pour stocker le match prédicate:

    ```csharp
    private Predicate<int> matches;

    ```

4. Ajoutez un constructeur qui hérite du <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> constructeur et spécifie un gestionnaire de commande et un <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> gestionnaire. Ajouter un prédicat pour faire correspondre la commande :

    ```csharp
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

5. Remplacer la <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.DynamicItemMatch%2A> méthode afin qu’elle appelle les <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.MatchedCommandId%2A> allumettes prédicate et définit la propriété:

    ```csharp
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

## <a name="add-the-command"></a>Ajouter la commande
 Le constructeur DynamicMenu est l’endroit où vous configurez des commandes de menu, y compris des menus dynamiques et des éléments de menu.

1. Dans *DynamicMenuPackage.cs*, ajouter le GUID de l’ensemble de commande et l’ID de commande:

    ```csharp
    public const string guidDynamicMenuPackageCmdSet = "00000000-0000-0000-0000-00000000";  // get the GUID from the .vsct file
    public const uint cmdidMyCommand = 0x104;
    ```

2. Dans le fichier *DynamicMenu.cs,* ajoutez les directives suivantes à l’aide de directives :

    ```csharp
    using EnvDTE;
    using EnvDTE80;
    using System.ComponentModel.Design;
    ```

3. Dans `DynamicMenu` la classe, ajouter un champ privé **dte2**.

    ```csharp
    private DTE2 dte2;
    ```

4. Ajouter un champ rootItemId privé :

    ```csharp
    private int rootItemId = 0;
    ```

5. Dans le constructeur DynamicMenu, ajoutez la commande du menu. Dans la section suivante, nous définirons `BeforeQueryStatus` le gestionnaire de commande, le gestionnaire d’événements et le match prédicat.

    ```csharp
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

## <a name="implement-the-handlers"></a>Mettre en œuvre les gestionnaires
 Pour implémenter des éléments de menu dynamiques sur un contrôleur de menu, vous devez gérer la commande lorsqu’un élément dynamique est cliqué. Vous devez également implémenter la logique qui définit l’état de l’élément de menu. Ajoutez les manutentionnaires à la `DynamicMenu` classe.

1. Pour mettre en œuvre la commande **Set Startup Project,** ajoutez le gestionnaire d’événements **OnInvokedDynamicItem.** Il recherche le projet dont le nom est le même que le texte de la commande qui a <xref:EnvDTE.SolutionBuild.StartupProjects%2A> été invoqué, et le définit comme le projet de démarrage en fixant son chemin absolu dans la propriété.

    ```csharp
    private void OnInvokedDynamicItem(object sender, EventArgs args)
    {
        DynamicItemMenuCommand invokedCommand = (DynamicItemMenuCommand)sender;
        // If the command is already checked, we don't need to do anything
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

2. Ajoutez `OnBeforeQueryStatusDynamicItem` le gestionnaire de l’événement. C’est le gestionnaire `QueryStatus` appelé avant un événement. Il détermine si l’élément du menu est un "vrai" élément, c’est-à-dire pas l’élément placeholder, et si l’article est déjà vérifié (ce qui signifie que le projet est déjà défini comme le projet de démarrage).

    ```csharp
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

## <a name="implement-the-command-id-match-predicate"></a>Mettre en œuvre le prédicat de correspondance d’identification de commande

Maintenant, implémenter le match predicate. Nous devons déterminer deux choses: premièrement, si l’ID de commande est valide (il est supérieur ou égal à l’ID de commande déclaré), et deuxièmement, si elle spécifie un projet possible (il est inférieur au nombre de projets dans la solution).

```csharp
private bool IsValidDynamicItem(int commandId)
{
    // The match is valid if the command ID is >= the id of our root dynamic start item
    // and the command ID minus the ID of our root dynamic start item
    // is less than or equal to the number of projects in the solution.
    return (commandId >= (int)DynamicMenuPackageGuids.cmdidMyCommand) && ((commandId - (int)DynamicMenuPackageGuids.cmdidMyCommand) < dte2.Solution.Projects.Count);
}
```

## <a name="set-the-vspackage-to-load-only-when-a-solution-has-multiple-projects"></a>Définissez le VSPackage pour charger uniquement lorsqu’une solution a plusieurs projets
 Étant donné que la commande **Set Startup Project** n’a pas de sens à moins que la solution active ne dispose de plus d’un projet, vous pouvez configurer votre VSPackage pour charger automatiquement uniquement dans ce cas. Vous <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> utilisez avec le <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids.SolutionHasMultipleProjects>contexte de l’interface utilisateur . Dans le *fichier DynamicMenuPackage.cs* ajouter les attributs suivants à la classe DynamicMenuPackage :

```csharp
[PackageRegistration(UseManagedResourcesOnly = true)]
[InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]
[ProvideMenuResource("Menus.ctmenu", 1)]
[ProvideAutoLoad(UIContextGuids.SolutionHasMultipleProjects)]
[Guid(DynamicMenuPackage.PackageGuidString)]
public sealed class DynamicMenuItemsPackage : Package
{}
```

## <a name="test-the-set-startup-project-command"></a>Testez la commande du projet de démarrage
 Maintenant, vous pouvez tester votre code.

1. Générez le projet et commencez le débogage. L’instance expérimentale devrait apparaître.

2. Dans le cas expérimental, ouvrez une solution qui a plus d’un projet.

     Vous devriez voir l’icône de flèche sur la barre d’outils **Solution Explorer.** Lorsque vous l’élargissez, les éléments de menu qui représentent les différents projets de la solution doivent apparaître.

3. Lorsque vous vérifiez l’un des projets, il devient le projet de démarrage.

4. Lorsque vous fermez la solution ou ouvrez une solution qui n’a qu’un seul projet, l’icône de la barre d’outils doit disparaître.

## <a name="see-also"></a>Voir aussi
- [Commandes, menus et barres d’outils](../extensibility/internals/commands-menus-and-toolbars.md)
- [Comment VSPackages ajoute des éléments d’interface utilisateur](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
