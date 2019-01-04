---
title: La gestion Annuler et rétablir à l’aide de l’API héritée | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - undo management
ms.assetid: 838c0ddf-fdf3-4df1-8d21-79610b8ba0b1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ccb49abc1251b489807efcb4d7e9ce89b25dcd16
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53842695"
---
# <a name="manage-undo-and-redo-by-using-the-legacy-api"></a>Gérer l’annulation et de restauration par progression à l’aide de l’API héritée
Les éditeurs doivent prendre en charge les opérations d’annulation qui permettent aux utilisateurs d’annuler leurs modifications récentes quand ils modifient le code. La plupart des éditeurs implémentés sous [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] et [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] peut avoir prise en charge de l’annulation fournie automatiquement par l’environnement de développement intégré (IDE).  
  
## <a name="in-this-section"></a>Dans cette section  
 [Guide pratique pour Gestion d’annulation implémenter](../extensibility/how-to-implement-undo-management.md)  
 Fournit une fonctionnalité de l’annulation pour les éditeurs avec unique ou plusieurs vues.  
  
 [Guide pratique pour Effacer la pile d’annulation](../extensibility/how-to-clear-the-undo-stack.md)  
 Décrit comment effacer une pile d’annulation.  
  
 [Guide pratique pour Utiliser la gestion d’annulation liée](../extensibility/how-to-use-linked-undo-management.md)  
 Inclut une gestion d’annulation liée dans votre éditeur.  
  
## <a name="reference"></a>Référence  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>  
 Fournit la gestion d’annulation pour un éditeur qui prend en charge plusieurs vues.  
