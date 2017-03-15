---
title: "StartTrackingContext | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "StartTrackingContext"
apilocation: 
  - "filetracker.dll"
apitype: "COM"
helpviewer_keywords: 
  - "StartTrackingContext"
ms.assetid: 720cd295-38e7-4974-86db-b8106b1207ba
caps.latest.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 5
---
# StartTrackingContext
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Démarrez un contexte de suivi.  
  
## Syntaxe  
  
```  
HRESULT WINAPI StartTrackingContext(LPCTSTR intermediateDirectory, LPCTSTR taskName);  
```  
  
#### Paramètres  
 \[in\] `intermediateDirectory`  
 Répertoire dans lequel stocker le journal de suivi.  
  
 \[in\] `taskName`  
 Identifie le contexte de suivi.  Ce nom est utilisé pour créer le nom de fichier journal.  
  
## Valeur de retour  
 Un [HRESULT](assetId:///HRESULT?qualifyHint=False&autoUpgrade=True) avec le bit [SUCCEEDED](assetId:///SUCCEEDED?qualifyHint=False&autoUpgrade=True) défini si le contexte de suivi a été créé.  
  
## Configuration requise  
 **En\-tête :** FileTracker.h