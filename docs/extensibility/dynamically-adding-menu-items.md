---
title: Ajout dynamique d’éléments de menu | Microsoft Docs
description: Découvrez comment utiliser l’indicateur de commande DynamicItemStart pour ajouter des éléments de menu au moment de l’exécution. Cet article explique comment définir le projet de démarrage dans une solution Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- DYNAMICITEMSTART
- menu items, adding dynamically
- menus, adding dynamic items
ms.assetid: d281e9c9-b289-4d64-8d0a-094bac6c333c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6867baafa45ca794f65b4cb0cc365dbebfbd4219
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898355"
---
# <a name="dynamically-add-menu-items"></a>Ajouter dynamiquement des éléments de menu
Vous pouvez ajouter des éléments de menu au moment de l’exécution en spécifiant l' `DynamicItemStart` indicateur de commande sur une définition de bouton d’espace réservé dans le fichier de table de commandes Visual Studio (*. vsct*), puis en définissant (dans le code) le nombre d’éléments de menu à afficher et en gérant la ou les commandes. Lorsque le VSPackage est chargé, l’espace réservé est remplacé par les éléments de menu dynamiques.

 Visual Studio utilise des listes dynamiques dans la liste des derniers fichiers **utilisés** (MRU), qui affiche les noms des documents qui ont été récemment ouverts et la liste **Windows** , qui affiche les noms des fenêtres qui sont actuellement ouvertes.   L' `DynamicItemStart` indicateur sur une définition de commande spécifie que la commande est un espace réservé jusqu’à l’ouverture du VSPackage. Lorsque le VSPackage est ouvert, l’espace réservé est remplacé par 0 ou plusieurs commandes créées au moment de l’exécution et ajoutées à la liste dynamique. Il se peut que vous ne puissiez pas voir la position dans le menu où la liste dynamique apparaît tant que le VSPackage n’est pas ouvert.  Pour remplir la liste dynamique, Visual Studio demande au VSPackage de rechercher une commande avec un ID dont les premiers caractères sont identiques à l’ID de l’espace réservé. Lorsque Visual Studio trouve une commande correspondante, il ajoute le nom de la commande à la liste dynamique. Elle incrémente ensuite l’ID et recherche une autre commande correspondante à ajouter à la liste dynamique jusqu’à ce qu’il n’y ait plus de commandes dynamiques.

 Cette procédure pas à pas montre comment définir le projet de démarrage dans une solution Visual Studio à l’aide d’une commande dans la barre d’outils **Explorateur de solutions** . Elle utilise un contrôleur de menu qui contient une liste déroulante dynamique des projets de la solution active. Pour empêcher l’affichage de cette commande quand aucune solution n’est ouverte ou lorsque la solution ouverte n’a qu’un seul projet, le VSPackage est chargé uniquement quand une solution contient plusieurs projets.

 Pour plus d’informations sur les fichiers *. vsct* , consultez [fichiers de table de commandes Visual Studio (. vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).

## <a name="create-an-extension-with-a-menu-command"></a>Créer une extension avec une commande de menu

1. Créez un projet VSIX nommé `DynamicMenuItems` .

2. Lorsque le projet s’ouvre, ajoutez un modèle d’élément de commande personnalisé et nommez-le **dynamicMenu**. Pour plus d’informations, consultez [créer une extension à l’aide d’une commande de menu](../extensibility/creating-an-extension-with-a-menu-command.md).

## <a name="setting-up-the-elements-in-the-vsct-file"></a>Configuration des éléments dans le fichier *. vsct*
 Pour créer un contrôleur de menu avec des éléments de menu dynamiques dans une barre d’outils, vous spécifiez les éléments suivants :

- Deux groupes de commandes, un qui contient le contrôleur de menu et un autre qui contient les éléments de menu dans la liste déroulante

- Un élément de menu de type `MenuController`

- Deux boutons, un qui joue le rôle d’espace réservé pour les éléments de menu et un autre qui fournit l’icône et l’info-bulle dans la barre d’outils.

1. Dans *DynamicMenuPackage. vsct*, définissez les ID de commande. Accédez à la section Symbols et remplacez les éléments IDSymbol dans le bloc GuidSymbol **guidDynamicMenuPackageCmdSet** . Vous devez définir des éléments IDSymbol pour les deux groupes, le contrôleur de menu, la commande d’espace réservé et la commande d’ancrage.

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

2. Dans la section groupes, supprimez les groupes existants et ajoutez les deux groupes que vous venez de définir :

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

     Ajoutez MenuController. Définissez l’indicateur de commande DynamicVisibility, car il n’est pas toujours visible. Le ButtonText n’est pas affiché.

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

3. Ajoutez deux boutons, l’un sous la forme d’un espace réservé pour les éléments de menu dynamiques et l’autre comme point d’ancrage pour le MenuController.

     Le parent du bouton d’espace réservé est le **MyMenuControllerGroup**. Ajoutez les indicateurs de commande DynamicItemStart, DynamicVisibility et Textchanges au au bouton d’espace réservé. Le ButtonText n’est pas affiché.

     Le bouton ancre contient l’icône et le texte d’info-bulle. Le parent du bouton d’ancrage est également le **MyMenuControllerGroup**. Vous ajoutez l’indicateur de commande NoShowOnMenuController pour vous assurer que le bouton n’apparaît pas réellement dans la liste déroulante du contrôleur de menu, et l’indicateur de commande FixMenuController pour en faire l’ancre permanente.

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

4. Ajoutez une icône au projet (dans le dossier *Resources* ), puis ajoutez-y la référence dans le fichier *. vsct* . Dans cette procédure pas à pas, nous utilisons l’icône de flèches qui est incluse dans le modèle de projet.

5. Ajoutez une section VisibilityConstraints en dehors de la section Commands juste avant la section Symbols. (Vous pouvez obtenir un avertissement si vous l’ajoutez après les symboles.) Cette section permet de s’assurer que le contrôleur de menu apparaît uniquement lorsqu’une solution avec plusieurs projets est chargée.

    ```xml
    <VisibilityConstraints>
         <!--Make the MenuController show up only when there is a solution with more than one project loaded-->
        <VisibilityItem guid="guidDynamicMenuPackageCmdSet" id="MyMenuController" context="UICONTEXT_SolutionHasMultipleProjects"/>
    </VisibilityConstraints>
    ```

## <a name="implement-the-dynamic-menu-command"></a>Implémenter la commande de menu dynamique
 Vous créez une classe de commande de menu dynamique qui hérite de <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> . Dans cette implémentation, le constructeur spécifie un prédicat à utiliser pour les commandes correspondantes. Vous devez substituer la <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.DynamicItemMatch%2A> méthode pour utiliser ce prédicat pour définir la <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.MatchedCommandId%2A> propriété, qui identifie la commande à appeler.

1. Créez un fichier de classe C# nommé *DynamicItemMenuCommand. cs* et ajoutez une classe nommée **DynamicItemMenuCommand** qui hérite de <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> :

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

3. Ajoutez un champ privé pour stocker le prédicat de correspondance :

    ```csharp
    private Predicate<int> matches;

    ```

4. Ajoutez un constructeur qui hérite du <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> constructeur et spécifie un gestionnaire de commandes et un <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> Gestionnaire. Ajoutez un prédicat pour la correspondance de la commande :

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

5. Substituez la <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.DynamicItemMatch%2A> méthode afin qu’elle appelle le prédicat matches et définit la <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.MatchedCommandId%2A> propriété :

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
 Le constructeur DynamicMenu est l’emplacement où vous configurez les commandes de menu, y compris les menus dynamiques et les éléments de menu.

1. Dans *DynamicMenuPackage. cs*, ajoutez le GUID du jeu de commandes et l’ID de commande :

    ```csharp
    public const string guidDynamicMenuPackageCmdSet = "00000000-0000-0000-0000-00000000";  // get the GUID from the .vsct file
    public const uint cmdidMyCommand = 0x104;
    ```

2. Dans le fichier *dynamicMenu. cs* , ajoutez les directives d’utilisation suivantes :

    ```csharp
    using EnvDTE;
    using EnvDTE80;
    using System.ComponentModel.Design;
    ```

3. Dans la `DynamicMenu` classe, ajoutez un champ privé **DTE2**.

    ```csharp
    private DTE2 dte2;
    ```

4. Ajoutez un champ rootItemId privé :

    ```csharp
    private int rootItemId = 0;
    ```

5. Dans le constructeur DynamicMenu, ajoutez la commande de menu. Dans la section suivante, nous allons définir le gestionnaire de commandes, le `BeforeQueryStatus` Gestionnaire d’événements et le prédicat de correspondance.

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

## <a name="implement-the-handlers"></a>Implémenter les gestionnaires
 Pour implémenter des éléments de menu dynamiques sur un contrôleur de menu, vous devez gérer la commande lorsqu’un utilisateur clique sur un élément dynamique. Vous devez également implémenter la logique qui définit l’état de l’élément de menu. Ajoutez les gestionnaires à la `DynamicMenu` classe.

1. Pour implémenter la commande **Set Startup Project** , ajoutez le gestionnaire d’événements **OnInvokedDynamicItem** . Il recherche le projet dont le nom est le même que le texte de la commande qui a été appelée, et le définit comme projet de démarrage en définissant son chemin d’accès absolu dans la <xref:EnvDTE.SolutionBuild.StartupProjects%2A> propriété.

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

2. Ajoutez le `OnBeforeQueryStatusDynamicItem` Gestionnaire d’événements. Il s’agit du gestionnaire appelé avant un `QueryStatus` événement. Elle détermine si l’élément de menu est un élément « réel », autrement dit, s’il ne s’agit pas de l’élément d’espace réservé, et si l’élément est déjà activé (ce qui signifie que le projet est déjà défini comme projet de démarrage).

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

## <a name="implement-the-command-id-match-predicate"></a>Implémenter le prédicat de correspondance d’ID de commande

Implémentez maintenant le prédicat match. Nous devons déterminer deux choses : tout d’abord, si l’ID de commande est valide (il est supérieur ou égal à l’ID de commande déclaré) et Deuxièmement, s’il spécifie un projet possible (il est inférieur au nombre de projets dans la solution).

```csharp
private bool IsValidDynamicItem(int commandId)
{
    // The match is valid if the command ID is >= the id of our root dynamic start item
    // and the command ID minus the ID of our root dynamic start item
    // is less than or equal to the number of projects in the solution.
    return (commandId >= (int)DynamicMenuPackageGuids.cmdidMyCommand) && ((commandId - (int)DynamicMenuPackageGuids.cmdidMyCommand) < dte2.Solution.Projects.Count);
}
```

## <a name="set-the-vspackage-to-load-only-when-a-solution-has-multiple-projects"></a>Définir le VSPackage pour qu’il se charge uniquement quand une solution contient plusieurs projets
 Étant donné que la commande **définir le projet de démarrage** n’a aucun sens, sauf si la solution active contient plusieurs projets, vous pouvez définir votre VSPackage pour un chargement automatique uniquement dans ce cas. Vous utilisez <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> conjointement avec le contexte de l’interface utilisateur <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids.SolutionHasMultipleProjects> . Dans le fichier *DynamicMenuPackage. cs* , ajoutez les attributs suivants à la classe DynamicMenuPackage :

```csharp
[PackageRegistration(UseManagedResourcesOnly = true)]
[InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]
[ProvideMenuResource("Menus.ctmenu", 1)]
[ProvideAutoLoad(UIContextGuids.SolutionHasMultipleProjects)]
[Guid(DynamicMenuPackage.PackageGuidString)]
public sealed class DynamicMenuItemsPackage : Package
{}
```

## <a name="test-the-set-startup-project-command"></a>Tester la commande définir le projet de démarrage
 Vous pouvez maintenant tester votre code.

1. Générez le projet et commencez le débogage. L’instance expérimentale doit apparaître.

2. Dans l’instance expérimentale, ouvrez une solution qui contient plusieurs projets.

     L’icône représentant une flèche doit s’afficher dans la barre d’outils **Explorateur de solutions** . Lorsque vous le développez, les éléments de menu qui représentent les différents projets de la solution doivent apparaître.

3. Lorsque vous activez l’un des projets, il devient le projet de démarrage.

4. Quand vous fermez la solution ou que vous ouvrez une solution qui n’a qu’un seul projet, l’icône de la barre d’outils doit disparaître.

## <a name="see-also"></a>Voir aussi
- [Commandes, menus et barres d’outils](../extensibility/internals/commands-menus-and-toolbars.md)
- [Comment les VSPackages ajoutent des éléments d’interface utilisateur](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
