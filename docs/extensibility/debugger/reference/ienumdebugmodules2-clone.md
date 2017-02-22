---
title: "IEnumDebugModules2::Clone | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugModules2::Clone"
helpviewer_keywords: 
  - "IEnumDebugModules2::Clone"
ms.assetid: fd6d3abc-20d9-4f6f-9c8e-5bd29f68d47d
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IEnumDebugModules2::Clone
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Retourne une copie de l'énumération actuelle dans un objet distinct.  
  
## Syntaxe  
  
```cpp#  
HRESULT Clone(  
   IEnumDebugModules2** ppEnum  
);  
```  
  
```c#  
int Clone(  
   out IEnumDebugModules2 ppEnum  
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
 [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)