---
title: "IActiveScriptErrorDebug110 (interface) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptErrorDebug110 (interface)"
ms.assetid: 5c1a4993-4cad-4ccf-89c2-53abfddfe1f2
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# IActiveScriptErrorDebug110 (interface)
Ajoute la fonctionnalité au [IActiveScriptDebug, interface](../../winscript/reference/iactivescriptdebug-interface.md).  Cette interface est implémentée par le moteur JavaScript pour déterminer pourquoi un événement BREAKREASON\_ERROR s'est produit.  
  
> [!IMPORTANT]
>  Elle est implémentée par PDM version v11.0 et supérieures.  Trouvée dans activdbg100.h.  
  
## Méthodes  
 L'interface `IActiveScriptErrorDebug110` expose les méthodes suivantes :  
  
|Méthode|Description|  
|-------------|-----------------|  
|[IActiveScriptErrorDebug110::GetExceptionThrownKind](../../winscript/reference/iactivescripterrordebug110-getexceptionthrownkind.md)|Retourne le type d'exception d'une exception levée.|