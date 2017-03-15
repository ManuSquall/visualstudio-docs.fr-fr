---
title: "IDiaSymbol::get_dataBytes | Microsoft Docs"
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
  - "IDiaSymbol::get_dataBytes (méthode)"
ms.assetid: 5eb37179-20d8-44ae-a72a-405c1b0435c4
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDiaSymbol::get_dataBytes
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Récupère les octets de données d'un symbole OEM.  
  
## Syntaxe  
  
```cpp#  
HRESULT get_dataBytes (   
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[]  
);  
```  
  
#### Paramètres  
 `cbData`  
 \[in\]  taille de la mémoire tampon pour contenir les données.  
  
 `pcbData`  
 \[out\]  Retourne le nombre d'octets écrits, ou, si le paramètre d' `data` est `NULL`, retourne le nombre d'octets disponibles.  
  
 `data[]`  
 \[,\] mémoire tampon d'Un qui est terminée avec les octets de données.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou un code d'erreur.  
  
> [!NOTE]
>  Une valeur de retour d' `S_FALSE` signifie que la propriété n'est pas disponible pour le symbole.  
  
## Configuration requise  
  
|Spécification|Description|  
|-------------------|-----------------|  
|en\-tête :|dia2.h|  
|version :|diamètre Kit de développement logiciel v7.0|  
  
## Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)