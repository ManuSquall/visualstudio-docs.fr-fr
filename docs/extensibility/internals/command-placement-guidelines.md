---
title: Directives de placement de commandement (lignes directrices sur le placement des commandes Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709570"
---
# <a name="command-placement-guidelines"></a>Lignes directrices sur le placement de commandement
Les meilleures pratiques de positionnement des commandes dans l’environnement de développement intégré Visual Studio (IDE) varient en fonction de la taille de l’ensemble de commandes. Les commandes sont définies et positionnées en fonction des informations contenues dans les fichiers *.vsct.*

## <a name="best-practices-for-all-command-sets"></a>Meilleures pratiques pour tous les ensembles de commandes
 Pour chaque ensemble de commandes, suivez ces lignes directrices :

- Préparer une carte de la structure de commande à l’avance. Identifiez les commandes, les boîtes combo, les groupes de commande et les menus de raccourci qui seront utilisés à plus d’un endroit.

- Les commandes qui apparaissent dans le même groupe doivent être liées.

- Les groupes qui ne contiennent qu’une seule commande sont acceptables.

- Les forfaits ne doivent pas ajouter beaucoup de commandes aux menus Visual Studio existants. Au lieu de cela, ils devraient créer des menus ou sous-hommes pour accueillir les nouvelles commandes.

- Lorsque vous mettez une commande sur un menu existant, nommez la commande de sorte que son but est clair et qu’elle ne soit pas confondue avec les commandes existantes.

## <a name="best-practices-for-small-command-sets"></a>Meilleures pratiques pour les petits ensembles de commandes
 Si vous développez un VSPackage qui n’a que quelques commandes, suivez également ces lignes directrices :

- Dans la mesure du possible, utilisez l’élément [Parent](../../extensibility/parent-element.md) d’une commande, d’une boîte combo, d’un groupe ou d’un menu pour enfants pour le mettre dans le groupe approprié.

- Attribuez ces groupes aux menus affichés par le VSPackage.

- Le parent d’un menu pour enfants ou d’une commande doit être un élément [du Groupe.](../../extensibility/group-element.md) Attribuez des commandes et des menus pour enfants à des groupes, puis attribuez les groupes aux menus parentaux.

- Vous pouvez mettre une commande dans d’autres groupes en ajoutant une section [d’élément CommandPlacements](../../extensibility/commandplacements-element.md) après la définition de la commande, puis en ajoutant à l’élément `CommandPlacements` un élément de position de [commandement](../../extensibility/commandplacement-element.md) pour chaque groupe supplémentaire.

## <a name="best-practices-for-large-command-sets"></a>Meilleures pratiques pour les grands ensembles de commandes
 Si votre VSPackage aura de nombreuses commandes qui apparaîtront dans plusieurs contextes, suivez également ces lignes directrices :

- Faire des menus, des groupes et des commandes auto-parentales. C’est-à-dire, n’attribuez pas un `Parent` élément dans la définition de l’élément.

- Utilisez `CommandPlacement` des entrées `CommandPlacements` d’éléments dans la section des éléments pour mettre des menus, des groupes et des commandes dans leurs menus et groupes parentaux.

- Dans `CommandPlacements` la section élément, les entrées qui peuplent un menu ou un groupe donné doivent être adjacentes les unes aux autres. Cela facilite la lisibilité et facilite la détables du `Priority` classement.

## <a name="see-also"></a>Voir aussi
- [Comment VSPackages ajoute des éléments d’interface utilisateur](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Fichiers visualister de table de commande de studio (.vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
