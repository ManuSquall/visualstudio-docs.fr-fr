---
title: 'IDebugComPlusSymbolProvider :: UnloadSymbols | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- UnloadSymbols
- IDebugComPlusSymbolProvider::UnloadSymbols
ms.assetid: 53e3ddc1-ab47-4097-8fef-b26e5504b37a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0e826f8190650eed26228b9ce54b7128139f981a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99842483"
---
# <a name="idebugcomplussymbolproviderunloadsymbols"></a>IDebugComPlusSymbolProvider::UnloadSymbols
Décharge les symboles de débogage pour le module spécifié à partir de la mémoire.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT UnloadSymbols(
    ULONG32 ulAppDomainID,
    GUID    guidModule
);
```

```csharp
int UnloadSymbols(
    uint ulAppDomainID,
    Guid guidModule
);
```

## <a name="parameters"></a>Paramètres
`ulAppDomainID`\
dans Identificateur du domaine d’application.

`guidModule`\
dans Identificateur unique du module.

## <a name="return-value"></a>Valeur de retour
En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="example"></a>Exemple
L’exemple suivant montre comment implémenter cette méthode pour un objet **CDebugSymbolProvider** qui expose l’interface [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) .

```cpp
HRESULT CDebugSymbolProvider::UnloadSymbols(
    ULONG32 ulAppDomainID,
    GUID guidModule
)
{
    HRESULT hr = S_OK;
    CComPtr<CModule> pmodule;
    Module_ID idModule(ulAppDomainID, guidModule);

    METHOD_ENTRY( CDebugSymbolProvider::UnloadSymbols );

#if DEBUG

    DebugVerifyModules();
#endif

    IfFailGo( GetModule( idModule, &pmodule ) );

#if DEBUG

    DebugVerifyModules();
#endif

    RemoveModule( pmodule );
    pmodule->Cleanup();

Error:
#if DEBUG

    DebugVerifyModules();
#endif

    METHOD_EXIT( CDebugSymbolProvider::UnloadSymbols, hr );

    return hr;
}
```

## <a name="see-also"></a>Voir aussi
- [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)
