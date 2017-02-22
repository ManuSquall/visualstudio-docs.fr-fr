---
title: "IDebugPointerObject::SetBytes | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPointerObject::SetBytes"
helpviewer_keywords: 
  - "IDebugPointerObject::SetBytes (méthode)"
ms.assetid: 8c578b38-38d7-46f3-bb2e-8a730fccd334
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugPointerObject::SetBytes
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

définit la valeur pointée sur d'une série d'octets consécutifs.  
  
## Syntaxe  
  
```cpp#  
HRESULT SetBytes(   
   DWORD  dwStart,  
   DWORD  dwCount,  
   BYTE*  pBytes,  
   DWORD* pdwBytes  
);  
```  
  
```c#  
int SetBytes(  
   uint     dwStart,   
   uint     dwCount,   
   byte[]   pBytes,   
   out uint pdwBytes  
);  
```  
  
#### Paramètres  
 `dwStart`  
 \[in\]  Un offset, en octets, le début de l'objet indiquée.  
  
 `dwCount`  
 \[in\]  Le nombre d'octets à définir.  
  
 `pBytes`  
 \[in\]  Un tableau d'octets représentant la nouvelle valeur.  Cette valeur est stockée dans l'objet, en commençant à l'offset donné.  
  
 `pdwBytes`  
 \[out\]  Retourne le nombre d'octets réellement définis.  
  
## Valeur de retour  
 En cas de réussite, retourne S\_OK ; sinon, retourne un code d'erreur.  
  
## Notes  
 Cette méthode est utilisée si le pointeur comme représentée par les points d' [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md) à un type primitif ou un simple tableau de types primitifs \(autrement dit, un tableau qui peut être représenté par une séquence simple d'octets\).  Cet objet d' `IDebugPointerObject` ne peut pas être une référence null \(il doit indiquer une adresse en mémoire\).  
  
## Voir aussi  
 [GetBytes](../../../extensibility/debugger/reference/idebugpointerobject-getbytes.md)   
 [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)