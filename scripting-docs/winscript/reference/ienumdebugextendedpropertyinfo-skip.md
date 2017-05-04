---
title: "IEnumDebugExtendedPropertyInfo::Skip | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumDebugExtendedPropertyInfo.Skip
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IEnumDebugExtendedPropertyInfo::Skip"
ms.assetid: a0b4a9fc-e122-482b-9384-b83c460b61fe
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumDebugExtendedPropertyInfo::Skip
Ignore un nombre spécifié de structures d' `ExtendedDebugPropertyInfo` dans une séquence d'énumération.  
  
## Syntaxe  
  
```  
HRESULT Skip(  
   ULONG celt  
);  
```  
  
#### Paramètres  
 `celt`  
 \[in\]  Le nombre de structures d' `ExtendedDebugPropertyInfo` dans la séquence d'énumération à ignorer.  
  
## Valeur de retour  
 Retourne `HRESULT`valide, en général `S_OK`.  Retourne `S_FALSE` et place le pointeur d'élément actuel à la fin de l'énumération si `celt` est supérieur au nombre d'éléments conservés dans l'énumérateur.  
  
## Voir aussi  
 [IEnumDebugExtendedPropertyInfo, interface](../../winscript/reference/ienumdebugextendedpropertyinfo-interface.md)   
 [ExtendedDebugPropertyInfo, structure](../../winscript/reference/extendeddebugpropertyinfo-structure.md)