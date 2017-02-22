---
title: "MemoryTypeEnum | Microsoft Docs"
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
  - "MemoryTypeEnum (énumération)"
ms.assetid: 8778c047-edeb-4495-8f9f-3f8bbb297099
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# MemoryTypeEnum
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

spécifie le type de mémoire pour accéder.  
  
## Syntaxe  
  
```cpp#  
enum MemoryTypeEnum {  
   MemTypeCode,  
   MemTypeData,  
   MemTypeStack,  
   MemTypeAny = -1  
};  
```  
  
#### Paramètres  
 `MemTypeCode`  
 Mémoire de code d'accès uniquement.  
  
 `MemTypeData`  
 accès données ou mémoire de pile.  
  
 `MemTypeStack`  
 Mémoire de pile d'accès uniquement.  
  
 `MemTypeAny`  
 Accède à tout type de mémoire.  
  
## Notes  
 Les valeurs de cette énumération passées à la méthode d' [IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md) pour limiter l'accès à différents types de mémoire.  
  
## Configuration requise  
 en\-tête : cvconst.h  
  
## Voir aussi  
 [Énumérations et structures](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md)