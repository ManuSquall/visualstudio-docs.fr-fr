---
title: IWebAppDiagnosticsObjectInitialization (Interface) | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IWebAppDiagnosticsObjectInitialization Interface
ms.assetid: 32847838-01d9-4205-a811-3043d8c7a917
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 159b81a336accea4e4e8c035119d5525de71ae90
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="iwebappdiagnosticsobjectinitialization-interface"></a>IWebAppDiagnosticsObjectInitialization (interface)
Cette interface peut être implémentée sur les classes qui implémentent [IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md). [IWebAppDiagnosticsSetup (Interface)](../../winscript/reference/iwebappdiagnosticssetup-interface.md) est implémentée par l’objet qui implémente [IDebugApplication (Interface)](../../winscript/reference/idebugapplication-interface.md). Dans la plupart des cas, cet objet est PDM.  
  
 Une fois que l’objet a été créé, [IWebAppDiagnosticsObjectInitialization::Initialize](../../winscript/reference/iwebappdiagnosticsobjectinitialization-initialize.md) est appelée avec une référence à l’application de débogage PDM et `hPassToObject` paramètre de `CreateObjectWithSiteAtWebApp`.  
  
> [!IMPORTANT]
>  `IWebAppDiagnosticsObjectInitialization`est trouvée dans activdbg100.h.  
  
## <a name="methods"></a>Méthodes  
 Cette interface expose les méthodes suivantes.  
  
|Méthode|Description|  
|------------|-----------------|  
|[IWebAppDiagnosticsObjectInitialization::Initialize](../../winscript/reference/iwebappdiagnosticsobjectinitialization-initialize.md)|Initialise l’objet.|