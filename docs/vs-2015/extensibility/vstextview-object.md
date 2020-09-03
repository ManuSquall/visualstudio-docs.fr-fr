---
title: Objet VSTextView | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- VSTextView
helpviewer_keywords:
- VSTextView object, reference
- views [Visual Studio SDK], reference
ms.assetid: 78272ddc-9718-4c65-a94e-a44a2e8d54f4
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 22e4d4cdf1e5ca610dbdb067f8195fb730139c3d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65690698"
---
# <a name="vstextview-object"></a>Objet VSTextView
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L’affichage de texte est une fenêtre qui permet aux utilisateurs d’afficher et de modifier le texte Unicode de la mémoire tampon de texte. Pour l’essentiel, la vue est ce que la plupart des utilisateurs font référence à l’éditeur. Étant donné que la vue est séparée de la mémoire tampon par différentes couches de texte (retour automatique à la ligne, texte en mode plan, etc.), il n’est pas garanti que la vue soit une représentation exacte du texte dans la mémoire tampon. Pour plus d’informations sur l’affichage de texte, consultez [accès à la vue theText à l’aide de l’API héritée](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md) .  
  
 Le tableau suivant répertorie les interfaces de l' <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> objet.  
  
|Interface|Description|  
|---------------|-----------------|  
|[IDropSource](/windows/desktop/api/oleidl/nn-oleidl-idropsource)|Interface OLE standard.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IDropTarget>|Interface OLE standard.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite>|Interface OLE standard.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Interface OLE standard.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Active la création d’actions composées (autrement dit, les actions regroupées en une seule unité d’annulation/de rétablissement).|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|Fournit les méthodes de base pour la gestion et l’accès à la vue. `IVsTextView` n'est pas sûr (thread safe).|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Crée et gère un volet de fenêtre.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>|Interagit avec les couches de texte.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsThreadSafeTextView>|Effectue des opérations sur la vue à partir d’un thread différent.|  
  
## <a name="see-also"></a>Voir aussi  
 [Modifications des figures](https://msdn.microsoft.com/f08872bd-fd9c-4e36-8cf2-a2a2622ef986)   
 [Objet VSTextBuffer](../extensibility/vstextbuffer-object.md)   
 [Accès à la vue texte à l’aide de l’API héritée](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)
