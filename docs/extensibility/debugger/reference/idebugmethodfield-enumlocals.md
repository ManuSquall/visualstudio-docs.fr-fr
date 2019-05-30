---
title: IDebugMethodField::EnumLocals | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumLocals
helpviewer_keywords:
- IDebugMethodField::EnumLocals method
ms.assetid: b0456a6d-2b96-49e2-a871-516571b4f6a5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bd4e2ffcaa66af58d3cc7ab57420de32d77eec92
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66346771"
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
[in] Un [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) objet représentant l’adresse de débogage qui sélectionne le contexte ou la portée à partir duquel obtenir les variables locales.

`ppLocals`\
[out] Retourne un [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) représentant une liste des variables locales de l’objet ; sinon, retourne une valeur null s’il en existe pas de variables locales.

## <a name="return-value"></a>Valeur de retour
En cas de réussite, retourne S_OK, ou retourne S_FALSE s’il n’y a aucuns variables locales. Sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
Uniquement les variables définies dans le bloc qui contient l’adresse de débogage donné sont énumérés. Si toutes les variables locales, y compris les variables locales générées par le compilateur sont nécessaires, appelez le [EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md) (méthode).

Une méthode peut contenir plusieurs contextes d’étendue ou de blocs. Par exemple, la méthode fictive suivante contient trois étendues, les deux blocs internes et le corps de la méthode.

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

Le [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) objet représente le `func` méthode proprement dite. Appelant le `EnumLocals` méthode avec un [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) défini sur le `Inner Scope 1` adresse retourne une énumération contenant le `temp1` variable, par exemple.

## <a name="see-also"></a>Voir aussi
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md)
