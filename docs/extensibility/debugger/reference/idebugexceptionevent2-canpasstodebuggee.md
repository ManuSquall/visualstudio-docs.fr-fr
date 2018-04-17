---
title: IDebugExceptionEvent2::CanPassToDebuggee | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugExceptionEvent2::CanPassToDebuggee
helpviewer_keywords:
- IDebugExceptionEvent2::CanPassToDebuggee
ms.assetid: ae4bbe0a-fbe1-49be-a310-ea64279a434b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f0ffea7be736cbf6d04c368ba6124d0faf22be61
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="idebugexceptionevent2canpasstodebuggee"></a>IDebugExceptionEvent2::CanPassToDebuggee
Détermine si le moteur de débogage (DE) prend en charge les transmettre cette exception au programme en cours de débogage lors de l’exécution se poursuit.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CanPassToDebuggee(  
   void  
);  
```  
  
```csharp  
int CanPassToDebuggee();  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne un `S_OK` (l’exception peut être passée au programme) ou `S_FALSE` (l’exception ne peut pas être passée).  
  
## <a name="remarks"></a>Notes  
 Le DE doit avoir une action par défaut pour passer à l’élément débogué. L’IDE peut recevoir le [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) événements et les appels le [continuer](../../../extensibility/debugger/reference/idebugprocess3-continue.md) méthode sans appeler le `CanPassToDebuggee` (méthode). Par conséquent, le DE doit avoir une casse par défaut pour le passage de l’exception ou pas.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)   
 [Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md)