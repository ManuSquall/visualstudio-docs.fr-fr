---
title: "SCRIPTLANGUAGEVERSION, &#233;num&#233;ration | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 58aa904a-e3ed-41c6-82d6-e91c8279a792
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# SCRIPTLANGUAGEVERSION, &#233;num&#233;ration
Spécifie les versions possibles de script.  
  
## Syntaxe  
  
```cpp  
typedef enum tagSCRIPTLANGUAGEVERSION  
{  
    SCRIPTLANGUAGEVERSION_DEFAULT = 0,  
    SCRIPTLANGUAGEVERSION_5_7  = 1,  
    SCRIPTLANGUAGEVERSION_5_8  = 2,  
    SCRIPTLANGUAGEVERSION_MAX  = 255  
} SCRIPTLANGUAGEVERSION ;  
  
```  
  
## Valeurs d'énumération  
  
|||  
|-|-|  
|SCRIPTLANGUAGEVERSION\_DEFAULT|Version par défaut.  La valeur entière est 0.|  
|SCRIPTLANGUAGEVERSION\_5\_7|Version 5,7 de scripts windows.  La valeur entière est 1.|  
|SCRIPTLANGUAGEVERSION\_5\_8|Version 5,8 de scripts windows.  La valeur entière est 2.|  
|SCRIPTLANGUAGEVERSION\_MAX|La version maximale.  La valeur entière est 255.|  
  
## Voir aussi  
 [Script actif, constantes, énumérations et codes d'erreur](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)