---
title: "BP_LOCATION_CODE_FILE_LINE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BP_LOCATION_CODE_FILE_LINE"
helpviewer_keywords: 
  - "Structure BP_LOCATION_CODE_FILE_LINE"
ms.assetid: 3ff32032-d412-44d3-91bf-870cc354a09e
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# BP_LOCATION_CODE_FILE_LINE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Contient les données pour l'emplacement d'un point d'arrêt sur une ligne spécifique dans un fichier source du code.  
  
## Syntaxe  
  
```cpp#  
typedef struct _BP_LOCATION_CODE_FILE_LINE {   
   BSTR                     bstrContext;  
   IDebugDocumentPosition2* pDocPos;  
} BP_LOCATION_CODE_FILE_LINE;  
```  
  
## Membres  
 `bstrContext`  
 Le contexte du point d'arrêt, en général une méthode ou un nom de fonction comme indiqué sur une pile des appels.  
  
 `pDocPos`  
 l'objet d' [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md) qui représente la position de document du point d'arrêt.  
  
## Notes  
 Cette structure est un membre de la structure de [BP\_LOCATION](../../../extensibility/debugger/reference/bp-location.md) dans le cadre d'une union.  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Structures et Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP\_LOCATION](../../../extensibility/debugger/reference/bp-location.md)   
 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)