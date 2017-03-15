---
title: "IDiaSession::findAcceleratorInlineesByLinenum | Microsoft Docs"
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
ms.assetid: 386c87aa-f7b2-4d38-9dd6-fffba9ff01f0
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IDiaSession::findAcceleratorInlineesByLinenum
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Retourne une énumération les symboles pour les frames intégrés qui correspondent à l'emplacement spécifié de la source.  
  
## Syntaxe  
  
```cpp#  
HRESULT findAcceleratorInlineeLinesByName (   
   IDiaSymbol*           parent,  
   IDiaSourceFile*       file,  
   DWORD                 linenum,  
   DWORD                 colnum,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### Paramètres  
 `parent`  
 \[in\]  `IDiaSymbol` qui correspond à la fonction du stub d'accélérateur qui doit être trouvée.  
  
 `file`  
 \[in\]  `IDiaSourceFile` de l'emplacement source.  
  
 `linenum`  
 \[in\]  Le numéro de la ligne de l'emplacement source.  
  
 `colnum`  
 \[in\]  Le nombre de colonnes de l'emplacement source.  
  
 `ppResult`  
 \[out\]  Un pointeur vers un pointeur d'interface de `IDiaEnumLineNumbers` qui est initialisé avec le résultat.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)