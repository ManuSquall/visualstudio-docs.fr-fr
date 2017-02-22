---
title: "IDiaFrameData::get_systemExceptionHandling | Microsoft Docs"
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
  - "IDiaFrameData::get_systemExceptionHandling (méthode)"
ms.assetid: e8df1972-913c-446c-9779-775575b0caa9
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaFrameData::get_systemExceptionHandling
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Extrait une balise qui indique si la gestion des exceptions du système est appliquée.  
  
## Syntaxe  
  
```cpp#  
HRESULT get_systemExceptionHandling (   
   BOOL* pRetVal  
);  
```  
  
#### Paramètres  
 pRetVal  
 \[out\]  Retourne `TRUE` si la gestion des exceptions du système est activé ; sinon, retourne `FALSE`.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`.  Retourne `S_FALSE` si cette propriété n'est pas prise en charge.  Sinon, retourne un code d'erreur.  
  
## Notes  
 La gestion des exceptions du système est généralement appelé la gestion structurée des exceptions.  
  
 Pour déterminer si la gestion des exceptions C\+\+ est active, appelez la méthode d' [IDiaFrameData::get\_cplusplusExceptionHandling](../../debugger/debug-interface-access/idiaframedata-get-cplusplusexceptionhandling.md) .  
  
## Voir aussi  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [IDiaFrameData::get\_cplusplusExceptionHandling](../../debugger/debug-interface-access/idiaframedata-get-cplusplusexceptionhandling.md)