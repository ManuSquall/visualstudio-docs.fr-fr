---
title: Directives relatives au placement des commandes | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, small command sets
- small command sets
- command sets
ms.assetid: 63b3478e-e08a-420b-a0ec-76767e0cb289
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 021a5fd9f9931e3041a431d211c8ab49978bbbab
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80709570"
---
# <a name="command-placement-guidelines"></a>Directives relatives au positionnement des commandes
Les meilleures pratiques pour le positionnement des commandes dans l’environnement de développement intégré (IDE) de Visual Studio varient en fonction de la taille du jeu de commandes. Les commandes sont définies et positionnées en fonction des informations contenues dans les fichiers *. vsct* .

## <a name="best-practices-for-all-command-sets"></a>Meilleures pratiques pour tous les jeux de commandes
 Pour chaque ensemble de commandes, suivez ces instructions :

- Préparez un graphique de la structure de commande à l’avance. Identifiez les commandes, les zones de liste modifiable, les groupes de commandes et les menus contextuels qui seront utilisés dans plusieurs emplacements.

- Les commandes qui s’affichent dans le même groupe doivent être liées.

- Les groupes qui contiennent une seule commande sont acceptables.

- Les packages ne doivent pas ajouter de nombreuses commandes aux menus Visual Studio existants. Au lieu de cela, ils doivent créer des menus ou des sous-menus pour héberger les nouvelles commandes.

- Lorsque vous placez une commande dans un menu existant, nommez la commande afin que son objectif soit clair et ne confondez pas avec les commandes existantes.

## <a name="best-practices-for-small-command-sets"></a>Meilleures pratiques pour les petits jeux de commandes
 Si vous développez un VSPackage qui ne contient que quelques commandes, suivez également les instructions suivantes :

- Lorsque cela est possible, utilisez l’élément [parent](../../extensibility/parent-element.md) d’une commande, d’une zone de liste déroulante, d’un groupe ou d’un menu enfant pour le placer dans le groupe approprié.

- Affectez ces groupes à des menus affichés par le VSPackage.

- Le parent d’un menu enfant ou d’une commande doit être un élément de [groupe](../../extensibility/group-element.md) . Assignez des commandes et des menus enfants à des groupes, puis affectez les groupes aux menus parents.

- Vous pouvez placer une commande dans des groupes supplémentaires en ajoutant une section d’élément [CommandPlacements](../../extensibility/commandplacements-element.md) après la définition de la commande, puis en ajoutant à l' `CommandPlacements` élément un élément [commandplacement ayant](../../extensibility/commandplacement-element.md) pour chaque groupe supplémentaire.

## <a name="best-practices-for-large-command-sets"></a>Meilleures pratiques pour les jeux de commandes volumineux
 Si votre VSPackage contient de nombreuses commandes qui s’affichent dans plusieurs contextes, suivez également les instructions suivantes :

- Rendez les menus, les groupes et les commandes auto-parentés. Autrement dit, n’assignez pas d' `Parent` élément dans la définition de l’élément.

- Utilisez `CommandPlacement` les entrées d’élément dans la `CommandPlacements` section de l’élément pour placer des menus, des groupes et des commandes dans leurs menus et groupes parents.

- Dans la `CommandPlacements` section de l’élément, les entrées qui remplissent un menu ou un groupe donné doivent être adjacentes les unes aux autres. Cela contribue à la lisibilité et facilite la `Priority` détermination des classements.

## <a name="see-also"></a>Voir aussi
- [Comment les VSPackages ajoutent des éléments d’interface utilisateur](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Fichiers de table de commandes Visual Studio (. vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
