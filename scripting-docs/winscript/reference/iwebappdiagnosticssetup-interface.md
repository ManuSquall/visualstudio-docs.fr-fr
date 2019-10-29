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
ms.openlocfilehash: 1e9bb3905da6227b978bc27b96493500f8d6d2ff
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72984540"
---
# <a name="iwebappdiagnosticssetup-interface"></a>IWebAppDiagnosticsSetup (interface)
Cette interface est implémentée par une application de débogage PDM pour créer des objets COM dans le processus en cours de débogage et pour activer les diagnostics Web. Si l’objet d’application de débogage PDM implémente [IObjectWithSite](/windows/win32/api/ocidl/nn-ocidl-iobjectwithsite), Internet Explorer appelle [SetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite) sur ce dernier après qu’il a été créé et passe une référence à [IWebBrowser2](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752127(v=vs.85)). Une application WWA appelle [SetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite) et passe l’interface WWA IWebApplicationHost à la place. Si [SetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite) a été appelé avec une valeur non null, [IWebAppDiagnosticsSetup ::D iagnosticssupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md) retourne la valeur true. Si ce n’est pas le cas, elle retourne false et les appels à [IWebAppDiagnosticsSetup :: CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md) échouent.  
  
> [!IMPORTANT]
> `IWebAppDiagnosticsSetup` est implémenté par PDM v 11.0 et ultérieur. Trouvée dans activdbg100.h.  
  
## <a name="methods"></a>Méthodes  
 Cette interface expose les méthodes suivantes.  
  
|Méthode|Description|  
|------------|-----------------|  
|[IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md)|Obtient les documents texte qui sont masqués par le filtre spécifié.|  
|[IWebAppDiagnosticsSetup::DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md)|Détermine si le document spécifié appartient à l’un des nœuds enfants de ce nœud.|