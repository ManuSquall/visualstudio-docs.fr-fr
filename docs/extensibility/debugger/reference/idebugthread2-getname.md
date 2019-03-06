---
title: IDebugThread2::GetName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: 04a76c88e5fd3eee146f6c174087298bac2b6974
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56679903"
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
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md)