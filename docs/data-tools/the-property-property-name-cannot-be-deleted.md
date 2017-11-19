---
title: "La propriété &lt;nom de la propriété&gt; ne peut pas être supprimé | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 55873f74-7834-4ec1-8815-eeeb65618d87
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: b3a896e64e048a5104bca84b726c730d4d9d524a
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="the-property-ltproperty-namegt-cannot-be-deleted"></a>La propriété &lt;nom de la propriété&gt; ne peut pas être supprimé.
La propriété \<nom de la propriété > ne peut pas être supprimé, car il est défini comme le **propriété de discriminateur** pour l’héritage entre \<nom de la classe > et \<nom de la classe >  
  
 La propriété sélectionnée est définie comme la **propriété de discriminateur** pour l’héritage entre les classes indiquée dans le message d’erreur. Les propriétés ne peuvent pas être supprimées si elles participent à la configuration d'héritage entre des classes de données.  
  
 Définir le **propriété de discriminateur** à une autre propriété de la classe de données pour permettre la suppression de la propriété désirée.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1.  Dans le Concepteur O/R, sélectionnez la ligne d'héritage qui connecte les classes de données indiquées dans le message d'erreur.  
  
2.  Définir le **discriminateur** propriété à une autre propriété.  
  
3.  Essayez une nouvelle fois de supprimer la propriété.  
  
## <a name="see-also"></a>Voir aussi
[Messages du Concepteur O/R](../data-tools/o-r-designer-messages.md)  
[LINQ to SQL des outils dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)