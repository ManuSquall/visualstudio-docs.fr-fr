---
title: Atteindre un point d’arrêt | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], hitting breakpoints
- breakpoints, hitting
ms.assetid: a77816e3-b15b-46a0-90cd-be7242e4d6c9
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5ae077b8ccb4ce41f94fbc5e11bfff1f16c826c0
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58949597"
---
# <a name="hitting-a-breakpoint"></a>Atteinte d’un point d’arrêt
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La section suivante décrit le processus lorsque le moteur de débogage (dé) atteint un point d’arrêt pendant l’exécution ou pas à pas :  
  
## <a name="troubleshooting-a-hit-breakpoint"></a>Résolution des problèmes d’un point d’arrêt d’accès  
  
1.  L’envoie DE un [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) interface comme une **EVENT_SYNC_STOP**.  
  
2.  Appelle le Gestionnaire de session de débogage (SDM) [IDebugBreakpointEvent2:::EnumBreakpoints](../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md) pour obtenir le point d’arrêt a été atteint.  
  
## <a name="see-also"></a>Voir aussi  
 [Événements d’appel du débogueur](../../extensibility/debugger/calling-debugger-events.md)
