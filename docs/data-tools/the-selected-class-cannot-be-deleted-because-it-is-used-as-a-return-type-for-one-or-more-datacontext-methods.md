---
title: La classe sélectionnée ne peut pas être supprimée car il est utilisé comme type de retour pour une ou plusieurs méthodes DataContext | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d68254a0-f3a1-47e2-aed3-a83471e1d711
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 0b5781508083524a5cf7374a12fd962f0fe34aaf
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="the-selected-class-cannot-be-deleted-because-it-is-used-as-a-return-type-for-one-or-more-datacontext-methods"></a>Impossible de supprimer la classe sélectionnée car elle est utilisée comme type de retour pour une ou plusieurs méthodes DataContext
Le type de retour d'une ou plusieurs méthodes <xref:System.Data.Linq.DataContext> est la classe d'entité sélectionnée. La suppression d'une classe d'entité utilisée comme type de retour pour une méthode <xref:System.Data.Linq.DataContext> fait échouer la compilation du projet. Pour supprimer la classe d'entité sélectionnée, identifiez les méthodes <xref:System.Data.Linq.DataContext> qui l'utilisent et affectez à leurs types de retour une classe d'entité différente.  
  
 Pour rétablir les types de retournés de <xref:System.Data.Linq.DataContext> méthodes à leurs types générés automatiquement d’origine, supprimez d’abord le <xref:System.Data.Linq.DataContext> (méthode) à partir du volet de méthodes puis faites glisser l’objet à partir de **l’Explorateur de serveurs** / **L’Explorateur de base de données** vers le Concepteur O/R.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1.  Identifier les <xref:System.Data.Linq.DataContext> les méthodes qui utilisent la classe d’entité comme type de retour en sélectionnant un <xref:System.Data.Linq.DataContext> méthode dans les méthodes volet et en inspectant la **Type de retour** propriété dans le **propriétés** fenêtre .  
  
2.  Définir le **Type de retour** à une classe d’entité différente ou supprimez la <xref:System.Data.Linq.DataContext> méthode à partir du volet de méthodes.  
  
## <a name="see-also"></a>Voir aussi
[Messages du Concepteur O/R](../data-tools/o-r-designer-messages.md)  
[LINQ to SQL des outils dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)