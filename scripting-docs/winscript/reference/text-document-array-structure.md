---
title: "TEXT_DOCUMENT_ARRAY (structure) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "TEXT_DOCUMENT_ARRAY (structure)"
ms.assetid: 47c08f23-981b-4105-9240-6dfffc6cb91b
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# TEXT_DOCUMENT_ARRAY (structure)
Tableau d'objets [IDebugDocumentText, interface](../../winscript/reference/idebugdocumenttext-interface.md).  Les membres sont alloués avec CoTaskMemAlloc.  
  
## Syntaxe  
  
```  
typedef struct tagTEXT_DOCUMENT_ARRAY  
{  
    DWORD dwCount;  
    [size_is(dwCount)] IDebugDocumentText **Members;  
} TEXT_DOCUMENT_ARRAY;  
  
```  
  
## Membres  
 `dwCount`  
 Le nombre de documents.  
  
 `Members`  
 l'ensemble de documents.  
  
## Voir aussi  
 [Débogueur de script actif, constantes, énumérations et structures](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)