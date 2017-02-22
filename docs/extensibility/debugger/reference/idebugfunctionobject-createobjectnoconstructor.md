---
title: "IDebugFunctionObject::CreateObjectNoConstructor | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugFunctionObject::CreateObjectNoConstructor"
helpviewer_keywords: 
  - "IDebugFunctionObject::CreateObjectNoConstructor (méthode)"
ms.assetid: 4e2bd6d5-f4bd-4c10-a998-3db451c9a0c8
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugFunctionObject::CreateObjectNoConstructor
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

crée un objet sans le constructeur.  
  
## Syntaxe  
  
```cpp#  
HRESULT CreateObjectNoConstructor(   
   IDebugField*   pClassObject,  
   IDebugObject** ppObject  
);  
```  
  
```c#  
int CreateObjectNoConstructor(  
   IDebugField      pClassField,   
   out IDebugObject ppObject  
);  
```  
  
#### Paramètres  
 `pClassObject`  
 \[in\]  Un objet d' [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) qui représente le type de l'objet à créer.  
  
 `ppObject`  
 \[out\]  Retourne [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) représentant l'objet nouvellement créé.  
  
## Valeur de retour  
 En cas de réussite, retourne S\_OK ; sinon, retourne un code d'erreur.  
  
## Notes  
 Appelez cette méthode pour créer un objet qui représente une instance d'une structure ou d'un type complexe \(qui ne requiert pas de constructeur\) qui est un paramètre de la fonction qui est représentée par l'interface d' [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) .  
  
 si le paramètre d'objet requiert un constructeur, appelez la méthode d' [CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject-createobject.md) .  
  
## Voir aussi  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)   
 [CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject-createobject.md)