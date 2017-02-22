---
title: "IDebugModule3::IsUserCode | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugModule3::IsUserCode"
helpviewer_keywords: 
  - "IDebugModule3::IsUserCode"
ms.assetid: 77022946-bb8b-4114-aa81-614df6e54b13
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugModule3::IsUserCode
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Récupère les informations en fonction, que le module représente le code utilisateur ou pas.  
  
## Syntaxe  
  
```cpp#  
HRESULT IsUserCode(  
   BOOL* pfUser  
);  
```  
  
```c#  
int IsUserCode(  
   out int pfUser  
);  
```  
  
#### Paramètres  
 `pfUser`  
 \[out\]  Une valeur différente de zéro \(`TRUE`\) si le module représente le code utilisateur, zéro \(`FALSE`\) dans le cas contraire.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, le code d'erreur de retour.  
  
## Voir aussi  
 [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)