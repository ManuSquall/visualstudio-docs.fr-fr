---
title: "IDebugAlias2::GetAppDomainId | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "GetAppDomainId"
  - "IDebugAlias2::GetAppDomainId"
ms.assetid: 23581aaa-5a53-4859-b264-eca49fc44bcd
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugAlias2::GetAppDomainId
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Extrait l'identificateur du domaine d'application.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetAppDomainId (  
   ULONG32* pappDomainId  
);  
```  
  
```c#  
int GetAppDomainId (  
   out uint pappDomainId  
);  
```  
  
#### Paramètres  
 `pappDomainId`  
 \[out\]  Retourne l'identificateur du domaine d'application.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 L'identificateur du domaine d'application remplace chaque fois que l'application est redémarrée et un nouveau domaine d'application est créé.  
  
## Voir aussi  
 [IDebugAlias2](../../../extensibility/debugger/reference/idebugalias2.md)