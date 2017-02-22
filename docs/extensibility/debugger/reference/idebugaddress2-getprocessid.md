---
title: "IDebugAddress2::GetProcessID | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugAddress2::GetProcessID"
helpviewer_keywords: 
  - "IDebugAddress2::GetProcessID (méthode)"
ms.assetid: 2c18889d-074a-4b95-87b4-bf1a067f44ed
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# IDebugAddress2::GetProcessID
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Extrait l'ID du processus propriétaire l'objet représenté par cette interface d' [IDebugAddress2](../../../extensibility/debugger/reference/idebugaddress2.md) .  
  
## Syntaxe  
  
```cpp  
HRESULT GetProcessID (  
   DWORD* pProcID  
);  
```  
  
```c#  
int GetProcessID (  
   out uint pProcID  
);  
```  
  
#### Paramètres  
 `pProcID`  
 \[out\]  L'identificateur de processus  
  
## Valeur de retour  
 En cas de réussite, retourne S\_OK ; sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDebugAddress2](../../../extensibility/debugger/reference/idebugaddress2.md)