---
title: "ERRORRESUMEACTION, &#233;num&#233;ration | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: ERRORRESUMEACTION
apilocation: scrobj.dll
helpviewer_keywords: 
  - "ERRORRESUMEACTION (énumération)"
ms.assetid: a68293c8-056b-439f-83e7-69e4a38f4976
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# ERRORRESUMEACTION, &#233;num&#233;ration
Décrit comment continuer d'une erreur d'exécution.  
  
## Syntaxe  
  
```  
typedef enum tagERRORRESUMEACTION {  
   ERRORRESUMEACTION_ReexecuteErrorStatement,  
   ERRORRESUMEACTION_AbortCallAndReturnErrorToCaller,  
   ERRORRESUMEACTION_SkipErrorStatement,  
} ERRORRESUMEACTION;  
```  
  
## Membres  
  
|Membre|Description|  
|------------|-----------------|  
|ERRORRESUMEACTION\_ReexecuteErrorStatement|Exécute à nouveau l'instruction qui est produite l'erreur.|  
|ERRORRESUMEACTION\_AbortCallAndReturnErrorToCaller|Permet au moteur de langage gérer l'erreur.|  
|ERRORRESUMEACTION\_SkipErrorStatement|Reprend l'exécution dans le code suivant l'instruction qui est produite l'erreur.|  
  
## Voir aussi  
 [Débogueur de script actif, constantes, énumérations et structures](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)