---
title: "Appelez l’évaluation de la pile | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], call stack evaluation
- call stacks, evaluation
ms.assetid: 373d6b49-0459-4cce-816e-05745a44fe49
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 21626804ae60ca14b360f23acf17b3e336fa600b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="call-stack-evaluation"></a>Évaluation de pile des appels
Pour afficher les frames de pile de la pile des appels en mode arrêt, vous devez implémenter la [EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) (méthode).  
  
## <a name="methods-for-evaluation"></a>Méthodes d’évaluation pour  
 Pour un moteur de débogage simple (DE), il peut exister qu’un seul frame de pile. Pour examiner le frame de pile en mode arrêt, vous devez implémenter les méthodes suivantes de [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md).  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)|Obtient le contexte de code pour un frame de pile. Le contexte de code représente le pointeur d’instruction en cours dans un frame de pile.|  
|[GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)|Obtient le contexte de document pour un frame de pile. Le contexte de document représente l’emplacement actuel dans le code source pour un frame de pile. Obligatoire pour l’affichage du code source lorsque vous êtes arrêté dans un programme.|  
  
 Ces méthodes requièrent une implémentation de plusieurs interfaces liées au contexte et de méthodes. Par conséquent, vous devez implémenter la [GetDocumentContext](../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md) méthode et les méthodes suivantes de [IDebugDocumentContext2](../../extensibility/debugger/reference/idebugdocumentcontext2.md).  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetStatementRange](../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)|Obtient la plage d’instruction de fichier d’un contexte de document.|  
  
 Pour énumérer les contextes de code, vous devez implémenter toutes les méthodes de [IEnumDebugCodeContexts2](../../extensibility/debugger/reference/ienumdebugcodecontexts2.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôle de l’exécution et évaluation de l’état](../../extensibility/debugger/execution-control-and-state-evaluation.md)