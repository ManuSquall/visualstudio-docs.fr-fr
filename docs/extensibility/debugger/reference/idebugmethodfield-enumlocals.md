---
description: Crée un énumérateur pour les variables locales sélectionnées de la méthode.
title: 'IDebugMethodField :: EnumLocals | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumLocals
helpviewer_keywords:
- IDebugMethodField::EnumLocals method
ms.assetid: b0456a6d-2b96-49e2-a871-516571b4f6a5
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d99b6e4b3cf30cccd4a2785f3712b34d9471bdd8
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166331"
---
# <a name="idebugmethodfieldenumlocals"></a>IDebugMethodField::EnumLocals
Crée un énumérateur pour les variables locales sélectionnées de la méthode.

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
dans Objet [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) qui représente l’adresse de débogage qui sélectionne le contexte ou la portée à partir duquel les variables locales doivent être extraites.

`ppLocals`\
à Retourne un objet [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) représentant une liste de variables locales ; Sinon, retourne une valeur null s’il n’y a pas de variables locales.

## <a name="return-value"></a>Valeur renvoyée
En cas de réussite, retourne S_OK ou retourne S_FALSE s’il n’y a pas de variables locales. Sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
Seules les variables définies dans le bloc qui contient l’adresse de débogage donnée sont énumérées. Si tous les paramètres régionaux, y compris les variables locales générées par le compilateur, sont nécessaires, appelez la méthode [EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md) .

Une méthode peut contenir plusieurs contextes ou blocs d’étendue. Par exemple, la méthode fictif suivante contient trois portées, les deux blocs internes et le corps de méthode lui-même.

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

L’objet [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) représente la `func` méthode elle-même. L’appel de la `EnumLocals` méthode avec un [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) défini sur l' `Inner Scope 1` adresse retourne une énumération contenant la `temp1` variable, par exemple.

## <a name="see-also"></a>Voir aussi
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md)
