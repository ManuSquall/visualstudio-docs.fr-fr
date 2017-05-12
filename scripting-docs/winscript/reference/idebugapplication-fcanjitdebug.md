---
title: "IDebugApplication::FCanJitDebug | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplication.FCanJitDebug
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplication::FCanJitDebug"
ms.assetid: d7ddac65-4864-411f-bf66-34a46c03f239
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplication::FCanJitDebug
Détermine si un débogueur juste\-à\-temps \(\(JIT\) est enregistré.  
  
## Syntaxe  
  
```  
BOOL FCanJitDebug();  
```  
  
#### Paramètres  
 Cette méthode n'accepte pas de paramètres.  
  
## Valeur de retour  
 Si la méthode réussit et un débogage JIT est enregistré, la méthode retourne `TRUE`.  Sinon, il retourne `FALSE`.  
  
## Notes  
 Cette méthode détermine si un débogueur JIT est enregistré.  
  
## Voir aussi  
 [IDebugApplication, interface](../../winscript/reference/idebugapplication-interface.md)