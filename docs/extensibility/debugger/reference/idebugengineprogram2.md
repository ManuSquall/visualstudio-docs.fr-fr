---
title: IDebugEngineProgram2 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugEngineProgram2
helpviewer_keywords: IDebugEngineProgram2 interface
ms.assetid: 151003a9-2e4d-4acf-9f4d-365dfa6b9596
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9e4b7d83f40607dbb94371e4ca3244a9bb5b9a5b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugengineprogram2"></a>IDebugEngineProgram2
Cette interface fournit la prise en charge du débogage multithread.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugEngineProgram2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 Un moteur de débogage implémente cette interface pour prendre en charge le débogage de simultané de plusieurs threads. Cette interface est implémentée sur le même objet qui implémente le [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interface.  
  
## <a name="notes-for-callers"></a>Remarques pour les appelants  
 Utilisez [QueryInterface](/cpp/atl/queryinterface) pour obtenir cette interface dans un `IDebugProgram2` interface.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IDebugEngineProgram2`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[Stop](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md)|Arrête tous les threads en cours d’exécution dans ce programme.|  
|[WatchForThreadStep](../../../extensibility/debugger/reference/idebugengineprogram2-watchforthreadstep.md)|Surveille l’exécution (ou arrêter la surveillance de l’exécution) sur le thread donné.|  
|[WatchForExpressionEvaluationOnThread](../../../extensibility/debugger/reference/idebugengineprogram2-watchforexpressionevaluationonthread.md)|Autorise (ou interdit) évaluation d’expression en se produisent sur le thread donné, même si le programme est arrêté.|  
  
## <a name="remarks"></a>Remarques  
 Visual Studio appelle cette interface en réponse à une [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) événement et de définir les États « Espion pour Thread Step » et « Espion pour Expression d’évaluation sur le Thread » du programme. [Arrêter](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) est appelée chaque fois que le programme doit être arrêté ; cette méthode permet du programme pour mettre fin à tous les threads.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)