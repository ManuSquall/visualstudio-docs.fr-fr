---
title: "IDebugSymbolProvider | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugSymbolProvider"
helpviewer_keywords: 
  - "Interface de IDebugSymbolProvider"
ms.assetid: df5f095f-1dee-46f9-84cf-92417c71d5fb
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# IDebugSymbolProvider
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette interface représente un fournisseur de symboles qui fournit des symboles et les types, les retournant en tant que champs.  
  
## Syntaxe  
  
```  
IDebugSymbolProvider : IUnknown  
```  
  
## Remarques à l'intention des implémenteurs  
 un fournisseur de symbole doit implémenter cette interface pour fournir le symbole et les informations de type à un évaluateur d'expression.  
  
## Remarques pour les appelants  
 Cette interface est obtenue à l'aide de la fonction d' `CoCreateInstance` COM \(pour les fournisseurs non managés de symboles\) ou lorsque vous chargez l'assembly approprié de code managé et en instanciant le fournisseur de symbole en fonction de les informations qui se trouve dans cet assembly.  le moteur de débogage instancie le fournisseur de symbole pour fonctionner en coordination avec l'évaluateur d'expression.  Consultez l'exemple pour une approche pour instancier cette interface.  
  
## méthodes en commande de Vtable  
 Le tableau suivant répertorie les méthodes d' `IDebugSymbolProvider`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|`Initialize`|Déconseillé.  Ne pas utiliser.|  
|`Uninitialize`|Déconseillé.  Ne pas utiliser.|  
|[GetContainerField](../../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md)|obtient le champ qui contient l'adresse de débogage.|  
|`GetField`|Déconseillé.  Ne pas utiliser.|  
|[GetAddressesFromPosition](../Topic/IDebugSymbolProvider::GetAddressesFromPosition.md)|Mappe une position de document dans un tableau d'adresses de débogage.|  
|[GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)|Mappe un contexte de document en un tableau d'adresses de débogage.|  
|[GetContextFromAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getcontextfromaddress.md)|mappe une adresse de débogage dans un contexte de document.|  
|[GetLanguage](../../../extensibility/debugger/reference/idebugsymbolprovider-getlanguage.md)|Obtient le langage utilisé pour compiler le code à l'adresse de débogage.|  
|`GetGlobalContainer`|Déconseillé.  Ne pas utiliser.|  
|[GetMethodFieldsByName](../Topic/IDebugSymbolProvider::GetMethodFieldsByName.md)|obtient le champ représentant un nom de méthode qualifié complet.|  
|[GetClassTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getclasstypebyname.md)|Obtient le type de champ de la classe qui représente un nom de classe complet.|  
|[GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md)|Crée un énumérateur pour les espaces de noms associés à l'adresse de débogage.|  
|[GetTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-gettypebyname.md)|mappe un nom de symbole à un type de symbole.|  
|[GetNextAddress](../Topic/IDebugSymbolProvider::GetNextAddress.md)|obtient l'adresse de débogage qui suit une adresse donnée de débogage dans une méthode.|  
  
## Notes  
 positions de ce document de mappages d'interface dans des adresses de débogage et vice versa.  
  
## Configuration requise  
 en\-tête : sh.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Exemple  
 Cet exemple montre comment instancier le fournisseur de symbole, selon son GUID \(un moteur de débogage doit connaître cette valeur\).  
  
```cpp#  
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
  
## Voir aussi  
 [Interfaces de fournisseur de symboles](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)