---
title: Interface IWebAppDiagnosticsSetup | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 71d4501fff04b62abe392c6684a4a0551dea9ee8
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63443666"
---
# <a name="iwebappdiagnosticssetup-interface"></a>IWebAppDiagnosticsSetup (interface)
Cette interface est implémentée par une application de débogage PDM pour créer des objets COM dans le processus en cours de débogage et pour activer les diagnostics de web. Si le PDM déboguer l’application objet implémente [IObjectWithSite](http://go.microsoft.com/fwlink/?LinkId=232438), Internet Explorer appelle [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439) après qu’il a été créé et transmet une référence à [IWebBrowser2](http://go.microsoft.com/fwlink/?LinkId=232449). Appelle une application WWA [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439) et transmet le WWA interface IWebApplicationHost à la place. Si [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439) a été appelé avec une valeur non NULL, [IWebAppDiagnosticsSetup::DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md) retourne la valeur true. Si pas, elle retourne la valeur false et les appels à [IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md) échouent.  
  
> [!IMPORTANT]
> `IWebAppDiagnosticsSetup` est implémentée par PDM version v11.0 et supérieures. Trouvée dans activdbg100.h.  
  
## <a name="methods"></a>Méthodes  
 Cette interface expose les méthodes suivantes.  
  
|Méthode|Description|  
|------------|-----------------|  
|[IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md)|Obtient les documents de texte qui sont masqués par le filtre spécifié.|  
|[IWebAppDiagnosticsSetup::DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md)|Détermine si le document spécifié appartient à un des nœuds enfants de ce nœud.|