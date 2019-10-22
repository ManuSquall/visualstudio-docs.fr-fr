---
title: Guide pratique pour visualiser une association de collections (Concepteur de classes) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.collectionassociationline
- vs.classdesigner.ShowAssociationException
helpviewer_keywords:
- collection associations
- collections, collection associations
- Class Designer [Visual Studio], collection associations
ms.assetid: 54e39838-2fc9-4dc2-85b6-7e88a743108e
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 434cfc541da3c670d8d444b9a4259b33476a17d8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670522"
---
# <a name="how-to-visualize-a-collection-association-class-designer"></a>Comment : visualiser une association de collections (Concepteur de classes)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les propriétés et les champs qui sont des collections d’autres types peuvent être affichés sur le diagramme de classes en tant qu’association de collection. Contrairement à une association normale, qui affiche un champ ou une propriété sous la forme d’une ligne reliant la classe propriétaire au type du champ, une association de collection s’affiche sous la forme d’une ligne reliant la classe propriétaire au type collecté.

### <a name="to-create-a-collection-association"></a>Pour créer une association de collection

1. Dans le code, créez une propriété ou un champ dont le type est lui-même une collection fortement typée.

2. Dans le diagramme de classes, développez la classe afin que les champs et propriétés soient affichés.

3. Dans la classe, cliquez avec le bouton droit sur le champ ou la propriété, puis choisissez **Afficher en tant qu’association de collection**.

     La propriété ou le champ s’affiche sous la forme d’une ligne reliée au type collecté.

## <a name="see-also"></a>Voir aussi
 [Comment : créer des associations entre des types (Concepteur de classes)](../ide/how-to-create-associations-between-types-class-designer.md) [conception de classes et de types (Concepteur de classes)](../ide/designing-classes-and-types-class-designer.md) [affichage des types et des relations (Concepteur de classes)](../ide/viewing-types-and-relationships-class-designer.md)
