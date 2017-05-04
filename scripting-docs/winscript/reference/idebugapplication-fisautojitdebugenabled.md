---
title: "IDebugApplication::FIsAutoJitDebugEnabled | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplication.FIsAutoJitDebugEnabled
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplication::FIsAutoJitDebugEnabled"
ms.assetid: 0551dd3b-e6eb-442a-8201-418f96fe62df
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplication::FIsAutoJitDebugEnabled
Détermine si un débogueur juste\-à\-temps \(\(JIT\) est enregistré automatiquement pour déboguer les hôtes muets.  
  
## Syntaxe  
  
```  
BOOL FIsAutoJitDebugEnabled();  
```  
  
#### Paramètres  
 Cette méthode n'accepte pas de paramètres.  
  
## Valeur de retour  
 Si la méthode réussit et un débogage JIT est enregistré automatiquement pour déboguer les hôtes muets, la méthode retourne `TRUE`.  Sinon, il retourne `FALSE`.  
  
## Notes  
 Cette méthode détermine si un débogueur JIT est enregistré automatiquement pour déboguer les hôtes muets.  
  
## Voir aussi  
 [IDebugApplication, interface](../../winscript/reference/idebugapplication-interface.md)