---
title: "IDebugArrayField::GetNumberOfElements | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugArrayField::GetNumberOfElements"
helpviewer_keywords: 
  - "IDebugArrayField::GetNumberOfElements (méthode)"
ms.assetid: a1961ef3-d69d-4022-b8c9-b9cfb9811345
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugArrayField::GetNumberOfElements
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtient le nombre d'éléments du tableau.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetNumberOfElements(   
   DWORD* pdwNumElements  
);  
```  
  
```c#  
int GetNumberOfElements(  
   out uint pdwNumElements  
);  
```  
  
#### Paramètres  
 `pdwNumElements`  
 \[out\]  Retourne le nombre d'éléments du tableau.  
  
## Valeur de retour  
 En cas de réussite, retourne S\_OK ; sinon, retourne un code d'erreur.  
  
## Notes  
 La valeur retournée correspond au nombre total d'éléments du tableau, indépendamment du nombre de dimensions.  
  
## Voir aussi  
 [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)