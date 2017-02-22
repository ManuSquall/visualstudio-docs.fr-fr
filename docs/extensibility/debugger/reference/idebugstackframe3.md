---
title: "IDebugStackFrame3 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugStackFrame3"
helpviewer_keywords: 
  - "Interface de IDebugStackFrame3"
ms.assetid: 39af2f57-0a01-42b8-b093-b7fbc61e2909
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# IDebugStackFrame3
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette interface étend [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) pour gérer des exceptions interceptées.  
  
## Syntaxe  
  
```  
IDebugStackFrame3 : IDebugStackFrame2  
```  
  
## Remarques à l'intention des implémenteurs  
 Le moteur \(DE\) de débogage implémente cette interface sur le même objet qui implémente l'interface d' [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) pour prendre en charge des exceptions interceptées.  
  
## Remarques pour les appelants  
 Appelez [QueryInterface](/visual-cpp/atl/queryinterface) à une interface de `IDebugStackFrame2` pour obtenir cette interface.  
  
## méthodes en commande de Vtable  
 En plus de les méthodes héritées d' [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md), `IDebugStackFrame3` expose les méthodes suivantes.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)|Gère une exception pour le frame de pile actuel avant les gestions d'exceptions normale.|  
|[GetUnwindCodeContext](../../../extensibility/debugger/reference/idebugstackframe3-getunwindcodecontext.md)|Retourne un contexte de code si le déroulement de pile devait se produire.|  
  
## Notes  
 Une exception interceptée signifie qu'un débogueur peut traiter une exception avant les routines normales de gestion des exceptions soient appelées par le runtime.  Les moyens de interception d'une exception en effectuant le runtime feignent qu'il existe un présent de gestionnaire d'exceptions même s'il n'existe pas.  
  
 [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md) est appelé pendant tous les événements de rappel d'exception normale \(la seule exception est si vous déboguez du code en mode mixte \(code managé et non managé\), auquel cas l'exception ne peut pas être interceptée pendant le rappel de dernier\-occasion\).  Si le De n'implémente pas `IDebugStackFrame3`, ou le De retourne une erreur d'IDebugStackFrame3 : :`InterceptCurrentException` \(tel qu' `E_NOTIMPL`\), le débogueur gérera l'exception normalement.  
  
 En interceptant une exception, le débogueur peut permettre à l'utilisateur d'apporter des modifications à l'état du programme débogué puis pour reprendre l'exécution au moment où l'exception a été levée.  
  
> [!NOTE]
>  Il permet des exceptions interceptées uniquement dans le code managé, c. autrement dit., dans un programme qui s'exécute sous le common langage \(CLR\) runtime.  
  
 Un moteur de débogage indique qu'il prend en charge les exceptions de interception en définissant des « metricExceptions » à la valeur 1 au moment de l'exécution à l'aide de la fonction d' `SetMetric` .  Pour plus d'informations, consultez [« Helpers » du Kit de développement logiciel pour le débogage](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md).  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [« Helpers » du Kit de développement logiciel pour le débogage](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)