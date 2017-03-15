---
title: "IDiaSymbol::findInlineFramesByAddr | Microsoft Docs"
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
ms.assetid: 36a122e6-f27e-40cd-9784-cdaf279e1905
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IDiaSymbol::findInlineFramesByAddr
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Extrait une énumération qui permet à un client pour itérer au sein de tous les frames intégrés sur une adresse donnée.  
  
## Syntaxe  
  
```cpp#  
HRESULT findInlineFramesByAddr (   
   DWORD             isect,  
   DWORD             offset,  
   IDiaEnumSymbols** ppResult  
);  
```  
  
#### Paramètres  
 `isect`  
 \[in\]  spécifie le composant de section de l'adresse.  
  
 `offset`  
 \[in\]  Spécifie le composant offset de l'adresse.  
  
 `ppResult`  
 \[out\]  Contient un objet d' `IDiaEnumSymbols` qui contient la liste des frames qui sont récupérés.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum, énumération](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)