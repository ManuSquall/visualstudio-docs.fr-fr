---
title: "IDiaSymbol::get_virtualBaseOffset | Microsoft Docs"
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
  - "IDiaSymbol::get_virtualBaseOffset (méthode)"
ms.assetid: 103b034f-36c4-42d5-aa34-1449a1e66d03
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaSymbol::get_virtualBaseOffset
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Récupère l'offset dans la table de fonctions virtuelles d'une fonction virtuelle.  
  
## Syntaxe  
  
```cpp#  
HRESULT get_virtualBaseOffset (   
   DWORD* pRetVal  
);  
```  
  
#### Paramètres  
 `pRetVal`  
 \[out\]  Retourne l'offset dans la table de fonctions virtuelles d'une fonction virtuelle.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou un code d'erreur.  
  
> [!NOTE]
>  Une valeur de retour d' `S_FALSE` signifie que la propriété n'est pas disponible pour le symbole.  
  
## Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)