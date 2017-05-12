---
title: "Solutions Project"
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
  - "projets (développement Office dans Visual Studio), Project"
  - "solutions Office (développement Office dans Visual Studio), Project"
  - "Projet (développement Office dans Visual Studio)"
  - "modèles (développement Office dans Visual Studio), Project"
  - "projets Office (développement Office dans Visual Studio), Project"
  - "solutions (développement Office dans Visual Studio), Project"
ms.assetid: 4ce92269-eb6d-44aa-bee3-6d38ec9995f9
caps.latest.revision: 34
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 30
---
# Solutions Project
  [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] fournit des modèles de projet que vous pouvez utiliser pour créer des compléments VSTO pour Microsoft Office Project. Vous pouvez utiliser les compléments VSTO pour automatiser Project, étendre les fonctionnalités de Project ou personnaliser l’interface utilisateur de Project.  
  
 Pour plus d’informations sur les compléments VSTO, consultez [Prise en main de la programmation de compléments VSTO](../vsto/getting-started-programming-vsto-add-ins.md) et [Architecture des compléments VSTO](../vsto/architecture-of-vsto-add-ins.md). Si vous débutez en programmation avec Microsoft Office, consultez [Mise en route &#40;Développement Office dans Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md).  
  
 [!INCLUDE[appliesto_projallapp](../vsto/includes/appliesto-projallapp-md.md)]  
  
## Automatisation de Project à l’aide du modèle objet Project  
 Le modèle objet Project expose de nombreux types que vous pouvez utiliser pour automatiser Project. Ces types vous permettent d’écrire du code pour accomplir des tâches courantes telles que la création et la modification de tâches dans un projet par programmation.  
  
 Pour accéder au modèle objet Project à partir d’un complément VSTO, utilisez le champ `Application` de la classe `ThisAddIn` dans votre projet. Le champ `Application` retourne un objet Microsoft.Office.Interop.MsProject.Application  qui représente l’instance actuelle de Project. Pour plus d'informations, consultez [Programmation de compléments VSTO](../vsto/programming-vsto-add-ins.md).  
  
 Quand vous appelez le modèle objet Project, vous utilisez des types fournis dans l’assembly PIA \(Primary Interop Assembly\) pour Project. L’assembly PIA fait office de pont entre le code managé du complément VSTO et le modèle objet COM dans Project. Tous les types de l’assembly PIA Project sont définis dans l’espace de noms Microsoft.Office.Interop.MSProject. Pour plus d’informations sur les assemblys PIA, consultez [Vue d'ensemble du développement des solutions Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md) et [Assemblys PIA &#40;Primary Interop Assembly&#41; Office](../vsto/office-primary-interop-assemblies.md).  
  
## Utilisation de la documentation du modèle objet Project  
 Pour obtenir des informations complètes sur le modèle objet Project, vous pouvez vous reporter à la référence du modèle objet Project VBA. La documentation de référence du modèle objet VBA présente le modèle objet Project tel qu’il est exposé au code VBA \(Visual Basic pour Applications\). Pour plus d’informations, consultez [Référence du modèle objet Project 2010](http://go.microsoft.com/fwlink/?LinkId=199771).  
  
 Tous les objets et membres mentionnés dans la documentation de référence du modèle objet VBA correspondent aux types et aux membres de l’assembly PIA Project. Par exemple, l’objet Calendar de la documentation de référence du modèle objet VBA correspond au type Microsoft.Office.Interop.MSProject.Calendar de l’assembly PIA Project. Même si la documentation de référence du modèle objet VBA fournit des exemples de code pour la plupart des propriétés, méthodes et événements, vous devez traduire le code VBA fourni dans la documentation de référence en Visual Basic ou Visual C\# pour pouvoir les utiliser dans un projet de complément Project VSTO créé à l’aide de Visual Studio.  
  
> [!NOTE]  
>  À l’heure actuelle, il n’existe aucune documentation de référence pour l’assembly PIA Project.  
  
### Types d’infrastructure dans l’assembly PIA Project  
 Lors de l’écriture de code qui utilise l’assembly PIA Project, vous remarquerez peut\-être de nombreux types qui ne sont pas décrits dans la référence VBA. Ces types supplémentaires aident à convertir des objets dans le modèle objet COM de Project en code managé. Ils ne sont pas censés être utilisés directement dans votre code.  
  
 Pour plus d’informations, consultez [Vue d’ensemble des classes et des interfaces dans les assemblys PIA \(Primary Interop Assembly\) d’Office](http://go.microsoft.com/fwlink/?LinkId=189592).  
  
## Personnalisation de l’interface utilisateur de Project  
 Vous pouvez personnaliser l’interface utilisateur de Project de différentes façons.  
  
|Tâche|Pour plus d'informations|  
|-----------|------------------------------|  
|Ajouter des onglets personnalisés au ruban dans Project|[Vue d'ensemble du ruban](../vsto/ribbon-overview.md)|  
  
 Pour plus d’informations sur la personnalisation de l’interface utilisateur de Project et des autres applications Microsoft Office, consultez [Personnalisation de l'interface utilisateur Office](../vsto/office-ui-customization.md).  
  
## Voir aussi  
 [Procédure pas à pas : création de votre premier complément VSTO pour Project](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)   
 [Prise en main de la programmation de compléments VSTO](../vsto/getting-started-programming-vsto-add-ins.md)   
 [Vue d'ensemble du développement des solutions Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Architecture des compléments VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Programmation de compléments VSTO](../vsto/programming-vsto-add-ins.md)   
 [Écriture de code dans les solutions Office](../vsto/writing-code-in-office-solutions.md)   
 [Assemblys PIA &#40;Primary Interop Assembly&#41; Office](../vsto/office-primary-interop-assemblies.md)   
 [Personnalisation de l'interface utilisateur Office](../vsto/office-ui-customization.md)   
 [Project 2010 et Project Server 2010 dans le développement Office](http://go.microsoft.com/fwlink/?LinkId=199016)  
  
  