---
title: IDebugSymbolProvider - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider
helpviewer_keywords:
- IDebugSymbolProvider interface
ms.assetid: df5f095f-1dee-46f9-84cf-92417c71d5fb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 11e180288a9312d9af5a3d3b1bd63d8f2266f581
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719174"
---
# <a name="idebugsymbolprovider"></a>IDebugSymbolProvider
Cette interface représente un fournisseur de symboles qui fournit des symboles et des types, les retournant comme champs.

## <a name="syntax"></a>Syntaxe

```
IDebugSymbolProvider : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
Un fournisseur de symboles doit implémenter cette interface pour fournir des informations de symbole et de type à un évaluateur d’expression.

## <a name="notes-for-callers"></a>Notes pour les appelants
Cette interface est obtenue en `CoCreateInstance` utilisant la fonction de COM (pour les fournisseurs de symboles non gérés) ou en chargeant l’assemblage de code géré approprié et en instantanéisant le fournisseur de symboles en fonction des informations trouvées dans cet assemblage. Le moteur de déboçons instantanément le fournisseur de symboles de travailler en coordination avec l’évaluateur d’expression. Voir l’exemple d’une approche pour instantanéler cette interface.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
Le tableau suivant montre `IDebugSymbolProvider`les méthodes de .

|Méthode|Description|
|------------|-----------------|
|`Initialize`|Action déconseillée. Ne pas utiliser.|
|`Uninitialize`|Action déconseillée. Ne pas utiliser.|
|[GetContainerField](../../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md)|Obtient le champ qui contient l’adresse de débogé.|
|`GetField`|Action déconseillée. Ne pas utiliser.|
|[GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)|Cartographiez une position de document dans un tableau d’adresses de débogé.|
|[GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)|Cartographiez un contexte de document dans un tableau d’adresses de débogé.|
|[GetContextFromAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getcontextfromaddress.md)|Cartographiez une adresse de débogé dans un contexte de document.|
|[GetLanguage](../../../extensibility/debugger/reference/idebugsymbolprovider-getlanguage.md)|Habite le langage pour compiler le code à l’adresse de débogé.|
|`GetGlobalContainer`|Action déconseillée. Ne pas utiliser.|
|[GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md)|Obtient le champ représentant un nom de méthode entièrement qualifié.|
|[GetClassTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getclasstypebyname.md)|Obtient le type de champ de classe représentant un nom de classe entièrement qualifié.|
|[GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md)|Crée un enumérateur pour les espaces de nom associés à l’adresse de débogé.|
|[GetTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-gettypebyname.md)|Cartographie un nom de symbole à un type de symbole.|
|[GetNextAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnextaddress.md)|Obtient l’adresse de débog qui suit une adresse de débogé donnée dans une méthode.|

## <a name="remarks"></a>Notes
Cette interface cartographie les positions de document dans les adresses de déboiffées et vice versa.

## <a name="requirements"></a>Spécifications
En-tête: sh.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Exemple
Cet exemple montre comment instantanéiser le fournisseur de symboles, compte tenu de son GUID (un moteur de débogé doit connaître cette valeur).

```cpp
// A debug engine uses its own symbol provider and would know the GUID
// of that provider.
IDebugSymbolProvider *GetSymbolProvider(GUID *pSymbolProviderGuid)
{
    // This is typically defined globally. For this example, it is
    // defined here.
    static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0Exp";
    IDebugSymbolProvider *pProvider = NULL;
    if (pSymbolProviderGuid != NULL) {
        CLSID clsidProvider = { 0 };
        ::GetSPMetric(*pSymbolProviderGuid,
                      storetypeFile,
                      metricCLSID,
                      &clsidProvider,
                      strRegistrationRoot);
        if (IsEqualGUID(clsidProvider,GUID_NULL)) {
            // No file type provider, try metadata provider.
            ::GetSPMetric(*pSymbolProviderGuid,
                          ::storetypeMetadata,
                          metricCLSID,
                          &clsidProvider,
                          strRegistrationRoot);
        }
        if (!IsEqualGUID(clsidProvider,GUID_NULL)) {
            CComPtr<IDebugSymbolProvider> spSymbolProvider;
            spSymbolProvider.CoCreateInstance(clsidProvider);
            if (spSymbolProvider != NULL) {
                pProvider = spSymbolProvider.Detach();
            }
        }
    }
    return(pProvider);
}
```

## <a name="see-also"></a>Voir aussi
- [Interfaces des fournisseurs de symboles](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
