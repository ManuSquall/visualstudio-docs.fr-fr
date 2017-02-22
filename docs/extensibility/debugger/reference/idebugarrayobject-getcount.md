---
title: "IDebugArrayObject::GetCount | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugArrayObject::GetCount"
helpviewer_keywords: 
  - "IDebugArrayObject::GetCount (méthode)"
ms.assetid: 7931f3f7-033c-4bf8-8abd-95183952ebb0
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugArrayObject::GetCount
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtient le nombre d'éléments du tableau.  
  
## Syntaxe  
  
```  
[C++]  
HRESULT GetCount(   
   DWORD* pdwElements  
);  
```  
  
```  
[C#]  
int GetCount(  
   out uint pdwElements  
);  
```  
  
#### Paramètres  
 `pdwElements`  
 \[out\]  Retourne le nombre.  
  
## Valeur de retour  
 En cas de réussite, retourne S\_OK ; sinon, retourne un code d'erreur.  
  
## Notes  
 Cette méthode affiche tous les éléments d'un objet tableau comme un tableau unidimensionnel, même si l'objet table est multidimensionnel.  Par exemple, dans le tableau `myarray[3][2][6]`, cette méthode retourne 36 dans le paramètre d' `pdwElements` .  Utilisez la méthode d' [GetElement](../Topic/IDebugArrayObject::GetElement.md) pour récupérer les différents éléments un par un.  
  
## Voir aussi  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)