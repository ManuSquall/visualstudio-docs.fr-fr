---
title: "IDebugEvent2::GetAttributes | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEvent2::GetAttributes"
helpviewer_keywords: 
  - "IDebugEvent2::GetAttributes"
ms.assetid: 2ac5b5fb-da17-43f7-811a-313f677e60d7
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugEvent2::GetAttributes
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtient les attributs de cet événement de débogage.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetAttribute(   
   DWORD* pdwAttrib  
);  
```  
  
```c#  
int GetAttribute(   
   out uint pdwAttrib  
);  
```  
  
#### Paramètres  
 `pdwAttrib`  
 \[out\]  Une combinaison des indicateurs d'énumération d' [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md) .  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 l'interface d' [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) est commune à tous les événements.  cette méthode décrit le type d'événement ; par exemple, est l'événement et synchrones ou asynchrones il est un événement arrêtant.  
  
## Voir aussi  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md)