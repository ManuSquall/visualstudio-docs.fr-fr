---
title: "IDiaEnumSymbolsByAddr::symbolByVA | Microsoft Docs"
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
  - "IDiaEnumSymbolsByAddr::symbolByVA (méthode)"
ms.assetid: ac84339f-70c6-48ed-85d0-6d7d1b5194e8
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaEnumSymbolsByAddr::symbolByVA
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

positionne l'énumérateur en effectuant une recherche par l'adresse virtuelle \(VA\).  
  
## Syntaxe  
  
```cpp#  
HRESULT symbolByVA (   
   DWORD**      virtualAddress,  
   IDiaSymbol** ppsymbol  
);  
```  
  
#### Paramètres  
 virtualAddress  
 \[in\]  adresse virtuelle.  
  
 ppsymbol  
 \[out\]  Retourne un objet d' [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) représentant le symbole trouvé.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`.  Retourne `S_FALSE` si le symbole est introuvable.  Sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)