---
title: "IDiaSymbol::getSrcLineOnTypeDefn | Microsoft Docs"
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
ms.assetid: ad554d18-9988-4b64-ad71-e7594c266e94
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IDiaSymbol::getSrcLineOnTypeDefn
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Extrait le fichier source et le numéro de ligne qui indiquent où un type défini par l'utilisateur spécifié est défini.  
  
## Syntaxe  
  
```cpp  
HRESULT getSrcLineOnTypeDefn(  
   IDiaLineNumber **ppResult);  
```  
  
#### Paramètres  
 `ppResult`  
 \[out\]  un objet d' `IDiaLineNumber` qui contient le fichier source et le numéro de ligne où le défini par l'utilisateur.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou code d'erreur.  
  
## Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)