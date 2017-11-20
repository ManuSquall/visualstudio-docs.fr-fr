---
title: "La gestion Annuler et rétablir à l’aide de l’API héritée | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - undo management
ms.assetid: 838c0ddf-fdf3-4df1-8d21-79610b8ba0b1
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 41672845d318707512472f556753f429661d008c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="managing-undo-and-redo-by-using-the-legacy-api"></a>La gestion des annulations et restauration par progression à l’aide de l’API héritée
Éditeurs doivent prendre en charge les opérations d’annulation qui permettent aux utilisateurs d’annuler leurs modifications récentes lorsqu’ils modifient le code. La plupart des éditeurs implémentés sous [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] et [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] peuvent avoir des annulations prises en charge automatiquement par l’environnement de développement intégré (IDE).  
  
## <a name="in-this-section"></a>Dans cette section  
 [Comment : implémenter la gestion de l’annulation](../extensibility/how-to-implement-undo-management.md)  
 Fournit une fonctionnalité de l’annulation des éditeurs avec un ou plusieurs vues.  
  
 [Comment : effacer la pile d’annulation](../extensibility/how-to-clear-the-undo-stack.md)  
 Décrit comment effacer une pile d’annulation.  
  
 [Comment : utiliser la gestion de l’opération d’annulation liée](../extensibility/how-to-use-linked-undo-management.md)  
 Inclut une gestion de l’opération d’annulation liée dans votre éditeur.  
  
## <a name="reference"></a>Référence  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>  
 Fournit un éditeur qui prend en charge plusieurs vues de gestion Annuler.  
  
## <a name="related-sections"></a>Rubriques connexes