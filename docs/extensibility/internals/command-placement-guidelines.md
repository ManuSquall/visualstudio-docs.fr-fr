---
title: "Instructions de sélection élective de commande | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- commands, small command sets
- small command sets
- command sets
ms.assetid: 63b3478e-e08a-420b-a0ec-76767e0cb289
caps.latest.revision: 28
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: ca84800a199e9db420379697051fece598eb9295
ms.lasthandoff: 02/22/2017

---
# <a name="command-placement-guidelines"></a>Instructions de sélection élective de commande
Meilleures pratiques pour le positionnement des commandes dans l’environnement de développement intégré (IDE) Visual Studio varient selon la taille de l’ensemble de commandes. Commandes sont définies et positionnés d’après les informations contenues dans les fichiers .vsct.  
  
## <a name="best-practices-for-all-command-sets"></a>Meilleures pratiques pour tous les jeux de commandes  
 Pour chaque jeu de commandes, suivez ces instructions :  
  
-   Préparer un plan de la structure de commande à l’avance. Identifiez les commandes, zones de liste déroulante, groupes de commandes et les menus contextuels qui seront utilisés dans plusieurs emplacements.  
  
-   Les commandes qui apparaissent dans le même groupe doivent être liés.  
  
-   Les groupes qui contiennent une simple commande sont acceptables.  
  
-   Les packages ne devraient pas ajouter de nombreuses commandes de menus de Visual Studio existants. Au lieu de cela, ils doivent créer des menus ou sous-menus pour héberger les nouvelles commandes.  
  
-   Lorsque vous placez une commande sur un menu existant, le nom de la commande afin que son objectif est clair et il ne sera pas confondre avec les commandes existantes.  
  
## <a name="best-practices-for-small-command-sets"></a>Meilleures pratiques pour les jeux de petites commandes  
 Si vous développez un VSPackage doté de quelques commandes, également suivre ces instructions :  
  
-   Si possible, utilisez la [élément Parent](../../extensibility/parent-element.md) d’une commande, zone de liste déroulante, groupe ou enfant pour la placer dans le groupe approprié.  
  
-   Affecter ces groupes aux menus affichés par le VSPackage.  
  
-   Le parent d’une commande ou un menu enfant doit être un [élément Group](../../extensibility/group-element.md). Affecter des commandes et les menus enfants à des groupes et ensuite affecter les groupes de menus parents.  
  
-   Vous pouvez placer une commande dans des groupes supplémentaires en ajoutant une [CommandPlacements élément](../../extensibility/commandplacements-element.md) section après la définition de la commande d’ajout à la `CommandPlacements Element` un [CommandPlacement élément](../../extensibility/commandplacement-element.md) pour chaque groupe supplémentaire.  
  
## <a name="best-practices-for-large-command-sets"></a>Meilleures pratiques pour les jeux de commandes volumineux  
 Si votre VSPackage aura de nombreuses commandes qui apparaîtront dans plusieurs contextes, également suivre ces instructions :  
  
-   Vérifiez les menus, les groupes et commandes apparenter automatique. Autrement dit, n’attribuez pas une `Parent Element` dans la définition de l’élément.  
  
-   Utilisez `CommandPlacement Element` entrées dans la `CommandPlacements Element` section pour placer des menus, les groupes et les commandes dans les menus parents et les groupes.  
  
-   Dans la `CommandPlacements` section, les entrées figurant dans un menu ou groupe doit être adjacente. Cela facilite la lisibilité et rend le `Priority` déterminer plus facilement les rangs.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment ajouter des éléments d’Interface utilisateur dans les packages VS](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Table de commandes de Visual Studio (. Fichiers VSCT)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
