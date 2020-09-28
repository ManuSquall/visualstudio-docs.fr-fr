---
title: 'IDebugStackFrame3 :: InterceptCurrentException, | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugStackFrame3::InterceptCurrentException
helpviewer_keywords:
- IDebugStackFrame3::InterceptCurrentException
ms.assetid: 116c7324-7645-4c15-b484-7a5cdd065ef5
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 42472690431d48a9baafbb0abee27c1a07d24fcd
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/11/2020
ms.locfileid: "91403866"
---
# <a name="idebugstackframe3interceptcurrentexception"></a>IDebugStackFrame3::InterceptCurrentException
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Appelée par le débogueur sur le frame de pile actuel lorsqu’il souhaite intercepter l’exception actuelle.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT InterceptCurrentException(  
   INTERCEPT_EXCEPTION_ACTION dwFlags,  
   UINT64*                    pqwCookie  
);  
```  
  
```csharp  
int InterceptCurrentException(  
   uint dwFlags,   
   out  ulong pqwCookie  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `dwFlags`  
 dans Spécifie des actions différentes. Actuellement, seule la [INTERCEPT_EXCEPTION_ACTION](../../../extensibility/debugger/reference/intercept-exception-action.md) valeur INTERCEPT_EXCEPTION_ACTION `IEA_INTERCEPT` est prise en charge et doit être spécifiée.  
  
 `pqwCookie`  
 à Valeur unique identifiant une exception particulière.  
  
## <a name="return-value"></a>Valeur renvoyée  
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.  
  
 Voici les erreurs les plus courantes retournées.  
  
|Erreur|Description|  
|-----------|-----------------|  
|`E_EXCEPTION_CANNOT_BE_INTERCEPTED`|L’exception actuelle ne peut pas être interceptée.|  
|`E_EXCEPTION_CANNOT_UNWIND_ABOVE_CALLBACK`|Le gestionnaire n’a pas encore été recherché dans la frame d’exécution en cours.|  
|`E_INTERCEPT_CURRENT_EXCEPTION_NOT_SUPPORTED`|Cette méthode n’est pas prise en charge pour ce frame.|  
  
## <a name="remarks"></a>Notes  
 Quand une exception est levée, le débogueur gagne le contrôle du runtime à des points clés pendant le processus de gestion des exceptions. Pendant ces moments clés, le débogueur peut demander le frame de pile actuel si le frame souhaite intercepter l’exception. De cette façon, une exception interceptée est essentiellement un gestionnaire d’exceptions à la volée pour un frame de pile, même si ce frame de pile n’a pas de gestionnaire d’exceptions (par exemple, un bloc try/catch dans le code du programme).  
  
 Quand le débogueur souhaite savoir si l’exception doit être interceptée, elle appelle cette méthode sur l’objet de frame de pile actuel. Cette méthode est chargée de gérer tous les détails de l’exception. Si l’interface [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md) n’est pas implémentée ou si la `InterceptStackException` méthode retourne une erreur, le débogueur continue de traiter l’exception normalement.  
  
> [!NOTE]
> Les exceptions peuvent être interceptées uniquement en code managé, c’est-à-dire lorsque le programme en cours de débogage s’exécute sous le Runtime .NET. Bien entendu, les implémenteurs de langage tiers peuvent implémenter `InterceptStackException` dans leurs propres moteurs de débogage s’ils le choisissent.  
  
 Une fois l’interception terminé, une [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md) est signalée.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)   
 [INTERCEPT_EXCEPTION_ACTION](../../../extensibility/debugger/reference/intercept-exception-action.md)   
 [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)
