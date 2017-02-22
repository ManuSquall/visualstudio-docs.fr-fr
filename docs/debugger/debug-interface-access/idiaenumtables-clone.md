---
title: "IDiaEnumTables::Clone | Microsoft Docs"
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
  - "IDiaEnumTables::Clone (méthode)"
ms.assetid: beb21109-b12c-44d8-8c1f-a332216b3713
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaEnumTables::Clone
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

crée un énumérateur qui contient le même état d'énumération que l'énumérateur actuel.  
  
## Syntaxe  
  
```cpp#  
HRESULT Clone (   
   IDiaEnumTables** ppenum  
);  
```  
  
#### Paramètres  
 `ppenum`  
 \[out\]  Retourne un objet d' [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md) qui contient un doublon de l'énumérateur.  Ceux\-ci ne sont pas dupliqués, seul l'énumérateur.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)