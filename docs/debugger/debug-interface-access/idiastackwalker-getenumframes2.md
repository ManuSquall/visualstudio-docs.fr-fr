---
title: "IDiaStackWalker::getEnumFrames2 | Microsoft Docs"
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
  - "IDiaStackWalker2::getEnumFrames2 (méthode)"
ms.assetid: 73196d3f-112c-4b3a-997b-7c6b815d4afc
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# IDiaStackWalker::getEnumFrames2
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Récupère un énumérateur du frame de pile pour un type spécifique de plateforme.  
  
## Syntaxe  
  
```cpp#  
  
      HRESULT getEnumFrames2(   
   enum  CV_CPU_TYPE_e    cpuid,  
   IDiaStackWalkHelper*   pHelper,  
   IDiaEnumStackFrames**  ppEnum  
);  
```  
  
#### Paramètres  
 `cpuid`  
 \[in\]  Une valeur de l'énumération de [CV\_CPU\_TYPE\_e, énumération](../../debugger/debug-interface-access/cv-cpu-type-e.md) , en spécifiant le type de plateforme.  
  
 `pHelper`  
 \[in\]  l'objet d'assistance d' [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md) .  
  
 `ppEnum`  
 \[out\]  Retourne un objet d' [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md) contenant une liste d'objets d' [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md) .  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Pour obtenir une liste de frame de pile uniquement pour la plateforme x86, appelez la méthode d' [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md) .  
  
## Voir aussi  
 [IDiaStackWalker](../../debugger/debug-interface-access/idiastackwalker.md)   
 [CV\_CPU\_TYPE\_e, énumération](../../debugger/debug-interface-access/cv-cpu-type-e.md)   
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)   
 [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)