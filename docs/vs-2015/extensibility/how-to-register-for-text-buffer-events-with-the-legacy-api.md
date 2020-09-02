---
title: 'Comment : inscrire des événements de mémoire tampon de texte avec l’API héritée | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - register for text buffer events
ms.assetid: 5fc00ced-882c-4b48-b46c-1fa5a2469f94
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5f36e8dd780788d241e3c286b1bbbe581311b143
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204097"
---
# <a name="how-to-register-for-text-buffer-events-with-the-legacy-api"></a>Guide pratique pour s’inscrire aux événements de mémoire tampon de texte avec l’API héritée
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Si vous accédez à la mémoire tampon de texte à l’aide de l’API héritée, vous devez vous inscrire pour les événements de mémoire tampon de texte, comme indiqué dans la procédure suivante.  
  
### <a name="to-advise-text-buffer-events"></a>Pour signaler des événements de mémoire tampon de texte  
  
1. D’un pointeur vers l’une des interfaces sur <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> , appelez `QueryInterface` pour un pointeur vers <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> .  
  
2. Appelez la <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer.FindConnectionPoint%2A> méthode et transmettez l’ID d’interface des événements pour lesquels vous souhaitez vous inscrire.  
  
     Par exemple, si vous souhaitez vous inscrire à <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents> , puis passer un ID d’interface de IID_IVsTextLinesEvents.  
  
     La mémoire tampon de texte retourne un pointeur vers l' <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> interface pour l’objet de point de connexion approprié.  
  
3. À l’aide de ce pointeur, appelez la <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A> méthode, en passant un pointeur vers votre implémentation de l’interface d’événements pour laquelle vous souhaitez enregistrer, par exemple, l' `IVsTextLinesEvents` interface.  
  
     L’environnement retourne un cookie que vous pouvez ensuite utiliser pour arrêter d’écouter les événements en appelant la <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Unadvise%2A> méthode.  
  
## <a name="see-also"></a>Voir aussi  
 [Événements de la mémoire tampon du texte dans l’API héritée](../extensibility/text-buffer-events-in-the-legacy-api.md)
