---
title: IDebugGenericParamField::GetFlags | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetFlags
- IDebugGenericParamField::GetFlags
ms.assetid: adcbbca1-8960-4c88-86b0-8b9467056c97
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a5f03eae07ff02d69f304d1a9bb9deaa668bf521
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56689640"
---
# <a name="idebuggenericparamfieldgetflags"></a>IDebugGenericParamField::GetFlags
Récupère les indicateurs pour ce paramètre générique.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetFlags(
    DWORD* pdwFlags
);
```

```csharp
int GetFlags(
    ref uint pdwFlags
);
```

#### <a name="parameters"></a>Paramètres
`pdwFlags`

 [out] Retourne les indicateurs pour ce paramètre générique.

## <a name="return-value"></a>Valeur de retour
En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
Ces indicateurs contiennent des informations sur les différentes contraintes spéciales.

## <a name="example"></a>Exemple
L’exemple suivant montre comment implémenter cette méthode pour un **CDebugGenericParamFieldType** objet qui expose le [IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md) interface.

```cpp
HRESULT CDebugGenericParamFieldType::GetFlags(DWORD *pdwFlags)
{
    HRESULT hr = S_OK;

    METHOD_ENTRY( CDebugGenericParamFieldType::GetFlags );

    IfFalseGo( pdwFlags, E_INVALIDARG );
    IfFailGo( this->LoadProps() );
    *pdwFlags = m_dwFlags;

Error:

    METHOD_EXIT( CDebugGenericParamFieldType::GetFlags, hr );
    return hr;
}
```

## <a name="see-also"></a>Voir aussi
- [IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md)
