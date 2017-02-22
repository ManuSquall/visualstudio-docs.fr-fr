---
title: "IDiaSymbol::get_typeIds | Microsoft Docs"
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
  - "IDiaSymbol::get_typeIds (méthode)"
ms.assetid: 5166e647-fde5-4efe-92bf-77f8ae3fbc9b
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaSymbol::get_typeIds
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Récupère un tableau de valeurs d'identificateur de type de compilateur\-détail pour ce symbole.  
  
## Syntaxe  
  
```cpp#  
HRESULT get_typeIds (   
   DWORD  cTypeIds,  
   DWORD* pcTypeIds,  
   DWORD  typeIds[]  
);  
```  
  
#### Paramètres  
 `cTypeIds`  
 \[in\]  taille de la mémoire tampon pour contenir les données.  
  
 `pcTypeIds`  
 \[out\]  Retourne le numéro d' `typeIds` écrit, ou, si `typeIds` est `NULL`, puis total d'identificateurs de type disponibles.  
  
 `typeIds[]`  
 \[out\]  Un tableau qui doit être effectuée avec les identificateurs de type.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou un code d'erreur.  
  
> [!NOTE]
>  Une valeur de retour d' `S_FALSE` signifie que la propriété n'est pas disponible pour le symbole.  
  
## Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)