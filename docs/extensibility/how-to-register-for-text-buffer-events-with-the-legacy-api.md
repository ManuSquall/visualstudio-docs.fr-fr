---
title: 'Procédure : S’inscrire aux événements de mémoire tampon de texte avec l’API héritée | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - register for text buffer events
ms.assetid: 5fc00ced-882c-4b48-b46c-1fa5a2469f94
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8ec5c271c023483ea64ddbabb83129ea9a44e4c2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62911612"
---
# <a name="how-to-register-for-text-buffer-events-with-the-legacy-api"></a>Procédure : S’inscrire aux événements de mémoire tampon de texte avec l’API héritée
Si vous accédez à la mémoire tampon de texte à l’aide de l’API héritée, vous devez vous inscrire pour les événements de mémoire tampon de texte comme indiqué dans la procédure suivante.

## <a name="to-advise-text-buffer-events"></a>Pour signaler des événements de mémoire tampon de texte

1. À partir d’un pointeur vers une des interfaces sur <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>, appelez `QueryInterface` pour un pointeur vers <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>.

2. Appelez le <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer.FindConnectionPoint%2A> (méthode) et passez l’ID d’interface des événements pour lesquels vous souhaitez inscrire.

     Par exemple, si vous souhaitez inscrire pour <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents>, puis passer dans une interface ID de IID_IVsTextLinesEvents.

     La mémoire tampon de texte retourne un pointeur vers le <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> interface pour l’objet de point de connexion approprié.

3. À l’aide de ce pointeur, appelez le <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A> méthode, en passant un pointeur à votre implémentation de l’interface d’événements pour lequel vous souhaitez enregistrer, par exemple, le `IVsTextLinesEvents` interface.

     L’environnement retourne un cookie que vous pouvez ensuite utiliser pour cesser d’écouter les événements en appelant le <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Unadvise%2A> (méthode).

## <a name="see-also"></a>Voir aussi
- [Événements de mémoire tampon de texte dans l’API héritée](../extensibility/text-buffer-events-in-the-legacy-api.md)