---
title: IDebugSymbolProvider | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugSymbolProvider
helpviewer_keywords:
- IDebugSymbolProvider interface
ms.assetid: df5f095f-1dee-46f9-84cf-92417c71d5fb
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 2fbafdf4e2227d7c4d4a69b8b310cf082ac72ee0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="idebugsymbolprovider"></a>IDebugSymbolProvider
Cette interface représente un fournisseur de symboles qui fournit des types, les retourner en tant que champs et des symboles.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugSymbolProvider : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 Un fournisseur de symbole doit implémenter cette interface pour fournir les symboles et les informations de type pour un évaluateur d’expression.  
  
## <a name="notes-for-callers"></a>Remarques pour les appelants  
 Cette interface est obtenue à l’aide de COM `CoCreateInstance` (fonction) (pour les fournisseurs de symbole non managé) ou en chargeant les assembly de code et l’instanciation du fournisseur de symboles selon les informations de cet assembly. Le moteur de débogage instancie le fournisseur de symbole à travailler en coordination avec l’évaluateur d’expression. Consultez l’exemple pour une approche de l’instanciation de cette interface.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IDebugSymbolProvider`.  
  
|Méthode|Description|  
|------------|-----------------|  
|`Initialize`|Obsolète. Ne pas utiliser.|  
|`Uninitialize`|Obsolète. Ne pas utiliser.|  
|[GetContainerField](../../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md)|Obtient le champ qui contient l’adresse de débogage.|  
|`GetField`|Obsolète. Ne pas utiliser.|  
|[GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)|Mappe une position de document dans un tableau d’adresses de débogage.|  
|[GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)|Mappe un contexte de document dans un tableau d’adresses de débogage.|  
|[GetContextFromAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getcontextfromaddress.md)|Mappe une adresse de débogage dans un contexte de document.|  
|[GetLanguage](../../../extensibility/debugger/reference/idebugsymbolprovider-getlanguage.md)|Obtient la langue utilisée pour compiler le code à l’adresse de débogage.|  
|`GetGlobalContainer`|Obsolète. Ne pas utiliser.|  
|[GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md)|Obtient le champ qui représente un nom qualifié complet de la méthode.|  
|[GetClassTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getclasstypebyname.md)|Obtient le type de champ de classe représentant un nom de classe qualifié complet.|  
|[GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md)|Crée un énumérateur pour les espaces de noms associé à l’adresse de débogage.|  
|[GetTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-gettypebyname.md)|Mappe un nom de symbole pour un type de symbole.|  
|[GetNextAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnextaddress.md)|Obtient l’adresse de débogage qui suit une adresse donnée debug dans une méthode.|  
  
## <a name="remarks"></a>Notes  
 Cette interface mappe les positions de document dans les adresses de débogage et vice versa.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : sh.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="example"></a>Exemple  
 Cet exemple montre comment instancier le fournisseur de symboles, étant donné son GUID (un moteur de débogage doit connaître cette valeur).  
  
```cpp  
// A debug engine uses its own symbol provider and would know the GUID  
// of that provider.  
IDebugSymbolProvider *GetSymbolProvider(GUID *pSymbolProviderGuid)  
{  
    // This is typically defined globally.  For this example, it is  
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
 [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)