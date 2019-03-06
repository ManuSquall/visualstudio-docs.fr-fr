---
title: IDebugAlias::GetObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAlias::GetObject
helpviewer_keywords:
- IDebugAlias::GetObject method
ms.assetid: 97bc3af6-6e55-4940-8a6d-692c61257806
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b2c32061ee330d4e8054e20971890d7d0d93a799
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56704122"
---
# <a name="idebugaliasgetobject"></a>IDebugAlias::GetObject
Obtient l’objet auquel cet alias est destinée.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetObject(
   IDebugObject2** ppObject
);
```

```csharp
int GetObject(
   Out IDebugObject2 ppObject
)
```

#### <a name="parameters"></a>Paramètres
 `ppObject`

 [out] Le [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) représente cet alias.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.

## <a name="see-also"></a>Voir aussi
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)