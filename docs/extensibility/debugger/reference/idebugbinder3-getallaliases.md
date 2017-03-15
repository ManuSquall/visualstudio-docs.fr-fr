---
title: "IDebugBinder3::GetAllAliases | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBinder3::GetAllAliases"
helpviewer_keywords: 
  - "IDebugBinder3::GetAllAliases (méthode)"
ms.assetid: 1f9ab2ee-2ab3-4a61-8b99-95dd7fdf3511
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# IDebugBinder3::GetAllAliases
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

cette méthode extrait une liste d'alias du programme.  
  
## Syntaxe  
  
```cpp  
HRESULT GetAllAliases(  
   UINT          uRequest,  
   IDebugAlias** ppAliases,  
   UINT*         puFetched  
);  
```  
  
```c#  
int GetAllAliases(  
   uint          uRequest,   
   IDebugAlias[] ppAliases,   
   out uint      puFetched  
);  
```  
  
#### Paramètres  
 `uRequest`  
 \[in\]  Le nombre maximal d'alias à retourner \(spécifie la longueur du tableau passé dans `ppAliases`\).  
  
 `ppAliases`  
 \[in, out\]  Tableau à remplir avec des alias \(dans le cas d'une valeur NULL et `uRequest` est 0, le nombre d'alias qui peuvent être retournés sera retourné par `puFetched`\).  
  
 `puFetched`  
 \[out\]  Retourne le nombre d'alias obtenus.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)