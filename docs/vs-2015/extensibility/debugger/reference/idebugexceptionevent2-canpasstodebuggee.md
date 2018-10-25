---
title: IDebugExceptionEvent2::CanPassToDebuggee | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugExceptionEvent2::CanPassToDebuggee
helpviewer_keywords:
- IDebugExceptionEvent2::CanPassToDebuggee
ms.assetid: ae4bbe0a-fbe1-49be-a310-ea64279a434b
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ac6c84005530f72ef9ed0f252bf40b035c3034e8
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49881937"
---
# <a name="idebugexceptionevent2canpasstodebuggee"></a>IDebugExceptionEvent2::CanPassToDebuggee
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Détermine si le moteur de débogage (dé) prend en charge la possibilité de transmettre cette exception au programme en cours de débogage lors de l’exécution reprend.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
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
 Le DE doit avoir une action par défaut pour le passer à l’élément débogué. L’IDE peut recevoir le [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) événements et les appels le [continuer](../../../extensibility/debugger/reference/idebugprocess3-continue.md) méthode sans appeler le `CanPassToDebuggee` (méthode). Par conséquent, l’Allemagne doit avoir une casse par défaut pour le passage de l’exception ou non.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)   
 [Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md)

