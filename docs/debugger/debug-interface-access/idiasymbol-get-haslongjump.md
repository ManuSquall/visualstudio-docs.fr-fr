---
title: "IDiaSymbol::get_hasLongJump | Microsoft Docs"
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
  - "IDiaSymbol::get_hasLongJump (méthode)"
ms.assetid: 14484cb1-43b0-47a1-a9a8-081b55566886
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaSymbol::get_hasLongJump
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Extrait une balise qui spécifie si la fonction contient une utilisation de la commande de [longjmp](/visual-cpp/c-runtime-library/reference/longjmp) \(associée à une commande de [setjmp](/visual-cpp/c-runtime-library/reference/setjmp) , ils forment la méthode de style C de gestion des exceptions\).  
  
## Syntaxe  
  
```cpp#  
HRESULT get_hasLongJump  
   BOOL *pFlag  
);  
```  
  
#### Paramètres  
 `pFlag`  
 \[out\]  Retourne `TRUE` si la fonction contient une commande d' `longjmp` ; sinon, retourne `FALSE`.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou un code d'erreur.  
  
> [!NOTE]
>  Une valeur de retour d' `S_FALSE` signifie que la propriété n'est pas disponible pour le symbole.  
  
## Configuration requise  
  
|Spécification|Description|  
|-------------------|-----------------|  
|en\-tête :|dia2.h|  
|version :|diamètre Kit de développement logiciel v8.0|  
  
## Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaSymbol::get\_hasSetJump](../../debugger/debug-interface-access/idiasymbol-get-hassetjump.md)   
 [longjmp](/visual-cpp/c-runtime-library/reference/longjmp)   
 [setjmp](/visual-cpp/c-runtime-library/reference/setjmp)