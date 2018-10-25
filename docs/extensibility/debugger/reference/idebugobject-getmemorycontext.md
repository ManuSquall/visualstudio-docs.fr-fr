---
title: IDebugObject::GetMemoryContext | Microsoft Docs
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
ms.openlocfilehash: 657b3b214cd099cf6359b7466c58a1311a8b1677
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49869884"
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
 Le contexte de la mémoire retournée Spécifie l’adresse de la valeur telle que représentée par ce [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) objet.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)