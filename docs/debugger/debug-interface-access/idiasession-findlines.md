---
title: "IDiaSession::findLines | Microsoft Docs"
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
  - "IDiaSession::findLines (méthode)"
ms.assetid: d6e84916-fd55-457e-b057-57f97b51fe73
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaSession::findLines
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Récupère les numéros de ligne dans les ID spécifiés de module \(compiland\) et du fichier source.  
  
## Syntaxe  
  
```cpp#  
HRESULT findLines (   
   IDiaSymbol*           compiland,  
   IDiaSourceFile*       file,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### Paramètres  
 `compiland`  
 \[in\]Un objet d' [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) représentant le module \(compiland\).  Utilisez cette interface comme un contexte dans lequel vous pouvez rechercher les numéros de ligne.  
  
 `file`  
 \[in\]  Un objet d' [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) représentant le fichier source dans lequel vous pouvez rechercher les numéros de ligne.  
  
 `ppResult`  
 \[out\]  Retourne un objet d' [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md) qui contient une liste des numéros de ligne récupérés.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)