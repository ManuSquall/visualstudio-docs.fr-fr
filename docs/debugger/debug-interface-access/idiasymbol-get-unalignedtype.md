---
title: "IDiaSymbol::get_unalignedType | Microsoft Docs"
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
  - "IDiaSymbol::get_unalignedType (méthode)"
ms.assetid: fdcb38fb-490e-4d15-b4e5-3770043a366c
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaSymbol::get_unalignedType
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Extrait une balise qui indique si le type de données défini par l'utilisateur est aligné.  
  
## Syntaxe  
  
```cpp#  
HRESULT get_unalignedType (   
   BOOL* pRetVal  
);  
```  
  
#### Paramètres  
 `pRetVal`  
 \[out\]  Retourne `TRUE` si le type de données défini par l'utilisateur est aligné ; sinon, retourne `FALSE`.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou un code d'erreur.  
  
> [!NOTE]
>  Une valeur de retour d' `S_FALSE` signifie que la propriété n'est pas disponible pour le symbole.  
  
## Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)