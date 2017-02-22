---
title: "IDebugProgram2::Terminate | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgram2::Terminate"
helpviewer_keywords: 
  - "IDebugProgram2::Terminate"
ms.assetid: 4d3127d3-b1e9-4b28-ac22-2f2eea255f86
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugProgram2::Terminate
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Arrête le programme.  
  
## Syntaxe  
  
```cpp#  
HRESULT Terminate(   
   void   
);  
```  
  
```c#  
int Terminate();  
```  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Si possible, le programme est interrompue et déchargé du processus ; sinon, le moteur de \(DE\) débogage exécute tout nettoyage nécessaire.  
  
 Cette méthode ou la méthode d' [Terminer](../../../extensibility/debugger/reference/idebugprocess2-terminate.md) est appelée par l'IDE, généralement en réponse à l'utilisateur d'arrêter tout débogage.  L'implémentation de cette méthode doit, idéalement, arrêter le programme dans le processus.  Si ce n'est pas possible, le De doit empêcher le programme d'exécuter plus dans ce processus \(et effectuer un nettoyage nécessaire\).  Si la méthode d' `IDebugProcess2::Terminate` a été appelé par l'IDE, le processus est interrompue un jour ou l'autre une fois que la méthode d' `IDebugProgram2::Terminate` soit appelée.  
  
## Voir aussi  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [Terminer](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)