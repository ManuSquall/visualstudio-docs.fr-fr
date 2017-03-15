---
title: "IDebugProcessEx2::Attach | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcessEx2::Attach"
helpviewer_keywords: 
  - "IDebugProcessEx2::Attach (méthode)"
ms.assetid: f3334ed7-39bf-4d02-a338-36f567b9b287
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# IDebugProcessEx2::Attach
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette méthode informe le processus qu'une session sont traduits maintenant le processus.  
  
## Syntaxe  
  
```cpp#  
HRESULT Attach(   
   IDebugSession2* pSession  
);  
```  
  
```c#  
int Attach(  
   IDebugSession2 pSession  
);  
```  
  
#### Paramètres  
 `pSession`  
 \[in\]  Une valeur qui identifie de façon unique la session l'attachement à ce processus.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 L'interface passée dans `pSession` doit être traitée uniquement comme un cookie, une valeur qui identifie le gestionnaire de débogage de session l'attachement à ce processus ; aucune des méthodes sur l'interface fournie n'est fonctionnelle.  
  
## Voir aussi  
 [IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)