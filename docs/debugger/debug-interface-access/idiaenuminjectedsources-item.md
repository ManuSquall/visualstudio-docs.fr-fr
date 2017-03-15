---
title: "IDiaEnumInjectedSources::Item | Microsoft Docs"
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
  - "IDiaEnumInjectedSources::Item (méthode)"
ms.assetid: 14846955-7270-451d-91d2-9cb34bb65187
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaEnumInjectedSources::Item
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Extrait une source injectée au moyen d'un index.  
  
## Syntaxe  
  
```cpp#  
HRESULT Item (   
   DWORD                index,  
   IDiaInjectedSource** injectedSource  
);  
```  
  
#### Paramètres  
 index  
 \[in\]  Index de l'objet d' [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md) à récupérer.  l'index est la plage 0 à `count`\-1, où `count` est retourné par la méthode d' [IDiaEnumInjectedSources::get\_Count](../../debugger/debug-interface-access/idiaenuminjectedsources-get-count.md) .  
  
 injectedSource  
 \[out\]  Retourne un objet d' [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md) représentant la source injectée.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)   
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)