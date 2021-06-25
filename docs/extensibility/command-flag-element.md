---
title: Élément d’indicateur de commande | Microsoft Docs
description: L’élément d’indicateur de commande modifie son élément parent. Examinez ses éléments parents et ses éléments enfants.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- CommandFlag element (VSCT XML schema)
- VSCT XML schema elements, CommandFlag
ms.assetid: 5ef63399-d2db-4dc1-97ce-be1bd4ef4e39
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6356fd02c8045aee9dc48ebc9d30a346159080bb
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902031"
---
# <a name="command-flag-eelement"></a>Indicateur de commande Eelement
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
|AllowParams|Indique que les utilisateurs peuvent entrer des paramètres de commande dans la fenêtre **commande** lorsqu’ils tapent le nom canonique de la commande.<br /><br /> Valide pour : `Button`|
|AlwaysCreate|Le menu est créé même s’il n’a pas de groupes ou de boutons.<br /><br /> Valide pour : `Menu`|
|CaseSensitive|Les entrées utilisateur respectent la casse.<br /><br /> Valide pour : `Combo`|
|CommandWellOnly|Appliquez cet indicateur si la commande n’apparaît pas dans le menu de niveau supérieur et si vous souhaitez la rendre disponible pour une personnalisation de l’interpréteur de commandes supplémentaire, par exemple pour la lier à un raccourci clavier. Une fois le VSPackage installé, vous pouvez personnaliser ces commandes en ouvrant la boîte de dialogue **options** , puis en modifiant le placement de la commande sous la catégorie **environnement clavier** . Cet indicateur n’affecte pas l’emplacement des menus contextuels, des barres d’outils, des contrôleurs de menu ou des sous-menus.<br /><br /> Valide pour : `Button` , `Combo`|
|DefaultDisabled|Par défaut, la commande est désactivée si le VSPackage qui l’implémente n’est pas chargé ou si la `QueryStatus` méthode n’a pas été appelée.<br /><br /> Valide pour : `Button` , `Combo`|
|DefaultDocked|Ancré par défaut. Ce paramètre ne s’applique plus aux barres d’outils car elles sont toujours ancrées.|
|DefaultInvisible|Par défaut, la commande est invisible si le VSPackage qui l’implémente n’est pas chargé ou si la `QueryStatus` méthode n’a pas été appelée.<br /><br /> Nous vous recommandons de combiner cela avec l' `DynamicVisibility` indicateur.<br /><br /> Valide pour : `Button` , `Combo` , `Menu`|
|DontCache|L’environnement de développement ne met pas en cache les `QueryStatus` résultats de la méthode pour cette commande.<br /><br /> Pour un menu, cela indique à un contrôleur de menu de ne pas mettre en cache le texte de ses éléments de menu. Utilisez cet indicateur lorsque le menu contient des éléments dynamiques ou des éléments qui ont du texte dynamique.<br /><br /> Valide pour : `Button` , `Menu`|
|DynamicItemStart|Indique le début d’une liste dynamique. Cela permet à l’environnement de générer une liste en appelant successivement la `QueryStatus` méthode sur les éléments de liste jusqu’à ce que l’indicateur OLECMDERR_E_UNSUPPORTED soit retourné. Cela fonctionne bien pour les éléments tels que les listes des fenêtres et listes des derniers fichiers utilisés.<br /><br /> Valide pour : `Button`|
|DynamicVisibility|La visibilité de la commande peut être modifiée par le biais de la `QueryStatus` méthode ou d’un GUID de contexte qui est inclus dans la `VisibilityConstraints` section.<br /><br /> S’applique aux commandes qui s’affichent dans les menus et les barres d’outils de la fenêtre outil, mais pas dans les barres d’outils de niveau supérieur qui s’affichent dans la fenêtre principale. Les éléments de barre d’outils de niveau supérieur peuvent être désactivés, mais ils ne sont pas masqués, lorsque l’indicateur OLECMDF_INVISIBLE est retourné à partir de la `QueryStatus` méthode. Les commandes de la barre d’outils qui s’affichent dans les barres d’outils de fenêtre outil peuvent être masquées.<br /><br /> Dans un menu, cet indicateur indique également qu’il doit être masqué automatiquement lorsque tous ses membres sont masqués. Cet indicateur est généralement affecté aux sous-menus, car les menus de niveau supérieur ont déjà ce comportement.<br /><br /> Cet indicateur doit être combiné avec l' `DefaultInvisible` indicateur.<br /><br /> Valide pour : `Button` , `Combo` , `Menu`|
|Rémanent|Consultez la rubrique relative aux clés de filtrage sous l' [élément de liste](../extensibility/combo-element.md).<br /><br /> Valide pour : `Combo`|
|FixMenuController|Si cette commande est positionnée sur un contrôleur de menu, la commande est toujours la valeur par défaut ; autrement dit, la commande est sélectionnée chaque fois que le bouton de contrôleur de menu lui-même est sélectionné. Si l’indicateur est défini pour le contrôleur de menu `TextIsAnchorCommand` , le contrôleur de menu prend également son texte à partir de la commande qui a l' `FixMenuController` indicateur.<br /><br /> Une seule commande sur un contrôleur de menu doit avoir l' `FixMenuController` indicateur. Si plusieurs commandes sont activées, la dernière commande du menu devient la commande par défaut.<br /><br /> Valide pour : `Button`|
|IconAndText|Affichez une icône et du texte dans le menu et la barre d’outils.<br /><br /> Valide pour : `Button` , `Combo` , `Menu`|
|NoAutoComplete|La fonctionnalité de saisie semi-automatique est désactivée.<br /><br /> Valide pour : `Combo`|
|NoButtonCustomize|Ne laissez pas l’utilisateur personnaliser ce bouton.<br /><br /> Valide pour : `Button` , `Combo`|
|NoKeyCustomize|N’activez pas la personnalisation du clavier.<br /><br /> Valide pour : `Button` , `Combo`|
|NoShowOnMenuController|Si cette commande est positionnée sur un contrôleur de menu, la commande n’apparaît pas dans la liste déroulante.<br /><br /> Valide pour : `Button`|
|NotInTBList|N’apparaît pas dans la liste des barres d’outils disponibles. Cela est valide uniquement pour les types de menu de barre d’outils.<br /><br /> Valide pour : `Menu`|
|NoToolbarClose|L’utilisateur ne peut pas fermer la barre d’outils. Cela est valide uniquement pour les types de menu de barre d’outils.<br /><br /> Valide pour : `Menu`|
|PICT|Afficher uniquement une icône dans une barre d’outils, mais uniquement du texte dans un menu. Si aucune icône n’est spécifiée, affiche un espace vide sur une barre d’outils.<br /><br /> Valide pour : `Button`|
|PostExec|Rend la commande non bloquante. L’environnement de développement diffère l’exécution jusqu’à ce que toutes les requêtes de pré-traitement soient terminées.<br /><br /> Valide pour : `Button`|
|RouteToDocs|La commande est routée vers le document actif.<br /><br /> Valide pour : `Button`|
|StretchHorizontally|Lorsque cet indicateur est défini, la largeur devient la largeur minimale de la zone de liste déroulante, et si la barre d’outils contient de la place, la zone de liste déroulante est étirée pour occuper de l’espace disponible. Cela se produit uniquement si la barre d’outils est ancrée horizontalement et qu’une seule zone de liste déroulante de la barre d’outils peut utiliser l’indicateur (l’indicateur est ignoré sur tous les sauf la première zone de liste modifiable).<br /><br /> Valide pour : `Combo`|
|Textchanges au|Le texte de la commande ou du menu peut être modifié au moment de l’exécution, en général via la `QueryStatus` méthode.<br /><br /> Valide pour : `Button` , `Menu`|
|TextChangesButton|Valide pour : `Button`|
|TextIsAnchorCommand|Pour un contrôleur de menu, le texte du menu est issu de la commande par défaut (ancre). Une commande d’ancrage est la dernière commande sélectionnée ou verrouillée. Si cet indicateur n’est pas défini, le contrôleur de menu utilise son propre `MenuText` champ. Toutefois, un clic sur le contrôleur de menu active toujours la dernière commande sélectionnée à partir de ce contrôleur.<br /><br /> Nous vous recommandons de combiner cet indicateur avec l' `TextChanges` indicateur.<br /><br /> Cet indicateur s’applique uniquement aux menus de type MenuController ou MenuControllerLatched.<br /><br /> Valide pour : `Menu`|
|TextMenuCtrlUseMenu|Utilisez le `MenuText` champ sur les contrôleurs de menu. Le champ par défaut est `ButtonText` .<br /><br /> Valide pour : `Button`|
|TextMenuUseButton|Utilisez le `ButtonText` champ pour les menus. Le champ par défaut est `MenuText` s’il est spécifié.<br /><br /> Valide pour : `Button`|
|TextOnly|Affichez uniquement du texte dans une barre d’outils ou un menu, mais pas d’icône même si l’icône est spécifiée.<br /><br /> Valide pour : `Button`|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Buttons, élément](../extensibility/buttons-element.md)|Fournit un groupe pour les éléments d' [élément de bouton](../extensibility/button-element.md) .|
|[Élément menus](../extensibility/menus-element.md)|Définit tous les menus qu’un VSPackage implémente.|

## <a name="see-also"></a>Voir aussi
- [Table de commandes Visual Studio (. Fichiers vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
