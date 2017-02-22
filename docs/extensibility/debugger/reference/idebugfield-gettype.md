---
title: "IDebugField::GetType | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugField::GetType"
helpviewer_keywords: 
  - "IDebugField::GetType (méthode)"
ms.assetid: b3cdec9f-ef7b-44d0-a775-d17ef7eae968
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugField::GetType
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette méthode extrait le type de champ.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetType(   
   IDebugField** ppType  
);  
```  
  
```c#  
int GetType(  
   out IDebugField ppType  
);  
```  
  
#### Paramètres  
 `ppType`  
 \[out\]  Retourne le type de champ comme un autre objet d' [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) .  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)