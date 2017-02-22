---
title: "IDiaStackWalkHelper::searchForReturnAddress | Microsoft Docs"
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
  - "IDiaStackWalkHelper2::searchForReturnAddress (méthode)"
ms.assetid: 904223b1-6e26-4980-b310-d0b222cdbbbd
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDiaStackWalkHelper::searchForReturnAddress
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

recherche le frame de pile spécifié pour l'adresse de retour de fonction la plus proche.  
  
## Syntaxe  
  
```cpp#  
HRESULT searchForReturnAddress(   
   IDiaFrameData*  frame,  
   ULONGLONG*      returnAddress  
);  
```  
  
#### Paramètres  
 `frame`  
 \[in\]  un objet d' [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) qui représente le frame de pile actuel.  
  
 `returnAddress`  
 \[out\]  Retourne l'adresse de retour de fonction la plus proche.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)