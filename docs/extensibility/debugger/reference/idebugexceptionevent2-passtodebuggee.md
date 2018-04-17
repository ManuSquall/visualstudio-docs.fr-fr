---
title: IDebugExceptionEvent2::PassToDebuggee | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugExceptionEvent2::PassToDebuggee
helpviewer_keywords:
- IDebugExceptionEvent2::PassToDebuggee
ms.assetid: a20d0f0b-2ca0-4437-bd22-9213c81d2738
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ce8e6b53a07f191d967bbd676e6fcfc96b53dc14
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="idebugexceptionevent2passtodebuggee"></a>IDebugExceptionEvent2::PassToDebuggee
Spécifie si l’exception doit être transmise au programme en cours de débogage lors de l’exécution se poursuit, ou si l’exception doit être ignorée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT PassToDebuggee(  
   BOOL fPass  
);  
```  
  
```csharp  
int PassToDebuggee(  
   int fPass  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `fPass`  
 [in] Différent de zéro (`TRUE`) si l’exception doit être transmise le programme en cours de débogage lors de l’exécution se poursuit, ou égale à zéro (`FALSE`) si l’exception doit être ignorée.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Appel de cette méthode ne provoque pas réellement tout code à exécuter dans le programme en cours de débogage. L’appel consiste simplement à définir l’état de l’exécution du code suivante. Par exemple, les appels à la [CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) méthode peut retourner `S_OK` avec la [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md).`dwState` champ valeur `EXCEPTION_STOP_SECOND_CHANCE`.  
  
 L’IDE peut recevoir le [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) événements et les appels le [continuer](../../../extensibility/debugger/reference/idebugprogram2-continue.md) (méthode). Le moteur de débogage (DE) doit avoir un comportement par défaut pour gérer le cas si le `PassToDebuggee` méthode n’est pas appelée.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)   
 [CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)   
 [Continue](../../../extensibility/debugger/reference/idebugprogram2-continue.md)