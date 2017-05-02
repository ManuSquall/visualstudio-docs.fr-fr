---
title: "IDebugStackFrame, interface | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugStackFrame (interface)"
ms.assetid: e95c1b4f-17c1-490c-a56b-c25fa45d4822
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugStackFrame, interface
Représente un frame de pile logique sur la pile des threads.  Appelez la méthode d' `IDebugStackFrame::QueryInterface` pour obtenir l'interface d' `IDebugExpressionContext` , qui permet l'évaluation de l'expression et les fenêtres Espion.  
  
 Outre les méthodes héritées de `IUnknown`, l'interface `IDebugStackFrame` expose les méthodes suivantes.  
  
## Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|-------------|-----------------|  
|[IDebugStackFrame::GetCodeContext](../../winscript/reference/idebugstackframe-getcodecontext.md)|Retourne le contexte de code actuel associé au frame de pile.|  
|[IDebugStackFrame::GetDescriptionString](../../winscript/reference/idebugstackframe-getdescriptionstring.md)|Retourne une description textuelle courte ou plus longue du frame de pile.|  
|[IDebugStackFrame::GetLanguageString](../../winscript/reference/idebugstackframe-getlanguagestring.md)|Retourne une description textuelle courte ou longue du langage.|  
|[IDebugStackFrame::GetThread](../../winscript/reference/idebugstackframe-getthread.md)|Retourne le thread associé à ce frame de pile.|  
|[IDebugStackFrame::GetDebugProperty](../../winscript/reference/idebugstackframe-getdebugproperty.md)|Retourne l'Explorateur de propriétés pour le frame en cours.|