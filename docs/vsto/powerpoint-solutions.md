---
title: "Solutions PowerPoint"
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
  - "solutions Office (développement Office dans Visual Studio), PowerPoint"
  - "modèles (développement Office dans Visual Studio), PowerPoint"
  - "solutions (développement Office dans Visual Studio), PowerPoint"
  - "projets (développement Office dans Visual Studio), PowerPoint"
  - "PowerPoint (développement Office dans Visual Studio)"
  - "projets Office (développement Office dans Visual Studio), PowerPoint"
ms.assetid: 02ebad64-9fd3-495f-ab27-4f6206b3d6d2
caps.latest.revision: 46
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 41
---
# Solutions PowerPoint
  Visual Studio fournit des modèles de projet que vous pouvez utiliser pour créer des compléments VSTO pour Microsoft Office PowerPoint. Vous pouvez utiliser les compléments VSTO pour automatiser PowerPoint, étendre les fonctionnalités PowerPoint ou personnaliser l’interface utilisateur PowerPoint.  
  
 Pour plus d’informations sur les compléments VSTO, consultez [Prise en main de la programmation de compléments VSTO](../vsto/getting-started-programming-vsto-add-ins.md) et [Architecture des compléments VSTO](../vsto/architecture-of-vsto-add-ins.md). Si vous débutez en programmation avec Microsoft Office, consultez [Mise en route &#40;Développement Office dans Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md).  
  
 [!INCLUDE[appliesto_pptallapp](../vsto/includes/appliesto-pptallapp-md.md)]  
  
 ![lien vers la vidéo](../vsto/media/playvideo.png "lien vers la vidéo") Pour visionner une vidéo de démonstration associée, consultez [Comment : créer un complément pour Microsoft PowerPoint](http://go.microsoft.com/fwlink/?LinkId=132767).  
  
## Automatisation de PowerPoint à l'aide du modèle objet PowerPoint  
 Le modèle objet PowerPoint expose de nombreux types que vous pouvez utiliser pour automatiser PowerPoint. Ces types permettent d'écrire le code pour accomplir les tâches courantes :  
  
-   créer et mettre en forme les présentations par programmation ;  
  
-   ajouter ou supprimer des diapositives des présentations ;  
  
-   ajouter ou modifier des formes sur une diapositive.  
  
 Pour accéder au modèle objet PowerPoint à partir d’un complément VSTO, utilisez le champ `Application` de la classe `ThisAddIn` de votre projet. Le champ `Application` retourne un objet <xref:Microsoft.Office.Interop.PowerPoint.Application> qui représente l'instance actuelle de PowerPoint. Pour plus d'informations, consultez [Programmation de compléments VSTO](../vsto/programming-vsto-add-ins.md).  
  
 Quand vous appelez le modèle objet PowerPoint, vous utilisez des types fournis dans l'assembly PIA \(Primary Interop Assembly\) pour PowerPoint. L’assembly PIA fait office de pont entre le code managé du complément VSTO et le modèle objet COM dans PowerPoint. Tous les types de l'assembly PIA PowerPoint sont définis dans l'espace de noms <xref:Microsoft.Office.Interop.PowerPoint>. Pour plus d’informations sur les assemblys PIA, consultez [Vue d'ensemble du développement des solutions Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md) et [Assemblys PIA &#40;Primary Interop Assembly&#41; Office](../vsto/office-primary-interop-assemblies.md).  
  
##  <a name="WordOMDocumentation"></a> Utilisation de la documentation du modèle objet PowerPoint  
 Pour obtenir des informations complètes sur le modèle objet PowerPoint, vous pouvez vous reporter à la documentation de référence de l'assembly PIA \(Primary Interop Assembly\) PowerPoint et à la documentation de référence du modèle objet VBA.  
  
### Documentation de référence de l'assembly PIA \(Primary Interop Assembly\)  
 La documentation de référence de l'assembly PIA PowerPoint décrit les types de l'assembly PIA pour PowerPoint. Cette documentation est disponible à l’emplacement suivant : [Documentation de référence de l’assembly PIA \(Primary Interop Assembly\) PowerPoint 2010](http://go.microsoft.com/fwlink/?LinkId=189588).  
  
 Pour plus d’informations sur la conception de l’assembly PIA PowerPoint, telles que les différences entre les classes et les interfaces dans l’assembly PIA, et l’implémentation des événements dans l’assembly PIA, consultez [Vue d’ensemble des classes et des interfaces dans les assemblys PIA \(Primary Interop Assembly\) Office](http://go.microsoft.com/fwlink/?LinkId=199885).  
  
### Documentation de référence du modèle objet VBA  
 La documentation de référence du modèle objet VBA présente le modèle objet PowerPoint tel qu'il est exposé au code VBA \(Visual Basic pour Applications\). Pour plus d’informations, consultez [Référence du modèle objet PowerPoint 2010](http://go.microsoft.com/fwlink/?LinkId=199770).  
  
 Tous les objets et membres mentionnés dans la documentation de référence du modèle objet VBA correspondent aux types et aux membres de l'assembly PIA PowerPoint. Par exemple, l'objet Presentation de la documentation de référence du modèle objet VBA correspond au type <xref:Microsoft.Office.Interop.PowerPoint.Presentation> de l'assembly PIA PowerPoint. Même si la documentation de référence du modèle objet VBA fournit des exemples de code pour la plupart des propriétés, méthodes et événements, vous devez traduire le code VBA fourni dans cette documentation de référence en Visual Basic ou Visual C\# pour pouvoir les utiliser dans un projet de complément VSTO PowerPoint créé à l’aide de Visual Studio.  
  
## Personnalisation de l'interface utilisateur de PowerPoint  
 Vous pouvez modifier l'interface utilisateur de PowerPoint comme suit.  
  
|Tâche|Pour plus d'informations|  
|-----------|------------------------------|  
|Créer un volet des tâches personnalisé.|[Volets de tâches personnalisés](../vsto/custom-task-panes.md)|  
|Ajouter des onglets personnalisés au ruban.|[Vue d'ensemble du ruban](../vsto/ribbon-overview.md)|  
|Ajouter des groupes personnalisés à un onglet intégré du ruban.|[Comment : personnaliser un onglet intégré](../vsto/how-to-customize-a-built-in-tab.md)|  
  
 Pour plus d’informations sur la personnalisation de l’interface utilisateur de PowerPoint et des autres applications Microsoft Office, consultez [Personnalisation de l'interface utilisateur Office](../vsto/office-ui-customization.md).  
  
## Voir aussi  
 [Procédure pas à pas : création de votre premier complément VSTO pour PowerPoint](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)   
 [Prise en main de la programmation de compléments VSTO](../vsto/getting-started-programming-vsto-add-ins.md)   
 [Vue d'ensemble du développement des solutions Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Architecture des compléments VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Programmation de compléments VSTO](../vsto/programming-vsto-add-ins.md)   
 [Écriture de code dans les solutions Office](../vsto/writing-code-in-office-solutions.md)   
 [Assemblys PIA &#40;Primary Interop Assembly&#41; Office](../vsto/office-primary-interop-assemblies.md)   
 [Personnalisation de l'interface utilisateur Office](../vsto/office-ui-customization.md)   
 [PowerPoint 2010 dans le développement Office](http://go.microsoft.com/fwlink/?LinkId=199015)  
  
  