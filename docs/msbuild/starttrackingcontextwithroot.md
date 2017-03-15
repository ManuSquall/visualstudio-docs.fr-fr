---
title: "StartTrackingContextWithRoot | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "StartTrackingContextWithRoot"
apilocation: 
  - "filetracker.dll"
apitype: "COM"
helpviewer_keywords: 
  - "StartTrackingContextWithRoot"
ms.assetid: f6ef2b76-8035-4a14-8195-aa221c46ef48
caps.latest.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 6
---
# StartTrackingContextWithRoot
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Démarre un contexte de suivi à l'aide d'un fichier réponse spécifiant un marqueur racine.  
  
## Syntaxe  
  
```  
HRESULT WINAPI StartTrackingContextWithRoot(LPCTSTR intermediateDirectory, LPCTSTR taskName, LPCTSTR rootMarkerResponseFile);  
```  
  
#### Paramètres  
 \[in\] `intermediateDirectory`  
 Répertoire dans lequel stocker le journal de suivi.  
  
 \[in\] `taskName`  
 Identifie le contexte de suivi.  Ce nom est utilisé pour créer le nom de fichier journal.  
  
 \[in\] `rootMarkerResponseFile`  
 Chemin d'accès d'un fichier réponse contenant un marqueur racine.  Le nom racine est utilisé afin de regrouper toutes les opérations de suivi pour un contexte.  
  
## Valeur de retour  
 Un [HRESULT](assetId:///HRESULT?qualifyHint=False&autoUpgrade=True) avec le bit [SUCCEEDED](assetId:///SUCCEEDED?qualifyHint=False&autoUpgrade=True) défini si le contexte de suivi a été créé.  
  
## Configuration requise  
 **En\-tête :** FileTracker.h  
  
## Voir aussi  
 [StartTrackingContext](../msbuild/starttrackingcontext.md)