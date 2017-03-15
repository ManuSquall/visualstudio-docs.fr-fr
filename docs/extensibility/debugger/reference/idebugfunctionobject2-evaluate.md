---
title: "IDebugFunctionObject2::Evaluate | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugFunctionObject2::Evaluate"
ms.assetid: bc54c652-904b-4297-a6db-faa329684881
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugFunctionObject2::Evaluate
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Appelle la fonction et retourne la valeur résultante en tant qu'objet.  
  
## Syntaxe  
  
```cpp#  
HRESULT Evaluate (  
   IDebugObject** ppParams,  
   DWORD          dwParams,  
   DWORD          dwEvalFlags,  
   DWORD          dwTimeout,  
   IDebugObject** ppResult  
);  
```  
  
```c#  
int Evaluate (  
   IDebugObject     ppParams,  
   uint             dwParams,  
   uint             dwEvalFlags,  
   uint             dwTimeout,  
   out IDebugObject ppResult  
);  
```  
  
#### Paramètres  
 `ppParams`  
 \[in\]  Un tableau d'objets d' [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) qui représente les paramètres d'entrée.  Chacun de ces paramètres a été créé à l'aide d'une des méthodes dans cette interface.  
  
 `dwParams`  
 \[in\]  Le nombre de paramètres dans le tableau d' `ppParams` .  
  
 `dwEvalFlags`  
 \[in\]  Une combinaison des indicateurs d'énumération d' [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) qui spécifient comment l'évaluation doit être exécutée.  
  
 `dwTimeout`  
 \[in\]  Spécifie le temps maximum, en millisecondes, d'attendre avant le retour de cette méthode.  Utilisation **INFINIE** d'attente dure indéfiniment.  
  
 `ppResult`  
 \[out\]  Retourne **un IDebugObject** qui représente la valeur de la fonction en tant qu'objet.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)