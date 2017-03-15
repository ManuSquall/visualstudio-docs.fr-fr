---
title: "IDebugStackFrame3::InterceptCurrentException | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugStackFrame3::InterceptCurrentException"
helpviewer_keywords: 
  - "IDebugStackFrame3::InterceptCurrentException"
ms.assetid: 116c7324-7645-4c15-b484-7a5cdd065ef5
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugStackFrame3::InterceptCurrentException
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Appelé par le débogueur sur le frame de pile actuel lorsqu'il souhaite intercepter l'exception actuelle.  
  
## Syntaxe  
  
```cpp  
HRESULT InterceptCurrentException(  
   INTERCEPT_EXCEPTION_ACTION dwFlags,  
   UINT64*                    pqwCookie  
);  
```  
  
```c#  
int InterceptCurrentException(  
   uint dwFlags,   
   out  ulong pqwCookie  
);  
```  
  
#### Paramètres  
 `dwFlags`  
 \[in\]  Spécifie les différentes actions.  Actuellement, seule la valeur `IEA_INTERCEPT` d' [INTERCEPT\_EXCEPTION\_ACTION](../../../extensibility/debugger/reference/intercept-exception-action.md) est prise en charge et doit être spécifié.  
  
 `pqwCookie`  
 \[out\]  valeur unique identifiant une exception particulière.  
  
## Valeur de retour  
 En cas de réussite, retourne S\_OK ; sinon, retourne un code d'erreur.  
  
 Voici le plus de retour d'erreur courante.  
  
|Erreur|Description|  
|------------|-----------------|  
|`E_EXCEPTION_CANNOT_BE_INTERCEPTED`|L'exception actuelle ne peut pas être interceptée.|  
|`E_EXCEPTION_CANNOT_UNWIND_ABOVE_CALLBACK`|Le frame actuel d'exécution n'a pas été trouvé un gestionnaire encore.|  
|`E_INTERCEPT_CURRENT_EXCEPTION_NOT_SUPPORTED`|cette méthode n'est pas prise en charge pour ce frame.|  
  
## Notes  
 Lorsqu'une exception est levée, le contrôle de gains de débogueur du runtime à des points importants durant le processus de gestion des exceptions.  Pendant ces points clés, le débogueur peut demander le frame de pile actuel si le frame souhaite intercepter l'exception.  Ainsi, une exception interceptée est essentiellement un gestionnaire d'exceptions à la volée pour un frame de pile, même si ce frame de pile n'a pas de gestionnaire d'exceptions \(par exemple, un bloc try\/catch dans le code du programme\).  
  
 Lorsque le débogueur souhaite de déterminer si l'exception est interceptée, elle appelle cette méthode sur l'objet actuel du frame de pile.  Cette méthode est chargé de gérer tous les détails de l'exception.  Si l'interface d' [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md) n'est pas implémentée ou la méthode d' `InterceptStackException` retourne une erreur, le débogueur continue de traiter l'exception normalement.  
  
> [!NOTE]
>  Les exceptions peuvent être désactivées uniquement dans le code managé, c. autrement dit., lorsque le programme débogué s'exécute sous le runtime ASP.NET.\).  Naturellement, des tiers implémenteurs de langage peut implémenter `InterceptStackException` dans leurs propres moteurs de débogage s'ils choisissent faire.  
  
 Une fois l'interception terminée, [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md) est signalé.  
  
## Voir aussi  
 [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)   
 [INTERCEPT\_EXCEPTION\_ACTION](../../../extensibility/debugger/reference/intercept-exception-action.md)   
 [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)