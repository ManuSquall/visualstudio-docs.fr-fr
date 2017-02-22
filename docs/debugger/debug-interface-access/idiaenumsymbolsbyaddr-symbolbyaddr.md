---
title: "IDiaEnumSymbolsByAddr::symbolByAddr | Microsoft Docs"
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
  - "IDiaEnumSymbolsByAddr::symbolByAddr (méthode)"
ms.assetid: 0b6f5a68-8402-4f29-8219-20576fda8166
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaEnumSymbolsByAddr::symbolByAddr
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Positionne l'énumérateur en effectuant une recherche par le nombre de sections et l'offset d'image.  
  
## Syntaxe  
  
```cpp#  
HRESULT symbolByAddr (   
   DWORD**      isect,  
   DWORD**      offsect,  
   IDiaSymbol** ppsymbol  
);  
```  
  
#### Paramètres  
 isect  
 \[in\]  Nombre de section d'image.  
  
 offsect  
 \[in\]  offset dans la section.  
  
 ppsymbol  
 \[out\]  Retourne un objet d' [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) représentant le symbole trouvé.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`.  Retourne `S_FALSE` si le symbole est introuvable.  Sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)