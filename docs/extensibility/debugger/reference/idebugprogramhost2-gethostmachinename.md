---
title: "IDebugProgramHost2::GetHostMachineName | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramHost2::GetHostMachineName"
helpviewer_keywords: 
  - "IDebugProgramHost2::GetHostMachineName"
ms.assetid: 4677ffe4-aa9b-4450-a63b-74cd3984d956
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProgramHost2::GetHostMachineName
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtient le nom de l'ordinateur sur lequel l'hébergement de processus que le programme s'exécute.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetHostMachineName(   
   BSTR* pbstrHostMachineName  
);  
```  
  
```c#  
int GetHostMachineName(   
   out string pbstrHostMachineName  
);  
```  
  
#### Paramètres  
 `pbstrHostMachineName`  
 \[out\]  Retourne le nom de l'ordinateur.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)