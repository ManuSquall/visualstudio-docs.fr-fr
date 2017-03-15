---
title: "IDebugFunctionObject::CreateObject | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugFunctionObject::CreateObject"
helpviewer_keywords: 
  - "IDebugFunctionObject::CreateObject (méthode)"
ms.assetid: c4c99dd5-609a-4e7c-8f29-eb728f57e995
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugFunctionObject::CreateObject
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Crée un objet à l'aide d'un constructeur.  
  
## Syntaxe  
  
```cpp#  
HRESULT CreateObject(   
   IDebugFunctionObject* pConstructor,  
   DWORD                 dwArgs,  
   IDebugObject*         pArgs[],  
   IDebugObject**        ppObject  
);  
```  
  
```c#  
int CreateObject(  
   IDebugFunctionObject pConstructor,   
   uint                 dwArgs,   
   IDebugObject[]       pArgs,   
   out IDebugObject     ppObject  
);  
```  
  
#### Paramètres  
 `pConstructor`  
 \[in\]  un objet d' [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) représentant le constructeur de l'objet à créer.  
  
 `dwArgs`  
 \[in\]  Le nombre de paramètres dans le tableau d'`pArg` .  représente le nombre de paramètres passés au constructeur.  
  
 `pArg`  
 \[in\]  Un tableau d'objets d' [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) représentant les paramètres sont passés au constructeur.  
  
 `ppObject`  
 \[out\]  Retourne `IDebugObject` représentant l'objet nouvellement créé.  
  
## Valeur de retour  
 En cas de réussite, retourne S\_OK ; sinon, retourne un code d'erreur.  
  
## Notes  
 Appelez cette méthode pour créer un objet qui représente une instance d'une classe \(ou un autre type complexe qui requiert un constructeur\) qui est un paramètre de la fonction qui est représentée par l'interface d' [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) .  
  
 Si le paramètre d'objet ne requiert pas de constructeur, appelez la méthode d' [CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md) .  
  
## Voir aussi  
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)   
 [CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md)