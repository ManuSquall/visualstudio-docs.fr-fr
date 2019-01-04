---
title: IDebugBinder::GetMemoryContext | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugBinder::GetMemoryContext
helpviewer_keywords:
- IDebugBinder::GetMemoryContext method
ms.assetid: 801c5b60-acff-4822-b23d-e9c7bbca8a0f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6a613efac19f9b84cc5b74cd502854892fa43694
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53952366"
---
# <a name="idebugbindergetmemorycontext"></a>IDebugBinder::GetMemoryContext
Cette méthode convertit une adresse mémoire ou un emplacement de l’objet à un contexte de la mémoire.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetMemoryContext(   
   IDebugField*           pField,  
   DWORD                  dwConstant,  
   IDebugMemoryContext2** ppMemCxt  
);  
```  
  
```csharp  
int GetMemoryContext(  
   IDebugField              pField,   
   uint                     dwConstant,   
   out IDebugMemoryContext2 ppMemCxt  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pField`  
 [in] Un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) décrivant l’objet à localiser. Si `NULL`, puis utilisez `dwConstant` à la place.  
  
 `dwConstant`  
 [in] Une adresse mémoire constante, telles que 0x5000.  
  
 `ppMemCxt`  
 [out] Retourne le [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) interface qui représente l’adresse de l’objet ou l’adresse en mémoire.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)