---
title: "IDebugProgramPublisher2::UnpublishProgram | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramPublisher2::UnpublishProgram"
helpviewer_keywords: 
  - "IDebugProgramPublisher2::UnpublishProgram"
ms.assetid: 627e7d38-b2ac-4873-9a40-37ff7f47cd1d
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugProgramPublisher2::UnpublishProgram
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

rend un programme non disponible pour être débogué.  
  
## Syntaxe  
  
```cpp  
HRESULT UnpublishProgram(  
   IUnknown* pDebuggeeInterface  
);  
```  
  
```c#  
int UnpublishProgram(  
   object pDebuggeeInterface  
);  
```  
  
#### Paramètres  
 `pDebuggeeInterface`  
 \[in\]  une interface d' `IUnknown` au programme.  C'est la même valeur fournie à la méthode d' [PublishProgram](../Topic/IDebugProgramPublisher2::PublishProgram.md) et identifie le programme en cours de suppression \(autrement dit, il est utilisé comme un cookie\).  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Pour rendre un programme disponible aux moteurs de débogage et à la session déboguez le gestionnaire, utilisez la méthode d' [PublishProgram](../Topic/IDebugProgramPublisher2::PublishProgram.md) .  
  
## Voir aussi  
 [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)   
 [PublishProgram](../Topic/IDebugProgramPublisher2::PublishProgram.md)