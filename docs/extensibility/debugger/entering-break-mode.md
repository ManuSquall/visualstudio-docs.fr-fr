---
title: Passage en mode arrêt | Microsoft Docs
description: En savoir plus sur le processus qui se produit pour un point d’arrêt rencontré dans une fonction, sur la ligne de code source au niveau du curseur ou sur un point d’arrêt.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- break mode
- debugging [Debugging SDK], entering break mode
ms.assetid: e9a8a241-cd21-4d4e-999a-283554c288b1
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d3ec09994f6998f87daafc690b1908b31e54706b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99840650"
---
# <a name="enter-break-mode"></a>Passer en mode arrêt
Les informations suivantes décrivent le processus qui se produit lorsqu’un point d’arrêt est rencontré après un pas à pas détaillé dans une fonction, en cours d’exécution jusqu’à la ligne de code source qui contient le curseur, ou en cours d’exécution jusqu’à un point d’arrêt.

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
- [Appel des événements du débogueur](../../extensibility/debugger/calling-debugger-events.md)
