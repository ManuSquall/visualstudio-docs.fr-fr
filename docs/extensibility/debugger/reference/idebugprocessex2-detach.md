---
title: "IDebugProcessEx2::Detach | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcessEx2::Detach"
helpviewer_keywords: 
  - "IDebugProcessEx2::Detach (méthode)"
ms.assetid: 66d54c2c-9302-47c8-9975-f30ed988ab29
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# IDebugProcessEx2::Detach
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette méthode informe le processus qu'une session ne débogue plus le processus.  
  
## Syntaxe  
  
```cpp#  
HRESULT Detach(   
   IDebugSession2* pSession  
);  
```  
  
```c#  
int Detach(  
   IDebugSession2 pSession  
);  
```  
  
#### Paramètres  
 `pSession`  
 \[in\]  Une valeur qui identifie de façon unique la session pour détacher ce processus.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 L'interface passée dans `pSession` doit être traitée uniquement comme un cookie, une valeur qui identifie le gestionnaire de débogage de session qui s'est initialement joint à ce processus ; aucune des méthodes sur l'interface fournie n'est fonctionnelle.  
  
## Voir aussi  
 [IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)