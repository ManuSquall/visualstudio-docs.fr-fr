---
title: "IDebugTypeFieldBuilder2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Interface de IDebugTypeFieldBuilder2"
ms.assetid: 23911c5b-2bbf-4734-9976-87a0bd6ea36c
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# IDebugTypeFieldBuilder2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

étend l' **IDebugTypeFieldBuilder** pour pouvoir créer des types de tableau.  
  
## Syntaxe  
  
```  
IDebugTypeFieldBuilder2 : IDebugTypeFieldBuilder  
```  
  
## Remarques pour les appelants  
 Cette interface peut être obtenue du fournisseur de symbole.  
  
## Méthodes  
 En plus de les méthodes sur l'interface d' [IDebugTypeFieldBuilder](../../../extensibility/debugger/reference/idebugtypefieldbuilder.md) , cette interface implémente la méthode suivante :  
  
|Méthode|Description|  
|-------------|-----------------|  
|[CreateArrayOfType](../../../extensibility/debugger/reference/idebugtypefieldbuilder2-createarrayoftype.md)|Crée un tableau du type et la taille indiquées.|  
  
## Configuration requise  
 en\-tête : Sh.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll