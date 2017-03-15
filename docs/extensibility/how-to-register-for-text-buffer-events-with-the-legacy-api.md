---
title: "Comment : s’inscrire aux événements de mémoire tampon de texte avec l’API héritée | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - register for text buffer events
ms.assetid: 5fc00ced-882c-4b48-b46c-1fa5a2469f94
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
ms.openlocfilehash: b7da1dc26631294b6e41aa6335f2dca064c2831d
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-register-for-text-buffer-events-with-the-legacy-api"></a>Comment : s’inscrire aux événements de mémoire tampon de texte avec l’API héritée
Si vous accédez à la mémoire tampon de texte à l’aide de l’API héritée, vous devez vous inscrire pour les événements de mémoire tampon de texte comme indiqué dans la procédure suivante.  
  
### <a name="to-advise-text-buffer-events"></a>Pour signaler des événements de mémoire tampon de texte  
  
1.  À partir d’un pointeur vers une des interfaces sur <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>, appelez `QueryInterface` pour un pointeur vers <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>.</xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> </xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>  
  
2.  Appelez le <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer.FindConnectionPoint%2A>(méthode) et passez l’ID d’interface des événements pour lesquels vous souhaitez inscrire.</xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer.FindConnectionPoint%2A>  
  
     Par exemple, si vous souhaitez enregistrer pour <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents>, puis passer dans une interface ID de IID_IVsTextLinesEvents.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents>  
  
     La mémoire tampon de texte retourne un pointeur vers le <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint>interface pour l’objet de point de connexion appropriée.</xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint>  
  
3.  À l’aide de ce pointeur, appelez le <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A>méthode, en passant un pointeur à votre implémentation de l’interface d’événements pour lesquels vous souhaitez enregistrer, par exemple, le `IVsTextLinesEvents` interface.</xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A>  
  
     L’environnement retourne un cookie qui vous permet ensuite d’arrêter d’écouter des événements en appelant le <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Unadvise%2A>méthode.</xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Unadvise%2A>  
  
## <a name="see-also"></a>Voir aussi  
 [Événements de mémoire tampon de texte dans l’API héritée](../extensibility/text-buffer-events-in-the-legacy-api.md)
