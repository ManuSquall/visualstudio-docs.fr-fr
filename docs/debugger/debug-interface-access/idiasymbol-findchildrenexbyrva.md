---
title: "IDiaSymbol::findChildrenExByRVA | Microsoft Docs"
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
  - "IDiaSymbol::findChildrenExByRVA"
ms.assetid: cbc57c6c-7d64-4469-a114-1dd6671e5ec5
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaSymbol::findChildrenExByRVA
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Récupère les enfants du symbole qui sont valides à une adresse virtuelle relative spécifiée \(RVA\).  
  
## Syntaxe  
  
```cpp#  
HRESULT findChildrenExByRVA (   
   enum SymTagEnum   symtag,  
   LPCOLESTR         name,  
   DWORD             compareFlags,  
   DWORD             address,  
   IDiaEnumSymbols** ppResult  
);  
```  
  
#### Paramètres  
 `symtag`  
 \[in\]  Spécifie des indicateurs de symbole des enfants à récupérer, comme défini dans [SymTagEnum, énumération](../../debugger/debug-interface-access/symtagenum.md).  Affectez à `SymTagNull` pour que tous les enfants soient extraits.  
  
 `name`  
 \[in\]  Spécifie le nom des enfants à récupérer.  Affectez à `NULL` pour que tous les enfants soient extraits.  
  
 `compareFlags`  
 \[in\]  Spécifie des options de comparaison d'être appliqué pour nommer la correspondance.  Les valeurs de l'énumération de [NameSearchOptions, énumération](../../debugger/debug-interface-access/namesearchoptions.md) peuvent être utilisées seul ou en association.  
  
 `address`  
 \[in\]  Spécifie le CONCERNANT.  
  
 `ppResult`  
 \[out\]  Retourne un objet d' [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) qui contient une liste des symboles enfants récupérés.  
  
## Valeur de retour  
 Retourne `S_OK` si au moins un enfant du symbole a été trouvé, ou retourne `S_FALSE` si aucun enfant n'a été trouvé ; sinon, retourne un code d'erreur.  
  
## Notes  
 Les symboles locaux qui sont retournées incluent des informations dynamiques de la plage.  
  
## Configuration requise  
 en\-tête : Dia2.h  
  
 bibliothèque : diaguids.lib  
  
 DLL : msdia100.dll  
  
## Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum, énumération](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [NameSearchOptions, énumération](../../debugger/debug-interface-access/namesearchoptions.md)