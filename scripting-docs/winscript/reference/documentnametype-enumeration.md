---
title: "DOCUMENTNAMETYPE, &#233;num&#233;ration | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: DOCUMENTNAMETYPE
apilocation: scrobj.dll
helpviewer_keywords: 
  - "DOCUMENTNAMETYPE (énumération)"
ms.assetid: d36d550e-efb4-493d-8971-4de267005654
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# DOCUMENTNAMETYPE, &#233;num&#233;ration
Décrit ce type pour obtenir d'un document.  
  
## Syntaxe  
  
```  
typedef enum tagDOCUMENTNAMETYPE {  
   DOCUMENTNAMETYPE_APPNODE,  
   DOCUMENTNAMETYPE_TITLE,  
   DOCUMENTNAMETYPE_FILE_TAIL,  
   DOCUMENTNAMETYPE_URL,  
DOCUMENTNAMETYPE_UNIQUE_TITLE,  
} DOCUMENTNAMETYPE;  
```  
  
## Membres  
  
|Membre|Description|  
|------------|-----------------|  
|DOCUMENTNAMETYPE\_APPNODE|Obtient le nom tel qu'il apparaît dans l'arborescence d'application.|  
|DOCUMENTNAMETYPE\_TITLE|Obtient le nom tel qu'il apparaît dans la barre de titre de visionneuse.|  
|DOCUMENTNAMETYPE\_FILE\_TAIL|Obtient le nom de fichier sans chemin d'accès.|  
|DOCUMENTNAMETYPE\_URL|Obtient l'URL du document.|  
|DOCUMENTNAMETYPE\_UNIQUE\_TITLE|Obtient le titre ajouté à l'énumération pour l'identification.|  
  
## Voir aussi  
 [Débogueur de script actif, constantes, énumérations et structures](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)