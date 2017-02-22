---
title: "IDiaSession::findInlineLinesByVA | Microsoft Docs"
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
ms.assetid: dffe6594-e0d1-4ed5-aeea-8773f88d82a6
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IDiaSession::findInlineLinesByVA
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Extrait une énumération qui permet à un client pour itérer au sein de les informations de numéro de ligne de toutes les fonctions qui sont inline, directement ou indirectement, par le symbole parent spécifié et est contenue dans l'adresse virtuelle spécifiée \(VA\).  
  
## Syntaxe  
  
```cpp#  
HRESULT findInlineeLinesByVA (   
   IDiaSymbol*           parent,  
   ULONGLONG             va,  
   DWORD                 length,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### Paramètres  
 `parent`  
 \[in\]  un objet d' `IDiaSymbol` représentant le parent.  
  
 `va`  
 \[in\]  spécifie l'adresse comme VA.  
  
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