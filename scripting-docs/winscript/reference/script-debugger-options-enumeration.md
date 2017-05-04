---
title: "SCRIPT_DEBUGGER_OPTIONS (&#233;num&#233;ration) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "SCRIPT_DEBUGGER_OPTIONS (énumération)"
ms.assetid: aef41ec0-6f65-48e8-a69e-44b4e4fb929f
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# SCRIPT_DEBUGGER_OPTIONS (&#233;num&#233;ration)
Indique un jeu d'options et\/ou de fonctionnalités qui s'appliquent au débogueur est attaché.  Utilisé dans [IDebugApplicationNode100::GetExcludedDocuments](../../winscript/reference/idebugapplicationnode100-getexcludeddocuments.md) et [IDebugApplicationNode100::SetFilterForEventSink](../../winscript/reference/idebugapplicationnode100-setfilterforeventsink.md)  
  
> [!IMPORTANT]
>  Ces constantes sont implémentées par PDM v10.0 et supérieur.  Trouvé dans activdbg100.h.  
  
## Syntaxe  
  
```  
typedef SCRIPT_DEBUGGER_OPTIONS  
```  
  
## Membres  
  
|Membre|Valeur|Description|  
|------------|------------|-----------------|  
|SDO\_NONE|0x00000000|Aucune option n'est définie.|  
|SDO\_ENABLE\_FIRST\_CHANCE\_EXCEPTIONS|0x00000001|Indique que le runtime de script doit déclencher des événements de BREAKREASON\_ERROR lorsqu'une exception est levée.  Cette option peut être définie par le débogueur, ou le jeu par utilisateur code via `Debug.enableFirstChanceExceptions(<true&#124;false>)`.|  
|SDO\_ENABLE\_WEB\_WORKER\_SUPPORT|0x00000002|Indique que le débogueur lié prend en charge des ouvriers de site Web.|  
  
## Voir aussi  
 [Débogueur de script actif, constantes, énumérations et structures](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)