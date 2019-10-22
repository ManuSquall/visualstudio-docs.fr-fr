---
title: Guide pratique pour afficher l’héritage entre des types (Concepteur de classes) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.AssociationTypeNotFoundError
helpviewer_keywords:
- types [Visual Studio], inheritance
- types [Visual Studio], base
- types [Visual Studio], derived
ms.assetid: ea3f0ada-f53b-4fb1-9fb5-908286f5ec3e
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e1e76d45847d0887b47746c60b836c7acf19d03b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670532"
---
# <a name="how-to-view-inheritance-between-types-class-designer"></a>Guide pratique pour afficher l'héritage entre les types (Concepteur de classes)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dans le Concepteur de classes, vous pouvez rechercher la relation d'héritage éventuellement existante entre un type de base et ses types dérivés dans un diagramme de classes. Pour créer une relation d’héritage, si aucune n’existe, entre deux types, consultez [Guide pratique pour créer un héritage entre des types (Concepteur de classes)](../ide/how-to-create-inheritance-between-types-class-designer.md).

### <a name="to-find-the-base-type"></a>Pour rechercher le type de base

1. Sur le diagramme de classes, cliquez sur le type dont vous souhaitez voir l'interface ou la classe de base.

2. Dans le menu **Diagramme de classes**, choisissez **Afficher la classe de base** ou **Afficher les interfaces de base**.

    L'interface ou la classe de base du type est alors sélectionnée dans le diagramme. Toutes les lignes d'héritage masquées apparaissent maintenant entre les deux formes.

   Vous pouvez également cliquer avec le bouton droit sur le type dont vous souhaitez afficher le type de base, puis choisir **Afficher la classe de base** ou **Afficher les interfaces de base**.

### <a name="to-find-the-derived-types"></a>Pour rechercher les types dérivés

1. Dans le diagramme de classes, cliquez sur le type dont vous souhaitez voir les interfaces ou classes dérivées.

2. Dans le menu **Diagramme de classes**, choisissez **Afficher les classes dérivées** ou **Afficher les interfaces dérivées**.

    Les classes ou interfaces dérivées du type apparaissent dans le diagramme. Toutes les lignes d'héritage masquées apparaissent maintenant entre les formes.

   Vous pouvez également cliquer avec le bouton droit sur le type dont vous souhaitez voir les types dérivés, puis choisir **Afficher les classes dérivées** ou **Afficher les interfaces dérivées**.

## <a name="see-also"></a>Voir aussi
 [Comment : créer des associations entre des types (Concepteur de classes)](../ide/how-to-create-associations-between-types-class-designer.md) [affichage des types et des relations (Concepteur de classes)](../ide/viewing-types-and-relationships-class-designer.md)
