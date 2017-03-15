---
title: "IDebugFunctionObject::Evaluate | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugFunctionObject::Evaluate"
helpviewer_keywords: 
  - "IDebugFunctionObject::Evaluate (méthode)"
ms.assetid: 29349ea3-d5c1-4135-aa76-ced073ab9683
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugFunctionObject::Evaluate
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Appelle la fonction et retourne la valeur résultante en tant qu'objet.  
  
## Syntaxe  
  
```cpp#  
HRESULT Evaluate(   
   IDebugObject** ppParams,  
   DWORD          dwParams,  
   DWORD          dwTimeout,  
   IDebugObject** ppResult  
);  
```  
  
```c#  
int Evaluate(  
   IDebugObject[]   ppParams,   
   IntPtr           dwParams,   
   uint             dwTimeout,   
   out IDebugObject ppResult  
);  
```  
  
#### Paramètres  
 `ppParams`  
 \[in\]  Un tableau d'objets d' [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) représentant les paramètres d'entrée.  chacun de ces paramètres a été créé avec une des méthodes d' `Create` dans l'interface d' [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) .  
  
 `dwParams`  
 \[in\]  Le nombre de paramètres dans le tableau d' `ppParams` .  
  
 `dwTimeout`  
 \[in\]  Spécifie le temps maximum, en millisecondes, d'attendre avant le retour de cette méthode.  Utilisation `INFINITE` d'attente dure indéfiniment.  
  
 `ppResult`  
 \[out\]  Retourne [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) représentant la valeur de la fonction en tant qu'objet.  
  
## Valeur de retour  
 En cas de réussite, retourne S\_OK ; sinon, retourne un code d'erreur.  
  
## Notes  
 Cette méthode est installé et s'exécute un appel à la fonction représentée par l'objet d' [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) .  
  
## Voir aussi  
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)