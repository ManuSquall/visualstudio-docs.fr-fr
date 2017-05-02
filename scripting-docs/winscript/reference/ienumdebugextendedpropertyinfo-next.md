---
title: "IEnumDebugExtendedPropertyInfo::Next | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumDebugExtendedPropertyInfo.Next
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IEnumDebugExtendedPropertyInfo::Next"
ms.assetid: ac41c9a3-19d1-4596-8a87-01c10b131be3
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumDebugExtendedPropertyInfo::Next
Récupère un nombrespécifié de structures d'`ExtendedDebugPropertyInfo` dans une séquence d'énumération.  
  
## Syntaxe  
  
```  
HRESULT Next (  
   ULONG celt,  
   ExtendedDebugPropertyInfo *rgelt,  
   ULONG* pceltFetched  
);  
```  
  
#### Paramètres  
 `celt`  
 \[in\]  Le nombre de structuresd' `ExtendedDebugPropertyInfo`à récupérer.  
  
 `rgelt`  
 \[out\]  Un tableau de structures d' `ExtendedDebugPropertyInfo` récupérées.  
  
 `pceltFetched`  
 \[out\]  Le nombre de structures d' `ExtendedDebugPropertyInfo` réellement récupérées.  
  
## Valeur de retour  
 Retourne `HRESULT`valide, en général `S_OK`.  
  
## Voir aussi  
 [IEnumDebugExtendedPropertyInfo, interface](../../winscript/reference/ienumdebugextendedpropertyinfo-interface.md)   
 [ExtendedDebugPropertyInfo, structure](../../winscript/reference/extendeddebugpropertyinfo-structure.md)