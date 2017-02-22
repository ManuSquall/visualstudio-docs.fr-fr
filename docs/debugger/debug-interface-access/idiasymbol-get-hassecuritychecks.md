---
title: "IDiaSymbol::get_hasSecurityChecks | Microsoft Docs"
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
  - "IDiaSymbol::get_hasSecurityChecks (méthode)"
ms.assetid: 4bb51f62-8645-41a4-bc44-1451010623fd
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaSymbol::get_hasSecurityChecks
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Extrait une balise qui spécifie si le module ou la fonction a été compilé avec des vérifications de sécurité de dépassement de mémoire tampon \(par exemple, le commutateur de compilation de [\/GS \(vérification de la sécurité des mémoires tampons\)](/visual-cpp/build/reference/gs-buffer-security-check) \).  
  
## Syntaxe  
  
```cpp#  
HRESULT get_hasSecurityChecks(  
   BOOL *pFlag  
);  
```  
  
#### Paramètres  
 `pFlag`  
 \[out\]  Retourne `TRUE` si la fonction a des vérifications de sécurité ; sinon, retourne `FALSE`.  
  
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
 [\/GS \(vérification de la sécurité des mémoires tampons\)](/visual-cpp/build/reference/gs-buffer-security-check)