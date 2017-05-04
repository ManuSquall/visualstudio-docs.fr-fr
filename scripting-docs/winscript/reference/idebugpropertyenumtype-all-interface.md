---
title: "IDebugPropertyEnumType_All, interface | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugPropertyEnumType_All
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugPropertyEnumType_All (interface)"
ms.assetid: 4d0f4fd5-e5f7-47cb-b746-860d6363e2cd
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugPropertyEnumType_All, interface
Les interfaces d' `IDebugPropertyEnumType` sont définies afin que chacune de leurs IID puisse être passé en tant que filtre à `IDebugProperty::EnumMembers` en demandant l'énumérateur approprié.  
  
## Syntaxe  
  
```  
IDebugPropertyEnumType_All : IUnknown  
```  
  
## Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|-------------|-----------------|  
|[IDebugPropertyEnumType\_All::GetName](../../winscript/reference/idebugpropertyenumtype-all-getname.md)|Retourne une chaîne de texte qui décrit le nom|  
  
 Les interfaces suivantes héritent d' `IDebugPropertyEnumType_All`, et n'ont aucune méthode supplémentaire.  
  
```  
IDebugPropertyEnumType_Arguments : IDebugPropertyEnumType_All   
IDebugPropertyEnumType_Locals : IDebugPropertyEnumType_All   
IDebugPropertyEnumType_LocalsPlusArgs : IDebugPropertyEnumType_All   
IDebugPropertyEnumType_Registers : IDebugPropertyEnumType_All  
```  
  
## Voir aussi  
 [IDebugProperty::EnumMembers](../../winscript/reference/idebugproperty-enummembers.md)