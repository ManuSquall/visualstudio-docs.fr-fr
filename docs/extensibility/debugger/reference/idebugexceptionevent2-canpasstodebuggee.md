---
title: IDebugExceptionEvent2::CanPassToDebuggee | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugExceptionEvent2::CanPassToDebuggee
helpviewer_keywords: IDebugExceptionEvent2::CanPassToDebuggee
ms.assetid: ae4bbe0a-fbe1-49be-a310-ea64279a434b
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ef10fd3ca7f41c2afd1c827fb71ca2178782e3d4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
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
  
## <a name="remarks"></a>Remarques  
 Le DE doit avoir une action par défaut pour passer à l’élément débogué. L’IDE peut recevoir le [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) événements et les appels le [continuer](../../../extensibility/debugger/reference/idebugprocess3-continue.md) méthode sans appeler le `CanPassToDebuggee` (méthode). Par conséquent, le DE doit avoir une casse par défaut pour le passage de l’exception ou pas.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)   
 [Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md)