---
title: "IDiaStackWalker::getEnumFrames | Microsoft Docs"
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
  - "IDiaStackWalker2::getEnumFrames (méthode)"
ms.assetid: f9f09729-4c34-441c-989c-e0b7339ee32c
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IDiaStackWalker::getEnumFrames
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Récupère un énumérateur du frame de pile pour les plateformes x86.  
  
## Syntaxe  
  
```cpp#  
HRESULT getEnumFrames(   
   IDiaStackWalkHelper*   pHelper,  
   IDiaEnumStackFrames**  ppEnum  
);  
```  
  
#### Paramètres  
 `pHelper`  
 \[in\]  l'objet d'assistance d' [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md) .  
  
 `ppEnum`  
 \[out\]  Retourne un objet d' [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md) qui contient une liste d'objets d' [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md) .  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Pour obtenir une liste de frame de pile sur toute autre plateforme, appelez la méthode d' [IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md) .  
  
## Voir aussi  
 [IDiaStackWalker](../../debugger/debug-interface-access/idiastackwalker.md)   
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)   
 [IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)