---
title: "IDiaSession::findInlineesByName | Microsoft Docs"
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
ms.assetid: 9860336d-f703-4ecb-bfc4-3f5beb175a76
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IDiaSession::findInlineesByName
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Extrait une énumération qui permet à un client pour itérer au sein de les informations de numéro de ligne de toutes les fonctions inline qui correspondent à un nom spécifié.  
  
## Syntaxe  
  
```cpp#  
HRESULT findInlineesByName (   
   LPCOLESTR             name,  
   DWORD                 option,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### Paramètres  
 `name`  
 \[in\]  Spécifie le nom à utiliser pour la comparaison.  
  
 `option`  
 \[in\]  spécifie les options de comparaison appliquées pour nommer rechercher.  Les valeurs de l'énumération de [NameSearchOptions, énumération](../../debugger/debug-interface-access/namesearchoptions.md) peuvent être utilisées unique ou en association.  
  
 `ppResult`  
 \[out\]  Retourne un objet d' [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md) qui contient une liste des numéros de ligne qui ont été récupérés.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum, énumération](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)