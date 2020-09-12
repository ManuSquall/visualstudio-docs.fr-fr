---
title: Propriété listée deux fois
description: Impossible de créer une association, propriété listée deux fois
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: error-reference
ms.technology: vs-data-tools
ms.assetid: 3ced8bda-210e-4caf-9d8f-96cdbba19251
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: d0e3475896c937f247fc64a0750da25c2d6edac9
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90036481"
---
# <a name="cannot-create-an-association-ltassociation-namegt---property-listed-twice"></a>Impossible de créer une association &lt;nom de l’association&gt;. La propriété est listée deux fois

Impossible de créer une association \<association name> . La même propriété est listée plusieurs fois : \<property name> .

Les associations sont définies par les **Propriétés d’association** sélectionnées dans la boîte de dialogue **Éditeur d’associations**. Les propriétés ne peuvent être répertoriées qu'une seule fois pour chaque classe dans l'association.

La propriété dans le message apparaît plusieurs fois dans les **Propriétés d’association** de la classe parente ou enfant.

## <a name="to-resolve-this-condition"></a>Pour résoudre cette condition

- Examinez le message et prenez note de la propriété spécifiée.

- Cliquez sur **OK** pour fermer la boîte de message.

- Inspectez les **Propriétés d’association** et supprimez les doublons.

- Cliquez sur **OK**.

## <a name="see-also"></a>Voir aussi

- [Outils de LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Comment : créer une association entre des classes LINQ to SQL (Concepteur O/R)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)