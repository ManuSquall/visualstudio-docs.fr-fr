---
title: "IWebAppDiagnosticsSetup (interface) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IWebAppDiagnosticsSetup (interface)"
ms.assetid: ec7359f2-633e-4d59-b64b-9cab0134dfd0
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IWebAppDiagnosticsSetup (interface)
Cette interface est implémentée par un PDM debug l'application de créer des objets COM dans le processus qui est débogué et d'activer des diagnostics de site Web.  Si les PDM debug des outils [IObjectWithSite](http://go.microsoft.com/fwlink/?LinkId=232438)d'objet application, les appels [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439) d'Internet Explorer lui après qu'il a été créé et passe par une référence à [IWebBrowser2](http://go.microsoft.com/fwlink/?LinkId=232449).  Les appels [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439) et passe d'une application de WWA dans le WWA avec onglets IWebApplicationHost à la place.  Si [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439) a été appelé avec une valeur non null, [IWebAppDiagnosticsSetup::DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md) retourne la valeur true.  Sinon, il retourne la valeur false et les appels à [IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md) échouent.  
  
> [!IMPORTANT]
>  `IWebAppDiagnosticsSetup` est implémenté par PDM v11.0 et supérieur.  Trouvé dans activdbg100.h.  
  
## Méthodes  
 Cette interface expose les méthodes suivantes.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md)|Obtient les documents texte qui sont masqués par le filtre spécifié.|  
|[IWebAppDiagnosticsSetup::DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md)|Détermine si le document spécifié appartient à l'un des nœuds enfants de ce nœud.|