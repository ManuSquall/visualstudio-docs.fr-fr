---
title: "IDebugPortEx2::ResumeProcess | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPortEx2::ResumeProcess"
helpviewer_keywords: 
  - "IDebugPortEx2::ResumeProcess"
ms.assetid: e80a6960-9456-4764-9320-e7b1bd57fe5d
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugPortEx2::ResumeProcess
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Reprend l'exécution d'un processus.  
  
## Syntaxe  
  
```cpp#  
HRESULT ResumeProcess(   
   IDebugProcess2* pPortProcess  
);  
```  
  
```cpp#  
int ResumeProcess(   
   IDebugProcess2 pPortProcess  
);  
```  
  
#### Paramètres  
 `pPortProcess`  
 \[in\]  un objet d' [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) représentant le processus à continuer.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)