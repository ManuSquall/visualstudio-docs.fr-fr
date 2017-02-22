---
title: "IDiaEnumStackFrames::Next | Microsoft Docs"
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
  - "IDiaEnumStackFrames::Next (méthode)"
ms.assetid: 09378a21-d5e3-4213-b7e2-10f04d85295f
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaEnumStackFrames::Next
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Récupère un nombre spécifié d'éléments du frame de pile de la séquence d'énumération.  
  
## Syntaxe  
  
```cpp#  
HRESULT Next(   
   ULONG             celt,  
   IDiaStackFrame**  rgelt,  
   ULONG*            pceltFetched  
);  
```  
  
#### Paramètres  
 celt  
 \[in\]  Le nombre d'éléments de stackframe dans l'énumérateur à récupérer.  
  
 rgelt  
 \[out\]  Un tableau qui doit être effectuée avec les objets demandés d' [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md) .  
  
 pceltFetched  
 \[out\]  Retourne le nombre d'éléments du frame de pile dans l'énumérateur extrait.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`.  Retourne `S_FALSE` s'il n'y a plus de frames de pile.  Sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md)   
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)