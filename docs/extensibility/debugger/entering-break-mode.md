---
title: Passage en Mode arrêt | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- break mode
- debugging [Debugging SDK], entering break mode
ms.assetid: e9a8a241-cd21-4d4e-999a-283554c288b1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0f9b41a111ecc6118c9bae0ff518d8421a9f2320
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2018
ms.locfileid: "39231936"
---
# <a name="enter-break-mode"></a>Passez en mode arrêt
Les informations suivantes décrivent le processus qui se produit lorsqu’un point d’arrêt est rencontrée après le pas à pas détaillé dans une fonction, en cours d’exécution à la ligne de code source qui comporte le curseur ou en cours d’exécution à un point d’arrêt.  
  
## <a name="break-mode-process"></a>Arrêter le processus de mode  
  
1.  Le moteur de débogage (dé) envoie [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md), [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md), ou tout autre événement d’arrêt pour provoquer l’IDE pour entrer en mode arrêt.  
  
2.  Le SDM Obtient les informations de pile des appels du thread, comme suit :  
  
    -   [IDebugThread2::EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)  
  
    -   [IEnumDebugFrameInfo2::GetCount](../../extensibility/debugger/reference/ienumdebugframeinfo2-getcount.md)  
  
    -   [IEnumDebugFrameInfo2::Next](../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md)  
  
    -   [IDebugStackFrame2::GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) pour obtenir les informations de code source  
  
    -   [IDebugDocumentContext2::GetName](../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md) pour obtenir le nom de fichier  
  
    -   [IDebugDocumentContext2::GetStatementRange](../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md) pour obtenir la plage d’instruction  
  
    -   [IDebugStackFrame2::GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md) pour obtenir des informations sur la mémoire  
  
## <a name="see-also"></a>Voir aussi  
 [Appel des événements de débogueur](../../extensibility/debugger/calling-debugger-events.md)