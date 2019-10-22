---
title: Impossible d'annuler la modification du type de retour d'une méthode DataContext
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 76b161fc-5075-4192-8d94-f15b02e199e9
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 95d75e084b4824cf7cc8e717b1ce9174e76aa2e7
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648691"
---
# <a name="changing-the-return-type-of-a-datacontext-method-cannot-be-undone"></a>Impossible d'annuler la modification du type de retour d'une méthode DataContext

Impossible d'annuler la modification du type de retour d'une méthode DataContext. Pour revenir au type généré automatiquement, vous devez déplacer à nouveau l’élément de l’**Explorateur de serveurs** ou l’**Explorateur de bases de données** vers le Concepteur O/R. Êtes-vous sûr de vouloir modifier le type de retour ?

Le type de retour d’une méthode <xref:System.Data.Linq.DataContext> diffère selon l’endroit où vous déposez l’élément dans le [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. Si vous déposez directement un élément dans une classe d’entité existante, une méthode <xref:System.Data.Linq.DataContext> qui a le type de retour de la classe d’entité est créée. Si vous déposez un élément dans une zone vide du [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], une méthode <xref:System.Data.Linq.DataContext> qui retourne un type généré automatiquement est créée. Vous pouvez modifier le type de retour d’une méthode <xref:System.Data.Linq.DataContext> après l’avoir ajoutée au volet de méthodes. Pour inspecter ou modifier le type de retour d’une méthode <xref:System.Data.Linq.DataContext>, sélectionnez-la et cliquez sur la propriété **Type de retour** dans la fenêtre **Propriétés**.

## <a name="to-change-the-return-type-of-a-datacontext"></a>Pour modifier le type de retour d'un DataContext

- Cliquez sur **Oui**.

## <a name="to-exit-the-message-box-and-leave-the-return-type-unchanged"></a>Pour sortir de la boîte de message et laisser le type de retour inchangé

- Cliquez sur **Non**.

## <a name="to-revert-to-the-original-return-type-after-changing-the-return-type"></a>Pour rétablir le type de retour d'origine après l'avoir modifié

1. Sélectionnez la méthode <xref:System.Data.Linq.DataContext> dans le [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] et supprimez-la.

2. Localisez l’élément dans l’**Explorateur de serveurs/Explorateur de bases de données** et faites-le glisser vers le [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].

    Une méthode <xref:System.Data.Linq.DataContext> est créée avec le type de retour par défaut d’origine.

## <a name="see-also"></a>Voir aussi

- [Outils LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)