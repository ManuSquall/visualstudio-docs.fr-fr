---
title: "IDebugProgram2::Detach | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgram2::Detach"
helpviewer_keywords: 
  - "IDebugProgram2::Detach"
ms.assetid: 5e8d88b0-a8d4-4746-88c0-ad332ee73f33
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugProgram2::Detach
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

détache un moteur de débogage du programme.  
  
## Syntaxe  
  
```cpp#  
HRESULT Detach(   
   void   
);  
```  
  
```c#  
int Detach();  
```  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Un programme isolé continue de s'exécuter, mais ce n'est plus partie de la session de débogage.  Plus d'événements de débogage du programme n'est envoyé une fois que le moteur de débogage est détaché.  
  
## Voir aussi  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)