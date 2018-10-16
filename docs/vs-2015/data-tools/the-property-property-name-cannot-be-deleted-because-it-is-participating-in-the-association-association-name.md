---
title: La propriété &lt;nom de la propriété&gt; ne peut pas être supprimé, car il participe à l’association &lt;nom de l’association&gt; | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 389873cc-92dd-48da-bfca-0f6c8e0ae3c2
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: cdd2c2ab26709a017801e8ae34e4ee6f2223c2c3
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49177734"
---
# <a name="the-property-ltproperty-namegt-cannot-be-deleted-because-it-is-participating-in-the-association-ltassociation-namegt"></a>La propriété &lt;nom de la propriété&gt; ne peut pas être supprimé, car il participe à l’association &lt;nom de l’association&gt;
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
La propriété sélectionnée est définie comme le **propriété d’Association** pour l’association entre les classes indiquées dans le message d’erreur. Les propriétés ne peuvent pas être supprimées si elles participent à une association entre des classes de données.  
  
 Définir le **propriété d’Association** à une autre propriété de la classe de données pour permettre la suppression de la propriété désirée.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1.  Dans le Concepteur O/R, sélectionnez la ligne d'association qui connecte les classes de données indiquées dans le message d'erreur.  
  
2.  Double-cliquez sur la ligne pour ouvrir la **Éditeur d’associations** boîte de dialogue.  
  
3.  Supprimez la propriété à partir de la **propriétés d’Association**.  
  
4.  Essayez une nouvelle fois de supprimer la propriété.  
  
## <a name="see-also"></a>Voir aussi  
 [Outils LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Comment : créer une association (relation) entre les classes LINQ to SQL (Concepteur O/R)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)   
 [Procédure pas à pas : Création des Classes LINQ to SQL (Concepteur O-R)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)

