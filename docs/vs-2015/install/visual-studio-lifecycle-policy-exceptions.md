---
title: Exceptions de stratégie de cycle de vie de Visual Studio | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-install
ms.topic: conceptual
ms.assetid: c238489d-6181-42c6-aa60-f75d0889dc68
caps.latest.revision: 3
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: b17693523c75dc434fdda258c07a9b17ecfda1b0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68180240"
---
# <a name="visual-studio-lifecycle-policy-exceptions"></a>Exceptions liées à la stratégie de cycle de vie Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio comprend une collection de compilateurs, de langages, de runtimes, d’environnements et d’autres ressources qui permettent de développer sur de nombreuses plateformes Microsoft. À des fins pratiques, Visual Studio peut installer certains Kits de développement logiciel (SDK) Microsoft et d’autres composants Microsoft qui ciblent et prennent en charge ces plateformes Microsoft. Ces composants peuvent faire l’objet d’une licence et d’une prise en charge établissant leurs propres termes et stratégies.  
  
## <a name="external-components-that-follow-a-lifecycle-policy-other-than-the-visual-studio-policy"></a>Composants externes adhérant à une stratégie de cycle de vie autre que celle de Visual Studio  
 Le tableau suivant répertorie les composants de plateforme Microsoft qui peuvent être inclus avec Visual Studio (selon la version spécifique du logiciel Visual Studio) et ceux qui sont soumis à leurs propres stratégies de prise en charge et délais d’exécution.  
  
|FAMILLE DE PRODUITS|NOM EXTERNE|  
|--------------------|-------------------|  
|[.NET 3.5](http://support.microsoft.com/lifecycle/search/default.aspx?sort=PN&alpha=net%20framework%203.5&Filter=FilterNO)|.NET 3.5 SDK<br /><br /> Windows Identity Foundation|  
|[.NET 4.5](http://support.microsoft.com/lifecycle/search/default.aspx?sort=PN&alpha=net%20framework%204.5&Filter=FilterNO)|.NET 4.5, SDK|  
|[.NET 4.5.1](http://support.microsoft.com/lifecycle/search/default.aspx?sort=PN&alpha=.NET%20Framework%204.5.1&Filter=FilterNO)|.NET 4.5.1 MT Pack (Classic)<br /><br /> .NET 4.5.1 Multi-Targeting Pack (Store)<br /><br /> .NET 4.5.1 OOB MSU<br /><br /> Package redistribuable .NET 4.5.1<br /><br /> Modules linguistiques du package redistribuable .NET 4.5.1<br /><br /> .NET 4.5.1, SDK|  
|[Pile web ASP.NET](http://go.microsoft.com/fwlink/?LinkId=328918)|ASP.NET MVC 4<br /><br /> ASP.NET MVC 5<br /><br /> API web ASP.NET<br /><br /> API web ASP.NET 2<br /><br /> Pages web ASP.NET 2<br /><br /> Pages web ASP.NET 3|  
|[Entity Framework 6](http://go.microsoft.com/fwlink/?LinkId=328950)|Entity Framework 6|  
|[Exchange 2013](http://go.microsoft.com/fwlink/?LinkId=328950)|Services web Exchange|  
|[Microsoft OWIN](http://go.microsoft.com/fwlink/?LinkId=328951)|Microsoft OWIN|  
|[Microsoft Web Developer Tools 2013](http://go.microsoft.com/fwlink/?LinkId=328952)|Microsoft Web Developer Tools 2013|  
|Les mises à jour apportées à ces composants sont distribuées par le biais de NuGet et ne respectent pas les stratégies standard de cycle de vie Microsoft.  Pour plus d’informations, consultez [http://docs.nuget.org/](http://docs.nuget.org/).|Gestionnaire de jetons web JSON pour le Microsoft .NET Framework 4.5<br /><br /> NuGet 2.7<br /><br /> SignalR<br /><br /> Web Optimization Framework<br /><br /> WebGrease|  
|[ODataLib](http://go.microsoft.com/fwlink/?LinkId=328954)|ODataLib|  
|[Office 2013](http://support.microsoft.com/lifecycle/?p1=16674)|Open XML SDK|  
|[Stratégie des services en ligne](http://support.microsoft.com/gp/OSSLpolicy)|Microsoft Ads SDK|  
|[SharePoint 2013](http://support.microsoft.com/lifecycle/search/default.aspx?sort=PN&alpha=sharepoint%20server%202013&Filter=FilterNO)|Composant client SharePoint<br /><br /> SharePoint Foundation 2013<br /><br /> Extensions Windows Identity Foundation|  
|[Silverlight 5](http://support.microsoft.com/lifecycle/?p1=16278)<br /><br /> <br />> Voir aussi : [http://support.microsoft.com/gp/lifean45](http://support.microsoft.com/gp/lifean45)|Silverlight 5 Runtime<br /><br /> Silverlight 5, SDK|  
|[SQL Server 2008 R2](http://support.microsoft.com/lifecycle/search/default.aspx?sort=PN&alpha=SQL%20Server%202008%20R2&Filter=FilterNO)|Types CLR du système SQL (SQL Server 2008 R2)|  
|[SQL Server 2012](http://support.microsoft.com/lifecycle/search/default.aspx?sort=PN&alpha=SQL%20Server%202012&Filter=FilterNO)|DACFx (DACFramework)<br /><br /> SMO (SharedManagementObjects)<br /><br /> Utilitaires de ligne de commande SQL<br /><br /> Service de langage SQL - IntelliSense (TSQLLanguageService)<br /><br /> SQL LocalDB<br /><br /> SQL Native Client (Sqlncli)<br /><br /> SQL Server Express 2012 SP1<br /><br /> Types CLR du système SQL (SQL Server 2012)<br /><br /> SQLDOM|  
|[SQL Server 2014](https://support.microsoft.com/lifecycle/search?sort=PN&alpha=SQL%20Server%202014&Filter=FilterNO)|DACFx (DACFramework)<br /><br /> SMO (SharedManagementObjects)<br /><br /> Utilitaires de ligne de commande SQL<br /><br /> Service de langage SQL - IntelliSense (TSQLLanguageService)<br /><br /> SQL LocalDB<br /><br /> SQL Native Client (Sqlncli)<br /><br /> SQL Server Express 2014<br /><br /> Types CLR du système SQL (SQL Server 2014)<br /><br /> SQLDOM|  
|[SQL Server Compact Edition 4.0](http://support.microsoft.com/lifecycle/?p1=16106)|SQL Server Compact Edition 4.0|  
|[WCF RIA Services v1.0 SP2](http://go.microsoft.com/fwlink/?LinkId=328955)|Services RIA WCF V1.0 SP2|  
|[Windows Server 2008](http://support.microsoft.com/lifecycle/search/default.aspx?sort=PN&alpha=Windows%20Server%202008&Filter=FilterNO)|Windows Web Services (WWS) pour Windows Server 2008|  
|[Windows 7 ](http://support.microsoft.com/lifecycle/?c2=14019)|Windows 7, SDK|  
|[Windows 8](http://support.microsoft.com/lifecycle/?c2=16796)|Windows 8, SDK|  
|[Windows 8.1](http://support.microsoft.com/lifecycle/search/default.aspx?sort=PN&alpha=windows%208.1&Filter=FilterNO)|SDK Windows 8.1<br /><br /> Bibliothèque Windows pour JavaScript (WinJS)|  
|[Microsoft Azure](http://support.microsoft.com/gp/azure-cloud-lifecycle-faq)<br /><br /> <br />> Voir aussi : [Stratégie de cycle de vie en ligne](http://support.microsoft.com/gp/OSSLpolicy)|Microsoft Azure Mobile Services SDK<br /><br /> Outils Microsoft Azure Mobile Services|