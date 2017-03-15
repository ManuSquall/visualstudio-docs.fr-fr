---
title: "IDiaSymbol::get_lexicalParent | Microsoft Docs"
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
  - "IDiaSymbol::get_lexicalParent (méthode)"
ms.assetid: 4d119965-33a8-474c-9c64-95c5218c389c
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDiaSymbol::get_lexicalParent
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Extrait une référence au parent lexicale du symbole.  
  
## Syntaxe  
  
```cpp#  
HRESULT get_lexicalParent (   
   IDiaSymbol** pRetVal  
);  
```  
  
#### Paramètres  
 `pRetVal`  
 \[out\]  Retourne un objet d' [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) qui représente le parent lexicale du symbole.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou un code d'erreur.  
  
> [!NOTE]
>  Une valeur de retour d' `S_FALSE` signifie que la propriété n'est pas disponible pour le symbole.  
  
## Notes  
 Le parent lexicale d'un symbole est la fonction ou le module englobante.  Par exemple, le parent lexicale d'un paramètre de fonction ou d'une variable locale est la fonction elle\-même pendant que le parent lexicale de la fonction est le module qu'elle est définie dans.  
  
 Les symboles pouvant apparaître comme des parents lexicales sont documentés dans [Hiérarchie lexicale des types de symboles](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md).  
  
## Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Hiérarchie lexicale des types de symboles](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)