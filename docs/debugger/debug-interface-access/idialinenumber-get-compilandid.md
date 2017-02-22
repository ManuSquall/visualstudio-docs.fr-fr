---
title: "IDiaLineNumber::get_compilandId | Microsoft Docs"
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
  - "IDiaLineNumber::get_compilandId (méthode)"
ms.assetid: 2cd6f551-8091-47c7-803f-3f79a766a211
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaLineNumber::get_compilandId
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Extrait un identificateur unique pour le module qui a fourni cette ligne.  
  
## Syntaxe  
  
```cpp#  
HRESULT get_compilandId (   
   DWORD* pRetVal  
);  
```  
  
#### Paramètres  
 `pRetVal`  
 \[out\]  Retourne `DWORD` qui contient l'identificateur unique pour le module qui a fourni cette ligne.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`.  Retourne `S_FALSE` si cette propriété n'est pas prise en charge.  Sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)