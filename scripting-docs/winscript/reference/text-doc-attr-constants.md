---
title: "TEXT_DOC_ATTR, constantes | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: TEXT_DOC_ATTR
apilocation: scrobj.dll
helpviewer_keywords: 
  - "TEXT_DOC_ATTR (constantes)"
ms.assetid: fd9c53a4-8f73-4c6a-abe5-6b831ecd5b1e
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# TEXT_DOC_ATTR, constantes
Décrivez les attributs du document.  
  
## Syntaxe  
  
```  
typedef DWORD TEXT_DOC_ATTR;  
```  
  
## Constantes  
  
|Constante|Valeur|Description|  
|---------------|------------|-----------------|  
|TEXT\_DOC\_ATTR\_READONLY|0x00000001|Le document est en lecture seule.|  
|TEXT\_DOC\_ATTR\_TYPE\_PRIMARY|0x00000002|Le document est le fichier principal de cette arborescence de documents.|  
|TEXT\_DOC\_ATTR\_TYPE\_WORKER|0x00000004|Le document est un ouvrier.|  
|TEXT\_DOC\_ATTR\_TYPE\_SCRIPT|0x00000008|Le document est un fichier de script.|  
  
## Voir aussi  
 [Débogueur de script actif, constantes, énumérations et structures](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)