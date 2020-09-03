---
title: La classe sélectionnée ne peut pas être supprimée, car elle est utilisée comme type de retour pour une ou plusieurs méthodes DataContext | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: d68254a0-f3a1-47e2-aed3-a83471e1d711
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: cf16fe7453388e19308ed603ee9dbbac207cec41
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667255"
---
# <a name="the-selected-class-cannot-be-deleted-because-it-is-used-as-a-return-type-for-one-or-more-datacontext-methods"></a>Impossible de supprimer la classe sélectionnée car elle est utilisée comme type de retour pour une ou plusieurs méthodes DataContext
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le type de retour d’une ou plusieurs méthodes <xref:System.Data.Linq.DataContext> est la classe d’entité sélectionnée. La suppression d’une classe d’entité utilisée comme type de retour pour une méthode <xref:System.Data.Linq.DataContext> fait échouer la compilation du projet. Pour supprimer la classe d'entité sélectionnée, identifiez les méthodes <xref:System.Data.Linq.DataContext> qui l'utilisent et affectez à leurs types de retour une classe d'entité différente.

 Pour rétablir les types de retour des <xref:System.Data.Linq.DataContext> méthodes à leurs types générés automatiquement d’origine, supprimez <xref:System.Data.Linq.DataContext> d’abord la méthode du volet de méthodes, puis faites glisser l’objet de **Explorateur de serveurs** / **Explorateur de base de données** vers le Concepteur O/R.

### <a name="to-correct-this-error"></a>Pour corriger cette erreur

1. Identifiez les <xref:System.Data.Linq.DataContext> méthodes qui utilisent la classe d’entité comme type de retour en sélectionnant une <xref:System.Data.Linq.DataContext> méthode dans le volet de méthodes et en inspectant la propriété **type de retour** dans la fenêtre **Propriétés** .

2. Affectez au **Type de retour** une classe d’entité différente ou supprimez la méthode <xref:System.Data.Linq.DataContext> du volet de méthodes.

## <a name="see-also"></a>Voir aussi
 [Outils de LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [procédure pas à pas : création de classes de LINQ to SQL (concepteur o-R)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233) [méthodes DataContext (concepteur o/r)](../data-tools/datacontext-methods-o-r-designer.md) [Comment : modifier le type de retour d’une méthode DataContext (concepteur o/r)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md)
