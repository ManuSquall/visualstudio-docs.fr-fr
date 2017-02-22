---
title: "IDiaSymbol::get_isHLSLData | Microsoft Docs"
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
ms.assetid: 4662058b-c505-4ccf-ae03-739a62c814ca
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IDiaSymbol::get_isHLSLData
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Spécifie si ce symbole représente des données shadères de niveau supérieur de \(HLSL\) de langage.  
  
## Syntaxe  
  
```cpp  
HRESULT get_isHLSLData(   
   BOOL* pRetVal);  
```  
  
#### Paramètres  
 `pRetVal`  
 \[out\]  Un pointeur vers `BOOL` qui spécifie si ce symbole représente des données de HLSL.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou code d'erreur.  
  
## Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)