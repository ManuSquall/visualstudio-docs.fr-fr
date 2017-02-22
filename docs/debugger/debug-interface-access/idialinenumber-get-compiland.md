---
title: "IDiaLineNumber::get_compiland | Microsoft Docs"
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
  - "IDiaLineNumber::get_compiland (méthode)"
ms.assetid: c476d0b8-c473-47eb-96f5-c4e8f577b1c9
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDiaLineNumber::get_compiland
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Extrait une référence au symbole pour le module qui a fourni des octets de texte d'image.  
  
## Syntaxe  
  
```cpp#  
HRESULT get_compiland (   
   IDiaSymbol** pRetVal  
);  
```  
  
#### Paramètres  
 pRetVal  
 \[out\]  Retourne un objet d' [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) pour le module qui a fourni des octets de texte d'image.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`.  Retourne `S_FALSE` si cette propriété n'est pas prise en charge.  Sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)