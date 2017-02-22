---
title: "IDebugBinder3::GetTypeArguments | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBinder3::GetTypeArguments"
helpviewer_keywords: 
  - "IDebugBinder3::GetTypeArguments (méthode)"
ms.assetid: fa0c37a7-327f-463e-9a9d-bb3f534584cb
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# IDebugBinder3::GetTypeArguments
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette méthode extrait une liste de types d'argument associés à cet objet.  
  
## Syntaxe  
  
```cpp  
HRESULT GetTypeArguments(  
   UINT          skip,  
   UINT          count,  
   IDebugField** ppFields,  
   UINT*         pFetched  
);  
```  
  
```c#  
int GetTypeArguments(  
   uint          skip,  
   uint          count,  
   IDebugField[] ppFields,  
   out uint      pFetched  
);  
```  
  
#### Paramètres  
 `skip`  
 \[in\]Nombre de champs à ignorer avant d'obtenir des types d'argument.  
  
 `count`  
 \[in\]  Le nombre de champs d'argument à retourner \(spécifie également la taille du tableau d' `ppFields` \).  
  
 `ppFields`  
 \[in, out\]  Un tableau de champs qui seront ajoutés au retour de cette méthode.  
  
 `pFetched`  
 \[out\]  \(facultatif\) le nombre de champs de type d'argument s'est retourné.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 le nombre de types d'argument peut être obtenu à l'avance avec [GetTypeArgumentCount](../Topic/IDebugBinder3::GetTypeArgumentCount.md).  
  
## Voir aussi  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)   
 [GetTypeArgumentCount](../Topic/IDebugBinder3::GetTypeArgumentCount.md)