---
title: La propriété &lt;nom de la propriété&gt; ne peut pas être supprimé. | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 55873f74-7834-4ec1-8815-eeeb65618d87
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 22884e69c4802ec0bf699e383f0339d840f515e8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47494566"
---
# <a name="the-property-ltproperty-namegt-cannot-be-deleted"></a>La propriété &lt;nom de la propriété&gt; ne peut pas être supprimé.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [la propriété &lt;nom de la propriété&gt; ne peut pas être supprimé](https://docs.microsoft.com/visualstudio/data-tools/the-property-property-name-cannot-be-deleted).  
  
  
La propriété \<nom de propriété > ne peut pas être supprimé parce qu’elle est définie en tant que propriété de discriminateur pour l’héritage entre \<nom de la classe > et \<nom de la classe >  
  
 La propriété sélectionnée est définie comme le **propriété de discriminateur** pour l’héritage entre les classes indiquées dans le message d’erreur. Les propriétés ne peuvent pas être supprimées si elles participent à la configuration d'héritage entre des classes de données.  
  
 Définir le **propriété de discriminateur** à une autre propriété de la classe de données pour permettre la suppression de la propriété désirée.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1.  Dans le Concepteur O/R, sélectionnez la ligne d'héritage qui connecte les classes de données indiquées dans le message d'erreur.  
  
2.  Définir le **discriminateur** propriété une propriété différente.  
  
3.  Essayez une nouvelle fois de supprimer la propriété.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : configurer l’héritage à l’aide du Concepteur O/R](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md)   
 [Héritage de classes de données (Concepteur O/R)](../data-tools/data-class-inheritance-o-r-designer.md)   
 [Procédure pas à pas : création de classes LINQ to SQL à l’aide d’un héritage de table individuelle (Concepteur O/R)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)

