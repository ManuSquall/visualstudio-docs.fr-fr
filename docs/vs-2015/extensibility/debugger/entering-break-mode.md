---
title: Passage en mode arrêt | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- break mode
- debugging [Debugging SDK], entering break mode
ms.assetid: e9a8a241-cd21-4d4e-999a-283554c288b1
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c4251779593e237713258fd54c80dcb311ce4b80
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68182248"
---
# <a name="entering-break-mode"></a>Entrée dans le mode arrêt
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Les éléments suivants décrivent le processus qui se produit lorsqu’un point d’arrêt est rencontré après un pas à pas détaillé dans une fonction, en cours d’exécution jusqu’à la ligne de code source qui contient le curseur, ou en cours d’exécution jusqu’à un point d’arrêt.  
  
## <a name="break-mode-process"></a>Processus en mode arrêt  
  
1. Le moteur DE débogage (DE) envoie [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md), [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md)ou tout autre événement d’arrêt pour faire en sorte que l’IDE passe en mode arrêt.  
  
2. Le SDM obtient les informations de la pile des appels à partir du thread, comme suit :  
  
    - [IDebugThread2::EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)  
  
    - [IEnumDebugFrameInfo2::GetCount](../../extensibility/debugger/reference/ienumdebugframeinfo2-getcount.md)  
  
    - [IEnumDebugFrameInfo2::Next](../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md)  
  
    - [IDebugStackFrame2 :: GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) pour récupérer les informations de code source  
  
    - [IDebugDocumentContext2 :: GetName](../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md) pour récupérer le nom de fichier  
  
    - [IDebugDocumentContext2 :: GetStatementRange](../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md) pour récupérer la plage d’instructions  
  
    - [IDebugStackFrame2 :: GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md) pour recevoir des informations sur la mémoire  
  
## <a name="see-also"></a>Voir aussi  
 [Événements d’appel du débogueur](../../extensibility/debugger/calling-debugger-events.md)
