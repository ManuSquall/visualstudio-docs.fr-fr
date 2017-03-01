---
title: "Les objets de contexte de sélection | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- selection, tracking
- selection, context objects
ms.assetid: 7308ea8f-a42c-47e5-954e-7dee933dce7a
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 3fa5093ee38c364a4766160f8642755bc0b2a23f
ms.lasthandoff: 02/22/2017

---
# <a name="selection-context-objects"></a>Objets de contexte de sélection
Le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] l’environnement de développement intégré (IDE) utilise un objet de contexte de sélection global pour déterminer ce qui doit être affiché dans l’IDE. Chaque fenêtre de l’IDE peut avoir son propre objet de contexte de sélection vers le contexte de sélection globale. L’IDE met à jour le contexte global de sélection avec des valeurs à partir d’une fenêtre lorsque cette fenêtre a le focus. Pour plus d’informations, consultez [vos commentaires à l’utilisateur](../../extensibility/internals/feedback-to-the-user.md).  
  
 Chaque frame de fenêtre ou d’un site dans l’IDE dispose d’un service appelé <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>.</xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> L’objet créé par votre VSPackage est placé dans le frame de fenêtre doit appeler le `QueryService` méthode pour obtenir un pointeur vers le <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>interface.</xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>  
  
 Fenêtres frame peuvent conserver des parties de leurs informations de contexte de sélection soient répercutées dans le contexte de sélection global lorsqu’ils sont démarrés. Cette possibilité est utile pour les fenêtres Outil qui devra peut-être commencer par une sélection vide.  
  
 Modification des sélection global contexte déclenche des événements qui peut surveiller les VSPackages. Les VSPackages peut effectuer les tâches suivantes en implémentant `IVsTrackSelectionEx` et <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>interfaces :</xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>  
  
-   Mettre à jour le fichier actif dans une hiérarchie.  
  
-   Surveiller les modifications de certains types d’éléments. Par exemple, si votre VSPackage utilise un spécial **propriétés** fenêtre, vous pouvez surveiller les modifications de l’actif **propriétés** fenêtre et redémarrez le vôtre dès que nécessaire.  
  
 La séquence suivante montre le cours typique de suivi de sélection.  
  
1.  L’IDE récupère le contexte de sélection à partir de la fenêtre qui vient d’être ouverte et le place dans le contexte de sélection globale. Si le contexte de sélection utilise HIERARCHY_DONTPROPAGATE ou SELCONTAINER_DONTPROPAGATE, ces informations ne sont pas propagées dans le contexte global. Pour plus d’informations, consultez [vos commentaires à l’utilisateur](../../extensibility/internals/feedback-to-the-user.md).  
  
2.  Événements de notification sont diffusés sur un VSPackage qui a demandé les.  
  
3.  Le VSPackage agit sur les événements qu’il reçoit en effectuant des activités telles que la mise à jour d’une hiérarchie, la réactivation d’un outil ou autres tâches similaires.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx></xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection></xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>   
 [Hiérarchies dans Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)   
 [Sélection et la devise dans l’IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)   
 [Types de projets](../../extensibility/internals/project-types.md)
