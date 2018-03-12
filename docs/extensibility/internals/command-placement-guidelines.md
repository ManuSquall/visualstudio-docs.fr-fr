---
title: "Instructions de sélection élective de commande | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- commands, small command sets
- small command sets
- command sets
ms.assetid: 63b3478e-e08a-420b-a0ec-76767e0cb289
caps.latest.revision: "28"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 5c79d58530a7f6afc5779fab1bc0b5a1626cb595
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="command-placement-guidelines"></a>Instructions de sélection élective de commande
Meilleures pratiques pour le positionnement des commandes dans l’environnement de développement intégré (IDE) Visual Studio varient selon la taille du jeu de commandes. Commandes sont définis et positionnées en fonction des informations dans les fichiers .vsct.  
  
## <a name="best-practices-for-all-command-sets"></a>Meilleures pratiques pour tous les jeux de commandes  
 Pour chaque jeu de commandes, suivez ces instructions :  
  
-   Préparer un plan de la structure de la commande à l’avance. Identifier les commandes, zones de liste déroulante, groupes de commandes et les menus contextuels qui seront utilisés dans plusieurs emplacements.  
  
-   Les commandes qui s’affichent dans le même groupe doivent être liés.  
  
-   Les groupes qui contiennent une simple commande sont acceptables.  
  
-   Les packages ne devraient pas ajouter un grand nombre de commandes à des menus de Visual Studio existants. Au lieu de cela, ils doivent créer des menus ou sous-menus pour héberger les nouvelles commandes.  
  
-   Lorsque vous placez une commande sur un menu existant, le nom de la commande afin que son objectif est clair, et il ne sera pas confondre avec les commandes existantes.  
  
## <a name="best-practices-for-small-command-sets"></a>Meilleures pratiques pour la commande de petits jeux  
 Si vous développez un VSPackage qui dispose de quelques commandes, également suivre ces instructions :  
  
-   Si possible, utilisez le [élément Parent](../../extensibility/parent-element.md) d’une commande, zone de liste déroulante, groupe ou menu enfant à placer dans le groupe approprié.  
  
-   Ces groupes affectés aux menus affichés par le VSPackage.  
  
-   Le parent d’un menu enfant ou d’une commande doit être un [élément Group](../../extensibility/group-element.md). Affecter des commandes et les menus enfants à des groupes, puis affecter les groupes de menus du parent.  
  
-   Vous pouvez placer une commande dans des groupes supplémentaires en ajoutant un [CommandPlacements élément](../../extensibility/commandplacements-element.md) section après la définition de la commande d’ajout à la `CommandPlacements Element` un [CommandPlacement élément](../../extensibility/commandplacement-element.md) pour chaque groupe supplémentaire.  
  
## <a name="best-practices-for-large-command-sets"></a>Meilleures pratiques pour les jeux de commandes volumineux  
 Si votre VSPackage utilise de nombreuses commandes qui seront affiche dans plusieurs contextes, également suivre ces instructions :  
  
-   Vérifiez les menus, les groupes et les commandes apparenter automatique. Autrement dit, n’attribuez pas une `Parent Element` dans la définition de l’élément.  
  
-   Utilisez `CommandPlacement Element` entrées dans la `CommandPlacements Element` section à placer des menus, les groupes et les commandes dans leurs menus parents et les groupes.  
  
-   Dans la `CommandPlacements` section, les entrées qui remplissent un menu ou groupe doit être adjacent à un autre. Cela facilite la lisibilité et rend le `Priority` classements déterminer plus faciles.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment les VSPackages ajouter les éléments d’Interface utilisateur](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Fichiers Visual Studio Command Table (.Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)