---
title: Objet de VSTextView | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VSTextView
helpviewer_keywords:
- VSTextView object, reference
- views [Visual Studio SDK], reference
ms.assetid: 78272ddc-9718-4c65-a94e-a44a2e8d54f4
caps.latest.revision: 8
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
ms.openlocfilehash: fd11409382b2db5e5cbea8c0dad25dbdb3b6cb99
ms.lasthandoff: 02/22/2017

---
# <a name="vstextview-object"></a>Objet de VSTextView
L’affichage de texte est une fenêtre qui permet aux utilisateurs d’afficher et de modifier le texte de la mémoire tampon de texte Unicode. La vue est essentiellement ce que la plupart des utilisateurs, consultez comme éditeur. Étant donné que la vue est séparée de la mémoire tampon par différentes couches de texte (retour, texte en mode plan et ainsi de suite), la vue n’est pas garantie pour être une représentation exacte du texte dans la mémoire tampon. Pour plus d’informations sur l’affichage de texte, consultez [accéder à theText vue à l’aide de l’API héritée](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)  
  
 Le tableau suivant indique les interfaces dans le <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>objet.</xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>  
  
|Interface|Description|  
|---------------|-----------------|  
|[IDropSource](http://msdn.microsoft.com/library/windows/desktop/ms690071)|Interface OLE standard.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IDropTarget></xref:Microsoft.VisualStudio.OLE.Interop.IDropTarget>|Interface OLE standard.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite></xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite>|Interface OLE standard.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget></xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Interface OLE standard.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction></xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Permet la création d’actions composées (autrement dit, les actions qui sont regroupées en une unité d’annulation/de rétablissement unique).|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|Fournit les méthodes de base pour la gestion et l’accès à la vue. `IVsTextView`n’est pas thread-safe.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane></xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Crée et gère un volet de fenêtre.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView></xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>|Interagit avec les calques de texte.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsThreadSafeTextView></xref:Microsoft.VisualStudio.TextManager.Interop.IVsThreadSafeTextView>|Effectue des opérations sur la vue à partir d’un thread différent.|  
  
## <a name="see-also"></a>Voir aussi  
 [Édition de figures](http://msdn.microsoft.com/en-us/f08872bd-fd9c-4e36-8cf2-a2a2622ef986)   
 [Objet de VSTextBuffer](../extensibility/vstextbuffer-object.md)   
 [L’accès à theText vue à l’aide de l’API héritée](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)
