---
title: "IDebugProcess2::CauseBreak | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcess2::CauseBreak"
helpviewer_keywords: 
  - "IDebugProcess2::CauseBreak"
ms.assetid: efda8865-2319-4d53-90bf-6d9d74cd5195
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProcess2::CauseBreak
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Les demandes qui le programme suivant qui exécute le code de cet arrêt du processus et envoient un objet événement d' [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) .  
  
## Syntaxe  
  
```cpp#  
HRESULT CauseBreak(   
   void  
);  
```  
  
```c#  
int CauseBreak();  
```  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)