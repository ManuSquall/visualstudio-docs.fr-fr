---
title: IDebugSymbolProvider | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80719174"
---
# <a name="idebugsymbolprovider"></a>IDebugSymbolProvider
Cette interface représente un fournisseur de symboles qui fournit des symboles et des types, qui les retournent sous forme de champs.

## <a name="syntax"></a>Syntaxe

```
IDebugSymbolProvider : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
Un fournisseur de symboles doit implémenter cette interface pour fournir des informations de type et de symbole à un évaluateur d’expression.

## <a name="notes-for-callers"></a>Notes pour les appelants
Cette interface est obtenue à l’aide de `CoCreateInstance` la fonction de com (pour les fournisseurs de symboles non managés) ou en chargeant l’assembly de code managé approprié et en instanciant le fournisseur de symboles en fonction des informations trouvées dans cet assembly. Le moteur de débogage instancie le fournisseur de symboles pour fonctionner en coordination avec l’évaluateur d’expression. Consultez l’exemple pour une approche de l’instanciation de cette interface.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
Le tableau suivant présente les méthodes de `IDebugSymbolProvider` .

|Méthode|Description|
|------------|-----------------|
|`Initialize`|Obsolète. Ne pas utiliser.|
|`Uninitialize`|Obsolète. Ne pas utiliser.|
|[GetContainerField](../../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md)|Obtient le champ qui contient l’adresse de débogage.|
|`GetField`|Obsolète. Ne pas utiliser.|
|[GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)|Mappe une position de document à un tableau d’adresses de débogage.|
|[GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)|Mappe un contexte de document à un tableau d’adresses de débogage.|
|[GetContextFromAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getcontextfromaddress.md)|Mappe une adresse de débogage dans un contexte de document.|
|[GetLanguage](../../../extensibility/debugger/reference/idebugsymbolprovider-getlanguage.md)|Obtient le langage utilisé pour compiler le code à l’adresse de débogage.|
|`GetGlobalContainer`|Obsolète. Ne pas utiliser.|
|[GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md)|Obtient le champ représentant un nom de méthode complet.|
|[GetClassTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getclasstypebyname.md)|Obtient le type de champ de classe qui représente un nom de classe complet.|
|[GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md)|Crée un énumérateur pour les espaces de noms associés à l’adresse de débogage.|
|[GetTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-gettypebyname.md)|Mappe un nom de symbole à un type de symbole.|
|[GetNextAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnextaddress.md)|Obtient l’adresse de débogage qui suit une adresse de débogage donnée dans une méthode.|

## <a name="remarks"></a>Notes
Cette interface mappe les positions de document en adresses de débogage et vice versa.

## <a name="requirements"></a>Configuration requise
En-tête : SH. h

Espace de noms : Microsoft. VisualStudio. Debugger. Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Exemple
Cet exemple montre comment instancier le fournisseur de symboles, en fonction de son GUID (un moteur de débogage doit connaître cette valeur).

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
