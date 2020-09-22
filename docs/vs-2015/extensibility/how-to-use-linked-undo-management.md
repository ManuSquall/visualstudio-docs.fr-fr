---
title: 'Procédure : utiliser la gestion des annulations liées | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - linked undo management
ms.assetid: af5cc22a-c9cf-45b1-a894-1022d563f3ca
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 67d0d173909b8cdfe2eaf0d56aa5c99c437d5ad8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839521"
---
# <a name="how-to-use-linked-undo-management"></a>Guide pratique pour utiliser la gestion des opérations d’annulation liée
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L’annulation liée permet à l’utilisateur d’annuler simultanément les mêmes modifications dans plusieurs fichiers. Par exemple, les modifications de texte simultanées dans plusieurs fichiers programme, comme un fichier d’en-tête et un fichier Visual C++, sont une transaction d’annulation liée. La fonctionnalité d’annulation liée est intégrée à l’implémentation de l’environnement du gestionnaire d’annulations, et <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager> vous permet de manipuler cette fonctionnalité. La fonction d’annulation liée est implémentée par une unité d’annulation parente qui peut lier des piles d’annulations distinctes pour qu’elles soient traitées comme une seule unité d’annulation. La procédure d’utilisation de l’annulation liée est détaillée dans la section suivante.  
  
### <a name="to-use-linked-undo"></a>Pour utiliser une annulation liée  
  
1. Appelez `QueryService` sur `SVsLinkedUndoManager` pour obtenir un pointeur vers `IVsLinkedUndoTransactionManager` .  
  
2. Créez l’unité d’annulation liée parente initiale en appelant <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager.OpenLinkedUndo%2A> . Cela définit le point de départ d’un ensemble de piles d’annulations à regrouper en piles d’annulations liées. Dans la `OpenLinkedUndo` méthode, vous devez également spécifier si vous souhaitez que l’annulation liée soit stricte ou non stricte. Un comportement d’annulation lié non strict signifie que certains des documents avec des frères d’annulation liés peuvent se fermer tout en laissant les autres frères d’annulation liés dans leurs piles. Le comportement d’annulation lié strict spécifie que toutes les piles de frères d’annulations liées doivent être annulées ensemble ou pas du tout. Ajoutez les piles d’annulations liées suivantes en appelant la méthode [IOleUndoManager :: Add](/windows/desktop/api/ocidl/nf-ocidl-ioleundomanager-add) .  
  
3. Appelez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager.CloseLinkedUndo%2A> pour restaurer toutes les unités d’annulation liées comme un.  
  
    > [!NOTE]
    > Pour implémenter la gestion des annulations liées dans un éditeur, ajoutez gestion des annulations. Pour plus d’informations sur l’implémentation de la gestion des annulations liées, consultez [Comment : implémenter la gestion des annulations](../extensibility/how-to-implement-undo-management.md).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>   
 [IOleParentUndoUnit](/windows/desktop/api/ocidl/nn-ocidl-ioleparentundounit)   
 [IOleUndoUnit](/windows/desktop/api/ocidl/nn-ocidl-ioleundounit)   
 [Guide pratique pour implémenter la gestion des opérations d’annulation](../extensibility/how-to-implement-undo-management.md)
