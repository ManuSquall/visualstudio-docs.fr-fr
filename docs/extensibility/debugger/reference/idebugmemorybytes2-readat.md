---
title: "IDebugMemoryBytes2::ReadAt | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugMemoryBytes2::ReadAt"
helpviewer_keywords: 
  - "IDebugMemoryBytes2::ReadAt (méthode)"
  - "ReadAt (méthode)"
ms.assetid: b413684d-4155-4bd4-ae30-ffa512243b5f
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IDebugMemoryBytes2::ReadAt
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Lit une séquence d'octets, en commençant à un emplacement donné.  
  
## Syntaxe  
  
```cpp#  
HRESULT ReadAt(   
   IDebugMemoryContext2* pStartContext,  
   DWORD                 dwCount,  
   BYTE*                 rgbMemory,  
   DWORD*                pdwRead,  
   DWORD*                pdwUnreadable  
);  
```  
  
```c#  
int ReadAt(  
   IDebugMemoryContext2 pStartContext,  
   uint                 dwCount,  
   byte[]               rgbMemory,  
   out uint             pdwRead,  
   ref uint             pdwUnreadable  
);  
```  
  
#### Paramètres  
 `pStartContext`  
 \[in\]  L'objet d' [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) qui spécifie l'emplacement de démarrer des octets de lecture.  
  
 `dwCount`  
 \[in\]  Nombre d'octets à lire.  Spécifie également la longueur du tableau d' `rgbMemory` .  
  
 `rgbMemory`  
 \[in, out\]  La matrice l'a exécuté dans avec les octets réellement lus.  
  
 `pdwRead`  
 \[out\]  Retourne le nombre d'octets contigus le effectue.  
  
 `pdwUnreadable`  
 \[in, out\]  Retourne le nombre d'octets illisibles.  Peut être une valeur NULL si le client est invariant dans le nombre d'octets illisibles.  
  
## Valeur de retour  
 En cas de réussite, retourne S\_OK ; sinon, retourne un code d'erreur.  
  
## Notes  
 Si 100 octets sont demandés et les 50 premiers sont lisibles, les 20 suivants sont illisibles, et les autres 30 sont lisibles, cette méthode retourne :  
  
 \*`pdwRead` \= 50  
  
 \*`pdwUnreadable` \= 20  
  
 Dans ce cas, parce qu' `*pdwRead + *pdwUnreadable < dwCount`, l'appelant doit effectuer un appel supplémentaire pour lire les 30 octets restants des 100 d'origine demandés et l'objet d' [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) passé dans le paramètre d' `pStartContext` doivent être avancés par 70.  
  
## Voir aussi  
 [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)