---
title: La gestion Annuler et rétablir à l’aide de l’API héritée | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - undo management
ms.assetid: 838c0ddf-fdf3-4df1-8d21-79610b8ba0b1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: adf6a2405ae3d3408f9cf04199ba05dff9232326
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62856431"
---
# <a name="manage-undo-and-redo-by-using-the-legacy-api"></a>Gérer l’annulation et de restauration par progression à l’aide de l’API héritée
Les éditeurs doivent prendre en charge les opérations d’annulation qui permettent aux utilisateurs d’annuler leurs modifications récentes quand ils modifient le code. La plupart des éditeurs implémentés sous [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] et [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] peut avoir prise en charge de l’annulation fournie automatiquement par l’environnement de développement intégré (IDE).

## <a name="in-this-section"></a>Dans cette section
- [Guide pratique pour Implémenter la gestion de l’annulation](../extensibility/how-to-implement-undo-management.md) fournit les fonctionnalité d’annulation pour les éditeurs d’unique ou plusieurs vues.

- [Guide pratique pour Effacer la pile d’annulations](../extensibility/how-to-clear-the-undo-stack.md) explique comment effacer une pile d’annulation.

- [Guide pratique pour Utiliser la gestion d’annulation liée](../extensibility/how-to-use-linked-undo-management.md) Incorporates lié gestion d’annulation dans votre éditeur.

## <a name="reference"></a>Référence
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager> Fournit la gestion d’annulation pour un éditeur qui prend en charge plusieurs vues.
