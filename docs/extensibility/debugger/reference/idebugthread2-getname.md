---
title: IDebugThread2::GetName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugThread2::GetName
helpviewer_keywords:
- IDebugThread2::GetName
ms.assetid: eec54b8f-4a0e-4919-b0f9-81d4bd1e0b6f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f28726afd6dad7c193d552cd05e4c9a9335fef1b
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54951896"
---
# <a name="idebugthread2getname"></a>IDebugThread2::GetName
Obtient le nom d’un thread.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetName (   
   BSTR* pbstrName  
);  
```  
  
```csharp  
int GetName (   
   out string pbstrName  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pbstrName`  
 [out] Retourne le nom du thread.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Le nom récupéré est toujours un nom qui peut être affiché et ce nom décrit le thread. Le nom de thread peut être dérivé d’une architecture d’exécution que prend en charge nommées threads, ou il peut être un nom dérivé le moteur de débogage. Vous pouvez également le nom du thread peut être défini par un appel à la [SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md) (méthode).  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md)