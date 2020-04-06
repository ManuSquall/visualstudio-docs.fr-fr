---
title: IDebugMethodField::EnumLocals Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumLocals
helpviewer_keywords:
- IDebugMethodField::EnumLocals method
ms.assetid: b0456a6d-2b96-49e2-a871-516571b4f6a5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 08872160860d0d442f9807705dea70190dff9b28
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727208"
---
# <a name="idebugmethodfieldenumlocals"></a>IDebugMethodField::EnumLocals
Crée un enumérateur pour certaines variables locales de la méthode.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT EnumLocals(
    IDebugAddress*     pAddress,
    IEnumDebugFields** ppLocals
);
```

```csharp
int EnumLocals(
    IDebugAddress        pAddress,
    out IEnumDebugFields ppLocals
);
```

## <a name="parameters"></a>Paramètres
`pAddress`\
[dans] Un objet [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) représentant l’adresse de débogé qui sélectionne le contexte ou la portée à partir de laquelle obtenir les habitants.

`ppLocals`\
[out] Retourne un objet [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) représentant une liste des habitants; autrement, retourne une valeur nulle s’il n’y a pas d’habitants.

## <a name="return-value"></a>Valeur de retour
En cas de succès, les retours S_OK ou retournent S_FALSE s’il n’y a pas d’habitants. Sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
Seules les variables définies dans le bloc qui contient l’adresse de débaillement donnée sont énumérées. Si tous les habitants, y compris les habitants générés par les compilateur, sont nécessaires, appelez la méthode [EnumAllLocals.](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md)

Une méthode peut contenir plusieurs contextes ou blocs d’établissement de la portée. Par exemple, la méthode artificielle suivante contient trois portées, les deux blocs intérieurs et le corps de méthode lui-même.

```csharp
public void func(int index)
{
    // Method body scope
    int a = 0;
    if (index == 1)
    {
        // Inner scope 1
        int temp1 = a;
    }
    else
    {
        // Inner scope 2
        int temp2 = a;
    }
}
```

[L’objet IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) représente la `func` méthode elle-même. Appeler `EnumLocals` la méthode avec un [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) réglé à l’adresse `Inner Scope 1` retourne un recensement contenant la `temp1` variable, par exemple.

## <a name="see-also"></a>Voir aussi
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md)
