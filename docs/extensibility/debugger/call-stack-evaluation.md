---
title: Évaluation de la pile des appels | Microsoft Docs
description: Découvrez la méthode EnumFrameInfo et comment l’implémenter pour afficher les frames de pile de la pile des appels en mode arrêt.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], call stack evaluation
- call stacks, evaluation
ms.assetid: 373d6b49-0459-4cce-816e-05745a44fe49
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fc637ff3ce2fe596eed48684523da7114fe0a03a
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/09/2020
ms.locfileid: "96914671"
---
# <a name="call-stack-evaluation"></a>Évaluation de la pile des appels
Pour afficher les frames de pile de la pile des appels en mode arrêt, vous devez implémenter la méthode [EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) .

## <a name="methods-for-evaluation"></a>Méthodes d’évaluation
 Pour un moteur de débogage simple (DE), il peut y avoir un seul Frame DE pile. Pour examiner le frame de pile en mode arrêt, vous devez implémenter les méthodes suivantes de [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md).

|Méthode|Description|
|------------|-----------------|
|[GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)|Obtient le contexte de code d’un frame de pile. Le contexte de code représente le pointeur d’instruction actuel dans un frame de pile.|
|[GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)|Obtient le contexte de document pour un frame de pile. Le contexte de document représente l’emplacement actuel dans le code source d’un frame de pile. Requis pour afficher le code source lorsque vous êtes arrêté dans un programme.|

 Ces méthodes requièrent l’implémentation de plusieurs méthodes et interfaces liées au contexte. Par conséquent, vous devez implémenter la méthode [GetDocumentContext](../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md) et les méthodes suivantes de [IDebugDocumentContext2](../../extensibility/debugger/reference/idebugdocumentcontext2.md).

|Méthode|Description|
|------------|-----------------|
|[GetStatementRange](../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)|Obtient la plage d’instructions de fichier d’un contexte de document.|

 Pour énumérer des contextes de code, vous devez implémenter toutes les méthodes de [IEnumDebugCodeContexts2](../../extensibility/debugger/reference/ienumdebugcodecontexts2.md).

## <a name="see-also"></a>Voir aussi
- [Contrôle d’exécution et évaluation de l’État](../../extensibility/debugger/execution-control-and-state-evaluation.md)
