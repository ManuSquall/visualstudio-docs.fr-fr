---
title: "IDebugPointerObject::GetBytes | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPointerObject::GetBytes"
helpviewer_keywords: 
  - "IDebugPointerObject::GetBytes (méthode)"
ms.assetid: e986c188-87fb-4b51-86e9-ee6a0035bdab
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugPointerObject::GetBytes
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtient la valeur désignée comme une série d'octets consécutifs.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetBytes(   
   DWORD  dwStart,  
   DWORD  dwCount,  
   BYTE*  pBytes,  
   DWORD* pdwBytes  
);  
```  
  
```c#  
int GetBytes(  
   uint       dwStart,   
   uint       dwCount,   
   out byte[] pBytes,   
   out uint   pdwBytes  
);  
```  
  
#### Paramètres  
 `dwStart`  
 \[in\]  Un offset, en octets, le début de l'objet désigné.  
  
 `dwCount`  
 \[in\]  Nombre d'octets à récupérer.  
  
 `pBytes`  
 \[in, out\]  Un tableau qui est terminée avec la valeur comme une série d'octets consécutifs, en commençant à l'offset donné de l'objet indiquée.  
  
 `pdwBytes`  
 \[out\]  Retourne le nombre d'octets réellement récupérés.  
  
## Valeur de retour  
 En cas de réussite, retourne S\_OK ; sinon, retourne un code d'erreur.  
  
## Notes  
 Cette méthode est utilisée si le pointeur comme représentée par les points d' [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md) à un type primitif ou un simple tableau de types primitifs \(autrement dit, un tableau qui peut être représenté par une séquence simple d'octets\).  
  
## Voir aussi  
 [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)   
 [SetBytes](../../../extensibility/debugger/reference/idebugpointerobject-setbytes.md)