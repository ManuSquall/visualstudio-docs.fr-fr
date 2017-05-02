---
title: "IEnumDebugPropertyInfo::GetCount | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumDebugPropertyInfo.GetCount
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IEnumDebugPropertyInfo::GetCount"
ms.assetid: 83a3becd-8533-4880-9c4f-193227ff25a9
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumDebugPropertyInfo::GetCount
Obtient le nombre de structures d' `DebugPropertyInfo` dans l'énumérateur.  
  
## Syntaxe  
  
```  
HRESULT GetCount (  
   ULONG* pcelt  
);  
```  
  
#### Paramètres  
 `pcelt`  
 \[out\]  Retourne le nombre de structures d' `DebugPropertyInfo` dans l'énumérateur.  
  
## Valeur de retour  
 Retourne `HRESULT`valide, en général `S_OK`.  
  
## Voir aussi  
 [IEnumDebugPropertyInfo, interface](../../winscript/reference/ienumdebugpropertyinfo-interface.md)   
 [DebugPropertyInfo, structure](../../winscript/reference/debugpropertyinfo-structure.md)