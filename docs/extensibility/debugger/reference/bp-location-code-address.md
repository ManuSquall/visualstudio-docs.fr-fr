---
title: "BP_LOCATION_CODE_ADDRESS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BP_LOCATION_CODE_ADDRESS"
helpviewer_keywords: 
  - "Structure BP_LOCATION_CODE_ADDRESS"
ms.assetid: 83c9da8b-19d9-4be5-b225-854543654901
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# BP_LOCATION_CODE_ADDRESS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Décrit l'emplacement d'un point d'arrêt sur une adresse dans le code.  
  
## Syntaxe  
  
```cpp#  
typedef struct _BP_LOCATION_CODE_ADDRESS {   
   BSTR bstrContext;  
   BSTR bstrModuleUrl;  
   BSTR bstrFunction;  
   BSTR bstrAddress;  
} BP_LOCATION_CODE_ADDRESS;  
```  
  
## Membres  
 `bstrContext`  
 Le contexte du point d'arrêt, en général une méthode ou un nom de fonction comme indiqué sur une pile des appels.  
  
 `bstrModuleUrl`  
 L'URL du module qui contient le point d'arrêt.  
  
 `bstrFunction`  
 le nom de la fonction qui contient le point d'arrêt.  
  
 `bstrAddress`  
 L'adresse de point d'arrêt, analysé par un évaluateur d'expression à une liaison à un objet d' [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) .  
  
## Notes  
 Cette structure est un membre de la structure de [BP\_LOCATION](../../../extensibility/debugger/reference/bp-location.md) dans le cadre d'une union.  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Structures et Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP\_LOCATION](../../../extensibility/debugger/reference/bp-location.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)