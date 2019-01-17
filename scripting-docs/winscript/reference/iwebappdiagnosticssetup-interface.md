---
title: Interface IWebAppDiagnosticsSetup | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IWebAppDiagnosticsSetup Interface
ms.assetid: ec7359f2-633e-4d59-b64b-9cab0134dfd0
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fc29282ec9d00ff79131765d2bf294c54fa347c6
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54344900"
---
# <a name="iwebappdiagnosticssetup-interface"></a>IWebAppDiagnosticsSetup (interface)
Cette interface est implémentée par une application de débogage PDM pour créer des objets COM dans le processus en cours de débogage et pour activer les diagnostics de web. Si le PDM déboguer l’application objet implémente [IObjectWithSite](http://go.microsoft.com/fwlink/?LinkId=232438), Internet Explorer appelle [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439) après qu’il a été créé et transmet une référence à [IWebBrowser2](http://go.microsoft.com/fwlink/?LinkId=232449). Appelle une application WWA [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439) et transmet le WWA interface IWebApplicationHost à la place. Si [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439) a été appelé avec une valeur non NULL, [IWebAppDiagnosticsSetup::DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md) retourne la valeur true. Si pas, elle retourne la valeur false et les appels à [IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md) échouent.  
  
> [!IMPORTANT]
>  `IWebAppDiagnosticsSetup` est implémentée par PDM version v11.0 et supérieures. Trouvée dans activdbg100.h.  
  
## <a name="methods"></a>Méthodes  
 Cette interface expose les méthodes suivantes.  
  
|Méthode|Description|  
|------------|-----------------|  
|[IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md)|Obtient les documents de texte qui sont masqués par le filtre spécifié.|  
|[IWebAppDiagnosticsSetup::DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md)|Détermine si le document spécifié appartient à un des nœuds enfants de ce nœud.|