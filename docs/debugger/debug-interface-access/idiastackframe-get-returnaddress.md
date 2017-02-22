---
title: "IDiaStackFrame::get_returnAddress | Microsoft Docs"
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
  - "IDiaStackFrame::get_returnAddress (méthode)"
ms.assetid: 0df91981-919f-48ed-9c70-4121567d645b
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# IDiaStackFrame::get_returnAddress
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Récupère l'adresse de retour du frame.  
  
## Syntaxe  
  
```cpp#  
HRESULT get_returnAddress (   
   ULONGLONG* pRetVal  
);  
```  
  
#### Paramètres  
 `pRetVal`  
 \[out\]  Retourne l'adresse de retour du frame.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`.  Retourne `S_FALSE` si la propriété n'est pas prise en charge.  Sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)