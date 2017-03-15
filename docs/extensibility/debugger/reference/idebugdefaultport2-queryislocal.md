---
title: "IDebugDefaultPort2::QueryIsLocal | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDefaultPort2::QueryIsLocal"
helpviewer_keywords: 
  - "IDebugDefaultPort2::QueryIsLocal"
ms.assetid: 1a42e774-c6ed-419a-a0e3-cab5778652ca
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugDefaultPort2::QueryIsLocal
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

cette méthode détermine si ce port est sur l'ordinateur local.  
  
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
 Retourne `S_OK` si ce port est local \(sur le même ordinateur que l'appelant\) ou `S_FALSE` si le port est sur un autre ordinateur.  
  
## Voir aussi  
 [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)