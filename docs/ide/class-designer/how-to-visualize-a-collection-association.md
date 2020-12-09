---
title: Visualiser une association de collections
description: Découvrez comment visualiser une association de collection dans Concepteur de classes.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.classdesigner.collectionassociationline
- vs.classdesigner.ShowAssociationException
helpviewer_keywords:
- collection associations
- collections, collection associations
- Class Designer [Visual Studio], collection associations
ms.assetid: 54e39838-2fc9-4dc2-85b6-7e88a743108e
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eaec7d97cd92e65671dedca14c2dbae056b1af10
ms.sourcegitcommit: 60e5a8a7ee91854356797d05f3b502572c4a4884
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/09/2020
ms.locfileid: "96933581"
---
# <a name="how-to-visualize-a-collection-association-in-class-designer"></a>Guide pratique pour visualiser une association de collections dans le Concepteur de classes

Les propriétés et les champs qui sont des collections d’autres types peuvent être affichés sur le diagramme de classes en tant qu’association de collection. Contrairement à une association normale, qui affiche un champ ou une propriété sous la forme d’une ligne reliant la classe propriétaire au type du champ, une association de collection s’affiche sous la forme d’une ligne reliant la classe propriétaire au type collecté.

## <a name="to-create-a-collection-association"></a>Pour créer une association de collection

1. Dans le code, créez une propriété ou un champ dont le type est lui-même une collection fortement typée.

2. Dans le diagramme de classes, développez la classe afin que les champs et propriétés soient affichés.

3. Dans la classe, cliquez avec le bouton droit sur le champ ou la propriété, puis choisissez **Afficher en tant qu’association de collection**.

La propriété ou le champ s’affiche sous la forme d’une ligne reliée au type collecté.

## <a name="see-also"></a>Voir aussi

- [Guide pratique pour créer des associations entre des types](how-to-create-associations-between-types.md)
- [Conception des classes et des types](designing-and-viewing-classes-and-types.md)
