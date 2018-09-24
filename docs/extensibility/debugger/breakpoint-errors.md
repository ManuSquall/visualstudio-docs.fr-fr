---
title: Erreurs de point d’arrêt | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, errors
- debugging [Debugging SDK], breakpoint errors
- errors [Debugging SDK]
ms.assetid: 79221c6b-a924-4c8e-a778-e312e4e0c0c8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b08b9bee82a2505411be95ef2e6634e7897c15ec
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/19/2018
ms.locfileid: "39153752"
---
# <a name="breakpoint-errors"></a>Erreurs de point d’arrêt
Ce qui suit décrit le processus lorsqu’un point d’arrêt tente de se lier au code, mais échoue.  
  
## <a name="troubleshoot-a-breakpoint-error"></a>Corriger une erreur de point d’arrêt  
  
1.  Le moteur de débogage (dé) envoie une [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) pour le Gestionnaire de session de débogage (SDM).  
  
2.  Les appels SDM [IDebugBreakpointErrorEvent2::GetErrorBreakpoint](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md) (IDebugErrorBreakpoint2 ** `ppErrorBP`) pour obtenir le point d’arrêt de l’erreur.  
  
3.  Les appels SDM [IDebugErrorBreakpoint2::GetPendingBreakpoint](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md) pour obtenir le point d’arrêt en attente dont provenance le point d’arrêt de l’erreur.  
  
4.  Les appels SDM [IDebugErrorBreakpoint2::GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) pour obtenir la raison de l’échec le point d’arrêt de l’erreur à lier.  
  
## <a name="see-also"></a>Voir aussi  
 [Appel des événements de débogueur](../../extensibility/debugger/calling-debugger-events.md)