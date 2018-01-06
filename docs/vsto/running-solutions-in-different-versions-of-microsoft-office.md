---
title: "Exécution de Solutions dans différentes Versions de Microsoft Office | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- solutions [Office development in Visual Studio], multiple Office versions
- Office applications [Office development in Visual Studio], multiple Office versions
- Office development in Visual Studio, multiple Office versions
- Office solutions [Office development in Visual Studio]
- multiple Office versions
ms.assetid: 414e7741-c07d-4900-9d10-68b821413b3f
caps.latest.revision: "61"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: a52ab5c2f2f5a367681929966175ca4c4cb33b56
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="running-solutions-in-different-versions-of-microsoft-office"></a>Exécution de solutions dans différentes versions de Microsoft Office
    
## <a name="running-office-solutions-created-by-using-visual-studio-2010-and-above"></a>Exécution de solutions Office créées à l'aide de Visual Studio 2010 et versions ultérieures  
  
|Version d'Office ciblée par le modèle de projet|Cibler .NET Framework du projet<sup>1</sup>|Versions d'Office pouvant exécuter la solution|Runtime requis sur l'ordinateur de l'utilisateur final|  
|--------------------------------------------------------|------------------------------------------------------|--------------------------------------------------|-------------------------------------------|  
|Office 2016 et [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]|[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou version ultérieure|Office 2016<br /><br /> [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]<br /><br /> [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]<br /><br /> Microsoft Office system 2007<sup>2</sup>|Visual Studio 2010 Tools pour Office Runtime|  
|[!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]|[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou version ultérieure|Office 2016<br /><br /> [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]<br /><br /> [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]<br /><br /> Microsoft Office system 2007<sup>2</sup>|Visual Studio 2010 Tools pour Office Runtime|  
|[!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]|.NET Framework 3.5|Office 2016<br /><br /> [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]<br /><br /> [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]|Visual Studio 2010 Tools pour Office Runtime|  
|Version 2007 de Microsoft Office System|[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou version ultérieure<br /><br /> ou<br /><br /> .NET Framework 3.5|Office 2016<br /><br /> [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]<br /><br /> [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]<br /><br /> Version 2007 de Microsoft Office System|Visual Studio 2010 Tools pour Office Runtime|  
  
 1. La version du .NET Framework ciblée par votre projet doit être installée sur les ordinateurs des utilisateurs finaux pour que votre solution puisse fonctionner. Par exemple, si votre projet cible le .NET Framework 3.5, ce dernier doit être installé sur les ordinateurs des utilisateurs finaux. Dans cet exemple, votre solution ne fonctionnera pas si seul le [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] est installé sur les ordinateurs des utilisateurs finaux.  
  
 2. Dans ce scénario, la solution s'exécutera sans erreur dans la version 2007 de Microsoft Office System uniquement si elle n'utilise pas les nouvelles fonctionnalités d'[!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)].  
  
## <a name="running-office-solutions-created-by-using-versions-of-visual-studio-prior-to-visual-studio-2010"></a>Exécution de solutions Office créées à l'aide de versions de Visual Studio antérieures à Visual Studio 2010  
 Les applications Microsoft Office peuvent exécuter des solutions créées à l'aide de versions de Visual Studio antérieures à Visual Studio 2010. Dans certains cas, ces solutions requièrent des versions différentes de [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Des versions différentes de [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] peuvent être installées côte à côte sur le même ordinateur.  
  
 Le tableau suivant présente les versions de Microsoft Office peuvent exécuter des solutions créées à l’aide de versions antérieures de Visual Studio, ainsi que les versions de la [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] et le .NET Framework sont requises pour chaque solution.  
  
|Édition de Visual Studio utilisée pour créer la solution|Version d'Office ciblée par le modèle de projet|Versions d'Office pouvant exécuter la solution|Runtime requis sur l'ordinateur de l'utilisateur final|Version du .NET Framework requise sur l'ordinateur de l'utilisateur final|  
|----------------------------------------------------------|--------------------------------------------------------|--------------------------------------------------|-------------------------------------------|----------------------------------------------------------|  
|Visual Studio 2008 Professional<br /><br /> ou<br /><br /> Visual Studio Team System 2008|Version 2007 de Microsoft Office System|[!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]et [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] <sup>1</sup><br /><br /> Version 2007 de Microsoft Office System|Visual Studio 2010 Tools pour Office Runtime<sup>1</sup><br /><br /> ou<br /><br /> Microsoft Visual Studio Tools pour Microsoft Office System (Runtime version 3.0)|.NET Framework 3.5|  
|Une des éditions suivantes de Visual Studio 2005 avec VSTO 2005 SE<sup>2</sup> installé :<br /><br /> -Visual Studio 2005 Tools pour Office<br />-Visual Studio Team System 2005<br />-Visual Studio 2005 Professional|Version 2007 de Microsoft Office System|[!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]et [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] (32 bits uniquement<sup>3</sup>)<br /><br /> Version 2007 de Microsoft Office System|Visual Studio 2005 Tools pour Office Second Edition Runtime|.NET Framework 2.0, .NET Framework 3.0 ou .NET Framework 3.5|  
|Une des éditions suivantes de Visual Studio :<br /><br /> -Visual Studio 2008 Professional<br />-Visual Studio Team System 2008<br />-Visual Studio 2005 Tools pour Office (avec ou sans VSTO 2005 SE<sup>2</sup> installé)<br />-Visual Studio Team System 2005 (avec ou sans VSTO 2005 SE<sup>2</sup> installé)<br />-Visual Studio 2005 Professional avec VSTO 2005 SE<sup>2</sup> installé|Microsoft Office 2003|[!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]et [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] (32 bits uniquement<sup>3</sup>)<br /><br /> Version 2007 de Microsoft Office System<br /><br /> Microsoft Office 2003|Visual Studio 2005 Tools pour Office Second Edition Runtime|.NET Framework 2.0, .NET Framework 3.0 ou .NET Framework 3.5|  
  
 1. Les applications [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] et [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] incluent Visual Studio 2010 Tools pour Office Runtime. Par conséquent, ces applications utilisent toujours Visual Studio 2010 Tools pour Office Runtime plutôt que Visual Studio Tools pour Microsoft Office System (Runtime version 3.0) dans ce scénario. Les applications dans la version 2007 de Microsoft Office System peuvent utiliser Visual Studio 2010 Tools pour Office Runtime ou Visual Studio Tools pour Microsoft Office System (Runtime version 3.0).  
  
 2. VSTO 2005 SE est un complément Visual Studio gratuit qui fournit des modèles de projet de complément VSTO pour Microsoft Office 2003 et pour la version 2007 de Microsoft Office System. Il peut être installé avec Visual Studio 2005 Professional, Visual Studio 2005 Tools pour Office ou une édition de Visual Studio Team System 2005. Pour plus d’informations, consultez [Visual Studio 2005 Tools pour Office Second Edition](http://go.microsoft.com/fwlink/?LinkId=148446).  
  
 3. Les solutions Office qui nécessitent Visual Studio 2005 Tools pour Office Second Edition Runtime ne sont pas compatibles avec les versions 64 bits d'[!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] et d'[!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]. Pour exécuter ces solutions dans l'édition 64 bits d'[!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] ou d'[!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)], vous devez mettre le projet à niveau vers [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)] ou vers un projet Visual Studio 2008 qui cible la version 2007 de Microsoft Office System.  
  
## <a name="see-also"></a>Voir aussi  
 [Conception et création de Solutions Office](../vsto/designing-and-creating-office-solutions.md)   
 [Visual Studio Tools for Office Runtime Overview](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Visual Studio Tools for Office Runtime Installation Scenarios](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md)   
 [Configuration d’un ordinateur pour développer des solutions Office](../vsto/running-solutions-in-different-versions-of-microsoft-office.md)  
  
  