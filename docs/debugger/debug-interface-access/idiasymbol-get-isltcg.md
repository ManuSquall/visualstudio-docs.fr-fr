---
title: "IDiaSymbol::get_isLTCG | Microsoft Docs"
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
  - "IDiaSymbol::get_isLTCG (méthode)"
ms.assetid: 5f7f05b8-6b71-4958-9e1e-e4924ef9c59b
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaSymbol::get_isLTCG
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Extrait une balise qui spécifie si [Compiland](../../debugger/debug-interface-access/compiland.md) a été lié avec le commutateur [\/LTCG \(Génération de code durant l'édition de liens\)](/visual-cpp/build/reference/ltcg-link-time-code-generation)de l'éditeur de liens, qui facilite l'optimisation du programme.  Ce commutateur s'applique uniquement au code managé.  
  
## Syntaxe  
  
```cpp  
HRESULT get_iSLTCG(  
   BOOL *pFlag  
);  
```  
  
#### Paramètres  
 pFlag  
 \[out\]  Retourne `TRUE` si `compiland` a été lié avec le commutateur de l'éditeur de liens \/LTCG ; sinon, retourne `FALSE`.  
  
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