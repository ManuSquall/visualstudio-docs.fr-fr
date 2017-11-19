---
title: "La propriété &lt;nom de la propriété&gt; ne peut pas être supprimé, car il participe à l’association &lt;nom de l’association&gt; | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 389873cc-92dd-48da-bfca-0f6c8e0ae3c2
caps.latest.revision: "3"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 150d176c105e8368fc97f36a19774824dcb91c3e
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="the-property-ltproperty-namegt-cannot-be-deleted-because-it-is-participating-in-the-association-ltassociation-namegt"></a>La propriété &lt;nom de la propriété&gt; ne peut pas être supprimé, car il participe à l’association &lt;nom de l’association&gt;
La propriété sélectionnée est définie comme la **propriété d’Association** pour l’association entre les classes indiquée dans le message d’erreur. Les propriétés ne peuvent pas être supprimées si elles participent à une association entre des classes de données.  
  
 Définir le **propriété d’Association** à une autre propriété de la classe de données pour permettre la suppression de la propriété désirée.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1.  Dans le Concepteur O/R, sélectionnez la ligne d'association qui connecte les classes de données indiquées dans le message d'erreur.  
  
2.  Double-cliquez sur la ligne pour ouvrir la **Éditeur d’associations** boîte de dialogue.  
  
3.  Supprimez la propriété à partir de la **propriétés d’Association**.  
  
4.  Essayez une nouvelle fois de supprimer la propriété.  
  
## <a name="see-also"></a>Voir aussi
[Messages du Concepteur O/R](../data-tools/o-r-designer-messages.md)  
[LINQ to SQL des outils dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)