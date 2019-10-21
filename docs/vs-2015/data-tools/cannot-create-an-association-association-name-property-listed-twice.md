---
title: Impossible de créer une association &lt;association nom &gt;-propriété listé deux fois | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 3ced8bda-210e-4caf-9d8f-96cdbba19251
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9e4a1d20b5c341c1643836ae30e5de6243f35454
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662562"
---
# <a name="cannot-create-an-association-ltassociation-namegt---property-listed-twice"></a>Impossible de créer une association &lt;nom de l’association&gt;. La propriété est listée deux fois
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Impossible de créer une association \<nom de l’association>. La même propriété est listée plusieurs fois : \<nom de la propriété>.

 Les associations sont définies par les **Propriétés d’association** sélectionnées dans la boîte de dialogue **Éditeur d’associations**. Les propriétés ne peuvent être répertoriées qu'une seule fois pour chaque classe dans l'association.

 La propriété dans le message apparaît plusieurs fois dans les **Propriétés d’association** de la classe parente ou enfant.

### <a name="to-resolve-this-condition"></a>Pour résoudre cette condition

- Examinez le message et prenez note de la propriété spécifiée.

- Cliquez sur **OK** pour fermer la boîte de message.

- Inspectez les **Propriétés d’association** et supprimez les doublons.

- Cliquez sur **OK**.

## <a name="see-also"></a>Voir aussi
 [Outils de LINQ to SQL dans Visual Studio](https://msdn.microsoft.com/library/a57e82d5-f7e4-4894-8add-3d9ba4fce186) [Comment : créer une association (relation) entre des classes LINQ to SQL (concepteur o/R)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md) [procédure pas à pas : création de classes LINQ to SQL (concepteur o-r)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)
