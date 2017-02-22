---
title: "IDiaSegment::get_frame | Microsoft Docs"
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
  - "IDiaSegment::get_frame (méthode)"
ms.assetid: 9fece9c7-064a-4d6b-9cef-fc387f322205
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaSegment::get_frame
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Récupère le numéro du segment.  
  
## Syntaxe  
  
```cpp#  
HRESULT get_frame (   
   DWORD* pRetVal  
);  
```  
  
#### Paramètres  
 `pRetVal`  
 \[out\]  Retourne le numéro du segment.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`.  Retourne `S_FALSE` si cette propriété n'est pas prise en charge.  Sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)