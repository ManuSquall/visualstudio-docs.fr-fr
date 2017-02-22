---
title: "IDiaLineNumber::get_columnNumberEnd | Microsoft Docs"
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
  - "IDiaLineNumber::get_columnNumberEnd (méthode)"
ms.assetid: 02fa56c1-87b6-405a-adee-3bb6bc62de2d
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaLineNumber::get_columnNumberEnd
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Récupère le numéro de colonne source de base 1 où l'expression ou l'instruction se termine.  
  
## Syntaxe  
  
```cpp#  
HRESULT get_columnNumberEnd (   
   DWORD* pRetVal  
);  
```  
  
#### Paramètres  
 `pRetVal`  
 \[out\]  Retourne le numéro de colonne où l'expression ou l'instruction se termine.  Si la valeur est nulle, les informations de fin de colonne ne sont pas présentes.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`.  Retourne `S_FALSE` si cette propriété n'est pas prise en charge.  Sinon, retourne un code d'erreur.  
  
## Notes  
 La valeur de la colonne retournée par cette méthode est un décalage d'octet vers la ligne à la position après le dernier caractère de l'instruction sur la ligne.  
  
## Voir aussi  
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)