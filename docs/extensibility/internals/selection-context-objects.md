---
title: Les objets de contexte de sélection | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- selection, tracking
- selection, context objects
ms.assetid: 7308ea8f-a42c-47e5-954e-7dee933dce7a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 04ccc4a57ac7af144c134761119433b7533e9bec
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31131259"
---
# <a name="selection-context-objects"></a>Objets de contexte de sélection
Le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] l’environnement de développement intégré (IDE) utilise un objet de contexte de sélection global pour déterminer ce qui doit être affiché dans l’IDE. Chaque fenêtre de l’IDE peut avoir son propre objet de contexte de sélection vers le contexte de la sélection globale. L’IDE met à jour le contexte global de sélection avec des valeurs à partir d’une fenêtre lorsque cette fenêtre a le focus. Pour plus d’informations, consultez [des commentaires à l’utilisateur](../../extensibility/internals/feedback-to-the-user.md).  
  
 Chaque frame de fenêtre ou d’un site dans l’IDE dispose d’un service appelé <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>. L’objet créé par votre VSPackage est placé dans le frame de fenêtre doit appeler le `QueryService` méthode pour obtenir un pointeur vers le <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> interface.  
  
 Fenêtres frame peuvent conserver des parties de leurs informations de contexte de sélection soient répercutées dans le contexte de sélection global lorsqu’ils sont démarrés. Cette capacité est utile pour les fenêtres Outil qui doivent commencer par une sélection vide.  
  
 Modification des sélection globale contexte déclenche des événements qui peut surveiller les VSPackages. Les VSPackages peuvent effectuer les tâches suivantes en implémentant `IVsTrackSelectionEx` et <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> interfaces :  
  
-   Mettre à jour le fichier actuellement actif dans une hiérarchie.  
  
-   Surveiller les modifications apportées à certains types d’éléments. Par exemple, si votre VSPackage utilise une spéciale **propriétés** fenêtre, vous pouvez surveiller les modifications de l’actif **propriétés** fenêtre et redémarrez le vôtre à la demande.  
  
 La séquence suivante montre la marche à suivre le suivi de sélection par défaut.  
  
1.  L’IDE récupère le contexte de sélection à partir de la fenêtre récemment ouverte et le place dans le contexte de la sélection globale. Si le contexte de sélection utilise HIERARCHY_DONTPROPAGATE ou SELCONTAINER_DONTPROPAGATE, ces informations ne sont pas propagées vers le contexte global. Pour plus d’informations, consultez [des commentaires à l’utilisateur](../../extensibility/internals/feedback-to-the-user.md).  
  
2.  Événements de notification sont diffusés à un VSPackage qui a demandé les.  
  
3.  Le VSPackage agit sur les événements qu’il reçoit en effectuant des activités, telles que la mise à jour d’une hiérarchie, la réactivation d’un outil ou autres tâches similaires.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>   
 [Hiérarchies dans Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)   
 [Sélection et la devise dans l’IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)   
 [Types de projets](../../extensibility/internals/project-types.md)