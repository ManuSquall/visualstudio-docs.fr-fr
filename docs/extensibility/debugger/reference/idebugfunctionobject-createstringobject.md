---
title: "IDebugFunctionObject::CreateStringObject | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugFunctionObject::CreateStringObject"
helpviewer_keywords: 
  - "IDebugFunctionObject::CreateStringObject (méthode)"
ms.assetid: fd6070ab-07d4-4ea1-8d71-b16592d6f1a7
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugFunctionObject::CreateStringObject
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Crée un objet chaîne.  
  
## Syntaxe  
  
```cpp#  
HRESULT CreateStringObject(   
   LPCOLESTR      pcstrString,  
   IDebugObject** ppObject  
);  
```  
  
```c#  
int CreateStringObject(  
   string      pcstrString,   
   out IDebugObject ppOjbect  
);  
```  
  
#### Paramètres  
 `pcstrString`  
 \[in\]  La valeur de chaîne de l'objet String.  
  
 `ppObject`  
 \[out\]  Retourne un objet d' [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) qui représente l'objet String nouvellement créée.  
  
## Valeur de retour  
 En cas de réussite, retourne S\_OK ; sinon, retourne un code d'erreur.  
  
## Notes  
 Appelez cette méthode pour créer un objet qui représente une chaîne qui est un paramètre de la fonction qui est représentée par l'interface d' [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) .  
  
## Voir aussi  
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)