---
title: "IDebugDefaultPort2::GetServer | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDefaultPort2::GetServer"
helpviewer_keywords: 
  - "IDebugDefaultPort2::GetServer"
ms.assetid: cacb4b74-0f39-471c-af38-54b73f5b2868
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugDefaultPort2::GetServer
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette méthode extrait une interface au serveur que ce port est activé.  
  
## Syntaxe  
  
```cpp  
HRESULT GetServer(  
   IDebugCoreServer3** ppServer  
);  
```  
  
```c#  
int GetServer(  
   out IDebugCoreServer3 ppServer  
);  
```  
  
#### Paramètres  
 `ppServer`  
 \[out\]  Retourne un objet implémentant l'interface d' [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md) .  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md) est implémenté par Visual Studio et représente le serveur que le port se trouve sur.  
  
## Voir aussi  
 [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)   
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)