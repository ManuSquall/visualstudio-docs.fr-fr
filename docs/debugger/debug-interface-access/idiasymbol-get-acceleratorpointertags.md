---
title: "IDiaSymbol::get_acceleratorPointerTags | Microsoft Docs"
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
ms.assetid: 30e13cee-e511-49ec-affd-99b0097071b2
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IDiaSymbol::get_acceleratorPointerTags
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Retourne toutes les valeurs d'indicateur de pointeur d'accélérateur qui correspondent à la fonction du stub d'accélérateur C\+\+ ampère.  
  
## Syntaxe  
  
```cpp  
HRESULT get_acceleratorPointerTags(   
   DWORD          cnt,  
   DWORD*         pcnt,  
   DWORD*         pPointerTags);  
```  
  
#### Paramètres  
 `cnt`  
 \[in\]  La taille du tableau de sortie `pPointerTags`.  
  
 `pcnt`  
 \[out\]  Le nombre de balises de pointeur d'accélérateur dans la fonction du stub d'accélérateur C\+\+ ampère.  
  
 `pPointerTags`  
 \[out\]  Un pointeur de tableau d' `DWORD` rempli avec la balise du pointeur d'accélérateur valeurs dans la fonction du stub d'accélérateur C\+\+ ampère.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou code d'erreur.  
  
## Notes  
 Cette méthode est appelée sur une interface d' `IDiaSymbol` qui correspond à la fonction du stub d'accélérateur C\+\+ ampère.  
  
## Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)