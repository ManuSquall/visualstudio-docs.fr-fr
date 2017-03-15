---
title: "IDiaEnumSourceFiles::Next | Microsoft Docs"
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
  - "IDiaEnumSourceFiles::Next (méthode)"
ms.assetid: 83bf6317-ff39-4c5c-8987-cba34e7a6983
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaEnumSourceFiles::Next
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Récupère un nombre spécifié de fichiers sources dans la séquence d'énumération.  
  
## Syntaxe  
  
```cpp#  
HRESULT Next (   
   ULONG            celt,  
   IDiaSourceFile** rgelt,  
   ULONG*           pceltFetched  
);  
```  
  
#### Paramètres  
 celt  
 \[in\]  Le nombre de fichiers sources dans l'énumérateur à récupérer.  
  
 rgelt  
 \[out\]Un tableau qui doit être effectuée avec les objets d' [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) qui représentent les fichiers sources souhaités.  
  
 pceltFetched  
 \[out\]  Retourne le nombre de fichiers sources dans l'énumérateur extrait.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`.  Retourne `S_FALSE` s'il n'y a plus de fichiers sources.  Sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)   
 [IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)   
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)