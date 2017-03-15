---
title: "IDiaSymbol::findChildrenExByVA | Microsoft Docs"
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
  - "IDiaSymbol::findChildrenExByVA"
ms.assetid: 29080009-36e4-4697-acd7-50f2e3e1bf1b
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaSymbol::findChildrenExByVA
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Récupère les enfants du symbole qui sont valides à une adresse virtuelle spécifiée.  
  
## Syntaxe  
  
```cpp#  
HRESULT findChildrenExByVA (   
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
 \[in\]  spécifie l'adresse virtuelle.  
  
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