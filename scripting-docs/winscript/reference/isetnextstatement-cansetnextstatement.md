---
title: "ISetNextStatement::CanSetNextStatement | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: ISetNextStatement.CanSetNextStatement
apilocation: scrobj.dll
ms.assetid: e2a54634-31ec-4d16-84e8-2b123845d876
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# ISetNextStatement::CanSetNextStatement
Cette méthode détermine si le point d'exécution, qui détermine l'instruction suivante du code à exécuter, peut être défini à l'emplacement spécifié.  
  
## Syntaxe  
  
```  
HRESULT CanSetNextStatement(  
   IDebugStackFrame*  pStackFrame,  
   IDebugCodeContext*  pCodeContext  
)  
```  
  
#### Paramètres  
 `pStackFrame`  
 \[in\]  Pointeur vers un objet de frame de pile.  
  
 `pCodeContext`  
 \[in\]  Pointeur vers un objet de contexte de code.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La prochaine instruction peut être mise à jour dans le contexte de code spécifié.|  
|`S_FALSE`|L'instruction suivante ne peut pas être mise à jour dans le contexte de code spécifié.|  
  
## Notes  
  
## Voir aussi  
 [ISetNextStatement, interface](../../winscript/reference/isetnextstatement-interface.md)