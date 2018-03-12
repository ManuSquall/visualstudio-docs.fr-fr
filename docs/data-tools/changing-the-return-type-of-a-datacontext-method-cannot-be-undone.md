---
title: "Impossible d’annuler la modification du type de retour d’une méthode DataContext | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 76b161fc-5075-4192-8d94-f15b02e199e9
caps.latest.revision: "3"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: e28cf13486e21564c4acdf62e3edc89321a4f1b5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="changing-the-return-type-of-a-datacontext-method-cannot-be-undone"></a>Impossible d’annuler la modification du type de retour d’une méthode DataContext
Impossible d’annuler la modification du type de retour d’une méthode DataContext. Pour revenir au type généré automatiquement, vous devez déplacer à nouveau l'élément de l'Explorateur de serveurs/Explorateur de bases de données vers le Concepteur O/R. Êtes-vous sûr de vouloir modifier le type de retour ?  
  
Le type de retour d'une méthode <xref:System.Data.Linq.DataContext> diffère selon l'endroit où vous placez l'élément dans le [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. Si vous placez directement un élément dans une classe d'entité existante, une méthode <xref:System.Data.Linq.DataContext> qui a le type de retour de la classe d'entité est créée. Si vous déposez un élément dans une zone vide du [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], une méthode <xref:System.Data.Linq.DataContext> qui retourne un type généré automatiquement est créée. Vous pouvez modifier le type de retour d'une méthode <xref:System.Data.Linq.DataContext> après l'avoir ajoutée au volet de méthodes. Pour inspecter ou modifier le type de retour d’un <xref:System.Data.Linq.DataContext> méthode, sélectionnez-la, puis cliquez sur le **Type de retour** propriété dans le **propriétés** fenêtre.  
  
### <a name="to-change-the-return-type-of-a-datacontext"></a>Pour modifier le type de retour d’un DataContext  
  
-   Cliquez sur **Oui**.  
  
### <a name="to-exit-the-message-box-and-leave-the-return-type-unchanged"></a>Pour sortir de la boîte de message et laisser le type de retour inchangé  
  
-   Cliquez sur **Non**.  
  
### <a name="to-revert-to-the-original-return-type-after-changing-the-return-type"></a>Pour rétablir le type de retour d’origine après l’avoir modifié  
  
1.  Sélectionnez le <xref:System.Data.Linq.DataContext> méthode sur le [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] et supprimez-le.  
  
2.  Localisez l’élément dans **Server Explorer/Database Explorer** et faites-le glisser vers le [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
    Une méthode <xref:System.Data.Linq.DataContext> est créée avec le type de retour par défaut d'origine.  
  
## <a name="see-also"></a>Voir aussi
[Messages du Concepteur O/R](../data-tools/o-r-designer-messages.md)  
[LINQ to SQL des outils dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)