---
title: "IJsEnumDebugProperty::Next, m&#233;thode | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsEnumDebugProperty.Next
apilocation: jscript9diag.dll
ms.assetid: 9fad1893-483a-440c-88c1-469494212300
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsEnumDebugProperty::Next, m&#233;thode
Lit les propriétés de cet objet.  
  
## Syntaxe  
  
```  
HRESULT Next(  
   ULONG count,  
   IJsDebugProperty **ppDebugProperty,  
   ULONG *pActualCount  
);  
```  
  
#### Paramètres  
 `count`  
 \[in\] Nombre de propriétés à lire.  
  
 `ppDebugProperty`  
 \[out\] Objet représentant le navigateur de propriétés.  
  
 `pActualCount`  
 \[out\] Nombre réel de propriétés de l'objet.  
  
## Valeur de retour  
  
## Configuration requise  
 **En\-tête :** jscript9diag.h  
  
## Voir aussi  
 [IJsEnumDebugProperty, interface](../../winscript/reference/ijsenumdebugproperty-interface.md)