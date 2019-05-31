---
title: IEnumDebugFields::Reset | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugFields::Reset
helpviewer_keywords:
- IEnumDebugFields::Reset method
ms.assetid: 38ff61e4-0120-42e8-971a-16be6050b425
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c50a5e2ed55bf1550ca4a70bc566fb2504b100a3
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66350412"
---
# <a name="ienumdebugfieldsreset"></a>IEnumDebugFields::Reset
Cette méthode réinitialise l’énumération au premier élément.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Reset(void);
```

```csharp
int Reset();
```

#### <a name="parameters"></a>Paramètres
 None

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 Une fois que cette méthode est appelée, l’appel suivant à [suivant](../../../extensibility/debugger/reference/ienumdebugfields-next.md) retourne le premier élément de l’énumération.

## <a name="see-also"></a>Voir aussi
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [Next](../../../extensibility/debugger/reference/ienumdebugfields-next.md)