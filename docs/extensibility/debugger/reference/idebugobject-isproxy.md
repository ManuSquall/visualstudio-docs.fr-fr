---
title: "IDebugObject::IsProxy | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugObject::IsProxy"
  - "Proxy"
ms.assetid: 06c66b87-db95-4400-ab26-5d33e743a439
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugObject::IsProxy
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

détermine si l'objet est un proxy transparent.  
  
## Syntaxe  
  
```cpp#  
HRESULT IsProxy (  
   BOOL* pfIsProxy  
);  
```  
  
```c#  
int IsProxy (  
   out bool pfIsProxy  
);  
```  
  
#### Paramètres  
 `pfIsProxy`  
 \[out\]  `TRUE` si l'objet est un proxy transparent ; sinon, `FALSE`.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Cette méthode est implémentée par le moteur de débogage C\+\+ par défaut.  
  
## Voir aussi  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)