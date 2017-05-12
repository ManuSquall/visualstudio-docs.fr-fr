---
title: "Solutions Visio"
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
  - "projets Office (développement Office dans Visual Studio), Visio"
  - "solutions (développement Office dans Visual Studio), Visio"
  - "Visio (développement Office dans Visual Studio)"
  - "modèles (développement Office dans Visual Studio), Visio"
  - "projets (développement Office dans Visual Studio), Visio"
  - "solutions Office (développement Office dans Visual Studio), Visio"
ms.assetid: c52948c6-6891-43ec-93ff-c54c74ec6016
caps.latest.revision: 40
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 36
---
# Solutions Visio
  Visual Studio fournit des modèles de projet que vous pouvez utiliser pour créer des compléments VSTO pour Microsoft Office Visio. Vous pouvez utiliser les compléments VSTO pour automatiser Visio, étendre les fonctionnalités Visio ou personnaliser l'interface utilisateur de Visio.  
  
 Pour plus d’informations sur les compléments VSTO, consultez [Prise en main de la programmation de compléments VSTO](../vsto/getting-started-programming-vsto-add-ins.md) et [Architecture des compléments VSTO](../vsto/architecture-of-vsto-add-ins.md). Si vous débutez en programmation avec Microsoft Office, consultez [Mise en route &#40;Développement Office dans Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md).  
  
 **S’applique à :** les informations contenues dans cette rubrique s’appliquent aux projets de compléments VSTO pour Visio 2010. Pour plus d'informations, consultez [Fonctionnalités disponibles par type d'application et de projet Office](../vsto/features-available-by-office-application-and-project-type.md).  
  
## Automatisation de Visio à l'aide du modèle objet Visio  
 Le modèle objet Visio expose de nombreuses classes que vous pouvez utiliser pour automatiser Visio afin de créer des diagrammes pour les organigrammes, diagrammes de flux, chronologies de projet, réseaux de tâches, espaces de bureau, etc. L'API vous permet d'écrire du code pour accomplir les tâches courantes :  
  
-   Élaborer et positionner des formes et du texte dans les diagrammes.  
  
-   Gérer le comportement des formes en fonction de la logique métier et des entrées d'utilisateur.  
  
-   Contrôler la visualisation des diagrammes, comme l'affichage panoramique et le zoom.  
  
-   Personnaliser l'interface utilisateur de l'application.  
  
-   Importer des données externes dans Visio, les lier aux formes et les afficher graphiquement dans une page.  
  
 Vous pouvez visualiser des procédures pas à pas et des exemples de code illustrant l’utilisation du modèle objet de Visio pour utiliser des documents et des formes dans [Utilisation de documents Visio](../vsto/working-with-visio-documents.md) et [Utilisation de formes Visio](../vsto/working-with-visio-shapes.md).  
  
 Pour accéder au modèle objet Visio à partir d'un complément VSTO, utilisez le champ `Application` de la classe `ThisAddIn` dans votre projet. Le champ `Application` retourne un objet Microsoft.Office.Interop.Visio.Application qui représente l'instance actuelle de Visio. Pour plus d'informations, consultez [Programmation de compléments VSTO](../vsto/programming-vsto-add-ins.md).  
  
 Quand vous appelez le modèle objet Visio, vous utilisez des types fournis dans l'assembly PIA \(Primary Interop Assembly\) pour Visio. L'assembly PIA fait office de pont entre le code managé du complément VSTO et le modèle objet COM dans Visio. Tous les types figurant dans l'assembly PIA de Visio sont définis dans l'espace de noms Microsoft.Office.Interop.Visio. Pour plus d’informations sur les assemblys PIA, consultez [Vue d'ensemble du développement des solutions Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md) et [Assemblys PIA &#40;Primary Interop Assembly&#41; Office](../vsto/office-primary-interop-assemblies.md).  
  
## Vue d'ensemble du modèle objet Visio  
 Vous trouverez une vue d’ensemble du modèle objet Visio dans [Vue d'ensemble du modèle objet Visio](../vsto/visio-object-model-overview.md), qui inclut des liens vers la référence du modèle objet Visio et les Kits de développement logiciel \(SDK\).  
  
## Personnalisation de l'interface utilisateur de Visio  
 L'interface utilisateur de Visio inclut les options de personnalisation suivantes.  
  
|Tâche|Pour plus d'informations|  
|-----------|------------------------------|  
|Personnaliser le ruban|[Vue d'ensemble du ruban](../vsto/ribbon-overview.md)|  
  
 Pour plus d'informations sur la personnalisation de l'interface utilisateur de Visio, consultez la documentation de référence sur VBA pour la classe [Visio.UIObject](HV10077129).  
  
## Voir aussi  
 [Prise en main de la programmation de compléments VSTO](../vsto/getting-started-programming-vsto-add-ins.md)   
 [Vue d'ensemble du développement des solutions Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Architecture des compléments VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Programmation de compléments VSTO](../vsto/programming-vsto-add-ins.md)   
 [Écriture de code dans les solutions Office](../vsto/writing-code-in-office-solutions.md)   
 [Assemblys PIA &#40;Primary Interop Assembly&#41; Office](../vsto/office-primary-interop-assemblies.md)   
 [Personnalisation de l'interface utilisateur Office](../vsto/office-ui-customization.md)   
 [Vue d'ensemble du modèle objet Visio](../vsto/visio-object-model-overview.md)   
 [Visio 2010 dans le développement Office](http://go.microsoft.com/fwlink/?LinkId=199017)  
  
  