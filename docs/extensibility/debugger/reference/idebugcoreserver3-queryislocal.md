---
title: "IDebugCoreServer3::QueryIsLocal | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCoreServer3::QueryIsLocal"
helpviewer_keywords: 
  - "IDebugCoreServer3::QueryIsLocal"
ms.assetid: cca030de-f853-4ed7-b2fb-395f08a6b884
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# IDebugCoreServer3::QueryIsLocal
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

détermine si le serveur est local à l'appelant.  
  
## Syntaxe  
  
```cpp#  
HRESULT QueryIsLocal(  
   void  
);  
```  
  
```c#  
int QueryIsLocal();  
```  
  
## Valeur de retour  
 Retourne `S_OK` pour indiquer le serveur est local.  Retourne `S_FALSE` si le serveur exécute à partir d'une instance de msvsmon.exe, qui est généralement utilisé pour le débogage distant.  
  
## Voir aussi  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)