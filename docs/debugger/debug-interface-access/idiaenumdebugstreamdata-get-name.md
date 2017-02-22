---
title: "IDiaEnumDebugStreamData::get_name | Microsoft Docs"
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
  - "IDiaEnumDebugStreamData::get_Name (méthode)"
ms.assetid: e6cf2bed-ee2b-4122-886d-c20d93df7ff2
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaEnumDebugStreamData::get_name
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

extrait le nom d'un flux de données de débogage.  
  
## Syntaxe  
  
```cpp#  
HRESULT get_Name (   
   BSTR * pRetVal  
)  
```  
  
#### Paramètres  
 pRetVal  
 \[out\]  Retourne le nom d'un flux de données de débogage.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)