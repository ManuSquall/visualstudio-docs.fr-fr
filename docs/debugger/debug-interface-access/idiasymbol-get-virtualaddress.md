---
title: "IDiaSymbol::get_virtualAddress | Microsoft Docs"
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
  - "IDiaSymbol::get_virtualAddress (méthode)"
ms.assetid: dc20c7c0-15a6-4b78-a5c9-2e0b94cac522
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaSymbol::get_virtualAddress
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Récupère l'adresse \(VA\) virtuelle de l'emplacement.  Utilisez lorsque [LocationType, énumération](../../debugger/debug-interface-access/locationtype.md) est défini à `LocIsStatic`.  
  
## Syntaxe  
  
```cpp#  
HRESULT get_virtualAddress (   
   ULONGLONG* pRetVal  
);  
```  
  
#### Paramètres  
 `pRetVal`  
 \[out\]  Retourne l'adresse virtuelle de l'emplacement.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou un code d'erreur.  
  
> [!NOTE]
>  Une valeur de retour d' `S_FALSE` signifie que la propriété n'est pas disponible pour le symbole.  
  
## Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [LocationType, énumération](../../debugger/debug-interface-access/locationtype.md)