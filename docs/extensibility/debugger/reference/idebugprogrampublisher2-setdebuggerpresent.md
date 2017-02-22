---
title: "IDebugProgramPublisher2::SetDebuggerPresent | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramPublisher2::SetDebuggerPresent"
helpviewer_keywords: 
  - "IDebugProgramPublisher2::SetDebuggerPresent"
ms.assetid: c88c3ff4-3632-4199-b5de-83c6d21bcf75
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# IDebugProgramPublisher2::SetDebuggerPresent
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Indique au serveur de publication de programme qu'un débogueur est présent et en cours de exécution.  
  
## Syntaxe  
  
```cpp  
HRESULT SetDebuggerPresent(  
   BOOL fDebuggerPresent  
);  
```  
  
```c#  
int SetDebuggerPresent(  
   int fDebuggerPresent  
);  
```  
  
#### Paramètres  
 `fDebuggerPresent`  
 \[in\]  Différente de zéro \(`TRUE`\) si un débogueur est présent, zéro \(`FALSE`\) s'il n'est pas.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 la présence ou l'absence d'un débogueur est reflétée dans les données retournées de la méthode d' [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) : la valeur retournée est assurée définie ou désactivée par un appel précédent à la méthode d' `SetDebuggerPresent` .  
  
## Voir aussi  
 [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)   
 [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)