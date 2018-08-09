---
title: La gestion Annuler et rétablir à l’aide de l’API héritée | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - undo management
ms.assetid: 838c0ddf-fdf3-4df1-8d21-79610b8ba0b1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: be60b3f0dd45a40663770b4b0debe8023e277f32
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39638070"
---
# <a name="manage-undo-and-redo-by-using-the-legacy-api"></a>Gérer l’annulation et de restauration par progression à l’aide de l’API héritée
Les éditeurs doivent prendre en charge les opérations d’annulation qui permettent aux utilisateurs d’annuler leurs modifications récentes quand ils modifient le code. La plupart des éditeurs implémentés sous [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] et [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] peut avoir prise en charge de l’annulation fournie automatiquement par l’environnement de développement intégré (IDE).  
  
## <a name="in-this-section"></a>Dans cette section  
 [Comment : gestion d’annulation implémenter](../extensibility/how-to-implement-undo-management.md)  
 Fournit une fonctionnalité de l’annulation pour les éditeurs avec unique ou plusieurs vues.  
  
 [Comment : effacer la pile d’annulation](../extensibility/how-to-clear-the-undo-stack.md)  
 Décrit comment effacer une pile d’annulation.  
  
 [Comment : utiliser liée gestion d’annulation](../extensibility/how-to-use-linked-undo-management.md)  
 Inclut une gestion d’annulation liée dans votre éditeur.  
  
## <a name="reference"></a>Référence  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>  
 Fournit la gestion d’annulation pour un éditeur qui prend en charge plusieurs vues.  
