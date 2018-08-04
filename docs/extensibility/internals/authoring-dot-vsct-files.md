---
title: Création. Fichiers VSCT | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, manual authoring
ms.assetid: e9f715dc-12b7-439b-bdf3-f3dc75e62f1c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b03c36fdec85c638e708a4f7c99cedd870cc2a71
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2018
ms.locfileid: "39498809"
---
# <a name="author-vsct-files"></a>Fichiers .vsct auteur
Ce document montre comment créer un *.vsct* fichier à ajouter des éléments de menu, les barres d’outils et les autres éléments d’interface (UI) à l’environnement de développement intégré (IDE) Visual Studio. Utilisez ces étapes lorsque vous ajoutez des éléments d’interface utilisateur à un package Visual Studio (VSPackage) qui n’a pas déjà un *.vsct* fichier.  
  
 Pour les nouveaux projets, nous vous recommandons d’utiliser le modèle de package Visual Studio, car il génère un *.vsct* fichier, en fonction de vos sélections, a déjà les éléments requis pour une commande de menu, une fenêtre outil ou un éditeur personnalisé . Vous pouvez modifier ce *.vsct* fichier pour satisfaire les besoins de votre VSPackage. Pour plus d’informations sur comment modifier un *.vsct* de fichiers, consultez les exemples dans [étendre des menus et commandes](../../extensibility/extending-menus-and-commands.md).  
  
## <a name="author-the-file"></a>Créez le fichier  
 Auteur un *.vsct* fichier dans ces phases : créer la structure des fichiers de ressources, déclarer les éléments d’interface utilisateur, placez les éléments d’interface utilisateur dans l’IDE et ajoutez tout comportement spécialisé.  
  
### <a name="file-structure"></a>Structure de fichiers  
 La structure de base d’un *.vsct* fichier est un [CommandTable](../../extensibility/commandtable-element.md) élément racine qui contient un [commandes](../../extensibility/commands-element.md) élément et un [symboles](../../extensibility/symbols-element.md) élément.  
  
#### <a name="to-create-the-file-structure"></a>Pour créer la structure de fichiers  
  
1.  Ajouter un *.vsct* fichier à votre projet en suivant les étapes décrites dans [Comment : créer un fichier .vsct](../../extensibility/internals/how-to-create-a-dot-vsct-file.md).  
  
2. Ajouter des espaces de noms obligatoires à la `CommandTable` élément, comme indiqué dans l’exemple suivant :  
  
    ```xml  
    <CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable"   
        xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  
    ```  
  
3.  Dans le `CommandTable` élément, ajoutez un `Commands` élément pour héberger tous vos menus personnalisés, les barres d’outils, les groupes de commandes et les commandes. Pour que vos éléments d’interface utilisateur personnalisés peuvent charger, le `Commands` élément doit avoir son `Package` attribut défini sur le nom du package.  
  
     Après le `Commands` élément, ajoutez un `Symbols` élément à définir les GUID pour le package et les noms et ID de commande pour vos éléments d’interface utilisateur.  
  
### <a name="include-visual-studio-resources"></a>Inclure des ressources de Visual Studio  
 Utilisez le [Extern](../../extensibility/extern-element.md) élément à accéder aux fichiers qui définissent les commandes de Visual Studio et les menus sont obligés de mettre les éléments d’interface utilisateur dans l’IDE. Si vous souhaitez utiliser les commandes définies en dehors de votre package, utilisez le [UsedCommands](../../extensibility/usedcommands-element.md) élément pour informer Visual Studio.  
  
#### <a name="to-include-visual-studio-resources"></a>Inclure des ressources de Visual Studio  
  
1.  En haut de la `CommandTable` élément, ajouter un `Extern` élément pour chaque fichier externe être référencé et définir le `href` nom à l’attribut du fichier. Vous pouvez référencer les fichiers d’en-tête suivants pour accéder aux ressources de Visual Studio :  
  
    -   *Stdidcmd.h*: définit l’ID pour toutes les commandes exposées par Visual Studio.  
  
    -   *Vsshlids.h*: contient les ID de commande pour les menus de Visual Studio.  
  
2.  Si votre package appelle toutes les commandes qui sont définies par Visual Studio ou par d’autres packages, ajoutez un `UsedCommands` élément après le `Commands` élément. Remplir cet élément avec un [UsedCommand](../../extensibility/usedcommand-element.md) élément pour chaque commande que vous appelez c'est-à-dire ne fait pas partie de votre package. Définir le `guid` et `id` les attributs de la `UsedCommand` éléments aux valeurs GUID et l’ID des commandes à appeler. 

   Pour plus d’informations sur la façon de trouver les commandes de GUID et ID de Visual Studio, consultez [commandes GUID et ID de Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md). Pour appeler des commandes à partir d’autres packages, utilisez le GUID et l’ID de la commande tel que défini dans le *.vsct* fichier pour ces packages.
  
### <a name="declare-ui-elements"></a>Déclarer des éléments d’interface utilisateur  
 Déclarer tous les nouveaux éléments de l’interface utilisateur dans le `Symbols` section de la *.vsct* fichier.  
  
#### <a name="to-declare-ui-elements"></a>Pour déclarer des éléments d’interface utilisateur  
  
1.  Dans le `Symbols` élément, ajoutez trois [GuidSymbol](../../extensibility/guidsymbol-element.md) éléments. Chaque `GuidSymbol` élément a un `name` attribut et un `value` attribut. Définir le `name` afin qu’il reflète l’objectif de l’élément d’attribut. Le `value` attribut accepte un GUID. (Pour générer un GUID, sur le **outils** menu, sélectionnez **créer un GUID**, puis sélectionnez **Format du Registre**.)  
  
     Le premier `GuidSymbol` élément représente votre package et a généralement pas d’enfants. La seconde `GuidSymbol` élément représente la commande définie et contient tous les symboles qui définissent des menus, des groupes et des commandes. La troisième `GuidSymbol` élément représente votre magasin d’images et contient des symboles pour toutes les icônes pour vos commandes. Si vous n’avez aucuns commandes qui utilisent des icônes, vous pouvez omettre le troisième `GuidSymbol` élément.  
  
2.  Dans le `GuidSymbol` élément qui représente votre jeu de commandes, ajoutez un ou plusieurs [IDSymbol](../../extensibility/idsymbol-element.md) éléments. Chacune de ces représentent un menu, une barre d’outils, un groupe ou une commande que vous ajoutez à l’interface utilisateur.  
  
     Pour chaque `IDSymbol` élément, définissez la `name` nom à l’attribut vous permet de faire référence au menu correspondant, du groupe ou de la commande et puis définissez la `value` élément à un nombre hexadécimal qui représente son ID de commande. Aucun deux `IDSymbol` éléments qui ont le même parent peuvent avoir la même valeur.  
  
3.  Si un de vos éléments d’interface utilisateur requiert des icônes, ajoutez un `IDSymbol` élément pour chaque icône sur le `GuidSymbol` élément qui représente votre magasin d’images.  
  
### <a name="put-ui-elements-in-the-ide"></a>Placer des éléments d’interface utilisateur dans l’IDE  
 Le [Menus](../../extensibility/menus-element.md), [groupes](../../extensibility/groups-element.md), et [boutons](../../extensibility/buttons-element.md) éléments contiennent les définitions de tous les menus, les groupes et les commandes qui sont définis dans votre package. Placez ces menus, les groupes et les commandes dans l’IDE en utilisant un [Parent](../../extensibility/parent-element.md) élément, qui fait partie de la définition d’élément de l’interface utilisateur, ou en utilisant un [CommandPlacement](../../extensibility/commandplacement-element.md) élément qui est défini ailleurs.  
  
 Chaque `Menu`, `Group`, et `Button` élément a un `guid` attribut et un `id` attribut. Toujours défini le `guid` attribut à faire correspondre le nom de la `GuidSymbol` élément qui représente votre commande de définir et de définir le `id` nom à l’attribut de la `IDSymbol` élément qui représente votre menu, groupe ou une commande dans le `Symbols`section.  
  
#### <a name="to-define-ui-elements"></a>Pour définir les éléments d’interface utilisateur  
  
1.  Si vous définissez les nouveaux menus, sous-menus, menus contextuels ou barres d’outils, ajoutez un `Menus` élément à la `Commands` élément. Ensuite, pour chaque menu doit être créé, ajoutez un [Menu](../../extensibility/menu-element.md) élément à la `Menus` élément.  
  
     Définir le `guid` et `id` attributs de la `Menu` élément, puis définissez le `type` attribut au type de menu de votre choix. Vous pouvez également définir le `priority` attribut pour établir la position relative du menu dans le groupe parent.  
  
    > [!NOTE]
    >  Le `priority` attribut ne s’applique pas aux barres d’outils et des menus contextuels.  
  
2.  Toutes les commandes dans l’IDE Visual Studio doivent être hébergés par les groupes de commandes, qui sont les enfants directs de menus et barres d’outils. Si vous ajoutez des nouveaux menus ou barres d’outils à l’IDE, il doivent contenir nouveaux groupes de commandes. Vous pouvez également ajouter des groupes de commandes aux menus et aux barres d’outils existant afin que vous pouvez regrouper visuellement vos commandes.  
  
     Lorsque vous ajoutez de nouveaux groupes de commandes, vous devez d’abord créer un `Groups` élément, puis ajoutez à ce dernier un [groupe](../../extensibility/group-element.md) élément pour chaque groupe de commandes.  
  
     Définir le `guid` et `id` attributs de chaque `Group` élément, puis définissez le `priority` attribut pour établir la position relative du groupe dans le menu parent. Pour plus d’informations, consultez [créer des groupes de boutons réutilisables](../../extensibility/creating-reusable-groups-of-buttons.md).  
  
3.  Si vous ajoutez les nouvelles commandes à l’IDE, ajouter un `Buttons` élément à la `Commands` élément. Ensuite, pour chaque commande, ajoutez un [bouton](../../extensibility/button-element.md) élément à la `Buttons` élément.  
  
    1.  Définir le `guid` et `id` attributs de chaque `Button` élément, puis définissez la `type` le type de bouton que vous souhaitez que l’attribut. Vous pouvez également définir le `priority` attribut pour établir la position relative de la commande dans le groupe parent.  
  
        > [!NOTE]
        >  Utilisez `type="button"` pour les commandes de menu standard et des boutons des barres d’outils.  
  
    2.  Dans le `Button` élément, ajoutez un [chaînes](../../extensibility/strings-element.md) élément contenant un [ButtonText](../../extensibility/buttontext-element.md) élément et un [CommandName](../../extensibility/commandname-element.md) élément. Le `ButtonText` élément fournit l’étiquette de texte pour un élément de menu ou de l’info-bulle pour un bouton de barre d’outils. Le `CommandName` élément fournit le nom de la commande à utiliser dans la commande.  
  
    3.  Si votre commande aura une icône, créez un [icône](../../extensibility/icon-element.md) élément dans le `Button` élément et définissez son `guid` et `id` des attributs pour le `Bitmap` élément pour l’icône.  
  
        > [!NOTE]
        >  Boutons de barre d’outils doivent avoir des icônes.  
  
   Pour plus d’informations, consultez [MenuCommands et. OleMenuCommands](../../extensibility/menucommands-vs-olemenucommands.md).  
  
4.  Si vos commandes nécessitent des icônes, ajoutez un [Bitmaps](../../extensibility/bitmaps-element.md) élément à la `Commands` élément. Ensuite, pour chaque icône, ajoutez un [Bitmap](../../extensibility/bitmap-element.md) élément à la `Bitmaps` élément. Voici où vous spécifiez l’emplacement de la ressource bitmap. Pour plus d’informations, consultez [ajouter des icônes aux commandes de menu](../../extensibility/adding-icons-to-menu-commands.md).  
  
 Vous pouvez vous appuyer sur la structure parentage placer correctement la plupart des menus, des groupes et des commandes. Pour les jeux de commandes très volumineux, ou quand un menu, un groupe ou une commande doit apparaître à plusieurs endroits, nous vous recommandons de spécifier placement de commande.  
  
#### <a name="to-rely-on-parenting-to-place-ui-elements-in-the-ide"></a>S’appuyer sur le parentage pour placer des éléments d’interface utilisateur dans l’IDE  
  
1.  Pour le parentage typique, créez un `Parent` élément dans chaque `Menu`, `Group`, et `Command` élément qui est défini dans votre package.  
  
     La cible de la `Parent` élément est le menu ou un groupe qui contiendra le menu, un groupe ou une commande.  
  
    1.  Définir le `guid` nom à l’attribut de la `GuidSymbol` élément qui définit le jeu de commandes. Si l’élément cible ne fait pas partie de votre package, utilisez le guid pour ce jeu de commandes, comme défini dans le correspondantes *.vsct* fichier.  
  
    2.  Définir le `id` attribut à faire correspondre le `id` attribut du menu de la cible ou du groupe. Pour obtenir la liste des menus et des groupes qui sont exposées par Visual Studio, consultez [menus GUID et ID de Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md) ou [barres d’outils de GUID et ID de Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md).  
  
 Si vous avez un grand nombre d’éléments d’interface utilisateur à placer dans l’IDE, ou si vous avez des éléments qui doivent apparaître à plusieurs endroits, définir leurs placements dans le [CommandPlacements](../../extensibility/commandplacements-element.md) élément, comme indiqué dans les étapes suivantes.  
  
#### <a name="to-use-command-placement-to-place-ui-elements-in-the-ide"></a>Placement de commande permet de placer des éléments d’interface utilisateur dans l’IDE  
  
1.  Après le `Commands` élément, ajoutez un `CommandPlacements` élément.  
  
2.  Dans le `CommandPlacements` élément, ajoutez un `CommandPlacement` élément pour chaque menu, un groupe ou une commande à placer.  
  
     Chaque `CommandPlacement` élément ou `Parent` élément place un menu, groupe ou commande dans un emplacement de l’IDE. Un élément d’interface utilisateur peut avoir uniquement un seul parent, mais il peut avoir plusieurs placements de commandes. Pour placer un élément d’interface utilisateur dans plusieurs emplacements, ajouter un `CommandPlacement` élément pour chaque emplacement.  
  
3.  Définir le `guid` et `id` attributs de chaque `CommandPlacement` élément au menu hébergement ou au groupe, tout comme vous le feriez pour un `Parent` élément. Vous pouvez également définir le `priority` attribut pour établir la position relative de l’élément d’interface utilisateur.  
  
 Vous pouvez combiner le positionnement par parentage et commande. Toutefois, pour les jeux de commandes très volumineux, nous vous recommandons d’utiliser uniquement les placement de commande.  
  
### <a name="add-specialized-behaviors"></a>Ajouter des comportements spécialisés  
 Vous pouvez utiliser la [CommandFlag](../../extensibility/command-flag-element.md) élément pour modifier le comportement des menus et commandes, par exemple, pour modifier leur apparence et leur visibilité. Vous pouvez également changer lorsqu’une commande est visible à l’aide de la [VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) élément, ou ajouter des raccourcis clavier à l’aide de la [KeyBindings](../../extensibility/keybindings-element.md) élément. Certains types de menus et commandes déjà avaient spécialisé comportements intégrés.  
  
#### <a name="to-add-specialized-behaviors"></a>Pour ajouter des comportements spécialisés  
  
1.  Pour rendre un élément d’interface utilisateur visible uniquement dans certains contextes d’interface utilisateur, par exemple, quand une solution est chargée, utilisez des contraintes de visibilité.  
  
    1.  Après le `Commands` élément, ajoutez un `VisibilityConstraints` élément.  
  
    2.  Pour chaque élément d’interface utilisateur limiter, ajoutez un [VisibilityItem](../../extensibility/visibilityitem-element.md) élément.  
  
    3.  Pour chaque `VisibilityItem` élément, définissez la `guid` et `id` attributs pour le menu, groupe, ou commande, puis définissez le `context` d’attribut pour le contexte de l’interface utilisateur que vous le souhaitez, tel que défini dans le <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> classe.   
  
2.  Pour définir la visibilité ou la disponibilité d’un élément d’interface utilisateur dans le code, utilisez une ou plusieurs des indicateurs de commande suivants :  
  
    -   `DefaultDisabled`
  
    -   `DefaultInvisible`
  
    -   `DynamicItemStart` 
  
    -   `DynamicVisibility`
  
    -   `NoShowOnMenuController`
  
    -   `NotInTBList`
  
   Pour plus d’informations, consultez le [CommandFlag](../../extensibility/command-flag-element.md) élément.  
  
3.  Pour modifier la façon dont un élément s’affiche, ou modifier son apparence dynamiquement, utilisez une ou plusieurs des indicateurs de commande suivants :  
  
    -   `AlwaysCreate`  
  
    -   `CommandWellOnly`  
  
    -   `DefaultDocked`  
  
    -   `DontCache`  
  
    -   `DynamicItemStart`  
  
    -   `FixMenuController`  
  
    -   `IconAndText`  
  
    -   `Pict`  
  
    -   `StretchHorizontally`  
  
    -   `TextMenuUseButton`  
  
    -   `TextChanges`  
  
    -   `TextOnly`  
  
   Pour plus d’informations, consultez le [CommandFlag](../../extensibility/command-flag-element.md) élément.  
  
4.  Pour modifier la façon dont un élément réagit lorsqu’il reçoit des commandes, utilisez une ou plusieurs des indicateurs de commande suivants :  
  
    -   `AllowParams`  
  
    -   `CaseSensitive`  
  
    -   `CommandWellOnly`  
  
    -   `FilterKeys`  
  
    -   `NoAutoComplete`  
  
    -   `NoButtonCustomize`  
  
    -   `NoKeyCustomize`  
  
    -   `NoToolbarClose`  
  
    -   `PostExec`  
  
    -   `RouteToDocs`  
  
    -   `TextIsAnchorCommand`  
  
   Pour plus d’informations, consultez le [CommandFlag](../../extensibility/command-flag-element.md) élément.  
  
5.  Pour attacher un raccourci clavier de dépendant du menu à un menu ou d’un élément dans un menu, ajoutez une esperluette (&) dans le `ButtonText` élément au menu ou un élément de menu. Le caractère qui suit l’et commercial est le raccourci clavier active quand le menu parent est ouvert.  
  
6.  Pour attacher un raccourci clavier d’indépendant du menu à une commande, utilisez le [KeyBindings](../../extensibility/keybindings-element.md) élément. Pour plus d’informations, consultez le [KeyBinding](../../extensibility/keybinding-element.md) élément.  
  
7.  Pour localiser le texte de menu, utilisez le `LocCanonicalName` élément. Pour plus d’informations, consultez le [chaînes](../../extensibility/strings-element.md) élément.  
  
 Certains types de menu et le bouton inclure des comportements spécialisés. La liste suivante décrit certaines menu spécialisé et les types de bouton. Pour les autres types, consultez le `types` attribut descriptions dans le [Menu](../../extensibility/menu-element.md), [bouton](../../extensibility/button-element.md), et [liste déroulante](../../extensibility/combo-element.md) éléments.  
  
 - Zone de liste déroulante :  
    Une zone de liste modifiable est une liste déroulante qui peut être utilisée sur une barre d’outils. Pour ajouter des zones de liste déroulante à l’interface utilisateur, créez un [Combos](../../extensibility/combos-element.md) élément dans le `Commands` élément. Puis ajouter à la `Combos` élément un `Combo` élément pour chaque zone de liste déroulante à ajouter. `Combo` éléments ont les mêmes attributs et enfants en tant que `Button` éléments et avoir également `DefaultWidth` et `idCommandList` attributs. Le `DefaultWidth` attribut définit la largeur en pixels et le `idCommandList` points d’attribut à un ID de commande qui est utilisé pour remplir la zone de liste déroulante. 
  
 - Contrôleur de menu :  
    Un contrôleur de menu est un bouton comportant une flèche en regard de celle-ci. Ouvre la liste en cliquant sur la flèche. Pour ajouter un contrôleur de menu à l’interface utilisateur, créez un `Menu` élément et définissez son `type` attribut `MenuController` ou `MenuControllerLatched`, selon le comportement souhaité. Pour remplir un contrôleur de menu, définissez-le comme le parent d’un `Group` élément. Le contrôleur de menu affiche tous les enfants de ce groupe sur sa liste déroulante.  
  
## <a name="see-also"></a>Voir aussi  
 [Étendre des menus et commandes](../../extensibility/extending-menus-and-commands.md)   
 [Visual Studio fichiers command table (.vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Référence du schéma XML VSCT](../../extensibility/vsct-xml-schema-reference.md)