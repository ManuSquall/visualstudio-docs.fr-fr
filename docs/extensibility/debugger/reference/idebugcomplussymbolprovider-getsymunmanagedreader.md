---
title: IDebugComPlusSymbolProvider::GetSymUnmanagedReader | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugComPlusSymbolProvider::GetSymUnmanagedReader
- GetSymUnmanagedReader
ms.assetid: 8f1c1627-217f-4405-8141-7a2eb80310a5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0ebb8d92e552ef9052ad4878802ded05f5bb62dc
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66336748"
---
# <a name="idebugcomplussymbolprovidergetsymunmanagedreader"></a>IDebugComPlusSymbolProvider::GetSymUnmanagedReader
Récupère le lecteur de symboles à utiliser par le code non managé.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetSymUnmanagedReader(
    ULONG32    ulAppDomainID,
    GUID       guidModule,
    IUnknown** ppSymUnmanagedReader
);
```

```csharp
int GetSymUnmanagedReader(
    uint       ulAppDomainID,
    Guid       guidModule,
    out object ppSymUnmanagedReader
);
```

## <a name="parameters"></a>Paramètres
`ulAppDomainID`\
[in] Identificateur du domaine d’application.

`guidModule`\
[in] Identificateur unique du module.

`ppSymUnmanagedReader`\
[out] Retourne l’objet qui représente le lecteur de symboles.

## <a name="return-value"></a>Valeur de retour
En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.

## <a name="example"></a>Exemple
L’exemple suivant montre comment implémenter cette méthode pour un **CDebugSymbolProvider** objet qui expose le [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) interface.

```cpp
HRESULT CDebugSymbolProvider::GetSymUnmanagedReader(
    ULONG32 ulAppDomainID,
    GUID guidModule,
    IUnknown ** ppSymUnmanagedReader
)
{
    HRESULT hr = S_OK;
    CComPtr<CModule> pModule;
    Module_ID idModule(ulAppDomainID, guidModule);

    METHOD_ENTRY( CDebugSymbolProvider::GetSymUnmanagedReader );

    IfFailGo( GetModule( idModule, &pModule ) );
    IfFailGo( pModule->GetSymReader((ISymUnmanagedReader**) ppSymUnmanagedReader) );

Error:

    METHOD_EXIT( CDebugSymbolProvider::GetSymUnmanagedReader, hr );
    return hr;
}
```

## <a name="see-also"></a>Voir aussi
- [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)
