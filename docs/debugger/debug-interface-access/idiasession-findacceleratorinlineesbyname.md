---
title: "IDiaSession::findAcceleratorInlineesByName | Microsoft Docs"
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
ms.assetid: e203e5c2-6563-43fa-be56-3063955043ab
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IDiaSession::findAcceleratorInlineesByName
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Retourne une énumération les symboles pour les frames intégrés correspondant au nom de la fonction inline spécifié.  
  
## Syntaxe  
  
```cpp#  
HRESULT findAcceleratorInlineeLinesByName (   
   LPCOLESTR             name,  
   DWORD                 option,  
   IDiaEnumSymbols**     ppResult  
);  
```  
  
#### Paramètres  
 `name`  
 \[in\]  Le nom de la fonction de l'inlinee à rechercher.  
  
 `option`  
 \[in\]  Les options de recherche de nom d'être utilisé en recherchant les frames intégrés qui correspondent à `name`.  Pour plus d'informations, consultez [NameSearchOptions, énumération](../../debugger/debug-interface-access/namesearchoptions.md).  
  
 `ppResult`  
 \[out\]  Un pointeur vers un pointeur d'interface de `IDiaEnumSymbols` qui est initialisé avec le résultat.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.  
  
## Notes  
 Les recherches de cette fonction pour les inlinees uniquement dans le stub d'accélérateur s'exécute.  Il ignore les enregistrements natifs de procédure C\+\+.  
  
## Voir aussi  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)