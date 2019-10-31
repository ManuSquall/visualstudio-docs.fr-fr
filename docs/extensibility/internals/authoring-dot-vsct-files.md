---
title: Création. Fichiers vsct | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, manual authoring
ms.assetid: e9f715dc-12b7-439b-bdf3-f3dc75e62f1c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 82960de02c43a7c4002e189d573a914bb2a73f20
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73186656"
---
# <a name="author-vsct-files"></a>Fichiers Author. vsct
Ce document montre comment créer un fichier *. vsct* pour ajouter des éléments de menu, des barres d’outils et d’autres éléments d’interface utilisateur à l’environnement de développement intégré (IDE) de Visual Studio. Utilisez ces étapes Lorsque vous ajoutez des éléments d’interface utilisateur à un package Visual Studio (VSPackage) qui n’a pas encore de fichier *. vsct* .

 Pour les nouveaux projets, nous vous recommandons d’utiliser le modèle de package Visual Studio, car il génère un fichier *. vsct* qui, selon vos sélections, contient déjà les éléments requis pour une commande de menu, une fenêtre outil ou un éditeur personnalisé. Vous pouvez modifier ce fichier *. vsct* pour répondre aux exigences de votre VSPackage. Pour plus d’informations sur la modification d’un fichier *. vsct* , consultez les exemples dans [étendre les menus et les commandes](../../extensibility/extending-menus-and-commands.md).

## <a name="author-the-file"></a>Créer le fichier
 Créez un fichier *. vsct* dans ces phases : créez la structure des fichiers et des ressources, déclarez les éléments d’interface utilisateur, placez les éléments d’interface utilisateur dans l’IDE et ajoutez des comportements spécialisés.

### <a name="file-structure"></a>Structure de fichier
 La structure de base d’un fichier *. vsct* est un élément racine [CommandTable](../../extensibility/commandtable-element.md) qui contient un élément [Commands](../../extensibility/commands-element.md) et un élément [Symbols](../../extensibility/symbols-element.md) .

#### <a name="to-create-the-file-structure"></a>Pour créer la structure de fichiers

1. Ajoutez un fichier *. vsct* à votre projet en suivant les étapes décrites dans [Comment : créer un fichier. vsct](../../extensibility/internals/how-to-create-a-dot-vsct-file.md).

2. Ajoutez les espaces de noms requis à l’élément `CommandTable`, comme indiqué dans l’exemple suivant :

    ```xml
    <CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable"
        xmlns:xs="http://www.w3.org/2001/XMLSchema">

    ```

3. Dans l’élément `CommandTable`, ajoutez un élément `Commands` pour héberger tous vos menus, barres d’outils, groupes de commandes et commandes personnalisés. Pour que vos éléments d’interface utilisateur personnalisés puissent être chargés, l’attribut `Package` de l’élément `Commands` doit être défini sur le nom du package.

     Après l’élément `Commands`, ajoutez un élément `Symbols` pour définir les GUID du package, ainsi que les noms et les ID de commande de vos éléments d’interface utilisateur.

### <a name="include-visual-studio-resources"></a>Inclure les ressources Visual Studio
 Utilisez l’élément [extern](../../extensibility/extern-element.md) pour accéder aux fichiers qui définissent des commandes Visual Studio et aux menus requis pour placer vos éléments d’interface utilisateur dans l’IDE. Si vous utilisez des commandes définies en dehors de votre package, utilisez l’élément [UsedCommands](../../extensibility/usedcommands-element.md) pour informer Visual Studio.

#### <a name="to-include-visual-studio-resources"></a>Pour inclure des ressources Visual Studio

1. En haut de l’élément `CommandTable`, ajoutez un élément `Extern` pour chaque fichier externe à référencer et définissez l’attribut `href` sur le nom du fichier. Vous pouvez référencer les fichiers d’en-tête suivants pour accéder aux ressources Visual Studio :

   - *Stdidcmd. h*: définit des ID pour toutes les commandes exposées par Visual Studio.

   - *Vsshlids. h*: contient les ID de commande des menus Visual Studio.

2. Si votre package appelle une commande définie par Visual Studio ou par d’autres packages, ajoutez un élément `UsedCommands` après l’élément `Commands`. Remplissez cet élément avec un élément [UsedCommand](../../extensibility/usedcommand-element.md) pour chaque commande que vous appelez et qui ne fait pas partie de votre package. Définissez les attributs `guid` et `id` des éléments `UsedCommand` sur les valeurs GUID et ID des commandes à appeler.

   Pour plus d’informations sur la recherche des GUID et des ID des commandes Visual Studio, consultez [GUID et ID des commandes Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md). Pour appeler des commandes à partir d’autres packages, utilisez le GUID et l’ID de la commande tels qu’ils sont définis dans le fichier *. vsct* pour ces packages.

### <a name="declare-ui-elements"></a>Déclarer des éléments d’interface utilisateur
 Déclarez tous les nouveaux éléments d’interface utilisateur dans la section `Symbols` du fichier *. vsct* .

#### <a name="to-declare-ui-elements"></a>Pour déclarer des éléments d’interface utilisateur

1. Dans l’élément `Symbols`, ajoutez trois éléments [GuidSymbol](../../extensibility/guidsymbol-element.md) . Chaque élément `GuidSymbol` a un attribut `name` et un attribut `value`. Définissez l’attribut `name` pour qu’il reflète l’objectif de l’élément. L’attribut `value` prend un GUID. (Pour générer un GUID, dans le menu **Outils** , sélectionnez **créer un GUID**, puis sélectionnez le **format du Registre**.)

     Le premier élément `GuidSymbol` représente votre package et n’a généralement aucun enfant. Le deuxième élément `GuidSymbol` représente le jeu de commandes et contient tous les symboles qui définissent vos menus, groupes et commandes. Le troisième élément `GuidSymbol` représente votre magasin d’images et contient des symboles pour toutes les icônes de vos commandes. Si vous n’avez aucune commande qui utilise des icônes, vous pouvez omettre le troisième élément `GuidSymbol`.

2. Dans l’élément `GuidSymbol` qui représente votre jeu de commandes, ajoutez un ou plusieurs éléments [IDSymbol](../../extensibility/idsymbol-element.md) . Chacun d’eux représente un menu, une barre d’outils, un groupe ou une commande que vous ajoutez à l’interface utilisateur.

     Pour chaque élément `IDSymbol`, affectez à l’attribut `name` le nom que vous utiliserez pour faire référence au menu, au groupe ou à la commande correspondant, puis définissez l’élément `value` sur un nombre hexadécimal qui représente son ID de commande. Deux `IDSymbol` éléments ayant le même parent peuvent avoir la même valeur.

3. Si l’un de vos éléments d’interface utilisateur requiert des icônes, ajoutez un élément `IDSymbol` pour chaque icône à l’élément `GuidSymbol` qui représente votre magasin d’images.

### <a name="put-ui-elements-in-the-ide"></a>Placer des éléments d’interface utilisateur dans l’IDE
 Les éléments [menus](../../extensibility/menus-element.md), [groupes](../../extensibility/groups-element.md)et [boutons](../../extensibility/buttons-element.md) contiennent les définitions de tous les menus, groupes et commandes définis dans votre package. Placez ces menus, groupes et commandes dans l’IDE à l’aide d’un élément [parent](../../extensibility/parent-element.md) , qui fait partie de la définition de l’élément d’interface utilisateur, ou à l’aide d’un élément [commandplacement ayant](../../extensibility/commandplacement-element.md) défini ailleurs.

 Chaque élément `Menu`, `Group`et `Button` a un attribut `guid` et un attribut `id`. Définissez toujours l’attribut `guid` pour qu’il corresponde au nom de l’élément `GuidSymbol` qui représente votre jeu de commandes, et définissez l’attribut `id` sur le nom de l’élément `IDSymbol` qui représente votre menu, groupe ou commande dans la section `Symbols`.

#### <a name="to-define-ui-elements"></a>Pour définir des éléments d’interface utilisateur

1. Si vous définissez des menus, des sous-menus, des menus contextuels ou des barres d’outils nouveaux, ajoutez un élément `Menus` à l’élément `Commands`. Ensuite, pour chaque menu à créer, ajoutez un élément de [menu](../../extensibility/menu-element.md) à l’élément `Menus`.

    Définissez les attributs `guid` et `id` de l’élément `Menu`, puis définissez l’attribut `type` sur le type de menu souhaité. Vous pouvez également définir l’attribut `priority` pour établir la position relative du menu dans le groupe parent.

   > [!NOTE]
   > L’attribut `priority` ne s’applique pas aux barres d’outils et aux menus contextuels.

2. Toutes les commandes de l’IDE de Visual Studio doivent être hébergées par des groupes de commandes, qui sont les enfants directs des menus et des barres d’outils. Si vous ajoutez de nouveaux menus ou barres d’outils à l’IDE, ceux-ci doivent contenir de nouveaux groupes de commandes. Vous pouvez également ajouter des groupes de commandes à des menus et des barres d’outils existants afin de pouvoir regrouper visuellement vos commandes.

    Lorsque vous ajoutez de nouveaux groupes de commandes, vous devez d’abord créer un élément `Groups`, puis y ajouter un élément [Group](../../extensibility/group-element.md) pour chaque groupe de commandes.

    Définissez les attributs `guid` et `id` de chaque élément `Group`, puis définissez l’attribut `priority` pour établir la position relative du groupe dans le menu parent. Pour plus d’informations, consultez [créer des groupes de boutons réutilisables](../../extensibility/creating-reusable-groups-of-buttons.md).

3. Si vous ajoutez de nouvelles commandes à l’IDE, ajoutez un élément `Buttons` à l’élément `Commands`. Ensuite, pour chaque commande, ajoutez un élément [Button](../../extensibility/button-element.md) à l’élément `Buttons`.

   1. Définissez les attributs `guid` et `id` de chaque élément `Button`, puis définissez l’attribut `type` sur le type de bouton souhaité. Vous pouvez également définir l’attribut `priority` pour établir la position relative de la commande dans le groupe parent.

       > [!NOTE]
       > Utilisez `type="button"` pour les commandes de menu standard et les boutons des barres d’outils.

   2. Dans l’élément `Button`, ajoutez un élément [Strings](../../extensibility/strings-element.md) contenant un élément [ButtonText](../../extensibility/buttontext-element.md) et un élément [CommandName](../../extensibility/commandname-element.md) . L’élément `ButtonText` fournit l’étiquette de texte pour un élément de menu, ou l’info-bulle pour un bouton de barre d’outils. L’élément `CommandName` fournit le nom de la commande à utiliser dans la commande.

   3. Si votre commande a une icône, créez un élément [Icon](../../extensibility/icon-element.md) dans l’élément `Button` et affectez à ses attributs `guid` et `id` la valeur de l’élément `Bitmap` pour l’icône.

       > [!NOTE]
       > Les boutons de la barre d’outils doivent avoir des icônes.

   Pour plus d’informations, consultez [MenuCommands et OleMenuCommands](/visualstudio/extensibility/menucommands-vs-olemenucommands?view=vs-2015).

4. Si l’une de vos commandes nécessite des icônes, ajoutez un élément [bitmaps](../../extensibility/bitmaps-element.md) à l’élément `Commands`. Puis, pour chaque icône, ajoutez un élément [bitmap](../../extensibility/bitmap-element.md) à l’élément `Bitmaps`. C’est ici que vous spécifiez l’emplacement de la ressource bitmap. Pour plus d’informations, consultez [Ajouter des icônes à des commandes de menu](../../extensibility/adding-icons-to-menu-commands.md).

   Vous pouvez vous appuyer sur la structure de parente pour placer correctement la plupart des menus, groupes et commandes. Pour les jeux de commandes de très grande taille, ou lorsqu’un menu, un groupe ou une commande doit apparaître à plusieurs emplacements, nous vous recommandons de spécifier le placement de la commande.

#### <a name="to-rely-on-parenting-to-place-ui-elements-in-the-ide"></a>Pour s’appuyer sur le parent pour placer des éléments d’interface utilisateur dans l’IDE

1. Pour un parent classique, créez un élément `Parent` dans chaque `Menu`, `Group`et `Command` élément défini dans votre package.

    La cible de l’élément `Parent` est le menu ou le groupe qui contiendra le menu, le groupe ou la commande.

   1. Affectez à l’attribut `guid` le nom de l’élément `GuidSymbol` qui définit le jeu de commandes. Si l’élément cible ne fait pas partie de votre package, utilisez le GUID de ce jeu de commandes, tel que défini dans le fichier *. vsct* correspondant.

   2. Définissez l’attribut `id` pour qu’il corresponde à l’attribut `id` du menu ou du groupe cible. Pour obtenir la liste des menus et des groupes exposés par Visual Studio, consultez [GUID et ID des menus](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md) ou GUIDs Visual Studio [et ID des barres d’outils de Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md).

   Si vous avez un grand nombre d’éléments d’interface utilisateur à placer dans l’IDE, ou si vous avez des éléments qui doivent apparaître à plusieurs emplacements, définissez leurs emplacements dans l’élément [CommandPlacements](../../extensibility/commandplacements-element.md) , comme indiqué dans les étapes suivantes.

#### <a name="to-use-command-placement-to-place-ui-elements-in-the-ide"></a>Pour utiliser le positionnement de commande pour placer des éléments d’interface utilisateur dans l’IDE

1. Après l’élément `Commands`, ajoutez un élément `CommandPlacements`.

2. Dans l’élément `CommandPlacements`, ajoutez un élément `CommandPlacement` pour chaque menu, groupe ou commande à placer.

    Chaque élément `CommandPlacement` ou `Parent` place un menu, un groupe ou une commande dans un emplacement IDE. Un élément d’interface utilisateur ne peut avoir qu’un seul parent, mais il peut avoir plusieurs placements de commande. Pour placer un élément d’interface utilisateur à plusieurs emplacements, ajoutez un élément `CommandPlacement` pour chaque emplacement.

3. Définissez les attributs `guid` et `id` de chaque élément `CommandPlacement` sur le groupe ou le menu d’hébergement, comme vous le feriez pour un élément `Parent`. Vous pouvez également définir l’attribut `priority` pour établir la position relative de l’élément d’interface utilisateur.

   Vous pouvez mélanger l’emplacement par le biais du parent et de l’emplacement des commandes. Toutefois, pour les jeux de commandes de très grande taille, nous vous recommandons d’utiliser uniquement le placement de commande.

### <a name="add-specialized-behaviors"></a>Ajouter des comportements spécialisés
 Vous pouvez utiliser l’élément [CommandFlag](../../extensibility/command-flag-element.md) pour modifier le comportement des menus et des commandes, par exemple, pour modifier leur apparence et leur visibilité. Vous pouvez également avoir une incidence sur l’affichage d’une commande à l’aide de l’élément [VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) , ou ajouter des raccourcis clavier à l’aide de l’élément [KeyBindings](../../extensibility/keybindings-element.md) . Certains types de menus et de commandes ont déjà des comportements spécialisés intégrés.

#### <a name="to-add-specialized-behaviors"></a>Pour ajouter des comportements spécialisés

1. Pour rendre un élément d’interface utilisateur visible uniquement dans certains contextes d’interface utilisateur, par exemple, quand une solution est chargée, utilisez des contraintes de visibilité.

   1. Après l’élément `Commands`, ajoutez un élément `VisibilityConstraints`.

   2. Pour chaque élément d’interface utilisateur à contraindre, ajoutez un élément [VisibilityItem](../../extensibility/visibilityitem-element.md) .

   3. Pour chaque élément `VisibilityItem`, définissez les attributs `guid` et `id` sur le menu, le groupe ou la commande, puis définissez l’attribut `context` sur le contexte d’interface utilisateur de votre choix, tel que défini dans la classe <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80>.

2. Pour définir la visibilité ou la disponibilité d’un élément d’interface utilisateur dans le code, utilisez un ou plusieurs des indicateurs de commande suivants :

   - `DefaultDisabled`

   - `DefaultInvisible`

   - `DynamicItemStart`

   - `DynamicVisibility`

   - `NoShowOnMenuController`

   - `NotInTBList`

   Pour plus d’informations, consultez l’élément [CommandFlag](../../extensibility/command-flag-element.md) .

3. Pour modifier le mode d’affichage d’un élément ou modifier son apparence de manière dynamique, utilisez un ou plusieurs des indicateurs de commande suivants :

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

   Pour plus d’informations, consultez l’élément [CommandFlag](../../extensibility/command-flag-element.md) .

4. Pour modifier la façon dont un élément réagit lorsqu’il reçoit des commandes, utilisez un ou plusieurs des indicateurs de commande suivants :

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

   Pour plus d’informations, consultez l’élément [CommandFlag](../../extensibility/command-flag-element.md) .

5. Pour attacher un raccourci clavier dépendant du menu à un menu ou à un élément d’un menu, ajoutez une esperluette (&) dans l’élément `ButtonText` pour le menu ou l’élément de menu. Le caractère qui suit l’esperluette est le raccourci clavier actif lorsque le menu parent est ouvert.

6. Pour attacher un raccourci clavier indépendant du menu à une commande, utilisez l’élément [KeyBindings](../../extensibility/keybindings-element.md) . Pour plus d’informations, consultez l’élément [KeyBinding](../../extensibility/keybinding-element.md) .

7. Pour localiser le texte du menu, utilisez l’élément `LocCanonicalName`. Pour plus d’informations, consultez l’élément [Strings](../../extensibility/strings-element.md) .

   Certains types de menu et de bouton incluent des comportements spécialisés. La liste suivante décrit quelques types de menu et de bouton spécialisés. Pour les autres types, consultez les descriptions d’attribut `types` dans le [menu](../../extensibility/menu-element.md), le [bouton](../../extensibility/button-element.md)et les éléments de [liste déroulante](../../extensibility/combo-element.md) .

   - Zone de liste modifiable : une zone de liste déroulante est une liste déroulante qui peut être utilisée dans une barre d’outils. Pour ajouter des zones de liste déroulante à l’interface utilisateur, créez un élément [combos](../../extensibility/combos-element.md) dans l’élément `Commands`. Ajoutez ensuite à l’élément `Combos` un élément `Combo` pour chaque zone de liste déroulante à ajouter. `Combo` éléments ont les mêmes attributs et enfants que les éléments `Button` et ont également des attributs `DefaultWidth` et `idCommandList`. L’attribut `DefaultWidth` définit la largeur en pixels, et l’attribut `idCommandList` pointe sur un ID de commande utilisé pour remplir la zone de liste déroulante.

   - Contrôleur de menu : un contrôleur de menu est un bouton qui contient une flèche en regard de celui-ci. Cliquez sur la flèche pour ouvrir une liste. Pour ajouter un contrôleur de menu à l’interface utilisateur, créez un élément `Menu` et affectez à son attribut `type` la valeur `MenuController` ou `MenuControllerLatched`, selon le comportement souhaité. Pour remplir un contrôleur de menu, définissez-le en tant que parent d’un élément `Group`. Le contrôleur de menu affiche tous les enfants de ce groupe dans sa liste déroulante.

## <a name="see-also"></a>Voir aussi
- [Étendre des menus et des commandes](../../extensibility/extending-menus-and-commands.md)
- [Fichiers de table de commandes Visual Studio (. vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Référence du schéma XML VSCT](../../extensibility/vsct-xml-schema-reference.md)