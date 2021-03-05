---
description: Charger les symboles de débogage à partir d’un flux de données en fonction de l’objet ICorDebugModule.
title: IDebugComPlusSymbolProvider2::LoadSymbolsFromStreamWithCorModule
titleSuffix: ''
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugComPlusSymbolProvider2::LoadSymbolsFromStreamWithCorModule
- LoadSymbolsFromStreamWithCorModule
ms.assetid: f79b894f-52c4-43c2-9a68-c71536451f6c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 29ae5004869a6146e3a8bb22f2569d1cc4cd758f
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102163354"
---
# <a name="idebugcomplussymbolprovider2loadsymbolsfromstreamwithcormodule"></a>IDebugComPlusSymbolProvider2::LoadSymbolsFromStreamWithCorModule
Charger les symboles de débogage à partir d’un flux de données en fonction de l’objet **ICorDebugModule** .

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT LoadSymbolsFromStreamWithCorModule(
    ULONG32   ulAppDomainID,
    GUID      guidModule,
    ULONGLONG baseAddress,
    IUnknown* pUnkMetadataImport,
    IUnknown* pUnkCorDebugModule,
    IStream*  pStream
);
```

```csharp
int LoadSymbolsFromStreamWithCorModule(
    uint    ulAppDomainID,
    Guid    guidModule,
    ulong   baseAddress,
    object  pUnkMetadataImport,
    object  pUnkCorDebugModule,
    IStream pStream
);
```

## <a name="parameters"></a>Paramètres
`ulAppDomainID`\
dans Identificateur du domaine d’application.

`guidModule`\
dans Identificateur unique du module.

`baseAddress`\
dans Adresse mémoire de base.

`pUnkMetadataImport`\
dans Objet qui contient les métadonnées de symbole.

`pUnkCorDebugModule`\
dans Objet qui implémente l' [interface ICorDebugModule](/dotnet/framework/unmanaged-api/debugging/icordebugmodule-interface).

`pStream`\
dans Flux de données qui contient les symboles de débogage à charger.

## <a name="return-value"></a>Valeur renvoyée
En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="example"></a>Exemple
L’exemple suivant montre comment implémenter cette méthode pour un objet **CDebugSymbolProvider** qui expose l’interface [IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md) .

```cpp
HRESULT CDebugSymbolProvider::LoadSymbolsFromStreamWithCorModule(
    ULONG32 ulAppDomainID,
    GUID guidModule,
    ULONGLONG baseOffset,
    IUnknown* pUnkMetadataImport,
    IUnknown* pUnkCorDebugModule,
    IStream* pStream
)
{
    CAutoLock Lock(this);

    HRESULT hr = S_OK;
    CComPtr<IMetaDataImport> pMetadata;
    CComPtr<ICorDebugModule> pCorModule;

    CModule* pmodule = NULL;
    CModule* pmoduleNew = NULL;
    bool fAlreadyLoaded = false;
    Module_ID idModule(ulAppDomainID, guidModule);
    DWORD dwCurrentState = 0;

    ASSERT(IsValidObjectPtr(this, CDebugSymbolProvider));
    ASSERT(IsValidInterfacePtr(pUnkMetadataImport, IUnknown));

    METHOD_ENTRY( CDebugSymbolProvider::LoadSymbolsFromStream );

    IfFalseGo( pUnkMetadataImport, E_INVALIDARG );
    IfFalseGo( pUnkCorDebugModule, E_INVALIDARG );

    IfFailGo( pUnkMetadataImport->QueryInterface( IID_IMetaDataImport,
              (void**)&pMetadata) );

    IfFailGo( pUnkCorDebugModule->QueryInterface( IID_ICorDebugModule,
              (void**)&pCorModule) );

    ASSERT(guidModule != GUID_NULL);

    fAlreadyLoaded = GetModule( idModule, &pmodule ) == S_OK;

    IfNullGo( pmoduleNew = new CModule, E_OUTOFMEMORY );

    dwCurrentState = m_pSymProvGroup ? m_pSymProvGroup->GetCurrentState() : 0;

    IfFailGo( pmoduleNew->Create( idModule,
                                  dwCurrentState,
                                  pMetadata,
                                  pCorModule,
                                  pStream,
                                  baseOffset ) );

    if (fAlreadyLoaded)
    {
        IfFailGo(pmoduleNew->AddEquivalentModulesFrom(pmodule));
        RemoveModule(pmodule);
    }

    IfFailGo( AddModule( pmoduleNew ) );

Error:

    RELEASE (pmodule);
    RELEASE (pmoduleNew);

    METHOD_EXIT( CDebugSymbolProvider::LoadSymbolsFromStream, hr );

    return hr;
}
```

## <a name="see-also"></a>Voir aussi
- [IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md)
