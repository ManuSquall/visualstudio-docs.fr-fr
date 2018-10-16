---
title: Impossible de créer une association &lt;nom de l’association&gt; -propriété répertoriée deux fois | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3ced8bda-210e-4caf-9d8f-96cdbba19251
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7ae0458a0921177bfe3a5a8b499131c6dd5c3de5
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49172066"
---
# <a name="cannot-create-an-association-ltassociation-namegt---property-listed-twice"></a>Impossible de créer une association &lt;nom de l’association&gt; -propriété répertoriée deux fois
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Impossible de créer une association \<nom de l’association >. La même propriété est répertoriée plusieurs fois : \<nom_propriété >.  
  
 Les associations sont définies par le **propriétés d’Association** dans le **Éditeur d’associations** boîte de dialogue. Les propriétés ne peuvent être répertoriées qu'une seule fois pour chaque classe dans l'association.  
  
 La propriété dans le message apparaît plusieurs fois dans l’élément Parent ou enfant de la classe **propriétés d’Association**.  
  
### <a name="to-resolve-this-condition"></a>Pour résoudre cette condition  
  
-   Examinez le message et prenez note de la propriété spécifiée.  
  
-   Cliquez sur **OK** pour faire disparaître la boîte de message.  
  
-   Inspecter le **propriétés d’Association** et supprimez les entrées en double.  
  
-   Cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Outils LINQ to SQL dans Visual Studio](http://msdn.microsoft.com/library/a57e82d5-f7e4-4894-8add-3d9ba4fce186)   
 [Comment : créer une association (relation) entre les classes LINQ to SQL (Concepteur O/R)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)   
 [Procédure pas à pas : Création des Classes LINQ to SQL (Concepteur O-R)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)

