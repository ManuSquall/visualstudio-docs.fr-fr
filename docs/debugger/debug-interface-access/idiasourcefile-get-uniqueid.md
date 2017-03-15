---
title: "IDiaSourceFile::get_uniqueId | Microsoft Docs"
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
  - "IDiaSourceFile::get_uniqueId (méthode)"
ms.assetid: e0b8dbc0-6061-4f31-bead-2cd72be44e41
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaSourceFile::get_uniqueId
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Récupère une valeur de clé entière simple qui est unique pour cette image.  
  
## Syntaxe  
  
```cpp#  
HRESULT get_uniqueId (   
   DWORD* pRetVal  
);  
```  
  
#### Paramètres  
 `pRetVal`  
 \[out\]  Retourne une valeur de clé entière simple qui est unique pour cette image.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Comparaison de clés plutôt que des chaînes peut accélérer le traitement de numéro de ligne.  
  
## Voir aussi  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)