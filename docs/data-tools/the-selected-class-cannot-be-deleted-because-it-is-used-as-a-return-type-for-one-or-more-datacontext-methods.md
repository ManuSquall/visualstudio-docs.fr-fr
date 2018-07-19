---
title: Impossible de supprimer la classe sélectionnée car elle est utilisée comme type de retour pour une ou plusieurs méthodes DataContext
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: d68254a0-f3a1-47e2-aed3-a83471e1d711
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 21ef0f86d701c899328044a03cde8035a1e7292d
ms.sourcegitcommit: f37affbc1b885dfe246d4b2c295a6538b383a0ca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37174205"
---
# <a name="the-selected-class-cannot-be-deleted-because-it-is-used-as-a-return-type-for-one-or-more-datacontext-methods"></a>Impossible de supprimer la classe sélectionnée car elle est utilisée comme type de retour pour une ou plusieurs méthodes DataContext

Le type de retour d'une ou plusieurs méthodes <xref:System.Data.Linq.DataContext> est la classe d'entité sélectionnée. Suppression d’une classe d’entité qui est utilisée comme type de retour pour une <xref:System.Data.Linq.DataContext> méthode provoque la compilation du projet échoue. Pour supprimer la classe d'entité sélectionnée, identifiez les méthodes <xref:System.Data.Linq.DataContext> qui l'utilisent et affectez à leurs types de retour une classe d'entité différente.

Pour rétablir les types de retour de <xref:System.Data.Linq.DataContext> méthodes vers leurs types d’origine généré automatiquement, tout d’abord supprimer la <xref:System.Data.Linq.DataContext> méthode à partir de la **méthodes** volet puis faites glisser l’objet à partir de **Explorateur de serveurs** / **Database Explorer** sur le **Concepteur O/R** à nouveau.

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

1. Identifier <xref:System.Data.Linq.DataContext> les méthodes qui utilisent la classe d’entité comme type de retour en sélectionnant un <xref:System.Data.Linq.DataContext> méthode dans le **méthodes** volet et en inspectant le **Type de retour** propriété dans le **Propriétés** fenêtre.

2. Définir le **Type de retour** à une classe d’entité différente ou une suppression le <xref:System.Data.Linq.DataContext> méthode à partir du volet de méthodes.

## <a name="see-also"></a>Voir aussi

- [Messages du Concepteur O/R](../data-tools/o-r-designer-messages.md)
- [Outils LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)