---
title: Élément du drapeau de commande (en anglais seulement) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- CommandFlag element (VSCT XML schema)
- VSCT XML schema elements, CommandFlag
ms.assetid: 5ef63399-d2db-4dc1-97ce-be1bd4ef4e39
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 84138a69dbb42fc349c12276fd7cca4b593e4d47
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649369"
---
# <a name="command-flag-eelement"></a>Eelement de drapeau de commande
Modifie son élément parent.

## <a name="syntax"></a>Syntaxe

```
<CommandFlag>DynamicVisibility</CommandFlag>
```

## <a name="attributes-and-elements"></a>Attributs et éléments
 La section suivante décrit les valeurs d’éléments valides.

### <a name="attributes"></a>Attributs
 Aucun.

### <a name="child-elements"></a>Éléments enfants

|Valeur|Description|
|-----------|-----------------|
|AutoriserParams|Indique que les utilisateurs peuvent entrer les paramètres de commande dans la fenêtre **de commande** lorsqu’ils tapent le nom canonique de la commande.<br /><br /> Valable pour :`Button`|
|Toujourscréer|Le menu est créé même s’il n’a pas de groupes ou de boutons.<br /><br /> Valable pour :`Menu`|
|CaseSensitive|Les entrées des utilisateurs sont sensibles aux cas.<br /><br /> Valable pour :`Combo`|
|CommandWellOnly|Appliquez ce drapeau si la commande n’apparaît pas sur le menu de haut niveau et que vous souhaitez la rendre disponible pour une personnalisation supplémentaire de la coque, par exemple, pour la lier à un raccourci clavier. Une fois que le VSPackage est installé, vous pouvez personnaliser ces commandes en ouvrant la boîte de dialogue **Options,** puis en éditant le placement de commande dans la catégorie **Environnement Clavier.** Ce drapeau n’affecte pas le placement sur les menus de raccourcis, les barres d’outils, les contrôleurs de menu ou le sous-genre.<br /><br /> Valable pour: `Button`,`Combo`|
|DéfautDisabled|Par défaut, la commande est désactivée si le VSPackage `QueryStatus` qui l’implémente n’est pas chargé ou si la méthode n’a pas été appelée.<br /><br /> Valable pour: `Button`,`Combo`|
|DéfautDocked|Amarré par défaut. Ce paramètre ne s’applique plus aux barres d’outils parce qu’ils sont toujours amarrés.|
|DéfautInvisible|Par défaut, la commande est invisible si le VSPackage `QueryStatus` qui l’implémente n’est pas chargé ou si la méthode n’a pas été appelée.<br /><br /> Nous vous recommandons de `DynamicVisibility` combiner cela avec le drapeau.<br /><br /> Valable `Button`pour: `Combo`, ,`Menu`|
|DontCache (en)|L’environnement de développement `QueryStatus` ne cache pas les résultats de la méthode pour cette commande.<br /><br /> Pour un menu, cela indique à un contrôleur de menu de ne pas mettre en cache le texte de ses éléments de menu. Utilisez ce drapeau lorsque le menu contient des éléments dynamiques ou des éléments qui ont du texte dynamique.<br /><br /> Valable pour: `Button`,`Menu`|
|DynamicItemStart (en)|Indique le début d’une liste dynamique. Cela permet à l’environnement de construire `QueryStatus` une liste en appelant successivement la méthode sur les éléments de liste jusqu’à ce que le drapeau OLECMDERR_E_UNSUPPORTED soit retourné. Cela fonctionne bien pour des éléments tels que les listes les plus récemment utilisées (MRU) et les listes de fenêtres.<br /><br /> Valable pour :`Button`|
|DynamicVisibilité|La visibilité de la commande `QueryStatus` peut être modifiée par la méthode `VisibilityConstraints` ou par un contexte GUID qui est inclus dans la section.<br /><br /> S’applique aux commandes qui apparaissent sur les menus et les barres d’outils de fenêtre d’outil, mais pas sur les barres d’outils de haut niveau qui apparaissent sur la fenêtre principale. Les éléments de barre d’outils de haut niveau peuvent être désactivés `QueryStatus` mais non cachés, lorsque le drapeau OLECMDF_INVISIBLE est retourné de la méthode. Les commandes de barres d’outils qui apparaissent sur les barres d’outils de fenêtre d’outil peuvent être cachées.<br /><br /> Sur un menu, ce drapeau indique également qu’il doit être automatiquement caché lorsque tous ses membres sont cachés. Ce drapeau est généralement attribué à submenus parce que les menus de haut niveau ont déjà ce comportement.<br /><br /> Ce drapeau doit être `DefaultInvisible` combiné avec le drapeau.<br /><br /> Valable `Button`pour: `Combo`, ,`Menu`|
|FilterKeys (en)|Voir le sujet Filtering Keys sous [Combo Element](../extensibility/combo-element.md).<br /><br /> Valable pour :`Combo`|
|FixMenuController|Si cette commande est positionnée sur un contrôleur de menu, la commande est toujours la valeur par défaut ; c’est-à-dire que la commande est sélectionnée chaque fois que le bouton de contrôleur de menu lui-même est sélectionné. Si le contrôleur `TextIsAnchorCommand` de menu a l’ensemble de drapeau, alors `FixMenuController` le contrôleur de menu prend également son texte de la commande qui a le drapeau.<br /><br /> Une seule commande sur un `FixMenuController` contrôleur de menu devrait avoir le drapeau. Si plus d’une commande est si marquée, la dernière commande dans le menu devient la commande par défaut.<br /><br /> Valable pour :`Button`|
|IconAndText|Afficher une icône et un texte sur le menu et la barre d’outils.<br /><br /> Valable `Button`pour: `Combo`, ,`Menu`|
|NoAutoComplete|La fonction auto-complète est désactivée.<br /><br /> Valable pour :`Combo`|
|NoButtonCustomize|Ne laissez pas l’utilisateur personnaliser ce bouton.<br /><br /> Valable pour: `Button`,`Combo`|
|NoKeyCustomize NoKeyCustomize|N’activez pas la personnalisation du clavier.<br /><br /> Valable pour: `Button`,`Combo`|
|NoShowOnMenuController|Si cette commande est positionnée sur un contrôleur de menu, la commande n’apparaît pas dans la liste déroulante.<br /><br /> Valable pour :`Button`|
|NotInTBList|N’apparaît pas dans la liste des barres d’outils disponibles. Ceci est valable uniquement pour les types de menu Toolbar.<br /><br /> Valable pour :`Menu`|
|NoToolbarClose (noToolbarClose)|L’utilisateur ne peut pas fermer la barre d’outils. Ceci est valable uniquement pour les types de menu Toolbar.<br /><br /> Valable pour :`Menu`|
|Pict|Afficher seulement une icône sur une barre d’outils, mais seulement du texte sur un menu. Si aucune icône n’est spécifiée, affiche un espace vide cliquable sur une barre d’outils.<br /><br /> Valable pour :`Button`|
|PostExec (en anglais)|Rend la commande non-blocage. L’environnement de développement reporte l’exécution jusqu’à ce que toutes les requêtes préalables au traitement soient terminées.<br /><br /> Valable pour :`Button`|
|RouteToDocs|La commande est acheminée vers le document actif.<br /><br /> Valable pour :`Button`|
|StretchHorizontally|Lorsque ce drapeau est réglé, la largeur devient la largeur minimale pour la boîte combo, et s’il ya de la place sur la barre d’outils, la boîte combo s’étend pour remplir l’espace disponible. Cela ne se produit que si la barre d’outils est horizontalement amarré, et une seule boîte combo sur la barre d’outils peut utiliser le drapeau (le drapeau est ignoré sur tous sauf la première boîte combo).<br /><br /> Valable pour :`Combo`|
|TextChanges TextChanges TextChanges TextChang|Le texte de commande ou de menu peut `QueryStatus` être modifié au moment de l’exécution, généralement à travers la méthode.<br /><br /> Valable pour: `Button`,`Menu`|
|TextChangesButton|Valable pour :`Button`|
|TextIsAnchorCommand|Pour un contrôleur de menu, le texte du menu est tiré de la commande par défaut (ancre). Une commande d’ancrage est la dernière commande sélectionnée ou verrouillée. Si ce drapeau n’est pas défini, le contrôleur de menu utilise son propre `MenuText` champ. Cependant, en cliquant sur le contrôleur de menu permet toujours la dernière commande sélectionnée à partir de ce contrôleur.<br /><br /> Nous vous recommandons de combiner `TextChanges` ce drapeau avec le drapeau.<br /><br /> Ce drapeau ne s’applique qu’aux menus de type MenuController ou MenuControllerLatched.<br /><br /> Valable pour :`Menu`|
|TextMenuCtrlUseMenu|Utilisez `MenuText` le terrain sur les contrôleurs de menu. Le champ `ButtonText`par défaut est .<br /><br /> Valable pour :`Button`|
|TextMenuUseButton|Utilisez `ButtonText` le terrain pour les menus. Le champ `MenuText` par défaut est s’il est spécifié.<br /><br /> Valable pour :`Button`|
|TextOnly|Afficher uniquement du texte sur une barre d’outils ou un menu, mais pas d’icône même si l’icône est spécifiée.<br /><br /> Valable pour :`Button`|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément boutons](../extensibility/buttons-element.md)|Fournit un groupe pour les éléments [d’élément Bouton.](../extensibility/button-element.md)|
|[Élément menus](../extensibility/menus-element.md)|Définit tous les menus qu’un VSPackage met en œuvre.|

## <a name="see-also"></a>Voir aussi
- [Table de commande Visual Studio (. Vsct) Fichiers](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
