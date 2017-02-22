---
title: "IDebugAlias::GetObject | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugAlias::GetObject"
helpviewer_keywords: 
  - "IDebugAlias::GetObject (méthode)"
ms.assetid: 97bc3af6-6e55-4940-8a6d-692c61257806
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# IDebugAlias::GetObject
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

obtient l'objet que cet alias est pour.  
  
## Syntaxe  
  
```cpp  
HRESULT GetObject(  
   IDebugObject2** ppObject  
);  
```  
  
```c#  
int GetObject(  
   Out IDebugObject2 ppObject  
)  
```  
  
#### Paramètres  
 `ppObject`  
 \[out\]  [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) que cet alias représente.  
  
## Valeur de retour  
 En cas de réussite, retourne S\_OK ; sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)   
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)