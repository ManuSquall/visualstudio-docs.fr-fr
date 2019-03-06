---
title: Impossible de créer une association, propriété listée deux fois
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 3ced8bda-210e-4caf-9d8f-96cdbba19251
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 9c198518fca543eb9275afd918a640275f797b19
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55952617"
---
# <a name="cannot-create-an-association-ltassociation-namegt---property-listed-twice"></a>Impossible de créer une association &lt;nom de l’association&gt;. La propriété est listée deux fois

Impossible de créer une association \<nom de l’association>. La même propriété est listée plusieurs fois : \<nom de la propriété>.

Les associations sont définies par les **Propriétés d’association** sélectionnées dans la boîte de dialogue **Éditeur d’associations**. Les propriétés ne peuvent être répertoriées qu'une seule fois pour chaque classe dans l'association.

La propriété dans le message apparaît plusieurs fois dans les **Propriétés d’association** de la classe parente ou enfant.

## <a name="to-resolve-this-condition"></a>Pour résoudre cette condition

- Examinez le message et prenez note de la propriété spécifiée.

- Cliquez sur **OK** pour fermer la boîte de message.

- Inspectez les **Propriétés d’association** et supprimez les doublons.

- Cliquez sur **OK**.

## <a name="see-also"></a>Voir aussi

- [Messages du Concepteur O/R](../data-tools/o-r-designer-messages.md)
- [Outils LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Comment : créer une association entre les classes LINQ to SQL (Concepteur O/R)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)