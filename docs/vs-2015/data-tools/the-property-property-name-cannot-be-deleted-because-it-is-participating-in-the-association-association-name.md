---
title: La propriété &lt;nom de la propriété&gt; ne peut pas être supprimé, car il participe à l’association &lt;nom de l’association&gt; | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 389873cc-92dd-48da-bfca-0f6c8e0ae3c2
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 52dc1d42ab8fff879bd290fe1a9c9aa2ca0a08c0
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65700319"
---
# <a name="the-property-ltproperty-namegt-cannot-be-deleted-because-it-is-participating-in-the-association-ltassociation-namegt"></a>Impossible de supprimer la propriété &lt;nom de la propriété&gt;, car elle participe à l’association &lt;nom de l’association&gt;
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La propriété sélectionnée est définie comme **Propriété d’association** pour l’association de classes indiquée dans le message d’erreur. Les propriétés ne peuvent pas être supprimées si elles participent à une association entre des classes de données.  
  
 Affectez à **Propriété d’association** une propriété différente de la classe de données pour permettre la suppression de la propriété voulue.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1. Dans le Concepteur O/R, sélectionnez la ligne d'association qui connecte les classes de données indiquées dans le message d'erreur.  
  
2. Double-cliquez sur la ligne pour ouvrir la boîte de dialogue **Éditeur d’associations**.  
  
3. Supprimez la propriété des **Propriétés d’association**.  
  
4. Essayez une nouvelle fois de supprimer la propriété.  
  
## <a name="see-also"></a>Voir aussi  
 [Outils LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Guide pratique pour Créer une association (relation) entre les classes LINQ to SQL (Concepteur O/R)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)   
 [Procédure pas à pas : Création des Classes LINQ to SQL (Concepteur O-R)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)   
 [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)
