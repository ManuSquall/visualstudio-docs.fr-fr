---
title: Impossible de supprimer la classe sélectionnée
description: Impossible de supprimer la classe sélectionnée car elle est utilisée comme type de retour pour une ou plusieurs méthodes DataContext
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: d68254a0-f3a1-47e2-aed3-a83471e1d711
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: a9948df37df4faf7cc5349b2729ca4f648d973cb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99866383"
---
# <a name="the-selected-class-cannot-be-deleted-because-it-is-used-as-a-return-type-for-one-or-more-datacontext-methods"></a>Impossible de supprimer la classe sélectionnée car elle est utilisée comme type de retour pour une ou plusieurs méthodes DataContext

Le type de retour d’une ou plusieurs méthodes <xref:System.Data.Linq.DataContext> est la classe d’entité sélectionnée. La suppression d’une classe d’entité utilisée comme type de retour pour une <xref:System.Data.Linq.DataContext> méthode provoque l’échec de la compilation du projet. Pour supprimer la classe d'entité sélectionnée, identifiez les méthodes <xref:System.Data.Linq.DataContext> qui l'utilisent et affectez à leurs types de retour une classe d'entité différente.

Pour rétablir les types de retour de méthodes <xref:System.Data.Linq.DataContext> à leurs types générés automatiquement d’origine, supprimez en premier la méthode <xref:System.Data.Linq.DataContext> du volet **Méthodes**, puis faites glisser l’objet de l’**Explorateur de serveurs**/**Explorateur de bases de données** vers le **Concepteur O/R**.

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

1. Identifiez des méthodes <xref:System.Data.Linq.DataContext> qui utilisent la classe d’entité comme type de retour en sélectionnant une méthode <xref:System.Data.Linq.DataContext> dans le volet **Méthodes** et en inspectant la propriété **Type de retour** dans la fenêtre **Propriétés**.

2. Affectez au **Type de retour** une classe d’entité différente ou supprimez la méthode <xref:System.Data.Linq.DataContext> du volet de méthodes.

## <a name="see-also"></a>Voir aussi

- [Outils de LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
