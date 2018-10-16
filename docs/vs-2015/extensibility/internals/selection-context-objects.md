---
title: Les objets de contexte de sélection | Microsoft Docs
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
- selection, tracking
- selection, context objects
ms.assetid: 7308ea8f-a42c-47e5-954e-7dee933dce7a
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9c1a0c138cbfcf3892508fb9ae42685ffe895411
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49228655"
---
# <a name="selection-context-objects"></a>Objets de contexte de sélection
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Le [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] l’environnement de développement intégré (IDE) utilise un objet de contexte de sélection globale pour déterminer ce qui doit être affiché dans l’IDE. Chaque fenêtre dans l’IDE peut avoir son propre objet de contexte de sélection vers le contexte de la sélection globale. L’IDE met à jour le contexte de sélection global avec des valeurs à partir d’une fenêtre lorsque cette fenêtre a le focus. Pour plus d’informations, consultez [vos commentaires à l’utilisateur](../../extensibility/internals/feedback-to-the-user.md).  
  
 Chaque frame de fenêtre ou d’un site dans l’IDE dispose d’un service appelé <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>. L’objet créé par votre VSPackage est placé dans le frame de fenêtre doit appeler le `QueryService` méthode pour obtenir un pointeur vers le <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> interface.  
  
 Fenêtres frame peuvent conserver des parties de leurs informations de contexte de sélection se propager sur le contexte de sélection global lorsqu’ils sont démarrés. Cette possibilité est utile pour les fenêtres Outil qui devront peut-être commencer par une sélection vide.  
  
 Modification des sélection globale contexte déclenche des événements qui peut surveiller les VSPackages. Les VSPackages peuvent effectuer les tâches suivantes en implémentant `IVsTrackSelectionEx` et <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> interfaces :  
  
-   Mettre à jour le fichier actif dans une hiérarchie.  
  
-   Surveiller les modifications apportées à certains types d’éléments. Par exemple, si votre package Visual Studio utilise un spécial **propriétés** fenêtre, vous pouvez surveiller les modifications dans l’active **propriétés** fenêtre et redémarrez le vôtre si nécessaire.  
  
 La séquence suivante montre le cours typique de suivi de sélection.  
  
1.  L’IDE récupère le contexte de sélection à partir de la fenêtre qui vient d’être ouverte et le place dans le contexte de la sélection globale. Si le contexte de sélection utilise HIERARCHY_DONTPROPAGATE ou SELCONTAINER_DONTPROPAGATE, ces informations ne sont pas propagées vers le contexte global. Pour plus d’informations, consultez [vos commentaires à l’utilisateur](../../extensibility/internals/feedback-to-the-user.md).  
  
2.  Événements de notification sont diffusés à n’importe quel package Visual Studio qui les demande.  
  
3.  Le VSPackage agit sur les événements qu’il reçoit en effectuant des activités telles que la mise à jour d’une hiérarchie, la réactivation d’un outil ou autres tâches similaires.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>   
 [Hiérarchies dans Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)   
 [Sélection et la devise dans l’IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)   
 [Types de projets](../../extensibility/internals/project-types.md)

