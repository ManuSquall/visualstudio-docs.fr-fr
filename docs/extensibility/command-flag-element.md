---
title: "&#201;l&#233;ment indicateur de commande | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "CommandFlag, élément (schéma XML de VSCT)"
  - "Éléments du schéma XML de VSCT, CommandFlag"
ms.assetid: 5ef63399-d2db-4dc1-97ce-be1bd4ef4e39
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# &#201;l&#233;ment indicateur de commande
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Modifie son élément parent.  
  
## Syntaxe  
  
```  
<CommandFlag>DynamicVisibility</CommandFlag>  
```  
  
## Attributs et éléments  
 La section suivante décrit les valeurs d'élément valide.  
  
### Attributs  
 Aucun  
  
### Éléments enfants  
  
|Valeur|Description|  
|------------|-----------------|  
|AllowParams|Indique que les utilisateurs peuvent entrer des paramètres de commande dans le **commande** fenêtre lorsqu'ils tapent le nom canonique de la commande.<br /><br /> Valide pour : `Button`|  
|AlwaysCreate|Menu est créé même si elle n'a pas les groupes ou les boutons.<br /><br /> Valide pour : `Menu`|  
|CaseSensitive|Les entrées utilisateur respectent la casse.<br /><br /> Valide pour : `Combo`|  
|CommandWellOnly|Appliquer cet indicateur si la commande n'apparaît pas dans le menu de niveau supérieur et que vous souhaitez rendre disponibles pour la personnalisation d'interpréteur de commandes supplémentaires, par exemple, pour lier à un raccourci clavier. Une fois le VSPackage est installé, vous pouvez personnaliser ces commandes en ouvrant le **Options** boîte de dialogue, puis en modifiant l'emplacement de la commande sous la **clavier environnement** catégorie. Cet indicateur n'affecte pas la sélection élective sur les menus contextuels, les barres d'outils, les contrôleurs de menu ou les sous\-menus.<br /><br /> Valide pour : `Button`, `Combo`|  
|DefaultDisabled|Par défaut, la commande est désactivée si le VSPackage qui l'implémente n'est pas chargé ou `QueryStatus` méthode n'a pas été appelée.<br /><br /> Valide pour : `Button`, `Combo`|  
|DefaultDocked|Ancré par défaut. Ce paramètre n'est plus s'applique aux barres d'outils, car ils sont toujours ancrées.|  
|DefaultInvisible|Par défaut, la commande est invisible si le VSPackage qui l'implémente n'est pas chargé ou `QueryStatus` méthode n'a pas été appelée.<br /><br /> Nous vous recommandons combiner ceci avec la `DynamicVisibility` indicateur.<br /><br /> Valide pour : `Button`, `Combo`, `Menu`|  
|DontCache|L'environnement de développement ne met pas en cache le `QueryStatus` résultats de la méthode pour cette commande.<br /><br /> Un menu, cela indique un contrôleur menu ne pas mettre en cache le texte de ses éléments de menu. Utilisez cet indicateur lorsque le menu contient des éléments dynamiques ou des éléments ayant texte dynamique.<br /><br /> Valide pour : `Button`, `Menu`|  
|DynamicItemStart|Indique le début d'une liste dynamique. Cela permet à l'environnement créer une liste en appelant successivement la `QueryStatus` méthode sur les éléments de la liste jusqu'à ce que l'indicateur OLECMDERR\_E\_UNSUPPORTED est retourné. Cela fonctionne bien pour les éléments tels que des derniers fichiers utilisés \(MRU\) listes et des listes de fenêtres.<br /><br /> Valide pour : `Button`|  
|DynamicVisibility|La visibilité de la commande peut être modifiée via la `QueryStatus` méthode ou à un contexte de GUID qui est inclus dans la `VisibilityConstraints` section.<br /><br /> S'applique aux commandes qui s'affichent dans les menus et barres d'outils de la fenêtre outil, mais pas sur les barres d'outils de niveau supérieur qui s'affichent dans la fenêtre principale. Les éléments de barre d'outils de niveau supérieur peuvent être désactivés, mais ne pas cachés, lorsque l'indicateur OLECMDF\_INVISIBLE est retourné à partir de la `QueryStatus` méthode. Les commandes de barre d'outils qui s'affichent sur les barres d'outils de la fenêtre outil peuvent être masquées.<br /><br /> Dans un menu, cet indicateur indique également qu'il doit être automatiquement masqué lorsque tous ses membres sont masqués. Cet indicateur est généralement affecté aux sous\-menus, car les menus de niveau supérieur ont déjà ce comportement.<br /><br /> Cet indicateur doit être combiné avec le `DefaultInvisible` indicateur.<br /><br /> Valide pour : `Button`, `Combo`, `Menu`|  
|Touches filtres|Consultez la rubrique filtrage des clés sous [Élément de liste déroulante](../extensibility/combo-element.md).<br /><br /> Valide pour : `Combo`|  
|FixMenuController|Si cette commande est placée sur un contrôleur de menu, la commande est toujours la valeur par défaut ; Autrement dit, la commande est sélectionnée lorsque vous sélectionnez le bouton de contrôleur de menu lui\-même. Si le contrôleur de menu a la `TextIsAnchorCommand` l'indicateur est défini, le contrôleur de menu prend également le texte de la commande qui a le `FixMenuController` indicateur.<br /><br /> Une seule commande sur un contrôleur de menu doit avoir le `FixMenuController` indicateur. Si plusieurs commandes est donc marqué, la dernière commande dans le menu devient par défaut.<br /><br /> Valide pour : `Button`|  
|IconAndText|Afficher une icône et du texte de menu et barre d'outils.<br /><br /> Valide pour : `Button`, `Combo`, `Menu`|  
|NoAutoComplete|Fonctionnalité de saisie semi\-automatique est désactivée.<br /><br /> Valide pour : `Combo`|  
|NoButtonCustomize|Ne pas laisser l'utilisateur personnaliser ce bouton.<br /><br /> Valide pour : `Button`, `Combo`|  
|NoKeyCustomize|N'activez pas la personnalisation du clavier.<br /><br /> Valide pour : `Button`, `Combo`|  
|NoShowOnMenuController|Si cette commande est placée sur un contrôleur de menu, la commande n'apparaît pas dans la liste déroulante.<br /><br /> Valide pour : `Button`|  
|NotInTBList|N'apparaît pas dans la liste des barres d'outils disponibles. Ceci est valide uniquement pour les types de menu de barre d'outils.<br /><br /> Valide pour : `Menu`|  
|NoToolbarClose|Utilisateur ne peut pas fermer la barre d'outils. Ceci est valide uniquement pour les types de menu de barre d'outils.<br /><br /> Valide pour : `Menu`|  
|PICT|Afficher une icône sur une barre d'outils, mais uniquement du texte dans un menu. Si aucune icône n'est spécifié, affiche un espace interactif sur une barre d'outils.<br /><br /> Valide pour : `Button`|  
|PostExec|Rend la commande non bloquant. L'environnement de développement diffère de l'exécution jusqu'à ce que toutes les requêtes de pré\-traitement sont terminées.<br /><br /> Valide pour : `Button`|  
|RouteToDocs|La commande est acheminée vers le document actif.<br /><br /> Valide pour : `Button`|  
|StretchHorizontally|Lorsque cet indicateur est défini, la largeur est la largeur minimale de la zone de liste modifiable, et si l'espace est la barre d'outils, la zone de liste déroulante s'étire pour remplir l'espace disponible. Cela se produit uniquement si la barre d'outils est ancrée horizontalement, et qu'une liste déroulante dans la barre d'outils permettre utiliser l'indicateur \(l'indicateur est ignoré sur toutes à l'exception de la première zone de liste déroulante\).<br /><br /> Valide pour : `Combo`|  
|TextMenuUseButton|Utilisez le `ButtonText` champ pour les menus. Le champ de valeur par défaut est `MenuText` si elle est spécifiée.<br /><br /> Valide pour : `Button`|  
|TexteModifie|Le texte de commande ou un menu peut être modifié au moment de l'exécution, en général via la `QueryStatus` méthode.<br /><br /> Valide pour : `Button`, `Menu`|  
|TextChangesButton|Valide pour : `Button`|  
|TextIsAnchorCommand|Pour un contrôleur de menu, le texte du menu est extraite de la commande par défaut \(ancre\). Une commande d'ancre est la dernière commande sélectionnée ou verrouillée. Si cet indicateur n'est pas défini, le contrôleur de menu utilise son propre `MenuText` champ. Toutefois, en cliquant sur le contrôleur de menu permet toujours la dernière commande sélectionnée à partir de ce contrôleur.<br /><br /> Nous recommandons de combiner cet indicateur avec la `TextChanges` indicateur.<br /><br /> Cet indicateur s'applique uniquement aux menus de type MenuController ou MenuControllerLatched.<br /><br /> Valide pour : `Menu`|  
|TextMenuCtrlUseMenu|Utilisez le `MenuText` champ sur les contrôleurs de menu. Le champ de valeur par défaut est `ButtonText`.<br /><br /> Valide pour : `Button`|  
|TextMenuUseButton|Utilisez le `ButtonText` champ pour les menus. Le champ de valeur par défaut est `MenuText` si elle est spécifiée.<br /><br /> Valide pour : `Button`|  
|TextOnly|Afficher uniquement du texte sur une barre d'outils ou un menu, mais aucune icône, même si l'icône est spécifiée.<br /><br /> Valide pour : `Button`|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[Élément de boutons](../extensibility/buttons-element.md)|Fournit un groupe de [Élément de bouton](../extensibility/button-element.md) éléments.|  
|[Élément de menus](../extensibility/menus-element.md)|Définit tous les menus qui implémente un VSPackage.|  
  
## Voir aussi  
 [Table de commandes de Visual Studio \(. Fichiers VSCT\)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)