---
title: "IWebAppDiagnosticsObjectInitialization (interface) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IWebAppDiagnosticsObjectInitialization (interface)"
ms.assetid: 32847838-01d9-4205-a811-3043d8c7a917
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IWebAppDiagnosticsObjectInitialization (interface)
Cette interface peut être implémentée sur les classes qui implémentent [IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md).  [IWebAppDiagnosticsSetup \(interface\)](../../winscript/reference/iwebappdiagnosticssetup-interface.md) est implémentée par l'objet qui implémente [IDebugApplication, interface](../../winscript/reference/idebugapplication-interface.md).  Dans la plupart des cas cet objet est le PDM.  
  
 Une fois que l'objet créé, [IWebAppDiagnosticsObjectInitialization::Initialize](../../winscript/reference/iwebappdiagnosticsobjectinitialization-initialize.md) est appelé avec une référence au PDM débogage de l'application et le paramètre d' `hPassToObject` d' `CreateObjectWithSiteAtWebApp`.  
  
> [!IMPORTANT]
>  `IWebAppDiagnosticsObjectInitialization` est trouvé dans activdbg100.h.  
  
## Méthodes  
 Cette interface expose les méthodes suivantes.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[IWebAppDiagnosticsObjectInitialization::Initialize](../../winscript/reference/iwebappdiagnosticsobjectinitialization-initialize.md)|Initialise l'objet.|