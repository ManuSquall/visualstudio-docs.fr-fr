---
title: "BP_LOCATION_CODE_STRING | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BP_LOCATION_CODE_STRING"
helpviewer_keywords: 
  - "Structure BP_LOCATION_CODE_STRING"
ms.assetid: a4cd71c6-5052-45fe-907b-ebc6ca1df2e4
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# BP_LOCATION_CODE_STRING
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Utilisé pour définir des points d'arrêt de code en fonction d'une chaîne que l'utilisateur peut entrer de l'environnement de développement intégré \(IDE\) \(IDE\).  
  
## Syntaxe  
  
```cpp#  
typedef struct _BP_LOCATION_CODE_STRING {   
   BSTR bstrContext;  
   BSTR bstrCodeExpr;  
} BP_LOCATION_CODE_STRING;  
```  
  
## Membres  
 `bstrContext`  
 Le contexte du point d'arrêt dans le code, en général une méthode ou un nom de fonction comme indiqué sur une pile des appels.  
  
 `bstrCodeExpr`  
 La chaîne que l'utilisateur entre dans pour décrire le point d'arrêt de code.  
  
## Notes  
 Cette structure est un membre de la structure de [BP\_LOCATION](../../../extensibility/debugger/reference/bp-location.md) dans le cadre d'une union.  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Structures et Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP\_LOCATION](../../../extensibility/debugger/reference/bp-location.md)