---
title: "IDebugObject::IsReadOnly | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugObject::IsReadOnly"
helpviewer_keywords: 
  - "IDebugObject::IsReadOnly (méthode)"
ms.assetid: c460f772-d08a-4b36-81f3-dff6a51a93fd
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugObject::IsReadOnly
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

détermine si cet objet est en lecture seule.  
  
## Syntaxe  
  
```cpp#  
HRESULT IsReadOnly(   
   BOOL* pfIsReadOnly  
);  
```  
  
```c#  
int IsReadOnly(  
   out int pfIsReadOnly  
);  
```  
  
#### Paramètres  
 `pfIsReadOnly`  
 \[out\]  Retourne la valeur est différente de zéro \(`TRUE`\) si cet objet est en lecture seule ; sinon, retourne la valeur zéro \(`FALSE`\).  
  
## Valeur de retour  
 En cas de réussite, retourne S\_OK ; sinon, retourne un code d'erreur.  
  
## Notes  
 Un objet en lecture seule ne peut pas avoir sa valeur modifiée après sa création.  
  
## Voir aussi  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)