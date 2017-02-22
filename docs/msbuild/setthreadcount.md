---
title: "SetThreadCount | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "SetThreadCount"
apilocation: 
  - "filetracker.dll"
apitype: "COM"
helpviewer_keywords: 
  - "SetThreadCount"
ms.assetid: 335335a5-8ca0-4e18-95f5-62aa6a691386
caps.latest.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 4
---
# SetThreadCount
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Définit le nombre de threads global et assigne ce nombre au thread actuel.  
  
## Syntaxe  
  
```  
HRESULT WINAPI SetThreadCount(int threadCount);  
```  
  
#### Paramètres  
 \[in\] `threadCount`  
 Nombre de threads à utiliser.  
  
## Valeur de retour  
 Un [HRESULT](assetId:///HRESULT?qualifyHint=False&autoUpgrade=True) avec le bit [SUCCEEDED](assetId:///SUCCEEDED?qualifyHint=False&autoUpgrade=True) défini si le nombre de threads a été mis à jour.  
  
## Configuration requise  
 **En\-tête :** FileTracker.h