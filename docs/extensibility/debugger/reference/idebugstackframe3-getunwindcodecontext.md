---
title: "IDebugStackFrame3::GetUnwindCodeContext | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugStackFrame3::GetUnwindCodeContext"
helpviewer_keywords: 
  - "IDebugStackFrame3::GetUnwindCodeContext (méthode)"
ms.assetid: b25f7e7d-2b24-48e4-93b3-829e61d73ebf
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# IDebugStackFrame3::GetUnwindCodeContext
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Retourne le contexte de code représentant un emplacement si une opération de déroulement de pile s'est produite.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetUnwindCodeContext(  
   IDebugCodeContext2 **ppCodeContext  
);  
```  
  
```c#  
int GetUnwindCodeContext(  
   out IDebugCodeContext2 ppCodeContext  
);  
```  
  
#### Paramètres  
 `ppCodeContext`  
 \[out\]  Retourne un objet d' [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) qui représente l'emplacement de contexte de code si le déroulement de pile s'est produite.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Bien que cette méthode peut retourner un contexte de code pour l'emplacement après qu'un déroulement de pile, il ne signifie pas nécessairement le déroulement de pile peut réellement se produire dans le frame de pile actuel.  
  
## Voir aussi  
 [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)