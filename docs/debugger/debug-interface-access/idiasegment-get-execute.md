---
title: "IDiaSegment::get_execute | Microsoft Docs"
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
  - "IDiaSegment::get_execute (méthode)"
ms.assetid: 746cdf8e-9097-415d-ba10-069854153185
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaSegment::get_execute
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

extrait une balise qui indique si le segment est exécutable.  
  
## Syntaxe  
  
```cpp#  
HRESULT get_execute (   
   BOOL* pRetVal  
);  
```  
  
#### Paramètres  
 `pRetVal`  
 \[out\]  Retourne `TRUE` si le segment est marqué comme exécutable ; sinon, retourne `FALSE`.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`.  Retourne `S_FALSE` si cette propriété n'est pas prise en charge.  Sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)