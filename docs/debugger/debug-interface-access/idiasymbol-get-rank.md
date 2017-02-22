---
title: "IDiaSymbol::get_rank | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaSymbol::get_rank (méthode)"
ms.assetid: 14cc9c4b-a5ec-414a-b01f-4a142c17b7cc
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaSymbol::get_rank
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Récupère le rang \(nombre de dimensions\) d'un tableau multidimensionnel FORTRAN.  
  
## Syntaxe  
  
```cpp#  
HRESULT get_rank (   
   DWORD* pRetVal  
);  
```  
  
#### Paramètres  
 `pRetVal`  
 \[out\]  Retourne le nombre de dimensions d'un tableau multidimensionnel FORTRAN.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou un code d'erreur.  
  
> [!NOTE]
>  Une valeur de retour d' `S_FALSE` signifie que la propriété n'est pas disponible pour le symbole.  
  
## Notes  
 Le rang fait référence au nombre de dimensions d'un tableau où le tableau est déclaré comme `myarray[1,2,3]`.  Cet exemple a un rang de 3 et 3.  Classement ne s'applique pas à C\+\+ qui utilise le concept d'un tableau de tableaux pour chaque dimension \(autrement dit, `myarray[1][2][3]`\).  
  
## Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)