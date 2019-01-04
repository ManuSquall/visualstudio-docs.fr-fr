---
title: Appeler l’évaluation de la pile | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], call stack evaluation
- call stacks, evaluation
ms.assetid: 373d6b49-0459-4cce-816e-05745a44fe49
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d4d17c48f98a1f9bb0632df76ff5b04b0bdf5403
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53851220"
---
# <a name="call-stack-evaluation"></a>Version d’évaluation de la pile des appels
Pour afficher les frames de pile de la pile des appels en mode arrêt, vous devez implémenter le [EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) (méthode).  
  
## <a name="methods-for-evaluation"></a>Méthodes pour l’évaluation  
 Pour un moteur de débogage simple (DE), il peut exister qu’un seul frame de pile. Pour examiner le frame de pile en mode arrêt, vous devez implémenter les méthodes suivantes de [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md).  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)|Obtient le contexte de code pour un frame de pile. Le contexte de code représente le pointeur d’instruction en cours dans un frame de pile.|  
|[GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)|Obtient le contexte de document pour un frame de pile. Le contexte de document représente l’emplacement actuel dans le code source pour un frame de pile. Obligatoire pour l’affichage du code source lorsque vous êtes arrêté dans un programme.|  
  
 Ces méthodes requièrent l’implémentation de plusieurs interfaces associées à un contexte et des méthodes. Par conséquent, vous devez implémenter le [GetDocumentContext](../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md) (méthode) et les méthodes suivantes de [IDebugDocumentContext2](../../extensibility/debugger/reference/idebugdocumentcontext2.md).  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetStatementRange](../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)|Obtient la plage d’instruction de fichier d’un contexte de document.|  
  
 Pour énumérer les contextes de code, vous devez implémenter toutes les méthodes de [IEnumDebugCodeContexts2](../../extensibility/debugger/reference/ienumdebugcodecontexts2.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Évaluation de contrôle et l’état d’exécution](../../extensibility/debugger/execution-control-and-state-evaluation.md)