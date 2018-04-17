---
title: Solutions InfoPath | Documents Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- solutions [Office development in Visual Studio], InfoPath
- templates [Office development in Visual Studio], InfoPath
- InfoPath [Office development in Visual Studio]
- Office development in Visual Studio, InfoPath solutions
- projects [Office development in Visual Studio], InfoPath
- Office solutions [Office development in Visual Studio], InfoPath
- Office projects [Office development in Visual Studio], InfoPath
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9db28542e4141767be55241b98e0a6b762b0e236
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="infopath-solutions"></a>Solutions InfoPath
  Visual Studio fournit des modèles de projet à l’aide desquels vous pouvez créer des compléments VSTO pour Microsoft Office InfoPath 2013 et InfoPath 2010. InfoPath n’est pas disponible dans Office 2016.  
  
> [!NOTE]  
>  Vous pouvez toujours créer un complément VSTO dans pour InfoPath même si vous avez installé Office 2016. Pour cela, installez simplement InfoPath 2013 ou Office 2013 côte à côte avec Office 2016.  
  
 [!INCLUDE[appliesto_infoallapp](../vsto/includes/appliesto-infoallapp-md.md)]  
  
> [!NOTE]  
>  Vous souhaitez développer des solutions qui étendent l’expérience Office sur [plusieurs plateformes](https://dev.office.com/add-in-availability)? Découvrez le nouvel [modèle des compléments Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Compléments Office ont un faible encombrement mémoire par rapport aux compléments VSTO et les solutions, et vous pouvez les créer à l’aide de presque n’importe quel web technologies, telles que HTML5, JavaScript, CSS3 et XML de programmation.  
  
 Les compléments VSTO pour InfoPath sont semblables aux compléments VSTO conçus pour les autres applications Microsoft Office. Ces types de solutions se composent d'un assembly chargé par l'application. L'utilisateur final peut accéder aux fonctionnalités de cet assembly quel que soit le formulaire ou le modèle de formulaire ouvert. Pour plus d’informations sur les compléments VSTO, consultez [Getting Started Programming VSTO Add-ins](../vsto/getting-started-programming-vsto-add-ins.md) et [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md).  
  
> [!NOTE]  
>  Visual Studio 2015 n'inclut pas les projets de modèle de formulaire InfoPath qui étaient disponibles dans les versions antérieures de Visual Studio. Vous ne pouvez pas non plus utiliser Visual Studio 2015 pour ouvrir ou modifier un projet de modèle de formulaire InfoPath qui a été créé dans une version antérieure de Visual Studio. Toutefois, cela est possible en utilisant Visual Studio Tools pour Applications. Pour plus d’informations, consultez [Utilisation des projets VSTO 2008 dans InfoPath 2010](http://go.microsoft.com/fwlink/?LinkID=218903).  
  
## <a name="automating-infopath-by-using-an-add-in"></a>Automatisation d'InfoPath à l'aide d'un complément  
 Pour accéder au modèle objet d’InfoPath à partir d’un complément VSTO Office créé à l’aide des outils de développement Office dans Visual Studio, utilisez le champ `Application` de la classe `ThisAddIn` dans votre projet. Le champ `Application` retourne un objet <xref:Microsoft.Office.Interop.InfoPath.Application> qui représente l'instance actuelle d'InfoPath. Pour plus d'informations, consultez [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md).  
  
 Quand vous appelez le modèle objet d’InfoPath à partir d’un complément VSTO, vous utilisez des types fournis dans l’assembly PIA (Primary Interop Assembly) pour InfoPath. L’assembly PIA fait office de pont entre le code managé du complément VSTO et le modèle objet COM dans InfoPath. Tous les types dans l'assembly PIA d'InfoPath sont définis dans l'espace de noms <xref:Microsoft.Office.Interop.InfoPath> . Pour plus d'informations sur l'assembly PIA d'InfoPath, consultez [Présentation de l'assembly PIA de Microsoft Office InfoPath](http://msdn.microsoft.com/en-us/1b3ae03c-6951-49e4-a489-4712d3f7ba72). Pour plus d’informations sur les assemblys PIA en général, consultez [présentation du développement de Solutions Office &#40;VSTO&#41; ](../vsto/office-solutions-development-overview-vsto.md) et [assemblys PIA Office](../vsto/office-primary-interop-assemblies.md).  
  
## <a name="customizing-the-user-interface-of-infopath-by-using-an-add-in"></a>Personnalisation de l'interface utilisateur d'InfoPath à l'aide d'un complément  
 Quand vous créez un complément VSTO pour InfoPath, plusieurs options de personnalisation de l’interface utilisateur différentes s’offrent à vous. Le tableau suivant répertorie certaines de ces options.  
  
|Tâche|Pour plus d'informations|  
|----------|--------------------------|  
|Créer un volet des tâches personnalisé.|[Volets de tâches personnalisés](../vsto/custom-task-panes.md)|  
|Ajouter des onglets personnalisés au ruban dans InfoPath|[Personnalisation d’un ruban pour InfoPath](../vsto/customizing-a-ribbon-for-infopath.md)|  
  
 Pour plus d’informations sur la personnalisation de l’interface utilisateur d’InfoPath et d’autres applications Microsoft Office, consultez [personnalisation de l’interface utilisateur Office](../vsto/office-ui-customization.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Présentation de l'assembly PIA de Microsoft Office InfoPath](http://msdn.microsoft.com/en-us/1b3ae03c-6951-49e4-a489-4712d3f7ba72)   
 [Getting Started Programming VSTO Add-ins](../vsto/getting-started-programming-vsto-add-ins.md)   
 [Présentation du développement de Solutions Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Architecture des Compléments VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)   
 [Écriture de Code dans les Solutions Office](../vsto/writing-code-in-office-solutions.md)   
 [Assemblys PIA Office](../vsto/office-primary-interop-assemblies.md)   
 [Personnalisation de l’interface utilisateur Office](../vsto/office-ui-customization.md)   
 [InfoPath 2010 dans le développement Office](http://go.microsoft.com/fwlink/?LinkId=199012)  
  
  