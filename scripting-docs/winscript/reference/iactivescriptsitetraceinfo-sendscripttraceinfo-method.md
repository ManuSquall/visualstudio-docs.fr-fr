---
title: "IActiveScriptSiteTraceInfo::SendScriptTraceInfo, m&#233;thode | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 0419e4c5-eb7c-45a3-b6dc-1a5e157d95f9
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IActiveScriptSiteTraceInfo::SendScriptTraceInfo, m&#233;thode
Envoie les informations de traçage qui incluent le type d'événement, le contexte, et l'instruction de script.  
  
## Syntaxe  
  
```  
HRESULT SendScriptTraceInfo(   
    [in] SCRIPTTRACEINFO stiEventType,   
    [in] GUID guidContextID,   
    [in] DWORD dwScriptContextCookie,   
    [in] LONG lScriptStatementStart,   
    [in] LONG lScriptStatementEnd,   
    [in] DWORD64 dwReserved   
);   
```  
  
#### Paramètres  
 `stiEventType`  
 Le type d'événement.  
  
 `guidContextId`  
 GUID du contexte.  
  
 `dwScriptContextCookie`  
 Le cookie à partir de le contexte.  
  
 `lScriptStatementStart`  
 L'emplacement du début de l'instruction de script.  
  
 `lScriptStatementEnd`  
 L'emplacement de la fin de l'instruction de script.  
  
 `dwReserved`  
 Réservé.