---
description: Détermine si l’adresse de débogage spécifiée est un point de séquence.
title: 'IDebugComPlusSymbolProvider2 :: IsAddressSequencePoint | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugComPlusSymbolProvider2::IsAddressSequencePoint
- IsAddressSequencePoint
ms.assetid: 89b27c57-5295-428b-8229-a402500d8cd3
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 50e14f7e91457e2a7a0bd4719730e96d4019e82d
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102163380"
---
# <a name="idebugcomplussymbolprovider2isaddresssequencepoint"></a>IDebugComPlusSymbolProvider2::IsAddressSequencePoint
Détermine si l’adresse de débogage spécifiée est un point de séquence.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT IsAddressSequencePoint(
    IDebugAddress* pAddress
);
```

```csharp
int IsAddressSequencePoint(
    IDebugAddress pAddress
);
```

## <a name="parameters"></a>Paramètres
`pAddress`\
dans Adresse de débogage qui est représentée par l’interface [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) .

## <a name="return-value"></a>Valeur renvoyée
Si l’adresse de débogage est un point de séquence, retourne `S_OK` ; sinon, retourne `S_FALSE` .

## <a name="example"></a>Exemple
L’exemple suivant montre comment implémenter cette méthode pour un objet **CDebugSymbolProvider** qui expose l’interface [IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md) .

```cpp
HRESULT CDebugSymbolProvider::IsAddressSequencePoint(
    IDebugAddress* pAddress
)
{
    HRESULT hr = S_OK;
    CDEBUG_ADDRESS address;
    CComPtr<CModule> pModule;

    METHOD_ENTRY( CDebugSymbolProvider::LoadSymbol );

    IfFalseGo( pAddress, E_INVALIDARG );

    IfFailGo( pAddress->GetAddress( &address ) );

    ASSERT(address.addr.dwKind == ADDRESS_KIND_METADATA_METHOD);
    IfFalseGo( address.addr.dwKind == ADDRESS_KIND_METADATA_METHOD, S_FALSE );

    IfFailGo( GetModule( address.GetModule(), &pModule) );

    if (!pModule->IsSequencePoint( address.addr.addr.addrMethod.tokMethod,
                                   address.addr.addr.addrMethod.dwVersion,
                                   address.addr.addr.addrMethod.dwOffset ))
    {

        // S_FALSE indicates this is not a sequence point

        hr = S_FALSE;
    }

Error:

    METHOD_EXIT( CDebugSymbolProvider::LoadSymbol, hr );

    return hr;
}
```

## <a name="see-also"></a>Voir aussi
- [IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md)
