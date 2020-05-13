---
title: IDebugEnumField::GetStringFromValue ( Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEnumField::GetStringFromValue
helpviewer_keywords:
- IDebugEnumField::GetStringFromValue method
ms.assetid: 5f95fd0c-fdce-497f-9f54-2ad8749494e9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5de59c573f7e233ea2aacb0dfa38826051c59373
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730290"
---
# <a name="idebugenumfieldgetstringfromvalue"></a>IDebugEnumField::GetStringFromValue
Cette méthode obtient le nom de la constante d’énumération compte tenu de sa valeur.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetStringFromValue(
   ULONGLONG value,
   BSTR*     pbstrValue
);
```

```csharp
int GetStringFromValue(
   ulong      value,
   out string pbstrValue
);
```

## <a name="parameters"></a>Paramètres
`value`\
[dans] La valeur pour laquelle obtenir le nom de la constante de recensement.

`pbstrValue`\
[out] Retourne le nom de la constante de recensement.

## <a name="return-value"></a>Valeur de retour
 En cas `S_OK`de succès, les retours; autrement, `S_FALSE` retourne si la valeur n’a pas de nom associé, ou retourne un code d’erreur.

## <a name="remarks"></a>Notes
 S’il y a plus d’un nom associé à la même valeur, le prénom défini dans le recensement sera retourné.

## <a name="see-also"></a>Voir aussi
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
