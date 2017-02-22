---
title: "IDebugPrimitiveTypeField | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Interface de IDebugPrimitiveTypeField"
ms.assetid: 73a428fd-797e-4ceb-8392-ba16f1c5226b
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# IDebugPrimitiveTypeField
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

représente une valeur d'énumération de type primitif d'une interface d' [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) .  
  
## Syntaxe  
  
```  
IDebugPrimitiveTypeField : IDebugField  
```  
  
## Méthodes  
 En plus de les méthodes sur l'interface d' [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) , cette interface implémente la méthode suivante :  
  
|Méthode|Description|  
|-------------|-----------------|  
|[GetPrimitiveType](../../../extensibility/debugger/reference/idebugprimitivetypefield-getprimitivetype.md)|Récupère le type primitif associé à ce champ.|  
  
## Configuration requise  
 en\-tête : Sh.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll