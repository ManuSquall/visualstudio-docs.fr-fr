---
title: Création. Fichiers Vsct (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, manual authoring
ms.assetid: e9f715dc-12b7-439b-bdf3-f3dc75e62f1c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dfa276d04e2d312d7ff00b1e9bc0015beb1e254e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709996"
---
# <a name="author-vsct-files"></a>Auteur .vsct fichiers
Ce document montre comment écrire un fichier *.vsct* pour ajouter des éléments de menu, des barres d’outils et d’autres éléments d’interface utilisateur (interface utilisateur) à l’environnement de développement intégré Visual Studio (IDE). Utilisez ces étapes lorsque vous ajoutez des éléments d’interface utilisateur à un forfait Visual Studio (VSPackage) qui n’a pas déjà de fichier *.vsct.*

 Pour les nouveaux projets, nous vous recommandons d’utiliser le modèle de paquet Visual Studio car il génère un fichier *.vsct* qui, selon vos sélections, a déjà les éléments nécessaires pour une commande de menu, une fenêtre d’outil, ou un éditeur personnalisé. Vous pouvez modifier ce fichier *.vsct* pour répondre aux exigences de votre VSPackage. Pour plus d’informations sur la façon de modifier un fichier *.vsct,* voir les exemples dans [les menus et les commandes Extend](../../extensibility/extending-menus-and-commands.md).

## <a name="author-the-file"></a>Auteur du fichier
 Auteur d’un fichier *.vsct* dans ces phases: Créer la structure pour les fichiers et les ressources, déclarer les éléments d’interface utilisateur, mettre les éléments d’interface utilisateur dans l’IDE, et ajouter des comportements spécialisés.

### <a name="file-structure"></a>Structure de fichiers
 La structure de base d’un fichier *.vsct* est un élément racine [CommandTable](../../extensibility/commandtable-element.md) qui contient un élément [de commande](../../extensibility/commands-element.md) et un élément [symbole.](../../extensibility/symbols-element.md)

#### <a name="to-create-the-file-structure"></a>Créer la structure du fichier

1. Ajoutez un fichier *.vsct* à votre projet en suivant les étapes [de How to: Create a .vsct fichier](../../extensibility/internals/how-to-create-a-dot-vsct-file.md).

2. Ajoutez les espaces de `CommandTable` nom requis à l’élément, comme le montre l’exemple suivant :

    ```xml
    <CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable"
        xmlns:xs="http://www.w3.org/2001/XMLSchema">

    ```

3. Dans `CommandTable` l’élément, `Commands` ajoutez un élément pour héberger tous vos menus personnalisés, barres d’outils, groupes de commande et commandes. Afin que vos éléments d’interface `Commands` utilisateur personnalisés peuvent charger, l’élément doit avoir son `Package` attribut défini au nom du paquet.

     Après `Commands` l’élément, `Symbols` ajoutez un élément pour définir les GUIDs pour le paquet, ainsi que les noms et les articles de commande pour vos éléments d’interface utilisateur.

### <a name="include-visual-studio-resources"></a>Inclure les ressources visual Studio
 Utilisez l’élément [Extern](../../extensibility/extern-element.md) pour accéder aux fichiers qui définissent les commandes Visual Studio et les menus qui sont nécessaires pour mettre vos éléments d’interface utilisateur dans l’IDE. Si vous utilisez des commandes définies en dehors de votre forfait, utilisez l’élément [UsedCommands](../../extensibility/usedcommands-element.md) pour informer Visual Studio.

#### <a name="to-include-visual-studio-resources"></a>Pour inclure les ressources Visual Studio

1. En haut de `CommandTable` l’élément, ajoutez un `Extern` élément pour chaque fichier `href` externe à référencé, et définissez l’attribut au nom du fichier. Vous pouvez faire référence aux fichiers d’en-tête suivants pour accéder aux ressources visual Studio :

   - *Stdidcmd.h*: Définit les ID pour toutes les commandes exposées par Visual Studio.

   - *Vsshlids.h*: Contient des demandes d’identité de commande pour les menus Visual Studio.

2. Si votre forfait appelle des commandes définies par Visual Studio `UsedCommands` ou `Commands` par d’autres paquets, ajoutez un élément après l’élément. Remplissez cet élément avec un élément [UsedCommand](../../extensibility/usedcommand-element.md) pour chaque commande que vous appelez qui ne fait pas partie de votre paquet. Définissez `guid` `id` les éléments `UsedCommand` et les attributs des valeurs GUID et ID des commandes à appeler.

   Pour plus d’informations sur la façon de trouver les GUIDs et les ID des commandes Visual Studio, voir [GUIDs et IDs de Visual Studio commandes](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md). Pour appeler les commandes d’autres paquets, utilisez le GUID et l’ID de la commande tel que défini dans le fichier *.vsct* pour ces paquets.

### <a name="declare-ui-elements"></a>Déclarer les éléments de l’interface utilisateur
 Déclarez tous les nouveaux `Symbols` éléments d’interface utilisateur dans la section du fichier *.vsct.*

#### <a name="to-declare-ui-elements"></a>Déclarer les éléments de l’assurance-chômage

1. Dans `Symbols` l’élément, ajouter trois éléments [GuidSymbol.](../../extensibility/guidsymbol-element.md) Chaque `GuidSymbol` élément `name` a un `value` attribut et un attribut. Définissez `name` l’attribut de sorte qu’il reflète le but de l’élément. L’attribut `value` prend un GUID. (Pour générer un GUID, sur le menu **Outils,** sélectionnez **Créer GUID,** puis sélectionnez **le format d’enregistrement**.)

     Le `GuidSymbol` premier élément représente votre colis, et n’a généralement pas d’enfants. Le `GuidSymbol` deuxième élément représente l’ensemble de commandes et contiendra tous les symboles qui définissent vos menus, groupes et commandes. Le `GuidSymbol` troisième élément représente votre magasin d’images et contient des symboles pour toutes les icônes pour vos commandes. Si vous n’avez pas de commandes qui utilisent `GuidSymbol` des icônes, vous pouvez omettre le troisième élément.

2. Dans `GuidSymbol` l’élément qui représente votre ensemble de commandes, ajoutez un ou plusieurs éléments [IDSymbol.](../../extensibility/idsymbol-element.md) Chacun d’eux représente un menu, une barre d’outils, un groupe ou une commande que vous ajoutez à l’interface utilisateur.

     Pour `IDSymbol` chaque élément, `name` définissez l’attribut au nom que vous utiliserez pour désigner `value` le menu, le groupe ou la commande correspondant, puis définissez l’élément à un numéro hexadecimal qui représentera son ID de commande. Aucun `IDSymbol` des deux éléments qui ont le même parent ne peut avoir la même valeur.

3. Si l’un de vos éléments d’interface utilisateur nécessite des icônes, ajoutez un `IDSymbol` élément pour chaque icône à l’élément `GuidSymbol` qui représente votre magasin d’images.

### <a name="put-ui-elements-in-the-ide"></a>Mettre des éléments d’interface utilisateur dans l’IDE
 Les [menus,](../../extensibility/menus-element.md) [les groupes](../../extensibility/groups-element.md)et les éléments [Boutons](../../extensibility/buttons-element.md) contiennent les définitions de tous les menus, groupes et commandes qui sont définis dans votre forfait. Mettez ces menus, groupes et commandes dans l’IDE soit en utilisant un élément [Parent,](../../extensibility/parent-element.md) qui fait partie de la définition de l’élément d’interface utilisateur, ou en utilisant un élément [de position de commandement](../../extensibility/commandplacement-element.md) qui est défini ailleurs.

 Chaque `Menu` `Group`, `Button` , et `guid` l’élément a un attribut et un `id` attribut. Définissez `guid` toujours l’attribut pour `GuidSymbol` correspondre au nom de l’élément qui représente votre ensemble de commande, et définissez l’attribut `id` au nom de l’élément `IDSymbol` qui représente votre menu, groupe ou commande dans la `Symbols` section.

#### <a name="to-define-ui-elements"></a>Définir les éléments de l’interface utilisateur

1. Si vous définissez de nouveaux menus, sous-menus, menus raccourcis `Menus` ou `Commands` barres d’outils, ajoutez un élément à l’élément. Ensuite, pour chaque menu à créer, ajoutez `Menus` un élément de [menu](../../extensibility/menu-element.md) à l’élément.

    `guid` Réglez `id` les attributs et les attributs de l’élément, `Menu` puis définissez l’attribut `type` au type de menu que vous voulez. Vous pouvez également `priority` définir l’attribut pour établir la position relative du menu dans le groupe parent.

   > [!NOTE]
   > L’attribut `priority` ne s’applique pas aux barres d’outils et aux menus contextuels.

2. Toutes les commandes de l’IDE Visual Studio doivent être hébergées par des groupes de commandement, qui sont les enfants directs des menus et des barres d’outils. Si vous ajoutez de nouveaux menus ou barres d’outils à l’IDE, ceux-ci doivent contenir de nouveaux groupes de commande. Vous pouvez également ajouter des groupes de commande aux menus et barres d’outils existants afin que vous puissiez regrouper visuellement vos commandes.

    Lorsque vous ajoutez de nouveaux groupes `Groups` de commandement, vous devez d’abord créer un élément, puis y ajouter un élément [de groupe](../../extensibility/group-element.md) pour chaque groupe de commandement.

    Définissez `guid` `id` les attributs `Group` et les attributs de chaque élément, puis définissez l’attribut `priority` pour établir la position relative du groupe sur le menu parent. Pour plus d’informations, voir [Créer des groupes réutilisables de boutons](../../extensibility/creating-reusable-groups-of-buttons.md).

3. Si vous ajoutez de nouvelles commandes à `Buttons` l’IDE, ajoutez un élément à l’élément. `Commands` Ensuite, pour chaque commande, ajoutez `Buttons` un élément [bouton](../../extensibility/button-element.md) à l’élément.

   1. `guid` Réglez `id` les attributs et les attributs de chaque `Button` élément, puis définissez l’attribut `type` au type de bouton que vous voulez. Vous pouvez également `priority` définir l’attribut pour établir la position relative de la commande dans le groupe parent.

       > [!NOTE]
       > Utilisez `type="button"` pour les commandes de menu standard et les boutons sur les barres d’outils.

   2. Dans `Button` l’élément, ajoutez un élément [Cordes](../../extensibility/strings-element.md) qui contient un élément [ButtonText](../../extensibility/buttontext-element.md) et un élément [CommandName.](../../extensibility/commandname-element.md) L’élément `ButtonText` fournit l’étiquette de texte pour un élément de menu, ou la pointe d’outil pour un bouton de barre d’outils. L’élément `CommandName` fournit le nom de la commande à utiliser dans le puits de commande.

   3. Si votre commande a une [Icon](../../extensibility/icon-element.md) icône, créez `Button` un élément `guid` Icon `id` dans l’élément et définissez son et ses attributs à l’élément `Bitmap` de l’icône.

       > [!NOTE]
       > Les boutons de barre d’outils doivent avoir des icônes.

   Pour plus d’informations, voir [MenuCommands vs OleMenuCommands](/visualstudio/extensibility/menucommands-vs-olemenucommands?view=vs-2015).

4. Si l’une de vos commandes nécessite des icônes, ajoutez un élément [Bitmaps](../../extensibility/bitmaps-element.md) à l’élément. `Commands` Ensuite, pour chaque icône, ajoutez un `Bitmaps` élément [Bitmap](../../extensibility/bitmap-element.md) à l’élément. C’est là que vous spécifiez l’emplacement de la ressource de bitmap. Pour plus d’informations, voir [Ajouter des icônes aux commandes de menu](../../extensibility/adding-icons-to-menu-commands.md).

   Vous pouvez compter sur la structure parentale pour placer correctement la plupart des menus, des groupes et des commandes. Pour les ensembles de commandes très voluminés, ou lorsqu’un menu, un groupe ou une commande doit apparaître à plusieurs endroits, nous vous recommandons de spécifier le placement de commande.

#### <a name="to-rely-on-parenting-to-place-ui-elements-in-the-ide"></a>S’appuyer sur le rôle parental pour placer des éléments d’assurance-chômage dans l’IIDE

1. Pour les parents typiques, `Parent` `Menu`créez `Group`un `Command` élément dans chacun, et l’élément qui est défini dans votre paquet.

    La cible `Parent` de l’élément est le menu ou le groupe qui contiendra le menu, le groupe ou la commande.

   1. Définissez `guid` l’attribut au `GuidSymbol` nom de l’élément qui définit l’ensemble de commande. Si l’élément cible ne fait pas partie de votre paquet, utilisez le guid pour cet ensemble de commande, tel que défini dans le fichier *.vsct* correspondant.

   2. Définissez `id` l’attribut `id` pour correspondre à l’attribut du menu cible ou du groupe. Pour une liste des menus et des groupes exposés par Visual Studio, voir [GUIDs et IDs de visual Studio menus](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md) ou [GUIDs et IDs de barres d’outils Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md).

   Si vous avez un grand nombre d’éléments d’interface utilisateur à placer dans l’IIDE, ou si vous avez des éléments qui doivent apparaître à plusieurs endroits, définissez leurs placements dans l’élément [CommandPlacements,](../../extensibility/commandplacements-element.md) comme indiqué dans les étapes suivantes.

#### <a name="to-use-command-placement-to-place-ui-elements-in-the-ide"></a>Utiliser le placement de commande pour placer des éléments d’interface utilisateur dans l’IDE

1. Après l’élément `Commands`, ajoutez un élément `CommandPlacements`.

2. Dans `CommandPlacements` l’élément, `CommandPlacement` ajoutez un élément pour chaque menu, groupe ou commande à placer.

    Chaque `CommandPlacement` élément `Parent` ou élément place un menu, un groupe ou une commande dans un emplacement IDE. Un élément d’interface utilisateur ne peut avoir qu’un seul parent, mais il peut avoir plusieurs placements de commande. Pour placer un élément d’interface `CommandPlacement` utilisateur à plusieurs endroits, ajoutez un élément pour chaque emplacement.

3. `guid` Réglez `id` les attributs et les attributs de chaque `CommandPlacement` élément `Parent` au menu d’hébergement ou au groupe, tout comme vous le feriez pour un élément. Vous pouvez également `priority` définir l’attribut pour établir la position relative de l’élément d’interface utilisateur.

   Vous pouvez mélanger le placement par le rôle parental et le placement de commande. Cependant, pour les très grands ensembles de commandes, nous vous recommandons d’utiliser uniquement le placement de commande.

### <a name="add-specialized-behaviors"></a>Ajouter des comportements spécialisés
 Vous pouvez utiliser l’élément [CommandFlag](../../extensibility/command-flag-element.md) pour modifier le comportement des menus et des commandes, par exemple, pour changer leur apparence et leur visibilité. Vous pouvez également affecter lorsqu’une commande est visible en utilisant l’élément [VisibilityConstraints,](../../extensibility/visibilityconstraints-element.md) ou ajouter des raccourcis clavier en utilisant [l’élément KeyBindings.](../../extensibility/keybindings-element.md) Certains types de menus et de commandes ont déjà des comportements spécialisés intégrés.

#### <a name="to-add-specialized-behaviors"></a>Pour ajouter des comportements spécialisés

1. Pour rendre un élément d’interface utilisateur visible uniquement dans certains contextes d’interface utilisateur, par exemple, lorsqu’une solution est chargée, utilisez des contraintes de visibilité.

   1. Après l’élément `Commands`, ajoutez un élément `VisibilityConstraints`.

   2. Pour que chaque élément d’interface utilisateur soit contraint, ajoutez un élément [VisibilityItem.](../../extensibility/visibilityitem-element.md)

   3. Pour `VisibilityItem` chaque élément, `guid` `id` définissez le et les attributs au menu, au groupe ou à la commande, puis définissez l’attribut `context` au contexte de l’interface utilisateur que vous voulez, tel que défini dans la <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> classe.

2. Pour définir la visibilité ou la disponibilité d’un élément d’interface utilisateur dans le code, utilisez un ou plusieurs des indicateurs de commande suivants :

   - `DefaultDisabled`

   - `DefaultInvisible`

   - `DynamicItemStart`

   - `DynamicVisibility`

   - `NoShowOnMenuController`

   - `NotInTBList`

   Pour plus d’informations, consultez l’élément [CommandFlag.](../../extensibility/command-flag-element.md)

3. Pour modifier la façon dont un élément apparaît, ou changer son apparence dynamiquement, utilisez un ou plusieurs des drapeaux de commande suivants :

   - `AlwaysCreate`

   - `CommandWellOnly`

   - `DefaultDocked`

   - `DontCache`

   - `DynamicItemStart`

   - `FixMenuController`

   - `IconAndText`

   - `Pict`

   - `StretchHorizontally`

   - `TextMenuUseButton`

   - `TextChanges`

   - `TextOnly`

   Pour plus d’informations, consultez l’élément [CommandFlag.](../../extensibility/command-flag-element.md)

4. Pour modifier la façon dont un élément réagit lorsqu’il reçoit des commandes, utilisez un ou plusieurs des drapeaux de commandement suivants :

   - `AllowParams`

   - `CaseSensitive`

   - `CommandWellOnly`

   - `FilterKeys`

   - `NoAutoComplete`

   - `NoButtonCustomize`

   - `NoKeyCustomize`

   - `NoToolbarClose`

   - `PostExec`

   - `RouteToDocs`

   - `TextIsAnchorCommand`

   Pour plus d’informations, consultez l’élément [CommandFlag.](../../extensibility/command-flag-element.md)

5. Pour joindre un raccourci clavier dépendant du menu à un menu ou un élément sur un menu, ajoutez un caractère ampersand (&) dans l’élément `ButtonText` pour le menu ou l’élément du menu. Le personnage qui suit l’ampersand est le raccourci clavier actif lorsque le menu parent est ouvert.

6. Pour joindre un raccourci clavier indépendant au menu à une commande, utilisez l’élément [KeyBindings.](../../extensibility/keybindings-element.md) Pour plus d’informations, consultez l’élément [KeyBinding.](../../extensibility/keybinding-element.md)

7. Pour localiser le texte `LocCanonicalName` du menu, utilisez l’élément. Pour plus d’informations, voir l’élément [Cordes.](../../extensibility/strings-element.md)

   Certains types de menu et de boutons incluent des comportements spécialisés. La liste suivante décrit certains types de menu et de boutons spécialisés. Pour d’autres `types` types, voir les descriptions d’attribut dans le [menu](../../extensibility/menu-element.md), [bouton](../../extensibility/button-element.md), et les éléments [Combo.](../../extensibility/combo-element.md)

   - Boîte combo: Une boîte combo est une liste d’abandon qui peut être utilisé sur une barre d’outils. Pour ajouter des boîtes combo à l’interface `Commands` utilisateur, créez un élément [Combos](../../extensibility/combos-element.md) dans l’élément. Ajoutez ensuite `Combos` à `Combo` l’élément un élément pour chaque boîte combo à ajouter. `Combo`ont les mêmes attributs `Button` et les `DefaultWidth` mêmes `idCommandList` enfants que les éléments et ont également et les attributs. L’attribut `DefaultWidth` définit la largeur en `idCommandList` pixels, et les points d’attribut à un ID de commande qui est utilisé pour remplir la boîte combo.

   - Contrôleur de menu : Un contrôleur de menu est un bouton qui a une flèche à côté de lui. En cliquant sur la flèche ouvre une liste. Pour ajouter un contrôleur de menu `Menu` à l’interface utilisateur, créez un élément et définissez son `type` attribut `MenuController` `MenuControllerLatched`ou, selon le comportement que vous voulez. Pour peupler un contrôleur de menu, `Group` définissez-le comme le parent d’un élément. Le contrôleur de menu affichera tous les enfants de ce groupe sur sa liste d’abandon.

## <a name="see-also"></a>Voir aussi
- [Étendre les menus et les commandes](../../extensibility/extending-menus-and-commands.md)
- [Fichiers visualister de table de commande de studio (.vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [VSCT XML référence schéma](../../extensibility/vsct-xml-schema-reference.md)
