---
title: "Solutions InfoPath | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "solutions (développement Office dans Visual Studio), InfoPath"
  - "modèles (développement Office dans Visual Studio), InfoPath"
  - "InfoPath (développement Office dans Visual Studio)"
  - "développement Office dans Visual Studio, solutions InfoPath"
  - "projets (développement Office dans Visual Studio), InfoPath"
  - "solutions Office (développement Office dans Visual Studio), InfoPath"
  - "projets Office (développement Office dans Visual Studio), InfoPath"
ms.assetid: 20ac6bee-b17f-4217-9f78-11304a11236a
caps.latest.revision: 43
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 37
---
# Solutions InfoPath
  Visual Studio fournit des modèles de projet à l’aide desquels vous pouvez créer des compléments VSTO pour Microsoft Office InfoPath 2013 et InfoPath 2010. InfoPath n’est pas disponible dans Office 2016.  
  
> [!NOTE]  
>  Vous pouvez toutefois créer un complément VSTO pour InfoPath même si vous avez installé Office 2016. Pour cela, installez simplement InfoPath 2013 ou Office 2013 côte à côte avec Office 2016.  
  
 [!INCLUDE[appliesto_infoallapp](../vsto/includes/appliesto-infoallapp-md.md)]  
  
 Les compléments VSTO pour InfoPath sont semblables aux compléments VSTO conçus pour les autres applications Microsoft Office. Ces types de solutions se composent d'un assembly chargé par l'application. L'utilisateur final peut accéder aux fonctionnalités de cet assembly quel que soit le formulaire ou le modèle de formulaire ouvert. Pour plus d’informations sur les compléments VSTO, consultez [Prise en main de la programmation de compléments VSTO](../vsto/getting-started-programming-vsto-add-ins.md) et [Architecture des compléments VSTO](../vsto/architecture-of-vsto-add-ins.md).  
  
> [!NOTE]  
>  Visual Studio 2015 n'inclut pas les projets de modèle de formulaire InfoPath qui étaient disponibles dans les versions antérieures de Visual Studio. Vous ne pouvez pas non plus utiliser Visual Studio 2015 pour ouvrir ou modifier un projet de modèle de formulaire InfoPath qui a été créé dans une version antérieure de Visual Studio. Toutefois, cela est possible en utilisant Visual Studio Tools pour Applications. Pour plus d’informations, consultez [Utilisation des projets VSTO 2008 dans InfoPath 2010](http://go.microsoft.com/fwlink/?LinkID=218903).  
  
## Automatisation d'InfoPath à l'aide d'un complément  
 Pour accéder au modèle objet d’InfoPath à partir d’un complément VSTO Office créé à l’aide des outils de développement Office dans Visual Studio, utilisez le champ `Application` de la classe `ThisAddIn` dans votre projet. Le champ `Application` retourne un objet <xref:Microsoft.Office.Interop.InfoPath.Application> qui représente l'instance actuelle d'InfoPath. Pour plus d'informations, consultez [Programmation de compléments VSTO](../vsto/programming-vsto-add-ins.md).  
  
 Quand vous appelez le modèle objet d’InfoPath à partir d’un complément VSTO, vous utilisez des types fournis dans l’assembly PIA \(Primary Interop Assembly\) pour InfoPath. L’assembly PIA fait office de pont entre le code managé du complément VSTO et le modèle objet COM dans InfoPath. Tous les types dans l'assembly PIA d'InfoPath sont définis dans l'espace de noms <xref:Microsoft.Office.Interop.InfoPath>. Pour plus d'informations sur l'assembly PIA d'InfoPath, consultez [Présentation de l'assembly PIA de Microsoft Office InfoPath](http://msdn.microsoft.com/fr-fr/1b3ae03c-6951-49e4-a489-4712d3f7ba72). Pour plus d’informations sur les assemblys PIA en général, consultez [Vue d'ensemble du développement des solutions Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md) et [Assemblys PIA &#40;Primary Interop Assembly&#41; Office](../vsto/office-primary-interop-assemblies.md).  
  
## Personnalisation de l'interface utilisateur d'InfoPath à l'aide d'un complément  
 Quand vous créez un complément VSTO pour InfoPath, plusieurs options de personnalisation de l’interface utilisateur différentes s’offrent à vous. Le tableau suivant répertorie certaines de ces options.  
  
|Tâche|Pour plus d'informations|  
|-----------|------------------------------|  
|Créer un volet des tâches personnalisé.|[Volets de tâches personnalisés](../vsto/custom-task-panes.md)|  
|Ajouter des onglets personnalisés au ruban dans InfoPath|[Personnalisation d'un ruban pour InfoPath](../vsto/customizing-a-ribbon-for-infopath.md)|  
  
 Pour plus d’informations sur la personnalisation de l’interface utilisateur d’InfoPath et des autres applications Microsoft Office, consultez [Personnalisation de l'interface utilisateur Office](../vsto/office-ui-customization.md).  
  
## Voir aussi  
 [À propos de l’assembly PIA \(Primary Interop Assembly\) de Microsoft Office InfoPath](http://msdn.microsoft.com/fr-fr/1b3ae03c-6951-49e4-a489-4712d3f7ba72)   
 [Prise en main de la programmation de compléments VSTO](../vsto/getting-started-programming-vsto-add-ins.md)   
 [Vue d'ensemble du développement des solutions Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Architecture des compléments VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Programmation de compléments VSTO](../vsto/programming-vsto-add-ins.md)   
 [Écriture de code dans les solutions Office](../vsto/writing-code-in-office-solutions.md)   
 [Assemblys PIA &#40;Primary Interop Assembly&#41; Office](../vsto/office-primary-interop-assemblies.md)   
 [Personnalisation de l'interface utilisateur Office](../vsto/office-ui-customization.md)   
 [InfoPath 2010 dans le développement Office](http://go.microsoft.com/fwlink/?LinkId=199012)  
  
  