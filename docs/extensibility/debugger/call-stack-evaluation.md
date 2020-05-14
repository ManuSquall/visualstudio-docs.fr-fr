---
title: Évaluation des piles d’appels (en anglais seulement) Microsoft Docs
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
ms.openlocfilehash: b5557d7eae0ffe54b0f01f1f9e95935d71455229
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739180"
---
# <a name="call-stack-evaluation"></a>Évaluation de la pile d’appels
Afin de visualiser les cadres de pile de la pile d’appels pendant le mode de rupture, vous devez implémenter la méthode [EnumFrameInfo.](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)

## <a name="methods-for-evaluation"></a>Méthodes d’évaluation
 Pour un moteur de débogé simple (DE), il pourrait y avoir un seul cadre de pile. Pour examiner le cadre de pile pendant le mode de rupture, vous devez implémenter les méthodes suivantes de [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md).

|Méthode|Description|
|------------|-----------------|
|[GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)|Obtient le contexte de code pour un cadre de pile. Le contexte du code représente le pointeur d’instruction actuel dans un cadre de pile.|
|[GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)|Obtient le contexte de document pour un cadre de pile. Le contexte du document représente l’emplacement actuel dans le code source pour un cadre de pile. Nécessaire pour afficher le code source lorsque vous êtes arrêté dans un programme.|

 Ces méthodes nécessitent la mise en œuvre de plusieurs interfaces et méthodes liées au contexte. Ainsi, vous devez implémenter la méthode [GetDocumentContext](../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md) et les méthodes suivantes de [IDebugDocumentContext2](../../extensibility/debugger/reference/idebugdocumentcontext2.md).

|Méthode|Description|
|------------|-----------------|
|[GetStatementRange](../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)|Obtient la gamme de relevés de fichiers d’un contexte de document.|

 Pour énumérer les contextes de code, vous devez implémenter toutes les méthodes [d’IEnumDebugCodeContexts2](../../extensibility/debugger/reference/ienumdebugcodecontexts2.md).

## <a name="see-also"></a>Voir aussi
- [Contrôle des exécutions et évaluation de l’État](../../extensibility/debugger/execution-control-and-state-evaluation.md)
