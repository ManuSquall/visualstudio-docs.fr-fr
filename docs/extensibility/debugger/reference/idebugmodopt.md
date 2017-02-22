---
title: "IDebugModOpt | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Interface de IDebugModOpt"
ms.assetid: ebd525e3-d140-4071-9d8c-41871de4125e
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# IDebugModOpt
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

représente un modificateur facultatif de débogage.  
  
## Syntaxe  
  
```  
IDebugModOpt : IUnknown  
```  
  
## Remarques pour les appelants  
 Obtenu à partir d'un objet d' [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) qui représente une classe ou une méthode.  
  
## Méthodes  
 Cette interface implémente la méthode suivante :  
  
|Méthode|Description|  
|-------------|-----------------|  
|[GetModOpts](../../../extensibility/debugger/reference/idebugmodopt-getmodopts.md)|Extrait une liste des modificateurs facultatifs.|  
  
## Configuration requise  
 en\-tête : Sh.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll