---
title: "EndTrackingContext | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "EndTrackingContext"
apilocation: 
  - "filetracker.dll"
apitype: "COM"
helpviewer_keywords: 
  - "EndTrackingContext"
ms.assetid: c2c5d794-8dc8-4594-8717-70dc79a0e75d
caps.latest.revision: 3
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 3
---
# EndTrackingContext
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Mettez fin au contexte de suivi actuel.  
  
## Syntaxe  
  
```  
HRESULT WINAPI EndTrackingContext();  
```  
  
## Valeur de retour  
 Un [HRESULT](assetId:///HRESULT?qualifyHint=False&autoUpgrade=True) avec le bit [SUCCEEDED](assetId:///SUCCEEDED?qualifyHint=False&autoUpgrade=True) défini si le contexte de suivi est terminé.  
  
## Configuration requise  
 **En\-tête :** FileTracker.h  
  
## Voir aussi  
 [StartTrackingContext](../msbuild/starttrackingcontext.md)