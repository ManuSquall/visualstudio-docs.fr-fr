---
title: IDebugBinder3::GetMemoryObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugBinder3::GetMemoryObject
helpviewer_keywords:
- IDebugBinder3::GetMemoryObject method
ms.assetid: 71d959c7-45df-485f-b0ee-f1c0439d54fb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a646a5321b9a6b7ccf000ecba409434efcc3aea0
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53900754"
---
# <a name="idebugbinder3getmemoryobject"></a>IDebugBinder3::GetMemoryObject
Cette méthode récupère un objet de mémoire qui représente cet objet est lié à la mémoire.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetMemoryObject(  
   IDebugField*   pField,  
   UINT64         uConstant,  
   IDebugObject** ppObject  
);  
```  
  
```csharp  
int GetMemoryObject(  
   IDebugField      pField,  
   long             uConstant,  
   out IDebugObject ppObject  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pField`  
 [in] Spécifie le champ pour obtenir l’objet de mémoire pour.  
  
 `uConstant`  
 [in] Représente une adresse mémoire ou une valeur pour une valeur constante.  
  
 `ppObject`  
 [out] Un [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) représentant cet objet est lié à la mémoire.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)