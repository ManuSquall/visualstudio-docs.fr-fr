---
title: "IDebugProgram2::GetEngineInfo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgram2::GetEngineInfo"
helpviewer_keywords: 
  - "IDebugProgram2::GetEngineInfo"
ms.assetid: 3a4f2dc0-e082-4d8d-aeaf-463ab09d279b
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProgram2::GetEngineInfo
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtient le nom et le GUID du moteur de débogage \(DE\) l'exécution de ce programme.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetEngineInfo(   
   BSTR* pbstrEngine,  
   GUID* pguidEngine  
);  
```  
  
```c#  
int GetEngineInfo(   
   out string pbstrEngine,  
   out GUID   pguidEngine  
);  
```  
  
#### Paramètres  
 `pbstrEngine`  
 \[out\]  Retourne le nom de running ce programme.  
  
 `pguidEngine`  
 \[out\]  Retourne le GUID de running ce programme.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 chaque De définit son propre GUID pour l'identification.  
  
## Voir aussi  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)