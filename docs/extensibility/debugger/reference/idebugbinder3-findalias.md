---
title: "IDebugBinder3::FindAlias | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBinder3::FindAlias"
helpviewer_keywords: 
  - "IDebugBinder3::FindAlias (méthode)"
ms.assetid: b8333701-2718-4983-8513-0875fb7cb730
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugBinder3::FindAlias
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette méthode localise un alias, étant donné un nom.  Cela va trouver tous les alias dans le programme.  
  
## Syntaxe  
  
```cpp  
HRESULT FindAlias(  
   LPCOLESTR     pcstrName,  
   IDebugAlias** ppAlias  
);  
```  
  
```c#  
int FindAlias(  
   string          pcstrName,  
   out IDebugAlias ppAlias  
);  
```  
  
#### Paramètres  
 `pcstrName`  
 \[in\]  Nom de l'alias à rechercher.  
  
 `ppAlias`  
 \[out\]  Alias trouvé \(le cas échéant\) désigné par l'interface d' [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) .  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` \(si l'alias est introuvable\) ou un code d'erreur.  
  
## Notes  
 cette méthode initialise l'objet de destination à null avant d'appeler ; il teste une valeur NULL après pour déterminer si l'alias a été trouvé.  
  
## Voir aussi  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)   
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)