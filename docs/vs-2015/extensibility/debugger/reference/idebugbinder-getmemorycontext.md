---
title: IDebugBinder::GetMemoryContext | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugBinder::GetMemoryContext
helpviewer_keywords:
- IDebugBinder::GetMemoryContext method
ms.assetid: 801c5b60-acff-4822-b23d-e9c7bbca8a0f
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: db8d8d820c43d17194feda0bf228227a279dccc6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62423411"
---
# <a name="idebugbindergetmemorycontext"></a>IDebugBinder::GetMemoryContext
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Cette méthode convertit une adresse mémoire ou un emplacement de l’objet à un contexte de la mémoire.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
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
