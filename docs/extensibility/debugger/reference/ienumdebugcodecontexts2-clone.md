---
title: "IEnumDebugCodeContexts2::Clone | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugCodeContexts2::Clone"
helpviewer_keywords: 
  - "IEnumDebugCodeContexts2::Clone"
ms.assetid: 22c98975-4294-4fbd-a345-16f65fe1200d
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IEnumDebugCodeContexts2::Clone
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Retourne une copie de l'énumération actuelle dans un objet distinct.  
  
## Syntaxe  
  
```cpp#  
HRESULT Clone(  
   IEnumDebugCodeContexts2** ppEnum  
);  
```  
  
```c#  
int Clone(  
   out IEnumDebugCodeContexts2 ppEnum  
);  
```  
  
#### Paramètres  
 `ppEnum`  
 \[out\]  Retourne une copie de cette énumération comme un objet distinct.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 La copie de l'énumération a le même état à l'image d'origine lorsque cette méthode est appelée.  Toutefois, la copie et les états de l'origine sont distincts et peuvent être modifiés individuellement.  
  
## Voir aussi  
 [IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)