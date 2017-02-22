---
title: "IDiaSectionContrib::get_length | Microsoft Docs"
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
  - "IDiaSectionContrib::get_length (méthode)"
ms.assetid: d0f6b9c7-90fc-4e3c-945a-b8f683a8f006
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaSectionContrib::get_length
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Récupère le nombre d'octets dans une section.  
  
## Syntaxe  
  
```cpp#  
HRESULT get_length (   
   DWORD* pRetVal  
);  
```  
  
#### Paramètres  
 `pRetVal`  
 \[out\]  Retourne le nombre d'octets dans une section.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`.  Retourne `S_FALSE` si cette propriété n'est pas prise en charge.  Sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)