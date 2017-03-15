---
title: "IDiaSymbol::get_types | Microsoft Docs"
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
  - "IDiaSymbol::get_types (méthode)"
ms.assetid: 5f056e0c-e15b-4e00-8f78-aadc8574f7ea
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaSymbol::get_types
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Récupère un tableau de types de compilateur\-détail pour ce symbole.  
  
## Syntaxe  
  
```cpp#  
HRESULT get_types (   
   DWORD       cTypes,  
   DWORD*      pcTypes,  
   IDiaSymbol* types[]  
);  
```  
  
#### Paramètres  
 `cTypes`  
 \[in\]  taille de la mémoire tampon pour contenir les données.  
  
 `pcTypes`  
 \[out\]  Retourne le nombre de types développés, ou, si le paramètre d' `types` est `NULL`, puis de tout le nombre de types disponibles.  
  
 `types[]`  
 \[out\]  Un tableau qui doit être effectuée avec les objets d' [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) qui représentent tous les types de ce symbole.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou un code d'erreur.  
  
> [!NOTE]
>  Une valeur de retour d' `S_FALSE` signifie que la propriété n'est pas disponible pour le symbole.  
  
## Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)