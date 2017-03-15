---
title: "WriteAllTLogs | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "WriteAllTLogs"
apilocation: 
  - "filetracker.dll"
apitype: "COM"
helpviewer_keywords: 
  - "WriteAllTLogs"
ms.assetid: 1fa3e10b-263c-4960-a9ad-485c02a7a872
caps.latest.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 5
---
# WriteAllTLogs
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Écrit des journaux de suivi pour tous les contextes et threads.  
  
## Syntaxe  
  
```  
HRESULT WINAPI WriteAllTLogs(LPCTSTR intermediateDirectory, LPCTSTR tlogRootName);  
```  
  
#### Paramètres  
 \[in\] `intermediateDirectory`  
 Répertoire dans lequel stocker le journal de suivi.  
  
 \[in\] `tlogRootName`  
 Nom racine du nom du fichier journal.  
  
## Valeur de retour  
 Un [HRESULT](assetId:///HRESULT?qualifyHint=False&autoUpgrade=True) avec le bit [SUCCEEDED](assetId:///SUCCEEDED?qualifyHint=False&autoUpgrade=True) défini si le contexte de suivi a été créé.  
  
## Configuration requise  
 **En\-tête :** FileTracker.h  
  
## Voir aussi  
 [WriteContextTLogs](../msbuild/writecontexttlogs.md)