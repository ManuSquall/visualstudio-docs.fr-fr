---
title: "IDebugFormatter, interface | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugFormatter (interface)"
ms.assetid: 022142d4-c8e1-47ae-b771-3e24953293e5
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugFormatter, interface
Permet à un langage ou l'IDE pour personnaliser la conversion entre les valeurs VARIANTES ou le VARTYPE types et des chaînes.  
  
 Outre les méthodes héritées de `IUnknown`, l'interface `IDebugFormatter` expose les méthodes suivantes.  
  
## Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|-------------|-----------------|  
|[IDebugFormatter::GetStringForVariant](../../winscript/reference/idebugformatter-getstringforvariant.md)|Retourne une chaîne qui représente la valeur VARIANT donnée.|  
|[IDebugFormatter::GetVariantForString](../../winscript/reference/idebugformatter-getvariantforstring.md)|Retourne une VARIANT contenant la chaîne spécifiée.|  
|[IDebugFormatter::GetStringForVarType](../../winscript/reference/idebugformatter-getstringforvartype.md)|Retourne une chaîne qui représente la valeur donnée de VARTYPE.|