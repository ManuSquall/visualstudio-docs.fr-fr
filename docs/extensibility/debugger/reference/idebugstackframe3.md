---
title: IDebugStackFrame3 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugStackFrame3
helpviewer_keywords: IDebugStackFrame3 interface
ms.assetid: 39af2f57-0a01-42b8-b093-b7fbc61e2909
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8ed100cce9e4677538f12973b6c5586dce0d0548
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugstackframe3"></a>IDebugStackFrame3
Cette interface étend [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) pour gérer les exceptions interceptées.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugStackFrame3 : IDebugStackFrame2  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 Le moteur de débogage (DE) implémente cette interface sur le même objet qui implémente le [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) interface pour prendre en charge les exceptions interceptées.  
  
## <a name="notes-for-callers"></a>Remarques pour les appelants  
 Appelez [QueryInterface](/cpp/atl/queryinterface) sur une `IDebugStackFrame2` interface pour obtenir cette interface.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Outre les méthodes héritées de [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md), `IDebugStackFrame3` expose les méthodes suivantes.  
  
|Méthode|Description|  
|------------|-----------------|  
|[InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)|Gère une exception pour le frame de pile actuel avant que la gestion des exceptions normale.|  
|[GetUnwindCodeContext](../../../extensibility/debugger/reference/idebugstackframe3-getunwindcodecontext.md)|Retourne un contexte de code si un déroulement de pile se produit.|  
  
## <a name="remarks"></a>Remarques  
 Une exception interceptée signifie qu’un débogueur peut traiter une exception avant des routines de gestion des exceptions normales sont appelées par le temps d’exécution. Interception d’une exception essentiellement : la mise à l’heure d’exécution de prétendre qu’il existe un gestionnaire d’exceptions présent même quand il n’existe pas.  
  
 [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md) est appelé lors de tous les événements de rappel d’exception normale (la seule exception à cela est que si vous déboguez du code en mode mixte (managé et code non managé), auquel cas l’exception ne peut pas être interceptée lors de la rappel de la dernière chance). Si le DE n’implémente pas `IDebugStackFrame3`, ou le DE renvoie une erreur à partir de IDebugStackFrame3 ::`InterceptCurrentException` (tel que `E_NOTIMPL`), puis le débogueur gère l’exception normalement.  
  
 En interceptant une exception, le débogueur peut autoriser l’utilisateur d’apporter des modifications à l’état du programme débogué et reprendre l’exécution au point où l’exception a été levée.  
  
> [!NOTE]
>  Les exceptions interceptées sont autorisées uniquement dans le code managé, autrement dit, dans un programme qui s’exécute sous le Common Language Runtime (CLR).  
  
 Un moteur de débogage indique qu’il prend en charge interception des exceptions en définissant « metricExceptions » avec une valeur de 1 au moment de l’exécution à l’aide de la `SetMetric` (fonction). Pour plus d’informations, consultez [programmes d’assistance du Kit de développement logiciel pour le débogage](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md).  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [Aides SDK pour le débogage](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)