---
title: "IDiaLineNumber::get_sourceFileId | Microsoft Docs"
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
  - "IDiaLineNumber::get_sourceFileId (méthode)"
ms.assetid: 4f482a1e-e85f-4173-98de-8e5f7622554b
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaLineNumber::get_sourceFileId
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Récupère un identificateur unique de fichier source pour le fichier source qui a fourni cette ligne.  
  
## Syntaxe  
  
```cpp#  
HRESULT get_sourceFileId (   
   DWORD* pRetVal  
);  
```  
  
#### Paramètres  
 `pRetVal`  
 \[out\]  Retourne l'identificateur unique de fichier source pour le fichier source qui a fourni cette ligne.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`.  Retourne `S_FALSE` si cette propriété n'est pas prise en charge.  Sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)