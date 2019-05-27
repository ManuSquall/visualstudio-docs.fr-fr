---
title: IDebugComPlusSymbolProvider::LoadSymbols | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- LoadSymbols
- IDebugComPlusSymbolProvider::LoadSymbols
ms.assetid: 3499680d-0b9a-4f20-8432-c89a41b29b87
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fa910e483e4c743058d3671d8b873c5f88b4269e
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66206158"
---
# <a name="idebugcomplussymbolproviderloadsymbols"></a>IDebugComPlusSymbolProvider::LoadSymbols
Charge les symboles de débogage spécifié dans la mémoire.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT LoadSymbols(
    ULONG32   ulAppDomainID,
    GUID      guidModule,
    ULONGLONG baseAddress,
    IUnknown* pUnkMetadataImport,
    BSTR      bstrModuleName,
    BSTR      bstrSymSearchPath
);
```

```csharp
int LoadSymbols(
    uint   ulAppDomainID,
    Guid   guidModule,
    ulong  baseAddress,
    object pUnkMetadataImport,
    string bstrModuleName,
    string bstrSymSearchPath
);
```

## <a name="parameters"></a>Paramètres
`ulAppDomainID`\
[in] Identificateur du domaine d’application.

`guidModule`\
[in] Identificateur unique de le mondule.

`baseAddress`\
[in] Adresse mémoire de base.

`pUnkMetadataImport`\
[in] Objet qui contient les métadonnées de symbole.

`bstrModuleName`\
[in] Nom du module.

`bstrSymSearchPath`\
[in] Chemin d’accès pour rechercher le fichier de symboles.

## <a name="return-value"></a>Valeur de retour
En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.

## <a name="example"></a>Exemple
L’exemple suivant montre comment implémenter cette méthode pour un **CDebugSymbolProvider** objet qui expose le [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) interface.

```cpp
HRESULT CDebugSymbolProvider::LoadSymbols(
    ULONG32 ulAppDomainID,
    GUID guidModule,
    ULONGLONG baseOffset,
    IUnknown* _pMetadata,
    BSTR bstrModule,
    BSTR bstrSearchPath)
{
    return LoadSymbolsWithCorModule(ulAppDomainID, guidModule, baseOffset, _pMetadata, NULL, bstrModule, bstrSearchPath);
}
```

## <a name="see-also"></a>Voir aussi
- [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)
