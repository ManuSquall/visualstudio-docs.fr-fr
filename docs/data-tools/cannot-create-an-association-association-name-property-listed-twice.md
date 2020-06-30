---
title: Impossible de créer une association, propriété listée deux fois
ms.date: 11/04/2016
ms.topic: error-reference
ms.technology: vs-data-tools
ms.assetid: 3ced8bda-210e-4caf-9d8f-96cdbba19251
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 50c9311ef09172ea082d2419495f26b51ff1d6a4
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85536797"
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

- [Outils LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Comment : créer une association entre des classes LINQ to SQL (Concepteur O/R)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)