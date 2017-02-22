---
title: "IDiaEnumLineNumbers::Item | Microsoft Docs"
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
  - "IDiaEnumLineNumbers::Item (méthode)"
ms.assetid: 08efbeaf-22f7-49e9-96a8-bb906dfe4fd8
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaEnumLineNumbers::Item
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Récupère un numéro de ligne à l'aide d'un index.  
  
## Syntaxe  
  
```cpp#  
HRESULT Item (   
   DWORD            index,  
   IDiaLineNumber** lineNumber  
);  
```  
  
#### Paramètres  
 index  
 \[in\]  Index de l'objet d' [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md) à récupérer.  L'index est comprise entre 0 et `count`\-1, où `count` est retourné par la méthode d' [IDiaEnumLineNumbers::get\_Count](../../debugger/debug-interface-access/idiaenumlinenumbers-get-count.md) .  
  
 numéroligne  
 \[out\]  Retourne un objet d' [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md) représentant le numéro de ligne souhaité.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)   
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)