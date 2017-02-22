---
title: "IDiaEnumTables::Skip | Microsoft Docs"
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
  - "IDiaEnumTables::Skip (méthode)"
ms.assetid: 5c9db956-0654-4f1a-8775-530aa980d8ec
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaEnumTables::Skip
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ignore un nombre spécifié de tables dans une séquence d'énumération.  
  
## Syntaxe  
  
```cpp#  
HRESULT Skip (   
   ULONG celt  
);  
```  
  
#### Paramètres  
 `celt`  
 \[in\]  Le nombre de tables dans la séquence d'énumération à ignorer.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` s'il n'y a plus de tables à ignorer.  
  
## Voir aussi  
 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)