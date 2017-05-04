---
title: "SCRIPTTRACEINFO, &#233;num&#233;ration | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: cb8a4767-8c8e-4fa0-a735-038767a8c500
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# SCRIPTTRACEINFO, &#233;num&#233;ration
Représente l'événement de script qui est suivi.  Utilisé dans [IActiveScriptSiteTraceInfo::SendScriptTraceInfo, méthode](../../winscript/reference/iactivescriptsitetraceinfo-sendscripttraceinfo-method.md).  
  
## Syntaxe  
  
```  
typedef enum tagSCRIPTTRACEINFO {    
    SCRIPTTRACEINFO_SCRIPTSTART = 0,    
    SCRIPTTRACEINFO_SCRIPTEND   = 1,    
    SCRIPTTRACEINFO_COMCALLSTART    = 2,    
    SCRIPTTRACEINFO_COMCALLEND  = 3,    
    SCRIPTTRACEINFO_CREATEOBJSTART  = 4,    
    SCRIPTTRACEINFO_CREATEOBJEND    = 5,    
    SCRIPTTRACEINFO_GETOBJSTART = 6,    
    SCRIPTTRACEINFO_GETOBJEND   = 7,    
} SCRIPTTRACEINFO ;  
```  
  
## Valeurs d'énumération  
  
|||  
|-|-|  
|SCRIPTTRACEINFO\_SCRIPTSTART|Le début d'un script.|  
|SCRIPTTRACEINFO\_SCRIPTEND|La fin du script.|  
|SCRIPTTRACEINFO\_COMCALLSTART|Le début d'un appel de COM.|  
|SCRIPTTRACEINFO\_COMCALLEND|La fin d'un appel de COM.|  
|SCRIPTTRACEINFO\_CREATEOBJSTART|Le début de la création d'objets.|  
|SCRIPTTRACEINFO\_CREATEOBJEND|La fin de la création d'objets.|  
|SCRIPTTRACEINFO\_GETOBJSTART|Le début d'un appel de GetObject.|  
|SCRIPTTRACEINFO\_GETOBJEND|La fin d'un appel de GetObject.|