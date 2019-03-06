---
title: IEnumDebugFields::Reset | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugFields::Reset
helpviewer_keywords:
- IEnumDebugFields::Reset method
ms.assetid: 38ff61e4-0120-42e8-971a-16be6050b425
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a6bf669261a3ece31e452227b7c93d7ce8bf07c1
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56697713"
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
 Aucun.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 Une fois que cette méthode est appelée, l’appel suivant à [suivant](../../../extensibility/debugger/reference/ienumdebugfields-next.md) retourne le premier élément de l’énumération.

## <a name="see-also"></a>Voir aussi
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [Next](../../../extensibility/debugger/reference/ienumdebugfields-next.md)