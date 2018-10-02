---
title: Modification du type de retour d’une méthode DataContext ne peut pas être annulée | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 76b161fc-5075-4192-8d94-f15b02e199e9
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 2adc93f6426c39d26395bdeb88fb8c37112a1a98
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47506811"
---
# <a name="changing-the-return-type-of-a-datacontext-method-cannot-be-undone"></a>Impossible d’annuler la modification du type de retour d’une méthode DataContext
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [modification du type de retour d’une méthode DataContext ne peut pas être annulée](https://docs.microsoft.com/visualstudio/data-tools/changing-the-return-type-of-a-datacontext-method-cannot-be-undone).  
  
  
Impossible d’annuler la modification du type de retour d’une méthode DataContext. Pour revenir au type généré automatiquement, vous devez déplacer à nouveau l'élément de l'Explorateur de serveurs/Explorateur de bases de données vers le Concepteur O/R. Êtes-vous sûr de vouloir modifier le type de retour ?  
  
 Le type de retour d'une méthode <xref:System.Data.Linq.DataContext> diffère selon l'endroit où vous placez l'élément dans le [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Si vous placez directement un élément dans une classe d'entité existante, une méthode <xref:System.Data.Linq.DataContext> qui a le type de retour de la classe d'entité est créée. Si vous déposez un élément dans une zone vide du [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], une méthode <xref:System.Data.Linq.DataContext> qui retourne un type généré automatiquement est créée. Vous pouvez modifier le type de retour d'une méthode <xref:System.Data.Linq.DataContext> après l'avoir ajoutée au volet de méthodes. Pour inspecter ou modifier le type de retour d’un <xref:System.Data.Linq.DataContext> (méthode), sélectionnez-la et cliquez sur le **Type de retour** propriété dans le **propriétés** fenêtre.  
  
### <a name="to-change-the-return-type-of-a-datacontext"></a>Pour modifier le type de retour d’un DataContext  
  
-   Cliquez sur **Oui**.  
  
### <a name="to-exit-the-message-box-and-leave-the-return-type-unchanged"></a>Pour sortir de la boîte de message et laisser le type de retour inchangé  
  
-   Cliquez sur **Non**.  
  
### <a name="to-revert-to-the-original-return-type-after-changing-the-return-type"></a>Pour rétablir le type de retour d’origine après l’avoir modifié  
  
1.  Sélectionnez le <xref:System.Data.Linq.DataContext> méthode sur le [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] et supprimez-le.  
  
2.  Recherchez l’élément dans **Server Explorer/Database Explorer** et faites-le glisser sur le [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].  
  
     Une méthode <xref:System.Data.Linq.DataContext> est créée avec le type de retour par défaut d'origine.  
  
## <a name="see-also"></a>Voir aussi  
 [Outils LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Méthodes DataContext (Concepteur O/R)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Comment : créer des méthodes DataContext mappées aux procédures stockées et fonctions (Concepteur O/R)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)

