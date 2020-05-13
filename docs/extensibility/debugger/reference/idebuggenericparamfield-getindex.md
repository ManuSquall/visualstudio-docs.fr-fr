---
title: IDebugGenericParamField:GetIndex ( Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugGenericParamField::GetIndex
ms.assetid: 8e0bdb26-1247-44d9-8d80-ec6e35187fb4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6b31acd57685058795186fcecb73164218d5ad15
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727988"
---
# <a name="idebuggenericparamfieldgetindex"></a>IDebugGenericParamField::GetIndex
Récupère l’index de ce paramètre générique.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetIndex(
    DWORD* pIndex
);
```

```csharp
int GetIndex(
    out uint pIndex
);
```

## <a name="parameters"></a>Paramètres
`pIndex`\
[out] Valeur indicative de ce paramètre générique.

## <a name="return-value"></a>Valeur de retour
En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
Par exemple, pour Dictionary(K,V), K est l’index 0, V est l’index 1.

## <a name="example"></a>Exemple
L’exemple suivant montre comment implémenter cette méthode pour un objet **CDebugGenericParamFieldType** qui expose [l’interface IDebugGenericParamField.](../../../extensibility/debugger/reference/idebuggenericparamfield.md)

```cpp
HRESULT CDebugGenericParamFieldType::GetIndex(DWORD* pIndex)
{
    HRESULT hr = S_OK;

    METHOD_ENTRY( CDebugGenericParamFieldType::GetIndex );

    IfFalseGo(pIndex, E_INVALIDARG );
    IfFailGo( this->LoadProps() );
    *pIndex = m_index;

Error:

    METHOD_EXIT( CDebugGenericParamFieldType::GetIndex, hr );
    return hr;
}
```

## <a name="see-also"></a>Voir aussi
- [IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md)
