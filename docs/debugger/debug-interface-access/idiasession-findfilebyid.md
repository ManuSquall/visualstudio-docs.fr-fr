---
title: "IDiaSession::findFileById | Microsoft Docs"
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
  - "IDiaSession::findFileById (méthode)"
ms.assetid: 710efe04-78b5-4f3e-a1d8-f9b069063503
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDiaSession::findFileById
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Extrait un fichier source par l'identificateur du fichier source.  
  
## Syntaxe  
  
```cpp#  
HRESULT findFileById (   
   DWORD            uniqueId,  
   IDiaSourceFile** ppResult  
);  
```  
  
#### Paramètres  
 `uniqueId`  
 \[in\]  spécifie l'identificateur de fichier source.  
  
 `ppResult`  
 \[out\]  Retourne un objet d' [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) qui représente le fichier source extrait.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 l'identificateur de fichier source est une valeur unique utilisée en interne au diamètre Kit de développement logiciel pour rendre tous les fichiers sources uniques.  Cette méthode est généralement utilisée en interne au diamètre Kit de développement logiciel.  
  
## Voir aussi  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)   
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)