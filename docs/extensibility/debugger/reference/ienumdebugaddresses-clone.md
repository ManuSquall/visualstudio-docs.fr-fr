---
title: "IEnumDebugAddresses::Clone | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugAddresses::Clone"
helpviewer_keywords: 
  - "IEnumDebugAddresses::Clone (méthode)"
ms.assetid: 71189a00-34eb-4c71-b96e-8bd6e70c6966
caps.latest.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 5
---
# IEnumDebugAddresses::Clone
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette méthode retourne une copie de l'énumération actuelle dans un objet distinct.  
  
## Syntaxe  
  
```cpp#  
HRESULT Clone(  
   IEnumDebugAddresses** ppEnum  
);  
```  
  
```c#  
int Clone(  
   out IEnumDebugAddresses ppEnum  
);  
```  
  
#### Paramètres  
 `ppEnum`  
 \[out\]  Retourne une copie de cette énumération comme un objet distinct.  
  
## Valeur de propriété\/valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 La copie de l'énumération a le même état à l'image d'origine lorsque cette méthode est appelée.  Toutefois, la copie et les états de l'origine sont distincts et peuvent être modifiés individuellement.  
  
## Voir aussi  
 [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)