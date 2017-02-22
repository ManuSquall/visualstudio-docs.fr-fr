---
title: "IDebugObject2::GetField | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugObject2::GetField"
helpviewer_keywords: 
  - "IDebugObject2::GetField (méthode)"
ms.assetid: add6a6b5-e752-47dd-9613-29206ea809b0
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# IDebugObject2::GetField
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

obtient le type de cet objet.  
  
## Syntaxe  
  
```cpp  
HRESULT GetField(  
 IDebugField** ppField  
);  
```  
  
```c#  
int GetField(  
   out IDebugField ppField  
);  
```  
  
#### Paramètres  
 `ppField`  
 \[out\]  Retourne un objet d' [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) sinon une valeur NULL.  
  
## Valeur de retour  
 En cas de réussite, retourne S\_OK ; sinon, retourne un code d'erreur.  
  
## Notes  
 un champ décrit le type de l'objet.  
  
## Voir aussi  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)