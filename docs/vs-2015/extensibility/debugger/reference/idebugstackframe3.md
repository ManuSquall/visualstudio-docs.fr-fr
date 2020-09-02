---
title: IDebugStackFrame3 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugStackFrame3
helpviewer_keywords:
- IDebugStackFrame3 interface
ms.assetid: 39af2f57-0a01-42b8-b093-b7fbc61e2909
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d63d4dcd6e3b7a3b81504b485ee710779cef3c13
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65688535"
---
# <a name="idebugstackframe3"></a>IDebugStackFrame3
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Cette interface étend [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) pour gérer les exceptions interceptées.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugStackFrame3 : IDebugStackFrame2  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 Le moteur DE débogage (DE) implémente cette interface sur le même objet qui implémente l’interface [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) pour prendre en charge les exceptions interceptées.  
  
## <a name="notes-for-callers"></a>Notes pour les appelants  
 Appelez [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) sur une `IDebugStackFrame2` interface pour obtenir cette interface.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 En plus des méthodes héritées de [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md), `IDebugStackFrame3` expose les méthodes suivantes.  
  
|Méthode|Description|  
|------------|-----------------|  
|[InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)|Gère une exception pour le frame de pile actuel avant toute gestion normale des exceptions.|  
|[GetUnwindCodeContext](../../../extensibility/debugger/reference/idebugstackframe3-getunwindcodecontext.md)|Retourne un contexte de code si un déroulement de pile devait se produire.|  
  
## <a name="remarks"></a>Notes  
 Une exception interceptée signifie qu’un débogueur peut traiter une exception avant que les routines de gestion des exceptions normales ne soient appelées par le moment de l’exécution. L’interception d’une exception signifie essentiellement que l’exécution de l’exécution prétend qu’un gestionnaire d’exceptions est présent même si ce n’est pas le cas.  
  
 [InterceptCurrentException,](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md) est appelé pendant tous les événements de rappel d’exception normaux (la seule exception à cela est si vous déboguez du code en mode mixte (code managé et non managé), auquel cas l’exception ne peut pas être interceptée pendant le rappel de dernière chance). Si le DE n’implémente pas `IDebugStackFrame3` , ou si le de retourne une erreur à partir de IDebugStackFrame3 :: `InterceptCurrentException` (tel que `E_NOTIMPL` ), le débogueur gère l’exception normalement.  
  
 En interceptant une exception, le débogueur peut permettre à l’utilisateur d’apporter des modifications à l’état du programme en cours de débogage, puis de reprendre l’exécution au point où l’exception a été levée.  
  
> [!NOTE]
> Les exceptions interceptées sont autorisées uniquement dans le code managé, autrement dit, dans un programme qui s’exécute sous le Common Language Runtime (CLR).  
  
 Un moteur de débogage indique qu’il prend en charge l’interception des exceptions en affectant la valeur 1 à « metricExceptions » au moment de l’exécution à l’aide de la `SetMetric` fonction. Pour plus d’informations, consultez la page [applications auxiliaires du kit de développement logiciel (SDK) pour le débogage](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md).  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg. h  
  
 Espace de noms : Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces principales](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [Programmes d’assistance SDK pour le débogage](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
