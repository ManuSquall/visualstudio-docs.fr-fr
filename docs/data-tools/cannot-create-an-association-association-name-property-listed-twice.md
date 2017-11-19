---
title: "Impossible de créer une association &lt;nom de l’association&gt; -propriété apparaît deux fois | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3ced8bda-210e-4caf-9d8f-96cdbba19251
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 562ec97bbcd6031b9538713c65d6ec6229338f78
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="cannot-create-an-association-ltassociation-namegt---property-listed-twice"></a>Impossible de créer une association &lt;nom de l’association&gt; -propriété apparaît deux fois
Impossible de créer une association \<nom de l’association >. La même propriété est répertoriée plusieurs fois : \<nom de la propriété >.  
  
 Les associations sont définies par le **propriétés d’Association** dans les **Éditeur d’associations** boîte de dialogue. Les propriétés ne peuvent être répertoriées qu'une seule fois pour chaque classe dans l'association.  
  
 La propriété dans le message apparaît plusieurs fois dans l’élément Parent ou enfant classe **propriétés d’Association**.  
  
### <a name="to-resolve-this-condition"></a>Pour résoudre cette condition  
  
-   Examinez le message et prenez note de la propriété spécifiée.  
  
-   Cliquez sur **OK** pour fermer la boîte de message.  
  
-   Inspecter le **propriétés d’Association** et supprimer les entrées en double.  
  
-   Cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi
[Messages du Concepteur O/R](../data-tools/o-r-designer-messages.md)  
[LINQ to SQL des outils dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)  
[Comment : créer une association entre les classes LINQ to SQL (Concepteur O/R)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)