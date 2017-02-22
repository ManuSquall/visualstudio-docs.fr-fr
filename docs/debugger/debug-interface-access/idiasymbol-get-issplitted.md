---
title: "IDiaSymbol::get_isSplitted | Microsoft Docs"
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
  - "IDiaSymbol::get_isSplitted (méthode)"
ms.assetid: ff160cf6-003b-4ef5-a406-20a7b287b2bf
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaSymbol::get_isSplitted
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Extrait une balise qui spécifie si le symbole de données a été fractionné en regroupement ou collection d'autres symboles ; le compilateur traite les symboles en tant qu'entités distinctes, bien qu'elles soient réellement partie d'un plus grand symbole.  
  
## Syntaxe  
  
```cpp  
HRESULT get_isSplitted(  
   BOOL *pFlag  
);  
```  
  
#### Paramètres  
 `pFlag`  
 \[out\]  Retourne `TRUE` si le symbole a été fractionné en agrégat de symboles ; sinon, retourne `FALSE`.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou un code d'erreur.  
  
> [!NOTE]
>  Une valeur de retour d' `S_FALSE` signifie que la propriété n'est pas disponible pour le symbole.  
  
## Notes  
 La méthode d' [IDiaSymbol::get\_isAggregated](../../debugger/debug-interface-access/idiasymbol-get-isaggregated.md) retourne `TRUE` de tous les symboles qui font partie d'un symbole fractionné.  
  
## Configuration requise  
  
|Spécification|Description|  
|-------------------|-----------------|  
|en\-tête :|dia2.h|  
|version :|diamètre Kit de développement logiciel v8.0|  
  
## Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaSymbol::get\_isAggregated](../../debugger/debug-interface-access/idiasymbol-get-isaggregated.md)