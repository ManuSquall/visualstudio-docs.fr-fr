---
title: "IDiaStackWalkFrame::get_registerValue | Microsoft Docs"
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
  - "IDiaStackWalkFrame::get_registerValue (méthode)"
ms.assetid: ca3c20a9-934a-4b2c-a7f6-7d06e8611ff2
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDiaStackWalkFrame::get_registerValue
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

extrait la valeur d'un registre.  
  
## Syntaxe  
  
```cpp#  
HRESULT get_registerValue (   
   DWORD      index,  
   ULONGLONG* pRetVal  
);  
```  
  
#### Paramètres  
 `index`  
 \[in\]  une valeur de l'énumération de [CV\_HREG\_e, énumération](../../debugger/debug-interface-access/cv-hreg-e.md) spécifiant le registre pour obtenir la valeur pour.  
  
 `pRetVal`  
 \[out\]  Retourne la valeur actuelle du registre.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)   
 [CV\_HREG\_e, énumération](../../debugger/debug-interface-access/cv-hreg-e.md)