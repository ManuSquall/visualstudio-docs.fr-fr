---
title: "IDebugSymbolProviderDirect | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Interface de IDebugSymbolProviderDirect"
ms.assetid: 872b04a8-70de-4ab5-aceb-684c81828545
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# IDebugSymbolProviderDirect
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Représente un fournisseur de symbole qui a un accès direct aux métadonnées et vide des interfaces de symbole.  
  
## Syntaxe  
  
```  
IDebugSymbolProviderDirect: IUnknown  
```  
  
## Méthodes  
 Cette interface implémente les méthodes suivantes :  
  
|Méthode|Description|  
|-------------|-----------------|  
|[GetAppIDFromAddress](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getappidfromaddress.md)|Extrait l'identificateur du domaine d'application donné l'adresse de débogage.|  
|[GetCurrentModulesInfo](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getcurrentmodulesinfo.md)|Récupère des informations à propos de les modules au groupe de symbole.|  
|[GetCurrentModulesState](../Topic/IDebugSymbolProviderDirect::GetCurrentModulesState.md)|Récupère des informations à propos de le groupe de symbole dont le fournisseur de symbole est membre.|  
|[GetMetaDataImport](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getmetadataimport.md)|Extrait des informations d'importation de métadonnées.|  
|[GetMethodFromAddress](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getmethodfromaddress.md)|Récupère des informations concernant la méthode à l'adresse spécifiée de débogage.|  
|[GetSymUnmanagedReader](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getsymunmanagedreader.md)|Récupère un lecteur de symboles pour du code non managé.|  
  
## Notes  
 cette interface peut être utilisée au lieu de la plupart des autres interfaces de fournisseur de symbole.  Il fournit un accès direct aux métadonnées et les interfaces d' `CorSym` .  
  
## Configuration requise  
 en\-tête : Sh.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll