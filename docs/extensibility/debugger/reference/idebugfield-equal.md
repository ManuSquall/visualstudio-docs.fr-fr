---
title: "IDebugField::Equal | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugField::Equal"
helpviewer_keywords: 
  - "IDebugField::Equal (méthode)"
ms.assetid: 75369fe6-ddd3-497d-80d1-2488e6100e9f
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugField::Equal
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

cette méthode compare ce champ avec le champ spécifié pour l'égalité.  
  
## Syntaxe  
  
```cpp#  
HRESULT Equal(   
   IDebugField* pField  
);  
```  
  
```c#  
int Equal(  
   IDebugField pField  
);  
```  
  
#### Paramètres  
 `pField`  
 \[in\]  le champ à comparer à celui\-ci.  
  
## Valeur de retour  
 Si les champs sont identiques, retourne `S_OK`.  Si les champs sont différents, retourne `S_FALSE.` sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)