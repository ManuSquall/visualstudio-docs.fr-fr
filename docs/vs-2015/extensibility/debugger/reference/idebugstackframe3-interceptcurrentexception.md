---
title: IDebugStackFrame3::InterceptCurrentException | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugStackFrame3::InterceptCurrentException
helpviewer_keywords:
- IDebugStackFrame3::InterceptCurrentException
ms.assetid: 116c7324-7645-4c15-b484-7a5cdd065ef5
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 80bb98c22ecd220b4dbb8d817eb8bad6351e37bc
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47504325"
---
# <a name="idebugstackframe3interceptcurrentexception"></a>IDebugStackFrame3::InterceptCurrentException
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [IDebugStackFrame3::InterceptCurrentException](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception).  
  
Appelé par le débogueur sur le frame de pile actuel quand il souhaite intercepter l’exception actuelle.  
  
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
 [in] Spécifie les différentes actions. Actuellement, seuls les [INTERCEPT_EXCEPTION_ACTION](../../../extensibility/debugger/reference/intercept-exception-action.md) valeur `IEA_INTERCEPT` est pris en charge et doit être spécifié.  
  
 `pqwCookie`  
 [out] Valeur unique identifiant une exception particulière.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.  
  
 L’erreur réapparaît plus courantes sont les suivantes :  
  
|Error|Description|  
|-----------|-----------------|  
|`E_EXCEPTION_CANNOT_BE_INTERCEPTED`|Ne peut pas être interceptée l’exception actuelle.|  
|`E_EXCEPTION_CANNOT_UNWIND_ABOVE_CALLBACK`|Le frame d’exécution actuel n’a pas encore été analysé pour un gestionnaire de.|  
|`E_INTERCEPT_CURRENT_EXCEPTION_NOT_SUPPORTED`|Cette méthode n’est pas pris en charge pour ce frame.|  
  
## <a name="remarks"></a>Notes  
 Lorsqu’une exception est levée, le débogueur prend le contrôle à partir du moment de l’exécution à des points clés pendant le processus de gestion des exceptions. Pendant ces moments clés, le débogueur peut demander le frame de pile actuel si le frame souhaite intercepter l’exception. De cette façon, une exception interceptée est essentiellement un gestionnaire d’exceptions d’à la volée pour un frame de pile, même si ce frame de pile n’a pas un gestionnaire d’exceptions (par exemple, il s’agit d’un bloc try/catch dans le code du programme).  
  
 Lorsque le débogueur veut savoir si l’exception doit être interceptée, elle appelle cette méthode sur l’objet de frame de pile actuel. Cette méthode est chargée de gérer tous les détails de l’exception. Si le [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md) interface n’est pas implémentée ou `InterceptStackException` méthode retourne une erreur, puis le débogueur continue le traitement normal de l’exception.  
  
> [!NOTE]
>  Exceptions peuvent être interceptées que dans le code managé, autrement dit, lorsque le programme en cours de débogage s’exécute sous le runtime .NET. Bien sûr, les implémenteurs de langage tiers peuvent implémenter `InterceptStackException` dans leurs propres moteurs de débogage s’il le souhaite.  
  
 Une fois que l’interception est terminée, un [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md) est signalé.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)   
 [INTERCEPT_EXCEPTION_ACTION](../../../extensibility/debugger/reference/intercept-exception-action.md)   
 [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)

