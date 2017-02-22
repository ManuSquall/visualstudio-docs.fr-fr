---
title: "IDiaEnumLineNumbers::Clone | Microsoft Docs"
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
  - "IDiaEnumLineNumbers::Clone (méthode)"
ms.assetid: fcd2479a-8ff7-4aba-a737-06123c280d54
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaEnumLineNumbers::Clone
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

crée un énumérateur qui contient le même état d'énumération que l'énumérateur actuel.  
  
## Syntaxe  
  
```cpp#  
HRESULT Clone (   
   IDiaEnumLineNumbers** ppenum  
);  
```  
  
#### Paramètres  
 `ppenum`  
 \[out\]  Retourne un objet d' [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md) qui contient un doublon de l'énumérateur.  Les numéros de ligne ne sont pas dupliqués, seul l'énumérateur.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)