---
title: "IDiaStackWalkFrame::put_registerValue | Microsoft Docs"
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
  - "IDiaStackWalkFrame::put_registerValue (méthode)"
ms.assetid: 2d8b79b6-7240-43fe-b24e-e4ff3e2c15b0
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaStackWalkFrame::put_registerValue
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

définit la valeur d'un registre.  
  
## Syntaxe  
  
```cpp#  
HRESULT put_registerValue (   
   DWORD     index,  
   ULONGLONG NewVal  
);  
```  
  
#### Paramètres  
 `index`  
 \[in\]  Une valeur de l'énumération de [CV\_HREG\_e, énumération](../../debugger/debug-interface-access/cv-hreg-e.md) spécifiant le registre pour écrire.  
  
 `NewVal`  
 \[in\]  la nouvelle valeur de registre.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)   
 [CV\_HREG\_e, énumération](../../debugger/debug-interface-access/cv-hreg-e.md)