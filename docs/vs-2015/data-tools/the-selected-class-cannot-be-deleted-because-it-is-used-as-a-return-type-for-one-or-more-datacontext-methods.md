---
title: La classe sélectionnée ne peut pas être supprimée car il est utilisé comme type de retour pour une ou plusieurs méthodes DataContext | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d68254a0-f3a1-47e2-aed3-a83471e1d711
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9a285922a004669b75d33ac6d866e1f21f5d6442
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47506108"
---
# <a name="the-selected-class-cannot-be-deleted-because-it-is-used-as-a-return-type-for-one-or-more-datacontext-methods"></a>Impossible de supprimer la classe sélectionnée car elle est utilisée comme type de retour pour une ou plusieurs méthodes DataContext
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [la classe sélectionnée ne peut pas être supprimée car il est utilisé comme type de retour pour une ou plusieurs méthodes DataContext](https://docs.microsoft.com/visualstudio/data-tools/the-selected-class-cannot-be-deleted-because-it-is-used-as-a-return-type-for-one-or-more-datacontext-methods).  
  
  
Le type de retour d'une ou plusieurs méthodes <xref:System.Data.Linq.DataContext> est la classe d'entité sélectionnée. La suppression d'une classe d'entité utilisée comme type de retour pour une méthode <xref:System.Data.Linq.DataContext> fait échouer la compilation du projet. Pour supprimer la classe d'entité sélectionnée, identifiez les méthodes <xref:System.Data.Linq.DataContext> qui l'utilisent et affectez à leurs types de retour une classe d'entité différente.  
  
 Pour rétablir les types de retour de <xref:System.Data.Linq.DataContext> méthodes vers leurs types d’origine généré automatiquement, tout d’abord supprimer la <xref:System.Data.Linq.DataContext> (méthode) à partir du volet de méthodes puis faites glisser l’objet à partir de **Explorateur de serveurs** / **L’Explorateur de base de données** sur le Concepteur O/R à nouveau.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1.  Identifier <xref:System.Data.Linq.DataContext> les méthodes qui utilisent la classe d’entité comme type de retour en sélectionnant un <xref:System.Data.Linq.DataContext> méthode dans les méthodes volet et en inspectant le **Type de retour** propriété dans le **propriétés** fenêtre .  
  
2.  Définir le **Type de retour** à une classe d’entité différente ou une suppression le <xref:System.Data.Linq.DataContext> méthode à partir du volet de méthodes.  
  
## <a name="see-also"></a>Voir aussi  
 [Outils LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Procédure pas à pas : Création des Classes LINQ to SQL (Concepteur O-R)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)   
 [Méthodes DataContext (Concepteur O/R)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Guide pratique pour modifier le type de retour d’une méthode DataContext (Concepteur O/R)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md)

