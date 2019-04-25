---
title: La propriété &lt;nom de la propriété&gt; ne peut pas être supprimé. | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 55873f74-7834-4ec1-8815-eeeb65618d87
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 50e91c47ef848eda51fe71c9dce09cd1ea4893a8
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60106452"
---
# <a name="the-property-ltproperty-namegt-cannot-be-deleted"></a>La propriété &lt;nom de la propriété&gt; ne peut pas être supprimé.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La propriété \<nom de propriété > ne peut pas être supprimé parce qu’elle est définie en tant que propriété de discriminateur pour l’héritage entre \<nom de la classe > et \<nom de la classe >  
  
 La propriété sélectionnée est définie comme **Propriété de discriminateur** pour l’héritage entre les classes indiquées dans le message d’erreur. Les propriétés ne peuvent pas être supprimées si elles participent à la configuration d'héritage entre des classes de données.  
  
 Affectez à **Propriété de discriminateur** une propriété différente de la classe de données pour permettre la suppression de la propriété voulue.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1. Dans le Concepteur O/R, sélectionnez la ligne d'héritage qui connecte les classes de données indiquées dans le message d'erreur.  
  
2. Affectez à **Propriété de discriminateur** une propriété différente.  
  
3. Essayez une nouvelle fois de supprimer la propriété.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour Configurer l’héritage à l’aide du Concepteur O/R](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md)   
 [Héritage de classes de données (Concepteur O/R)](../data-tools/data-class-inheritance-o-r-designer.md)   
 [Procédure pas à pas : Création de classes LINQ to SQL à l’aide d’un héritage de table individuelle (Concepteur O/R)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)
