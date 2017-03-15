---
title: "IDiaSession::findInlineeLinesByAddr | Microsoft Docs"
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
ms.assetid: bb70e408-eed1-4c9c-b5b1-44323125f48b
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IDiaSession::findInlineeLinesByAddr
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Extrait une énumération qui permet à un client pour itérer au sein de les informations de numéro de ligne de toutes les fonctions qui sont inline, directement ou indirectement, par le symbole parent spécifié et est contenue dans la marge d'adresse spécifiée.  
  
## Syntaxe  
  
```cpp#  
HRESULT findInlineeLinesByAddr (   
   IDiaSymbol*           parent,  
   DWORD                 isect,  
   DWORD                 offset,  
   DWORD                 length,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### Paramètres  
 `parent`  
 \[in\]  un objet d' `IDiaSymbol` représentant le parent.  
  
 `isect`  
 \[in\]  spécifie le composant de section de l'adresse.  
  
 `offset`  
 \[in\]  Spécifie le composant offset de l'adresse.  
  
 `length`  
 \[in\]  Spécifie la plage d'adresses, en nombre d'octets, pour couvrir de cette requête.  
  
 `ppResult`  
 \[out\]  Contient un objet d' `IDiaEnumLineNumbers` qui contient la liste des numéros de ligne qui sont récupérés.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum, énumération](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)