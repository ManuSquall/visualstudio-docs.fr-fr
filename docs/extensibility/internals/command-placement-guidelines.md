---
title: Instructions de positionnement de commande | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, small command sets
- small command sets
- command sets
ms.assetid: 63b3478e-e08a-420b-a0ec-76767e0cb289
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0c04ea981fc190b2e0074e767e086303e6950f2a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62861657"
---
# <a name="command-placement-guidelines"></a>Instructions de positionnement de commande
Meilleures pratiques pour le positionnement des commandes dans l’environnement de développement intégré (IDE) Visual Studio varient selon la taille du jeu de commandes. Commandes sont définies et positionnés selon les informations contenues dans *.vsct* fichiers.

## <a name="best-practices-for-all-command-sets"></a>Meilleures pratiques pour tous les jeux de commandes
 Pour chaque ensemble de commandes, suivez ces instructions :

- Préparer un graphique de la structure de commande à l’avance. Identifier les commandes, les zones de liste déroulante, les groupes de commandes et les menus contextuels qui seront utilisés dans plusieurs emplacements.

- Commandes qui s’affichent dans le même groupe doivent être liés.

- Les groupes qui contiennent une simple commande sont acceptables.

- Les packages ne devraient pas ajouter un grand nombre de commandes à des menus de Visual Studio existants. Au lieu de cela, ils doivent créer des menus ou sous-menus pour héberger les nouvelles commandes.

- Lorsque vous placez une commande sur un menu existant, le nom de la commande afin que son objectif est clair, et il ne sera pas confondre avec les commandes existantes.

## <a name="best-practices-for-small-command-sets"></a>Meilleures pratiques pour les jeux de commandes petit
 Si vous développez un VSPackage doté de quelques commandes, également suivre ces instructions :

- Si possible, utilisez le [Parent](../../extensibility/parent-element.md) élément d’une commande, zone de liste déroulante, groupe ou menu enfant à placer dans le groupe approprié.

- Ces groupes affectés aux menus affichés par le VSPackage.

- Le parent d’un menu enfant ou d’une commande doit être un [groupe](../../extensibility/group-element.md) élément. Affecter des commandes et les menus enfants aux groupes et ensuite affecter les groupes aux menus parents.

- Vous pouvez placer une commande dans des groupes supplémentaires en ajoutant un [CommandPlacements](../../extensibility/commandplacements-element.md) section de l’élément après la définition de la commande et en ajoutant à la `CommandPlacements` élément un [CommandPlacement](../../extensibility/commandplacement-element.md) élément pour chaque groupe supplémentaire.

## <a name="best-practices-for-large-command-sets"></a>Meilleures pratiques pour les jeux de commandes volumineux
 Si votre VSPackage doit avoir de nombreuses commandes qui seront affiche dans plusieurs contextes, également suivre ces instructions :

- Vérifiez les menus, les groupes et les commandes apparenter automatique. Autrement dit, n’affectez pas un `Parent` élément dans la définition de l’élément.

- Utilisez `CommandPlacement` entrées d’élément dans la `CommandPlacements` section de l’élément à placer des menus, les groupes et les commandes dans leurs menus parents et les groupes.

- Dans la `CommandPlacements` section de l’élément, les entrées qui remplissent un menu donné ou un groupe doivent être adjacentes à l’autre. Cela facilite la lisibilité et rend le `Priority` classements déterminer plus faciles.

## <a name="see-also"></a>Voir aussi
- [Comment VSPackages ajoute des éléments d’interface utilisateur](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Visual Studio fichiers command table (.vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)