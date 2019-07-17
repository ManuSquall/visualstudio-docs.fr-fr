---
title: La gestion Annuler et rétablir à l’aide de l’API héritée | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - undo management
ms.assetid: 838c0ddf-fdf3-4df1-8d21-79610b8ba0b1
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7c2133c75b32e56c1a054740bd829bd04cac97cc
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68194368"
---
# <a name="managing-undo-and-redo-by-using-the-legacy-api"></a>Gestion de l’annulation et du rétablissement à l’aide de l’API héritée
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les éditeurs doivent prendre en charge les opérations d’annulation qui permettent aux utilisateurs d’annuler leurs modifications récentes quand ils modifient le code. La plupart des éditeurs implémentés sous [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] et [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] peut avoir prise en charge de l’annulation fournie automatiquement par l’environnement de développement intégré (IDE).  
  
## <a name="in-this-section"></a>Dans cette section  
 [Guide pratique pour implémenter la gestion des opérations d’annulation](../extensibility/how-to-implement-undo-management.md)  
 Fournit une fonctionnalité de l’annulation pour les éditeurs avec unique ou plusieurs vues.  
  
 [Guide pratique pour effacer la pile des opérations d’annulation](../extensibility/how-to-clear-the-undo-stack.md)  
 Décrit comment effacer une pile d’annulation.  
  
 [Guide pratique pour utiliser la gestion des opérations d’annulation liée](../extensibility/how-to-use-linked-undo-management.md)  
 Inclut une gestion d’annulation liée dans votre éditeur.  
  
## <a name="reference"></a>Référence  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>  
 Fournit la gestion d’annulation pour un éditeur qui prend en charge plusieurs vues.  
  
## <a name="related-sections"></a>Rubriques connexes
