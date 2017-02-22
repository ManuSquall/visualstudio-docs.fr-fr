---
title: "IDiaEnumLineNumbers::Skip | Microsoft Docs"
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
  - "IDiaEnumLineNumbers::Skip (méthode)"
ms.assetid: d182c269-8c76-4d8b-8275-c6807c5ae4e1
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaEnumLineNumbers::Skip
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ignore un nombre spécifié de numéros de ligne dans une séquence d'énumération.  
  
## Syntaxe  
  
```cpp#  
HRESULT Skip (   
   ULONG celt  
);  
```  
  
#### Paramètres  
 celt  
 \[in\]  le nombre de numéros de ligne dans la séquence d'énumération à ignorer.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` s'il n'y a plus de numéros de ligne à ignorer.  
  
## Voir aussi  
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)