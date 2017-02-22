---
title: "IDiaSymbol::get_machineType | Microsoft Docs"
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
  - "IDiaSymbol::get_machineType (méthode)"
ms.assetid: 30870b10-6f32-45c6-a0d7-020dea707710
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaSymbol::get_machineType
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Récupère le type de la cible UC.  
  
## Syntaxe  
  
```cpp#  
HRESULT get_machineType (   
   DWORD* pRetVal  
);  
```  
  
#### Paramètres  
 `pRetVal`  
 \[out\]  Retourne une valeur de l'énumération de [CV\_CPU\_TYPE\_e, énumération](../../debugger/debug-interface-access/cv-cpu-type-e.md) qui spécifie la cible type de processeur.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou un code d'erreur.  
  
> [!NOTE]
>  Une valeur de retour d' `S_FALSE` signifie que la propriété n'est pas disponible pour le symbole.  
  
## Voir aussi  
 [CV\_CPU\_TYPE\_e, énumération](../../debugger/debug-interface-access/cv-cpu-type-e.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)