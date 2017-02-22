---
title: "IDebugTypeFieldBuilder | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Interface de IDebugTypeFieldBuilder"
ms.assetid: 2dfed0be-6972-4bec-baec-f0b78df9ef97
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# IDebugTypeFieldBuilder
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

représente la capacité de créer un champ qui représente un type.  
  
## Syntaxe  
  
```  
IDebugTypeFieldBuilder : IUnknown  
```  
  
## Remarques pour les appelants  
 Cette interface est obtenue du fournisseur de symbole.  
  
## Méthodes  
 Cette interface implémente les méthodes suivantes :  
  
|Méthode|Description|  
|-------------|-----------------|  
|[CreatePrimitive](../../../extensibility/debugger/reference/idebugtypefieldbuilder-createprimitive.md)|crée un objet qui représente un type primitif.|  
|[CreatePointerToType](../../../extensibility/debugger/reference/idebugtypefieldbuilder-createpointertotype.md)|Crée un pointeur vers le type spécifié.|  
  
## Configuration requise  
 en\-tête : Sh.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll