---
title: La gestion Annuler et rétablir à l’aide de l’API héritée | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - undo management
ms.assetid: 838c0ddf-fdf3-4df1-8d21-79610b8ba0b1
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ab655c4822f7f5186cbcd18d451cfa3bb0aa656e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51764177"
---
# <a name="managing-undo-and-redo-by-using-the-legacy-api"></a>La gestion des Annuler et rétablir à l’aide de l’API héritée
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

