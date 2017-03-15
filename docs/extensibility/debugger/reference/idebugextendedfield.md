---
title: "IDebugExtendedField | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Interface de IDebugExtendedField"
ms.assetid: b491499c-af57-47da-87d6-34b7398f6591
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# IDebugExtendedField
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Étend les types de champs qui sont disponibles pour prendre en charge les génériques de code managé.  
  
## Syntaxe  
  
```  
IDebugExtendedField : IDebugField  
```  
  
## Méthodes  
 En plus de les méthodes sur l'interface d' [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) , cette interface implémente les méthodes suivantes :  
  
|Méthode|Description|  
|-------------|-----------------|  
|[GetExtendedKind](../../../extensibility/debugger/reference/idebugextendedfield-getextendedkind.md)|Récupère le type étendu spécifié de champ.|  
|[IsClosedType](../../../extensibility/debugger/reference/idebugextendedfield-isclosedtype.md)|détermine si le champ représente un type fermé.|  
  
## Configuration requise  
 en\-tête : Sh.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll