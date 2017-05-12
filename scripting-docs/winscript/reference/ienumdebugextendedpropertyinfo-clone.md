---
title: "IEnumDebugExtendedPropertyInfo::Clone | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumDebugExtendedPropertyInfo.Clone
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IEnumDebugExtendedPropertyInfo::Clone"
ms.assetid: dd645cf6-bfb3-486c-829e-bb91a6639665
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumDebugExtendedPropertyInfo::Clone
Crée un énumérateur qui contient le même état d'énumération que l'énumérateur actuel.  
  
## Syntaxe  
  
```  
HRESULT Clone (  
   IEnumDebugExtendedPropertyInfo** ppEnum  
);  
```  
  
#### Paramètres  
 `ppEnum`  
 \[out\] Retourne l'interface `IEnumDebugExtendedPropertyInfo` clonée.  
  
## Valeur de retour  
 Retourne `HRESULT`valide, en général `S_OK`.  
  
## Voir aussi  
 [IEnumDebugExtendedPropertyInfo, interface](../../winscript/reference/ienumdebugextendedpropertyinfo-interface.md)