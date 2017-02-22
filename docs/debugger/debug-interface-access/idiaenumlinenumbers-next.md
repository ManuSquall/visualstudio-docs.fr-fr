---
title: "IDiaEnumLineNumbers::Next | Microsoft Docs"
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
  - "IDiaEnumLineNumbers::Next (méthode)"
ms.assetid: 363d5b40-1316-4ab8-836f-63637f619e0a
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaEnumLineNumbers::Next
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Récupère un nombre spécifié de numéros de ligne dans la séquence d'énumération.  
  
## Syntaxe  
  
```cpp#  
HRESULT Next (   
   ULONG            celt,  
   IDiaLineNumber** rgelt,  
   ULONG*           pceltFetched  
);  
```  
  
#### Paramètres  
 celt  
 \[in\]  Le nombre de numéros de ligne dans l'énumérateur à récupérer.  
  
 rgelt  
 \[out\]  Retourne un tableau d'objets d' [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md) qui représentent les numéros de ligne souhaités.  
  
 pceltFetched  
 \[out\]  Retourne le nombre de numéros de ligne dans l'énumérateur extrait.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`.  Retourne `S_FALSE` s'il n'y a plus de numéros de ligne.  Sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)   
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)   
 [IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)