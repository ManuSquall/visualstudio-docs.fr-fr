---
title: "WriteContextTLogs | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "WriteContextTLogs"
apilocation: 
  - "filetracker.dll"
apitype: "COM"
helpviewer_keywords: 
  - "WriteContextTLogs"
ms.assetid: ffc6c7be-3f22-4624-9ffc-0122fe72b6ec
caps.latest.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 5
---
# WriteContextTLogs
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Écrit des fichiers journaux pour le contexte actuel.  
  
## Syntaxe  
  
```  
HRESULT WINAPI WriteContextTLogs(LPCTSTR intermediateDirectory, LPCTSTR tlogRootName);  
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
 [WriteAllTLogs](../msbuild/writealltlogs.md)