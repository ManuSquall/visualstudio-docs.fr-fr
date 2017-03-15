---
title: "IDiaEnumInjectedSources::Clone | Microsoft Docs"
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
  - "IDiaEnumInjectedSources::Clone (méthode)"
ms.assetid: 18038691-c140-426a-8617-27f0360650f3
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaEnumInjectedSources::Clone
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

crée un énumérateur qui contient le même état d'énumération que l'énumérateur actuel.  
  
## Syntaxe  
  
```cpp#  
HRESULT Clone (   
   IDiaEnumInjectedSources** ppenum  
);  
```  
  
#### Paramètres  
 `ppenum`  
 \[out\]  Retourne un objet d' [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md) qui contient un doublon de l'énumérateur.  Les sources injectées ne sont pas dupliquées, seul l'énumérateur.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)