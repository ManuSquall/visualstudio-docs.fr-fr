---
title: Erreurs de point d’arrêt | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, errors
- debugging [Debugging SDK], breakpoint errors
- errors [Debugging SDK]
ms.assetid: 79221c6b-a924-4c8e-a778-e312e4e0c0c8
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e98dc5e4645ac67ecdf5ebb06ecf0f31510202e2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68147981"
---
# <a name="breakpoint-errors"></a>Erreurs de point d’arrêt
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Les éléments suivants décrivent le processus lorsqu’un point d’arrêt tente de se lier à du code mais échoue :  
  
## <a name="troubleshooting-a-breakpoint-error"></a>Dépannage d’une erreur de point d’arrêt  
  
1. Le moteur DE débogage (DE) envoie un [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) au gestionnaire de débogage de session (SDM).  
  
2. Le SDM appelle [IDebugBreakpointErrorEvent2 :: GetErrorBreakpoint](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md) (IDebugErrorBreakpoint2 * * `ppErrorBP` ) pour recevoir le point d’arrêt d’erreur.  
  
3. Le SDM appelle [IDebugErrorBreakpoint2 :: GetPendingBreakpoint](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md) pour recevoir le point d’arrêt en attente d’origine du point d’arrêt de l’erreur.  
  
4. Le SDM appelle [IDebugErrorBreakpoint2 :: GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) pour connaître la raison pour laquelle le point d’arrêt de l’erreur n’a pas pu être lié.  
  
## <a name="see-also"></a>Voir aussi  
 [Événements d’appel du débogueur](../../extensibility/debugger/calling-debugger-events.md)
