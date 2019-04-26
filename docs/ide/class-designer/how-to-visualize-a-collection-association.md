---
title: 'Procédure : Visualiser une association de collections (Concepteur de classes)'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.collectionassociationline
- vs.classdesigner.ShowAssociationException
helpviewer_keywords:
- collection associations
- collections, collection associations
- Class Designer [Visual Studio], collection associations
ms.assetid: 54e39838-2fc9-4dc2-85b6-7e88a743108e
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 09c23b59711a95f0729555acfd0203160bd9995d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62975071"
---
# <a name="how-to-visualize-a-collection-association-in-class-designer"></a>Procédure : Visualiser une association de collections dans le Concepteur de classes

Les propriétés et les champs qui sont des collections d’autres types peuvent être affichés sur le diagramme de classes en tant qu’association de collection. Contrairement à une association normale, qui affiche un champ ou une propriété sous la forme d’une ligne reliant la classe propriétaire au type du champ, une association de collection s’affiche sous la forme d’une ligne reliant la classe propriétaire au type collecté.

## <a name="to-create-a-collection-association"></a>Pour créer une association de collection

1. Dans le code, créez une propriété ou un champ dont le type est lui-même une collection fortement typée.

2. Dans le diagramme de classes, développez la classe afin que les champs et propriétés soient affichés.

3. Dans la classe, cliquez avec le bouton droit sur le champ ou la propriété, puis choisissez **Afficher en tant qu’association de collection**.

La propriété ou le champ s’affiche sous la forme d’une ligne reliée au type collecté.

## <a name="see-also"></a>Voir aussi

- [Guide pratique pour créer des associations entre des types](how-to-create-associations-between-types.md)
- [Conception des classes et des types](designing-and-viewing-classes-and-types.md)
