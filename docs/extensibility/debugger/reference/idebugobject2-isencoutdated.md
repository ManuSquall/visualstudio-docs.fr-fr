---
title: "IDebugObject2::IsEncOutdated | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugObject2::IsEncOutdated"
helpviewer_keywords: 
  - "IDebugObject2::IsEncOutdated (méthode)"
ms.assetid: d3a8c02d-895b-478c-9957-d663130f308e
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugObject2::IsEncOutdated
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette méthode détermine si la modification et poursuit l'état de cet objet ou du conteneur parent est obsolète.  Un évaluateur d'expression personnalisé n'applique pas cette méthode et ne retourne pas toujours `E_NOTIMPL`.  
  
## Syntaxe  
  
```cpp  
HRESULT IsEncOutdated(  
   BOOL* pfEncOutdated  
);  
```  
  
```c#  
int IsEncOutdated(  
   out int pfEncOutdated  
);  
```  
  
#### Paramètres  
 `pfEncOutdated`  
 \[out\]  Une valeur différente de zéro \(`TRUE`\) si la modification et reprenez l'état est obsolète, zéro \(`FALSE`\) s'il n'est pas.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
> [!NOTE]
>  Un évaluateur d'expression personnalisé doit toujours retourner `E_NOTIMPL`.  
  
## Voir aussi  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)