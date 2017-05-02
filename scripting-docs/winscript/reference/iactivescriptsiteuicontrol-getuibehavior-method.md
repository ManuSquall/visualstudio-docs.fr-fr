---
title: "IActiveScriptSiteUIControl::GetUIBehavior, m&#233;thode | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 9a944335-856a-4c6b-b2bc-8872542941b7
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# IActiveScriptSiteUIControl::GetUIBehavior, m&#233;thode
Obtient [SCRIPTUICHANDLING, énumération](../../winscript/reference/scriptuichandling-enumeration.md) qui représente la manière dont un contrôle d'IU doit être exécuté.  
  
## Syntaxe  
  
```  
HRESULT GetUIBehavior(   
    [in] SCRIPTUICITEM UicItem,   
    [out] SCRIPTUICHANDLING * pUicHandling   
);  
  
```  
  
#### Paramètres  
 `UicItem`  
 Type du contrôle.  
  
 `pUicHandling`  
 La méthode du contrôle doit être gérée.