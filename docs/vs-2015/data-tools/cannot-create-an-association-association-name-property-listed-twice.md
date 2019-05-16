---
title: Impossible de créer une association &lt;nom de l’association&gt; -propriété répertoriée deux fois | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 3ced8bda-210e-4caf-9d8f-96cdbba19251
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 257490a91ac21868be276cfc3ae5514222dae86d
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65703834"
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
 [Outils LINQ to SQL dans Visual Studio](https://msdn.microsoft.com/library/a57e82d5-f7e4-4894-8add-3d9ba4fce186)   
 [Guide pratique pour Créer une association (relation) entre les classes LINQ to SQL (Concepteur O/R)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)   
 [Procédure pas à pas : Création des Classes LINQ to SQL (Concepteur O-R)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)   
 [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)
