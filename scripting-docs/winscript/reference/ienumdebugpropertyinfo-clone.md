---
title: "IEnumDebugPropertyInfo::Clone | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumDebugPropertyInfo.Clone
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IEnumDebugPropertyInfo::Clone"
ms.assetid: ba6bdfdb-4c12-475c-bafc-efa6c109d7ee
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumDebugPropertyInfo::Clone
Crée un énumérateur qui contient le même état d'énumération que l'énumérateur actuel.  
  
## Syntaxe  
  
```  
HRESULT Clone (  
   IEnumDebugPropertyInfo** ppEnum  
);  
```  
  
#### Paramètres  
 `ppEnum`  
 \[out\] Retourne l'interface `IEnumDebugPropertyInfo` clonée.  
  
## Valeur de retour  
 Retourne `HRESULT`valide, en général `S_OK`.  
  
## Voir aussi  
 [IEnumDebugPropertyInfo, interface](../../winscript/reference/ienumdebugpropertyinfo-interface.md)