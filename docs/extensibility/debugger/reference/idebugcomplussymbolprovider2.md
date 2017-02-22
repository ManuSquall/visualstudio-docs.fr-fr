---
title: "IDebugComPlusSymbolProvider2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Interface de IDebugComPlusSymbolProvider2"
ms.assetid: fa2f9b49-03ad-43c7-92d6-6dcb9c3d0531
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# IDebugComPlusSymbolProvider2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Représente un fournisseur de symbole COM\+ avec les méthodes qui sont spécifiques au code managé et étend **l'IDebugComPlusSymbolProvider[IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)**.  
  
## Syntaxe  
  
```  
IDebugComPlusSymbolProvider2 : IDebugComPlusSymbolProvider  
```  
  
## Méthodes  
 En plus de les méthodes sur l'interface d' [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) , cette interface implémente les méthodes suivantes :  
  
|Méthode|Description|  
|-------------|-----------------|  
|[FunctionHasLineInfo](../Topic/IDebugComPlusSymbolProvider2::FunctionHasLineInfo.md)|Détermine si la méthode spécifiée a des informations de ligne.|  
|[GetTypesByName](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-gettypesbyname.md)|Récupère un type avec son nom.|  
|[GetTypeFromToken](../Topic/IDebugComPlusSymbolProvider2::GetTypeFromToken.md)|Récupère un type donné son jeton.|  
|[IsAddressSequencePoint](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-isaddresssequencepoint.md)|détermine si l'adresse spécifiée de débogage est un point de séquence.|  
|[LoadSymbolsFromCallback](../Topic/IDebugComPlusSymbolProvider2::LoadSymbolsFromCallback.md)|Symboles de débogage de charge à l'aide de la méthode de rappel spécifiée.|  
|[LoadSymbolsFromStreamWithCorModule](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-loadsymbolsfromstreamwithcormodule.md)|Chargez les symboles de débogage d'un flux donné l'objet **d'ICorDebugModule** .|  
|[LoadSymbolsWithCorModule](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-loadsymbolswithcormodule.md)|symboles de débogage de charges donnés l'objet d' **ICorDebugModule** .|  
  
## Configuration requise  
 en\-tête : Sh.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll