---
title: IDebugObject::GetMemoryContext | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugObject::GetMemoryContext
helpviewer_keywords:
- IDebugObject::GetMemoryContext method
ms.assetid: 6760a0d3-a898-4e81-b68f-c45c584b225b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3befdcb9991f3623e78398faef7647a873d7a702
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="idebugobjectgetmemorycontext"></a>IDebugObject::GetMemoryContext
Obtient le contexte de la mémoire qui représente l’adresse de la valeur de l’objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetMemoryContext(   
   IDebugMemoryContext2** pContext  
);  
```  
  
```csharp  
int GetMemoryContext(  
   ref IDebugMemoryContext2 pContext  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pContext`  
 [out] Retourne un [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) objet représentant l’adresse de la valeur de l’objet.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Le contexte de la mémoire retournée Spécifie l’adresse de la valeur représentée par ce [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) objet.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)