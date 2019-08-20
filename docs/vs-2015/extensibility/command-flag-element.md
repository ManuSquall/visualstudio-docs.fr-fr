---
title: Élément de l’indicateur de commande | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- CommandFlag element (VSCT XML schema)
- VSCT XML schema elements, CommandFlag
ms.assetid: 5ef63399-d2db-4dc1-97ce-be1bd4ef4e39
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 39b2377dd1599d58eac4ca967ca540d8ce0e6847
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68184354"
---
# <a name="command-flag-element"></a>Élément Command Flag
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Modifie son élément parent.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<CommandFlag>DynamicVisibility</CommandFlag>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 La section suivante décrit les valeurs d’élément valide.  
  
### <a name="attributes"></a>Attributs  
 Aucun.  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Valeur|Description|  
|-----------|-----------------|  
|AllowParams|Indique que les utilisateurs peuvent entrer des paramètres de commande dans le **commande** fenêtre lorsqu’ils tapent le nom canonique de la commande.<br /><br /> Valide pour : `Button`|  
|AlwaysCreate|Menu est créé même si elle n’a aucun groupe ou les boutons.<br /><br /> Valide pour : `Menu`|  
|CaseSensitive|Les entrées utilisateur respectent la casse.<br /><br /> Valide pour : `Combo`|  
|CommandWellOnly|Appliquer cet indicateur si la commande n’apparaît pas dans le menu de niveau supérieur et que vous souhaitez rendre disponible pour la personnalisation d’interpréteur de commandes supplémentaires, par exemple, pour lier à un raccourci clavier. Une fois le VSPackage est installé, vous pouvez personnaliser ces commandes en ouvrant le **Options** boîte de dialogue, puis en modifiant le placement de commande sous la **clavier environnement** catégorie. Cet indicateur n’affecte pas la sélection élective sur les menus contextuels, des barres d’outils, des contrôleurs de menu ou des sous-menus.<br /><br /> Valide pour : `Button`, `Combo`|  
|DefaultDisabled|Par défaut, la commande est désactivée si le VSPackage qui l’implémente n’est pas chargé ou `QueryStatus` méthode n’a pas été appelée.<br /><br /> Valide pour : `Button`, `Combo`|  
|DefaultDocked|Ancré par défaut. Ce paramètre n’est plus s’applique aux barres d’outils, car ils sont toujours ancrées.|  
|DefaultInvisible|Par défaut, la commande est invisible si le VSPackage qui l’implémente n’est pas chargé ou `QueryStatus` méthode n’a pas été appelée.<br /><br /> Nous vous recommandons de combiner ceci avec la `DynamicVisibility` indicateur.<br /><br /> Valide pour : `Button`, `Combo`, `Menu`|  
|DontCache|L’environnement de développement ne met pas en cache le `QueryStatus` les résultats de méthode pour cette commande.<br /><br /> Pour un menu, cela indique un contrôleur de menu ne pas mettre en cache le texte de ses éléments de menu. Utilisez cet indicateur lorsque le menu contient des éléments dynamiques ou qui ont un texte dynamique.<br /><br /> Valide pour : `Button`, `Menu`|  
|DynamicItemStart|Indique le début d’une liste dynamique. Cela permet à l’environnement générer la liste en appelant successivement le `QueryStatus` méthode sur les éléments de la liste jusqu'à ce que l’indicateur OLECMDERR_E_UNSUPPORTED est retourné. Cela fonctionne bien pour les éléments tels que des derniers fichiers utilisés (MRU) listes et des listes de fenêtres.<br /><br /> Valide pour : `Button`|  
|DynamicVisibility|La visibilité de la commande peut être modifiée via le `QueryStatus` (méthode) ou via un GUID de contexte qui est inclus dans le `VisibilityConstraints` section.<br /><br /> S’applique aux commandes qui s’affichent dans les menus et barres d’outils de la fenêtre outil, mais pas sur les barres d’outils de niveau supérieur qui apparaissent dans la fenêtre principale. Éléments de barre d’outils de niveau supérieur peuvent être désactivés, mais ne pas masquées, lorsque l’indicateur OLECMDF_INVISIBLE est retourné à partir de la `QueryStatus` (méthode). Les commandes de barre d’outils qui apparaissent dans les barres d’outils de la fenêtre outil peuvent être masquées.<br /><br /> Dans un menu, cet indicateur indique également qu’il doit être automatiquement masqué lorsque tous ses membres sont masqués. Cet indicateur est généralement affecté à sous-menus, car les menus de niveau supérieur ont déjà ce comportement.<br /><br /> Cet indicateur doit être combiné avec la `DefaultInvisible` indicateur.<br /><br /> Valide pour : `Button`, `Combo`, `Menu`|  
|FilterKeys|Consultez la rubrique de filtrage des clés sous [élément de liste déroulante](../extensibility/combo-element.md).<br /><br /> Valide pour : `Combo`|  
|FixMenuController|Si cette commande est positionnée sur un contrôleur de menu, la commande est toujours la valeur par défaut ; Autrement dit, la commande est sélectionnée chaque fois que le bouton de contrôleur de menu lui-même est sélectionné. Si le contrôleur de menu a la `TextIsAnchorCommand` l’indicateur est défini, le contrôleur de menu prend également son texte à partir de la commande qui a le `FixMenuController` indicateur.<br /><br /> Une seule commande sur un contrôleur de menu doit avoir le `FixMenuController` indicateur. Si plusieurs commandes est marqué par conséquent, la dernière commande dans le menu devient la commande par défaut.<br /><br /> Valide pour : `Button`|  
|IconAndText|Afficher une icône et du texte sur le menu et barre d’outils.<br /><br /> Valide pour : `Button`, `Combo`, `Menu`|  
|NoAutoComplete|Fonctionnalité de saisie semi-automatique est désactivée.<br /><br /> Valide pour : `Combo`|  
|NoButtonCustomize|Ne laissez pas l’utilisateur personnaliser ce bouton.<br /><br /> Valide pour : `Button`, `Combo`|  
|NoKeyCustomize|N’activez pas la personnalisation du clavier.<br /><br /> Valide pour : `Button`, `Combo`|  
|NoShowOnMenuController|Si cette commande est positionnée sur un contrôleur de menu, la commande n’apparaît pas dans la liste déroulante.<br /><br /> Valide pour : `Button`|  
|NotInTBList|N’apparaît pas dans la liste des barres d’outils disponibles. Cela n’est valide uniquement pour les types de menu de barre d’outils.<br /><br /> Valide pour : `Menu`|  
|NoToolbarClose|Utilisateur ne peut pas fermer la barre d’outils. Cela n’est valide uniquement pour les types de menu de barre d’outils.<br /><br /> Valide pour : `Menu`|  
|PICT|Afficher une icône uniquement sur une barre d’outils, mais uniquement du texte dans un menu. Si aucune icône n’est spécifié, affiche un espace vide interactif sur une barre d’outils.<br /><br /> Valide pour : `Button`|  
|PostExec|Rend la commande non bloquant. L’environnement de développement diffère de l’exécution jusqu'à ce que toutes les requêtes de pré-traitement sont terminées.<br /><br /> Valide pour : `Button`|  
|RouteToDocs|La commande est acheminée vers le document actif.<br /><br /> Valide pour : `Button`|  
|StretchHorizontally|Lorsque cet indicateur est défini, la largeur devient la largeur minimale de la zone de liste modifiable, et si l’espace est sur la barre d’outils, la zone de liste déroulante s’étire pour remplir l’espace disponible. Cela se produit uniquement si la barre d’outils est ancrée horizontalement, et qu’une seule liste déroulante dans la barre d’outils permettre utiliser l’indicateur (l’indicateur est ignoré sur tout sauf la première zone de liste déroulante).<br /><br /> Valide pour : `Combo`|  
|TextMenuUseButton|Utilisez le `ButtonText` champ pour les menus. Le champ de valeur par défaut est `MenuText` s’il est spécifié.<br /><br /> Valide pour : `Button`|  
|TextChanges|Le texte de commande ou de menu sont modifiables au moment de l’exécution, généralement via le `QueryStatus` (méthode).<br /><br /> Valide pour : `Button`, `Menu`|  
|TextChangesButton|Valide pour : `Button`|  
|TextIsAnchorCommand|Pour un contrôleur de menu, le texte du menu est pris à partir de la commande par défaut (ancre). Une commande d’ancre est la dernière commande sélectionné ou verrouillée. Si cet indicateur n’est pas défini, le contrôleur de menu utilise son propre `MenuText` champ. Toutefois, en cliquant sur le contrôleur de menu permet toujours de la dernière commande sélectionnée à partir de ce contrôleur.<br /><br /> Nous recommandons que vous combinez cet indicateur avec la `TextChanges` indicateur.<br /><br /> Cet indicateur s’applique uniquement aux menus de type MenuController ou MenuControllerLatched.<br /><br /> Valide pour : `Menu`|  
|TextMenuCtrlUseMenu|Utilisez le `MenuText` champ sur les contrôleurs de menu. Le champ de valeur par défaut est `ButtonText`.<br /><br /> Valide pour : `Button`|  
|TextMenuUseButton|Utilisez le `ButtonText` champ pour les menus. Le champ de valeur par défaut est `MenuText` s’il est spécifié.<br /><br /> Valide pour : `Button`|  
|TextOnly|Afficher uniquement du texte sur une barre d’outils ou d’un menu, mais aucune icône, même si l’icône est spécifiée.<br /><br /> Valide pour : `Button`|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[Élément Buttons](../extensibility/buttons-element.md)|Fournit un groupe pour [élément Button](../extensibility/button-element.md) éléments.|  
|[Élément Menus](../extensibility/menus-element.md)|Définit tous les menus qui implémente un VSPackage.|  
  
## <a name="see-also"></a>Voir aussi  
 [Fichiers Visual Studio Command Table (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
