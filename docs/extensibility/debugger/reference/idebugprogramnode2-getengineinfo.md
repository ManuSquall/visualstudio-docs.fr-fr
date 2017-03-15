---
title: "IDebugProgramNode2::GetEngineInfo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramNode2::GetEngineInfo"
helpviewer_keywords: 
  - "IDebugProgramNode2::GetEngineInfo"
ms.assetid: 664e7fe5-9100-4b7d-9dc5-e5a4dd0d0451
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IDebugProgramNode2::GetEngineInfo
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtient le nom et l'identificateur du moteur de débogage \(DE\) exécution d'un programme.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetEngineInfo (   
   BSTR* pbstrEngine,  
   GUID* pguidEngine  
);  
```  
  
```c#  
int GetEngineInfo(  
   out string pbstrEngine,   
   out Guid pguidEngine  
);  
```  
  
#### Paramètres  
 `pbstrEngine`  
 \[out\]  Retourne le nom de côté du programme \(C\+\+\-specific : cela peut être un pointeur null indiquant que l'appelant n'est pas effectuer au nom de le moteur\).  
  
 `pguidEngine`  
 \[out\]  Retourne l'identificateur global unique de côté du programme \(C\+\+\-specific : cela peut être un pointeur null indiquant que l'appelant n'est pas intéressé par le GUID du moteur\).  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)