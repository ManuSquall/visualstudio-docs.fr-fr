---
title: "IDebugArrayObject::GetRank | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugArrayObject::GetRank"
helpviewer_keywords: 
  - "IDebugArrayObject::GetRank (méthode)"
ms.assetid: 9948551a-e334-4ff6-979c-08dab633b9b6
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugArrayObject::GetRank
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtient le rang du tableau, c. autrement dit., le nombre de dimensions.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetRank(   
   DWORD* pdwRank  
);  
```  
  
```c#  
int GetRank(  
   out uint pdwRank  
);  
```  
  
#### Paramètres  
 `pdwRank`  
 \[out\]  Retourne le classement.  
  
## Valeur de retour  
 En cas de réussite, retourne S\_OK ; sinon, retourne un code d'erreur.  
  
## Notes  
 Utilisez la méthode d' [GetDimensions](../../../extensibility/debugger/reference/idebugarrayobject-getdimensions.md) pour récupérer la taille de chaque dimension de l'objet table.  
  
## Voir aussi  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)