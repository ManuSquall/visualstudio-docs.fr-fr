---
title: "StopTrackingAndCleanup | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "StopTrackingAndCleanup"
apilocation: 
  - "filetracker.dll"
apitype: "COM"
helpviewer_keywords: 
  - "StopTrackingAndCleanup"
ms.assetid: 9f8c5994-2dfc-43c3-a5fb-89b2f8990429
caps.latest.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 4
---
# StopTrackingAndCleanup
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Arrête toute opération de suivi et libère toute la mémoire utilisée par la session de suivi.  
  
## Syntaxe  
  
```  
HRESULT WINAPI StopTrackingAndCleanup(void);  
```  
  
## Valeur de retour  
 Retourne un [HRESULT](assetId:///HRESULT?qualifyHint=False&autoUpgrade=True) avec le bit [SUCCEEDED](assetId:///SUCCEEDED?qualifyHint=False&autoUpgrade=True) défini si le suivi a été arrêté.  
  
## Configuration requise  
 **En\-tête :** FileTracker.h  
  
## Voir aussi  
 [StartTrackingContext](../msbuild/starttrackingcontext.md)