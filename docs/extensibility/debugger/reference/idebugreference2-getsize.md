---
title: "IDebugReference2::GetSize | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugReference2::GetSize"
helpviewer_keywords: 
  - "IDebugReference2::GetSize"
ms.assetid: a404ddd9-d940-4513-97cd-f52b8ab6a560
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugReference2::GetSize
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

obtient la taille, en octets, de la valeur de la référence.  Réservé à une utilisation future.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetSize (   
   DWORD* pdwSize  
);  
```  
  
```c#  
int GetSize (   
   out uint pdwSize  
);  
```  
  
#### Paramètres  
 `pdwSize`  
 \[out\]  Retourne la taille, en octets, de la valeur de la référence.  
  
## Valeur de retour  
 Retourne toujours `E_NOTIMPL`.  
  
## Voir aussi  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)