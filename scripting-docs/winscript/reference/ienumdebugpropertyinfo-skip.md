---
title: "IEnumDebugPropertyInfo::Skip | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumDebugPropertyInfo.Skip
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IEnumDebugPropertyInfo::Skip"
ms.assetid: 2f6361fb-d66d-4fc0-8fe0-c859593a183f
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumDebugPropertyInfo::Skip
Ignore un nombre spécifié de structures d' `DebugPropertyInfo` dans une séquence d'énumération.  
  
## Syntaxe  
  
```  
HRESULT Skip(  
   ULONG celt  
);  
```  
  
#### Paramètres  
 `celt`  
 \[in\]  Le nombre de structures d' `DebugPropertyInfo` dans la séquence d'énumération à ignorer.  
  
## Valeur de retour  
 Retourne `HRESULT`valide, en général `S_OK`.  Retourne `S_FALSE` et place le pointeur d'élément actuel à la fin de l'énumération si `celt` est supérieur au nombre d'éléments conservés dans l'énumérateur.  
  
## Voir aussi  
 [IEnumDebugPropertyInfo, interface](../../winscript/reference/ienumdebugpropertyinfo-interface.md)   
 [DebugPropertyInfo, structure](../../winscript/reference/debugpropertyinfo-structure.md)