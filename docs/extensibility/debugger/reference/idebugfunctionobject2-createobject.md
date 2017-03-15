---
title: "IDebugFunctionObject2::CreateObject | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugFunctionObject2::CreateObject"
  - "CreateObject"
ms.assetid: 148de615-941e-4b64-ab11-75b692aae465
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugFunctionObject2::CreateObject
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Crée un objet qui utilise un constructeur donné des paramètres de balise d'évaluation et une valeur de délai d'attente.  
  
## Syntaxe  
  
```cpp#  
HRESULT CreateObject (  
   IDebugFunctionObject* pConstructor,  
   DWORD                 dwArgs,  
   IDebugObject*         pArgs[],  
   DWORD                 dwEvalFlags,  
   DWORD                 dwTimeout,  
   IDebugObject**        ppObject  
);  
```  
  
```c#  
int CreateObject (  
   IDebugFunctionObject pConstructor,  
   uint                 dwArgs,  
   IDebugObject[]       pArgs,  
   uint                 dwEvalFlags,  
   uint                 dwTimeout,  
   out IDebugObject**   ppObject  
);  
```  
  
#### Paramètres  
 `pConstructor`  
 \[in\]  un objet d' [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) qui représente le constructeur de l'objet à créer.  
  
 `dwArgs`  
 \[in\]  Le nombre de paramètres dans le tableau d' `pArg` .  représente le nombre de paramètres passés au constructeur.  
  
 `pArgs`  
 \[in\]  Un tableau d'objets d' [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) qui représente les paramètres sont passés au constructeur.  
  
 `dwEvalFlags`  
 \[in\]  Une combinaison des indicateurs d'énumération d' [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) qui spécifient comment l'évaluation doit être exécutée.  
  
 `dwTimeout`  
 \[in\]  Durée maximale, en millisecondes, d'attendre avant le retour de cette méthode.  Utilisation **INFINIE** d'attente dure indéfiniment.  
  
 `ppObject`  
 \[out\]  Retourne **un IDebugObject** représentant l'objet nouvellement créé.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 appelez cette méthode pour créer un objet qui représente une instance d'une classe, ou tout autre type complexe qui requiert un constructeur, qui est un paramètre.  
  
## Voir aussi  
 [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)