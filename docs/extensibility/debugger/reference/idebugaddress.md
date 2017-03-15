---
title: "IDebugAddress | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugAddress"
helpviewer_keywords: 
  - "Interface de IDebugAddress"
ms.assetid: bc709ff7-4966-4f36-9af2-690efe2cea1d
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugAddress
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

cette interface représente l'adresse d'un élément.  Il est retourné par le gestionnaire de symboles.  
  
## Syntaxe  
  
```  
IDebugAddress : IUnknown  
```  
  
## Remarques à l'intention des implémenteurs  
 un fournisseur de symbole implémente cette interface pour représenter une adresse d'un objet.  
  
## Remarques pour les appelants  
 De nombreuses méthodes dans de nombreuses interfaces retournent cette interface.  
  
## méthodes en commande de Vtable  
 Cette interface implémente la méthode suivante :  
  
|Méthode|Description|  
|-------------|-----------------|  
|[GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)|extrait une structure de [DEBUG\_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) décrivant un objet et son emplacement.|  
  
## Notes  
 Le fournisseur de symbole retourne cette interface pour représenter un objet et son emplacement dans une portée particulière \(par exemple, la fonction, méthode, ou classe\).  Cette interface est retournée à partir de et passée à différentes méthodes de fournisseur et évaluateur d'expression du symbole.  normalement, le fournisseur de symbole est la seule entité qui doit interpréter le contenu de cette interface.  
  
## Configuration requise  
 en\-tête : sh.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Interfaces de fournisseur de symboles](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [DEBUG\_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)