---
title: "IDebugModOpt::GetModOpts | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugModOpt::GetModOpts"
  - "GetModOpts"
ms.assetid: cb513fa9-d521-4a65-b968-f55f53a368df
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugModOpt::GetModOpts
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Extrait une liste des modificateurs facultatifs.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetModOpts(  
   ULONG  celt,  
   BSTR*  rgelt,  
   ULONG* pceltFetched  
);  
```  
  
```c#  
int GetModOpts(  
   uint         celt,  
   out string[] rgelt,  
   ref uint     pceltFetched  
);  
```  
  
#### Paramètres  
 `celt`  
 \[in\]  Nombre d'éléments à retourner.  
  
 `rgelt`  
 \[out\]  Retourne un tableau qui contient les options.  
  
 `pceltFetched`  
 \[in, out\]  Le nombre d'éléments retournés dans le tableau d' `rgelt` .  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDebugModOpt](../../../extensibility/debugger/reference/idebugmodopt.md)