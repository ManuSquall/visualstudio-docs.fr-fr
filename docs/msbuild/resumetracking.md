---
title: "ResumeTracking | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "ResumeTracking"
apilocation: 
  - "filetracker.dll"
apitype: "COM"
helpviewer_keywords: 
  - "ResumeTracking"
ms.assetid: d637e019-7c50-4b0a-812e-bc822001e697
caps.latest.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 4
---
# ResumeTracking
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Reprend le suivi dans le contexte actuel.  
  
## Syntaxe  
  
```  
HRESULT WINAPI ResumeTracking();  
```  
  
## Valeur de retour  
 Un [HRESULT](assetId:///HRESULT?qualifyHint=False&autoUpgrade=True) avec le bit [SUCCEEDED](assetId:///SUCCEEDED?qualifyHint=False&autoUpgrade=True) défini si le suivi a repris.  [E\_FAIL](assetId:///E_FAIL?qualifyHint=False&autoUpgrade=True) est retourné si le suivi ne peut pas être repris parce que le contexte n'était pas disponible.  
  
## Configuration requise  
 **En\-tête :** FileTracker.h  
  
## Voir aussi  
 [SuspendTracking](../msbuild/suspendtracking.md)