---
title: IDebugGenericParamField::GetIndex | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugGenericParamField::GetIndex
ms.assetid: 8e0bdb26-1247-44d9-8d80-ec6e35187fb4
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 77c5a2ccb8ff81cade0a110f8226f54a04ef65ea
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62919084"
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

#### <a name="parameters"></a>Paramètres
`pIndex`

 [out] Valeur d’index de ce paramètre générique.

## <a name="return-value"></a>Valeur de retour
En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
Par exemple, pour Dictionary(K,V), est l’index 0 K, V est l’index 1.

## <a name="example"></a>Exemple
L’exemple suivant montre comment implémenter cette méthode pour un **CDebugGenericParamFieldType** objet qui expose le [IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md) interface.

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
