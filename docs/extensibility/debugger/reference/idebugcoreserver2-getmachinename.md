---
title: "IDebugCoreServer2::GetMachineName | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCoreServer2::GetName"
helpviewer_keywords: 
  - "IDebugCoreServer2::GetName"
ms.assetid: 693bd794-7215-4f07-8651-b57366d39953
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugCoreServer2::GetMachineName
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtient le nom de l'ordinateur sur lequel le principal serveur s'exécute.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetName(   
   BSTR* pbstrName  
);  
```  
  
```c#  
int GetName(   
   out string pbstrName  
);  
```  
  
#### Paramètres  
 `pbstrName`  
 \[out\]  Retourne une chaîne contenant le nom de l'ordinateur.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)