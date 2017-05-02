---
title: "APPLICATION_NODE_EVENT_FILTER, &#233;num&#233;ration | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "APPLICATION_NODE_EVENT_FILTER (constantes)"
ms.assetid: dccb2cf7-0598-46f8-b3eb-16b752815e96
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# APPLICATION_NODE_EVENT_FILTER, &#233;num&#233;ration
Spécifie les types de nœuds pour exclure lorsque le filtrage des documents de code.  Utilisé dans [IDebugApplicationNode100::GetExcludedDocuments](../../winscript/reference/idebugapplicationnode100-getexcludeddocuments.md) et [IDebugApplicationNode100::SetFilterForEventSink](../../winscript/reference/idebugapplicationnode100-setfilterforeventsink.md)  
  
> [!IMPORTANT]
>  Ces constantes sont implémentées par PDM v10.0 et supérieur.  Trouvé dans activdbg100.h.  
  
## Syntaxe  
  
```cpp  
typedef enum tagAPPLICATION_NODE_EVENT_FILTER {  
    FILTER_EXCLUDE_NOTHING = 0,  
    FILTER_EXCLUDE_ANONYMOUS_CODE = 0x1,  
    FILTER_EXCLUDE_EVAL_CODE = 0x2  
} APPLICATION_NODE_EVENT_FILTER;  
  
```  
  
## Membres  
  
|Membre|Valeur|Description|  
|------------|------------|-----------------|  
|FILTER\_EXCLUDE\_NOTHING|0x00000000|Envoyez tous les événements.|  
|FILTER\_EXCLUDE\_ANONYMOUS\_CODE|0x00000001|Excluez les nœuds anonymes de code.  Ces nœuds sont utilisés par le runtime JScript pour `new Function([args,] <code>)'`.|  
|FILTER\_EXCLUDE\_EVAL\_CODE|0x00000002|Excluez les nœuds de code eval.  Ces nœuds sont utilisés par le runtime JScript pour la prise en charge eval.|  
  
## Voir aussi  
 [Débogueur de script actif, constantes, énumérations et structures](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)