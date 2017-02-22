---
title: "IDebugArrayObject::GetDimensions | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugArrayObject::GetDimensions"
helpviewer_keywords: 
  - "IDebugArrayObject::GetDimensions (méthode)"
ms.assetid: 113e0aff-9028-49d6-b104-9fe7be4772d7
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugArrayObject::GetDimensions
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtient les dimensions du tableau.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetDimensions(   
   DWORD dwCount,  
   DWORD dwDimensions[]  
);  
```  
  
```c#  
int GetDimensions(  
   [In] uint    dwCount,   
   [Out] uint[] dwDimensions  
);  
```  
  
#### Paramètres  
 `dwCount`  
 \[in\]  Le nombre de dimensions à récupérer.  
  
 `dwDimensions`  
 \[in, out\]  Un tableau qui est terminée avec les tailles de chaque dimension.  `dwCount` spécifie la taille maximale du tableau d' `dwDimensions` .  
  
## Valeur de retour  
 En cas de réussite, retourne S\_OK ; sinon, retourne un code d'erreur.  
  
## Notes  
 Un tableau multidimensionnel peut avoir des tailles différentes pour chaque dimension.  Par exemple, dans la tableau à trois dimensions `myarray[3][2][6]`, cette méthode retourne 3, 2, et 6 dans le paramètre d' `dwDimensions` dans cet ordre.  
  
## Voir aussi  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)