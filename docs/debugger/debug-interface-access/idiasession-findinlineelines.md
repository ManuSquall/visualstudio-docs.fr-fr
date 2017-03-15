---
title: "IDiaSession::findInlineeLines | Microsoft Docs"
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
ms.assetid: b6822d8b-70d5-470b-8278-3aec4680326c
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IDiaSession::findInlineeLines
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Extrait une énumération qui permet à un client pour itérer au sein de les informations de numéro de ligne de toutes les fonctions qui sont inline, directement ou indirectement, par le symbole parent spécifié.  
  
## Syntaxe  
  
```cpp#  
HRESULT findInlineeLines (   
   IDiaSymbol*       parent,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### Paramètres  
 `parent`  
 \[in\]  un objet d' `IDiaSymbol` représentant le parent.  
  
 `ppResult`  
 \[out\]  Contient un objet d' `IDiaEnumLineNumbers` qui contient la liste des numéros de ligne qui sont récupérés.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum, énumération](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)