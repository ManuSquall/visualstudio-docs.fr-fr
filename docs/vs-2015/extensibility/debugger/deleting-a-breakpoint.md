---
title: Suppression d’un point d’arrêt | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, deleting
- debugging [Debugging SDK], deleting breakpoints
ms.assetid: 75a046cc-d20a-4c79-ad2d-1f18426ac5d0
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 42cd353c216c21d14c4f6592da809c72acdba664
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839733"
---
# <a name="deleting-a-breakpoint"></a>Suppression d’un point d’arrêt
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Les éléments suivants décrivent le processus de suppression d’un point d’arrêt en attente :  
  
## <a name="deletion-process"></a>Processus de suppression  
 Le gestionnaire de débogage de session (SDM) appelle la méthode [IDebugPendingBreakpoint2 ::D supprimable](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md) pour supprimer le point d’arrêt en attente et tous les points d’arrêt liés qui y sont liés.  
  
> [!NOTE]
> Un point d’arrêt à liaison unique peut également être supprimé par un appel à [IDebugBoundBreakpoint2 ::D supprim](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Événements d’appel du débogueur](../../extensibility/debugger/calling-debugger-events.md)
