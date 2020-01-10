---
title: Guide pratique pour afficher l'héritage entre les types (Concepteur de classes)
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.AssociationTypeNotFoundError
helpviewer_keywords:
- types [Visual Studio], inheritance
- types [Visual Studio], base
- types [Visual Studio], derived
ms.assetid: ea3f0ada-f53b-4fb1-9fb5-908286f5ec3e
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 47907493451841b631d561bfddb74676a460ff29
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75591773"
---
# <a name="how-to-view-inheritance-between-types-in-class-designer"></a>Guide pratique pour afficher l’héritage entre les types dans le Concepteur de classes

Dans le **Concepteur de classes**, vous pouvez rechercher la relation d’héritage éventuellement existante entre un type de base et ses types dérivés dans un diagramme de classes. Pour créer une relation d’héritage entre deux types, s’il n’en n’existe aucune, consultez [Guide pratique pour créer un héritage entre des types](how-to-create-inheritance-between-types.md).

## <a name="to-find-the-base-type"></a>Pour rechercher le type de base

1. Sur le diagramme de classes, cliquez sur le type dont vous souhaitez voir l'interface ou la classe de base.

2. Dans le menu **Diagramme de classes**, choisissez **Afficher la classe de base** ou **Afficher les interfaces de base**.

     L'interface ou la classe de base du type est alors sélectionnée dans le diagramme. Toutes les lignes d'héritage masquées apparaissent maintenant entre les deux formes.

Vous pouvez également cliquer avec le bouton droit sur le type dont vous souhaitez afficher le type de base, puis choisir **Afficher la classe de base** ou **Afficher les interfaces de base**.

## <a name="to-find-the-derived-types"></a>Pour rechercher les types dérivés

1. Dans le diagramme de classes, cliquez sur le type dont vous souhaitez voir les interfaces ou classes dérivées.

2. Dans le menu **Diagramme de classes**, choisissez **Afficher les classes dérivées** ou **Afficher les interfaces dérivées**.

     Les classes ou interfaces dérivées du type apparaissent dans le diagramme. Toutes les lignes d'héritage masquées apparaissent maintenant entre les formes.

Vous pouvez également cliquer avec le bouton droit sur le type dont vous souhaitez voir les types dérivés, puis choisir **Afficher les classes dérivées** ou **Afficher les interfaces dérivées**.

## <a name="see-also"></a>Voir aussi

- [Guide pratique pour créer des associations entre des types](how-to-create-associations-between-types.md)
- [Affichage des types et des relations](designing-and-viewing-classes-and-types.md)
