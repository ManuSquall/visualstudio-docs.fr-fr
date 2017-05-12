---
title: "IDebugProperty::GetParent | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugProperty.GetParent
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugProperty::GetParent"
ms.assetid: 673d625b-acca-45c4-88f4-b72275042f8f
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugProperty::GetParent
Obtient la propriété parent d'une propriété.  
  
## Syntaxe  
  
```  
HRESULT GetParent (  
   IDebugProperty** ppParent  
);  
```  
  
#### Paramètres  
 `ppParent`  
 \[out\]  Retourne l'interface d' `IDebugProperty` qui représente le parent de la propriété.  
  
## Valeur de retour  
 Retourne `HRESULT`valide, en général `S_OK`.  
  
## Voir aussi  
 [IDebugProperty, interface](../../winscript/reference/idebugproperty-interface.md)