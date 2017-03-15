---
title: "IDiaStackWalkHelper::imageForVA | Microsoft Docs"
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
  - "IDiaStackWalkHelper::imageForVA (méthode)"
ms.assetid: 8d4edabf-3c01-4fef-8b61-4779f3371067
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaStackWalkHelper::imageForVA
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Retourne le début de l'image d'un fichier exécutable en mémoire donnée une adresse virtuelle trouve dans l'espace mémoire du fichier exécutable.  
  
## Syntaxe  
  
```cpp#  
HRESULT imageForVA(  
   ULONGLONG  vaContext,  
   ULONGLONG *pvaImageStart  
);  
```  
  
#### Paramètres  
 `vaContext`  
 \[in\]  Adresse virtuelle qui se trouve en cours dans l'espace du fichier exécutable.  
  
 `pvaImageStart`  
 \[out\]  Retourne l'adresse virtuelle de début de l'image du fichier exécutable.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)