---
title: "Cr&#233;ation. Fichiers VSCT | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Création de fichiers VSCT, manuels"
ms.assetid: e9f715dc-12b7-439b-bdf3-f3dc75e62f1c
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# Cr&#233;ation. Fichiers VSCT
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ce document montre comment créer un fichier .vsct pour ajouter des éléments de menu, les barres d'outils et autres éléments d'interface \(UI\) à l'environnement de développement intégré \(IDE\) Visual Studio. Utilisez ces étapes lorsque vous ajoutez des éléments d'interface utilisateur à un Package Visual Studio \(VSPackage\) qui n'a pas déjà un fichier .vsct.  
  
 Pour les nouveaux projets, nous vous recommandons d'utiliser le modèle de Package Visual Studio, car il génère un fichier .vsct qui, selon vos sélections, possède déjà les éléments requis pour un éditeur personnalisé, une fenêtre outil ou une commande de menu. Vous pouvez modifier ce fichier .vsct pour satisfaire les besoins de votre VSPackage. Pour plus d'informations sur la modification d'un fichier .vsct, consultez les exemples dans [Extension des Menus et commandes](../../extensibility/extending-menus-and-commands.md).  
  
## Création du fichier  
 Créez un fichier .vsct dans ces phases : créer la structure de fichiers et de ressources, déclarer les éléments d'interface utilisateur, placer les éléments d'interface utilisateur dans l'IDE et ajoutez tous les comportements spécifiques.  
  
### Structure de fichiers  
 La structure de base d'un fichier .vsct est un [CommandTable](../../extensibility/commandtable-element.md) élément racine contenant un [commandes](../../extensibility/commands-element.md) élément et un [symboles](../../extensibility/symbols-element.md) élément.  
  
##### Pour créer la structure de fichiers  
  
1.  Ajoutez un fichier .vsct à votre projet en suivant les étapes de [Comment : créer un. Fichier VSCT](../../extensibility/internals/how-to-create-a-dot-vsct-file.md).  
  
2.  Ajouter des espaces de noms obligatoires à la `CommandTable` élément, comme indiqué dans l'exemple suivant.  
  
    ```xml  
    <CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable"   
    	xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  
    ```  
  
3.  Dans la `CommandTable` élément, ajouter un `Commands` élément pour héberger toutes vos commandes, barres d'outils, de groupes de commandes et des menus personnalisés. Pour que vos éléments d'interface utilisateur personnalisées peuvent charger, le `Commands` élément doit avoir son `Package` attribut défini sur le nom du package.  
  
     Après le `Commands` élément, ajouter un `Symbols` élément à définir les GUID pour le package et les noms et les ID de commande pour vos éléments d'interface utilisateur.  
  
### Y compris des ressources de Visual Studio  
 Utilisez le [Extern](../../extensibility/extern-element.md) élément à accéder aux fichiers qui définissent les commandes de Visual Studio et les menus sont obligés de mettre vos éléments d'interface utilisateur dans l'IDE. Si vous utilisez les commandes définies en dehors de votre package, utilisez la [UsedCommands](../../extensibility/usedcommands-element.md) élément pour informer Visual Studio.  
  
##### Inclure des ressources de Visual Studio  
  
1.  En haut de la `CommandTable` élément, ajouter un `Extern` élément pour chaque fichier externe référencé, et définir le `href` d'attribut pour le nom du fichier. Vous pouvez référencer les fichiers d'en\-tête suivant pour accéder aux ressources de Visual Studio :  
  
    -   Stdidcmd.h, définit des ID pour toutes les commandes sont exposées par Visual Studio.  
  
    -   Vsshlids.h, contient les ID de commande de menus Visual Studio.  
  
2.  Si votre package appelle toutes les commandes qui sont définies par Visual Studio ou par d'autres packages, ajouter un `UsedCommands` élément après le `Commands` élément. Remplir cet élément avec un [UsedCommand](../../extensibility/usedcommand-element.md) élément pour chaque commande que vous appelez c'est\-à\-dire ne fait pas partie de votre package. Définir le `guid` et `id` les attributs de la `UsedCommand` éléments aux valeurs GUID et l'ID des commandes pour appeler. Pour plus d'informations sur la façon de trouver les commandes de GUID et ID de Visual Studio, consultez [GUID et ID de commandes de Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md). Pour appeler des commandes à partir d'autres packages, utilisez le GUID et l'ID de la commande, tel que défini dans le fichier .vsct pour ces packages.  
  
### Déclarer des éléments d'interface utilisateur  
 Déclarez tous les nouveaux éléments de l'interface utilisateur dans la `Symbols` section du fichier .vsct.  
  
##### Pour déclarer des éléments d'interface utilisateur  
  
1.  Dans la `Symbols` élément, ajouter trois [GuidSymbol](../../extensibility/guidsymbol-element.md) éléments. Chaque `GuidSymbol` élément a un `name` attribut et un `value` attribut. Définir le `name` afin qu'il reflète l'objectif de l'élément d'attribut. Le `value` attribut prend un GUID. \(Pour générer un GUID, sur le **outils** menu, cliquez sur **créer un GUID**, puis sélectionnez **Format du Registre**.\)  
  
     Le premier `GuidSymbol` élément représente votre package et n'a généralement pas d'enfants. La seconde `GuidSymbol` élément représente la commande définie et contient tous les symboles qui définissent des menus, des groupes et des commandes. La troisième `GuidSymbol` élément représente votre magasin d'image et contient des symboles pour toutes les icônes pour vos commandes. Si vous ne possédez aucuns commandes qui utilisent des icônes, vous pouvez omettre le troisième `GuidSymbol` élément.  
  
2.  Dans la `GuidSymbol` élément qui représente votre jeu de commandes, ajoutez un ou plusieurs [IDSymbol](../../extensibility/idsymbol-element.md) éléments. Chacune de ces représente un menu, une barre d'outils, un groupe ou une commande que vous ajoutez à l'interface utilisateur.  
  
     Pour chaque `IDSymbol` élément, définissez la `name` nom à l'attribut vous permet de faire référence au menu correspondant, du groupe ou de la commande et puis définissez la `value` élément en un nombre hexadécimal qui représente son id de commande. Deux `IDSymbol` éléments qui ont le même parent peuvent avoir la même valeur.  
  
3.  Si un de vos éléments d'interface utilisateur requiert icônes, ajoutez un `IDSymbol` élément pour chaque icône du `GuidSymbol` élément qui représente votre magasin d'image.  
  
### Placer des éléments d'interface utilisateur dans l'IDE  
 Le [Menus](../../extensibility/menus-element.md) élément [groupes](../../extensibility/groups-element.md) élément, et [boutons](../../extensibility/buttons-element.md) élément contiennent les définitions de tous les menus, les groupes et les commandes qui sont définis dans votre package. Placer ces menus, les groupes et les commandes dans l'IDE en utilisant un [Parent](../../extensibility/parent-element.md) élément, qui fait partie de la définition d'élément de l'interface utilisateur, ou en utilisant un [CommandPlacement](../../extensibility/commandplacement-element.md) élément qui est défini ailleurs.  
  
 Chaque `Menu`, `Group`, et `Button` élément a un `guid` attribut et un `id` attribut. Toujours la valeur la `guid` attribut à faire correspondre le nom de la `GuidSymbol` élément qui représente votre commande de définir et de définir la `id` le nom de l'attribut le `IDSymbol` élément qui représente votre menu, un groupe ou une commande dans la `Symbols` section.  
  
##### Pour définir les éléments d'interface utilisateur  
  
1.  Si vous définissez nouveaux menus, sous\-menus, menus contextuels, des barres d'outils, ajoutez un `Menus` élément vers le `Commands` élément. Ensuite, pour chaque menu doit être créé, ajoutez un [Menu](../../extensibility/menu-element.md) élément à la `Menus` élément.  
  
     Définir le `guid` et `id` les attributs de la `Menu` élément et définissez la `type` attribut au type de menu que vous voulez. Vous pouvez également définir le `priority` attribut pour établir la position relative du menu dans le groupe parent.  
  
    > [!NOTE]
    >  Le `priority` attribut ne s'applique pas aux barres d'outils et des menus contextuels.  
  
2.  Toutes les commandes dans l'IDE Visual Studio doivent être hébergés par les groupes de commandes, qui sont les enfants directs des menus et barres d'outils. Si vous ajoutez des nouveaux menus ou barres d'outils de l'IDE, ces doivent contenir des groupes de commandes. Vous pouvez également ajouter des groupes de commandes aux menus et barres d'outils existants afin que vous pouvez regrouper visuellement vos commandes.  
  
     Lorsque vous ajoutez de nouveaux groupes de commande, vous devez d'abord créer un `Groups` élément, puis ajoutez à celui\-ci un [groupe](../../extensibility/group-element.md) élément pour chaque groupe de commandes.  
  
     Définir le `guid` et `id` les attributs de chaque `Group` élément et définissez la `priority` attribut pour établir la position relative du groupe dans le menu parent. Pour plus d'informations, consultez [Création de groupes de boutons réutilisables](../../extensibility/creating-reusable-groups-of-buttons.md).  
  
3.  Si vous ajoutez les nouvelles commandes à l'IDE, ajoutez un `Buttons` élément vers le `Commands` élément. Ensuite, pour chaque commande, ajoutez un [bouton](../../extensibility/button-element.md) élément vers le `Buttons` élément.  
  
    1.  Définir le `guid` et `id` les attributs de chaque `Button` élément et définissez la `type` le type de bouton que vous souhaitez que l'attribut. Vous pouvez également définir le `priority` attribut pour établir la position relative de la commande dans le groupe parent.  
  
        > [!NOTE]
        >  Utilisez `type="button"` pour les boutons des barres d'outils et les commandes de menu standard.  
  
    2.  Dans la `Button` élément, ajouter un [chaînes](../../extensibility/strings-element.md) élément contenant un [ButtonText](../../extensibility/buttontext-element.md) élément et un [CommandName](../../extensibility/commandname-element.md) élément. Le `ButtonText` élément fournit l'étiquette de texte pour un élément de menu ou de l'info\-bulle pour un bouton de barre d'outils. Le `CommandName` élément fournit le nom de la commande à utiliser dans la commande.  
  
    3.  Si votre commande aura une icône, créez un [icône](../../extensibility/icon-element.md) élément dans le `Button` et affectez sa `guid` et `id` des attributs pour le `Bitmap` élément pour l'icône.  
  
        > [!NOTE]
        >  Boutons de barre d'outils doit avoir des icônes.  
  
     Pour plus d'informations, consultez [MenuCommands Vs. OleMenuCommands](../../misc/menucommands-vs-olemenucommands.md).  
  
4.  Si vos commandes requièrent des icônes, ajoutez un [Bitmaps](../../extensibility/bitmaps-element.md) élément vers le `Commands` élément. Ensuite, pour chaque icône, ajoutez un [Bitmap](../../extensibility/bitmap-element.md) élément vers le `Bitmaps` élément. Voici où vous spécifiez l'emplacement de la ressource bitmap. Pour plus d'informations, consultez [Ajouter des icônes aux commandes de Menu](../../extensibility/adding-icons-to-menu-commands.md).  
  
 Vous pouvez compter sur la structure de parenté placer correctement la plupart des menus, les groupes et commandes. Pour les jeux de commandes très volumineux, ou quand un menu, un groupe ou une commande doit apparaître à plusieurs endroits, nous vous recommandons de spécifier la sélection élective de la commande.  
  
##### S'appuyer sur le lien de parenté pour placer les éléments d'interface utilisateur dans l'IDE  
  
1.  Pour parenté classique, créez un `Parent` dans chaque élément de `Menu`, `Group`, et `Command` un élément qui est défini dans votre package.  
  
     La cible de la `Parent` élément est le menu ou un groupe qui contient le menu, un groupe ou une commande.  
  
    1.  Définissez la `guid` le nom de l'attribut le `GuidSymbol` élément qui définit le jeu de commandes. Si l'élément cible ne fait pas partie de votre package, utilisez le guid de ce jeu de commandes, comme défini dans le fichier .vsct correspondant.  
  
    2.  Définir le `id` attribut correspondent à la `id` attribut du groupe ou de cible. Pour obtenir la liste des menus et des groupes qui sont exposées par Visual Studio, consultez la page [GUID et ID de Menus de Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md) ou [GUID et ID des barres d'outils de Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md).  
  
 Si vous avez un grand nombre d'éléments d'interface utilisateur à placer dans l'IDE, ou si les éléments qui doivent apparaître dans plusieurs endroits, définir leur placement dans le [CommandPlacements](../../extensibility/commandplacements-element.md) élément, comme indiqué dans les étapes suivantes.  
  
##### Placement de la commande permet de placer les éléments d'interface utilisateur dans l'IDE  
  
1.  Après le `Commands` élément, ajouter un `CommandPlacements` élément.  
  
2.  Dans la `CommandPlacements` élément, ajouter un `CommandPlacement` élément pour chaque menu, un groupe ou une commande à la place.  
  
     Chaque `CommandPlacement` élément ou `Parent` élément place un menu, groupe ou une commande dans un emplacement de l'IDE. Un élément d'interface utilisateur peut avoir uniquement un seul parent, mais il peut avoir plusieurs positionnements de commande. Pour placer un élément d'interface utilisateur dans plusieurs emplacements, ajoutez un `CommandPlacement` élément pour chaque emplacement.  
  
3.  Définir le `guid` et `id` les attributs de chaque `CommandPlacement` élément au menu hébergement ou au groupe, comme vous le feriez pour un `Parent` élément. Vous pouvez également définir le `priority` attribut pour établir la position relative de l'élément d'interface utilisateur.  
  
 Vous pouvez combiner le positionnement par parenté et commande. Toutefois, pour les jeux de commandes très volumineux, nous vous recommandons d'utiliser uniquement la sélection élective de commande.  
  
### Ajout de comportements spécialisées  
 Vous pouvez utiliser [CommandFlag](../../extensibility/command-flag-element.md) éléments pour modifier le comportement des menus et des commandes, par exemple, pour modifier leur apparence et la visibilité. Vous pouvez également changer lorsqu'une commande est visible à l'aide de [VisibilityConstraints](../../extensibility/visibilityconstraints-element.md), ou ajouter des raccourcis clavier à l'aide de [thèmes](../../extensibility/keybindings-element.md). Certains types de menus et des commandes déjà ont spécialisé des comportements intégrés.  
  
##### Pour ajouter des comportements spécifiques  
  
1.  Pour rendre un élément d'interface utilisateur visibles uniquement dans certains contextes d'interface utilisateur, par exemple, lorsqu'une solution est chargée, utilisez les contraintes de visibilité.  
  
    1.  Après le `Commands` élément, ajouter un `VisibilityConstraints` élément.  
  
    2.  Pour chaque élément d'interface utilisateur limiter, ajoutez un [VisibilityItem](../../extensibility/visibilityitem-element.md) élément.  
  
    3.  Pour chaque `VisibilityItem` ensemble d'éléments, le `guid` et `id` attributs au menu, groupe, ou de commande et puis définissez la `context` attribut tel que défini dans le contexte de l'interface utilisateur que vous le souhaitez, le <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> \(classe\). Pour plus d'informations, consultez [Élément de VisibilityItem](../../extensibility/visibilityitem-element.md).  
  
2.  Pour définir la visibilité ou la disponibilité d'un élément d'interface utilisateur dans le code, utilisez une ou plusieurs des indicateurs de commande suivants :  
  
    -   DefaultDisabled  
  
    -   DefaultInvisible  
  
    -   DynamicItemStart  
  
    -   DynamicVisibility  
  
    -   NoShowOnMenuController  
  
    -   NotInTBList  
  
     Pour plus d'informations, consultez [Élément indicateur de commande](../../extensibility/command-flag-element.md).  
  
3.  Pour modifier comment un élément s'affiche, ou modifier son apparence de façon dynamique, utilisez une ou plusieurs des indicateurs de commande suivants :  
  
    -   AlwaysCreate  
  
    -   CommandWellOnly  
  
    -   DefaultDocked  
  
    -   DontCache  
  
    -   DynamicItemStart  
  
    -   FixMenuController  
  
    -   IconAndText  
  
    -   PICT  
  
    -   StretchHorizontally  
  
    -   TextMenuUseButton  
  
    -   TexteModifie  
  
    -   TextOnly  
  
     Pour plus d'informations, consultez [Élément indicateur de commande](../../extensibility/command-flag-element.md).  
  
4.  Pour modifier la manière dont un élément réagit lorsqu'il reçoit des commandes, utilisez une ou plusieurs des indicateurs de commande suivants :  
  
    -   AllowParams  
  
    -   CaseSensitive  
  
    -   CommandWellOnly  
  
    -   Touches filtres  
  
    -   NoAutoComplete  
  
    -   NoButtonCustomize  
  
    -   NoKeyCustomize  
  
    -   NoToolbarClose  
  
    -   PostExec  
  
    -   RouteToDocs  
  
    -   TextIsAnchorCommand  
  
     Pour plus d'informations, consultez [Élément indicateur de commande](../../extensibility/command-flag-element.md).  
  
5.  Pour attacher un raccourci clavier du menu dépendant à un menu ou un élément dans un menu, ajoutez une esperluette \(« & »\) dans le `ButtonText` élément au menu ou un élément de menu. Le caractère qui suit le signe est le raccourci clavier lorsque le menu parent est ouvert.  
  
6.  Pour attacher un raccourci clavier du menu indépendant à une commande, utilisez [thèmes](../../extensibility/keybindings-element.md). Pour plus d'informations, consultez [Élément de KeyBinding](../../extensibility/keybinding-element.md).  
  
7.  Pour localiser le texte de menu, utilisez la `LocCanonicalName` élément. Pour plus d'informations, consultez [Élément de chaînes](../../extensibility/strings-element.md).  
  
 Certains types de menus et des boutons incluent des comportements spécifiques. Le tableau suivant décrit certains types de bouton et un menu spécialisé. Pour les autres types, consultez le `types` attribut descriptions dans [Élément de menu](../../extensibility/menu-element.md), [Élément de bouton](../../extensibility/button-element.md), et [Élément de liste déroulante](../../extensibility/combo-element.md).  
  
 Zone de liste modifiable  
 Une zone de liste déroulante est une liste déroulante qui peut être utilisée sur une barre d'outils. Pour ajouter des zones de liste déroulante à l'interface utilisateur, créez un [combinés](../../extensibility/combos-element.md) élément dans le `Commands` élément. Ajoutez ensuite à la `Combos` élément un `Combo` élément pour chaque zone de liste déroulante Ajouter.`Combo` les éléments ont les mêmes attributs et les enfants comme `Button` éléments et ont également `DefaultWidth` et `idCommandList` les attributs. Le `DefaultWidth` attribut définit la largeur en pixels et le `idCommandList` attribuent des points à un ID de commande qui est utilisé pour remplir la zone de liste déroulante. Pour plus d'informations, consultez la `Combo` documentation de l'élément.  
  
 MenuController  
 Un contrôleur de menu est un bouton comportant une flèche en regard de celui\-ci. Ouvre la liste en cliquant sur la flèche. Pour ajouter un contrôleur de menu à l'interface utilisateur, créez un `Menu` élément et définissez son `type` attribut **MenuController** ou **MenuControllerLatched**, selon le comportement souhaité. Pour remplir un contrôleur de menu, définissez\-le comme le parent d'un `Group` élément. Le contrôleur de menu affiche tous les enfants de ce groupe dans la liste déroulante.  
  
## Voir aussi  
 [Extension des Menus et commandes](../../extensibility/extending-menus-and-commands.md)   
 [Table de commandes de Visual Studio \(. Fichiers VSCT\)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Référence de schéma XML de VSCT](../../extensibility/vsct-xml-schema-reference.md)