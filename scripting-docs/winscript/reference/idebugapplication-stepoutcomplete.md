---
title: "IDebugApplication::StepOutComplete | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplication.StepOutComplete
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplication::StepOutComplete"
ms.assetid: 9675b214-7be5-4cf7-a63f-7865f3c54371
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplication::StepOutComplete
Informe le processus de débogage le gestionnaire qu'un moteur de langage en mode en pas \- à \- pas est sur le point de revenir à son appelant.  
  
## Syntaxe  
  
```  
HRESULT StepOutComplete();  
```  
  
#### Paramètres  
 Cette méthode n'accepte pas de paramètres.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 Les moteurs de langages appellent cette méthode en mode en pas \- à \- pas juste avant qu'ils retournent à leur appelant.  Le processus de débogage utilise de gestionnaire cette possibilité de signaler toutes autres moteurs de script qu'ils doivent qu'il s'arrête à la première possibilité.  Cette technique est comment les modes pas \- à \- pas interlangages sont implémentés.  
  
## Voir aussi  
 [IDebugApplication, interface](../../winscript/reference/idebugapplication-interface.md)