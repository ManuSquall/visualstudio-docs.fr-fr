---
title: "IRemoteDebugApplication::EnumGlobalExpressionContexts | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplication.EnumGlobalExpressionContexts
apilocation: pdm.dll
helpviewer_keywords: 
  - "IRemoteDebugApplication::EnumGlobalExpressionContexts"
ms.assetid: 61598a34-f409-42a2-810d-a9e92e2f4861
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IRemoteDebugApplication::EnumGlobalExpressionContexts
Énumère les contextes globaux d'expression pour tous les langages qui s'exécutent dans cette application.  
  
## Syntaxe  
  
```  
HRESULT EnumGlobalExpressionContexts(  
   IEnumDebugExpressionContexts**  ppedec  
);  
```  
  
#### Paramètres  
 `ppedec`  
 \[out\]  Énumérateur qui répertorie les contextes globaux d'expression pour tous les langages qui s'exécutent dans cette application.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 Cette méthode énumère les contextes globaux d'expression pour tous les langages qui s'exécutent dans cette application.  
  
## Voir aussi  
 [IRemoteDebugApplication, interface](../../winscript/reference/iremotedebugapplication-interface.md)