---
title: Solutions PowerPoint | Documents Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office solutions [Office development in Visual Studio], PowerPoint
- templates [Office development in Visual Studio], PowerPoint
- solutions [Office development in Visual Studio], PowerPoint
- projects [Office development in Visual Studio], PowerPoint
- PowerPoint [Office development in Visual Studio]
- Office projects [Office development in Visual Studio], PowerPoint
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 3808ecf78e8a7e110561c558a6278ee4873843c0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="powerpoint-solutions"></a>Solutions PowerPoint
  Visual Studio fournit des modèles de projet que vous pouvez utiliser pour créer des compléments VSTO pour Microsoft Office PowerPoint. Vous pouvez utiliser les compléments VSTO pour automatiser PowerPoint, étendre les fonctionnalités PowerPoint ou personnaliser l’interface utilisateur PowerPoint.  
  
 Pour plus d’informations sur les compléments VSTO, consultez [Getting Started Programming VSTO Add-ins](../vsto/getting-started-programming-vsto-add-ins.md) et [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md). Si vous débutez en programmation avec Microsoft Office, consultez [mise en route &#40;développement Office dans Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md).  
  
 [!INCLUDE[appliesto_pptallapp](../vsto/includes/appliesto-pptallapp-md.md)]  
  
> [!NOTE]  
>  Vous souhaitez développer des solutions qui étendent l’expérience Office sur [plusieurs plateformes](https://dev.office.com/add-in-availability)? Découvrez le nouvel [modèle des compléments Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Compléments Office ont un faible encombrement mémoire par rapport aux compléments VSTO et les solutions, et vous pouvez les créer à l’aide de presque n’importe quel web technologies, telles que HTML5, JavaScript, CSS3 et XML de programmation.  
  
 ![lien vers la vidéo](../vsto/media/playvideo.gif "lien vidéo") pour une démonstration vidéo connexe, consultez [comment faire pour créer un complément pour Microsoft PowerPoint ?](http://go.microsoft.com/fwlink/?LinkId=132767).  
  
## <a name="automating-powerpoint-by-using-the-powerpoint-object-model"></a>Automatisation de PowerPoint à l'aide du modèle objet PowerPoint  
 Le modèle objet PowerPoint expose de nombreux types que vous pouvez utiliser pour automatiser PowerPoint. Ces types permettent d'écrire le code pour accomplir les tâches courantes :  
  
-   créer et mettre en forme les présentations par programmation ;  
  
-   ajouter ou supprimer des diapositives des présentations ;  
  
-   ajouter ou modifier des formes sur une diapositive.  
  
 Pour accéder au modèle objet PowerPoint à partir d’un complément VSTO, utilisez le champ `Application` de la classe `ThisAddIn` de votre projet. Le champ `Application` retourne un objet <xref:Microsoft.Office.Interop.PowerPoint.Application> qui représente l'instance actuelle de PowerPoint. Pour plus d'informations, consultez [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md).  
  
 Quand vous appelez le modèle objet PowerPoint, vous utilisez des types fournis dans l'assembly PIA (Primary Interop Assembly) pour PowerPoint. L’assembly PIA fait office de pont entre le code managé du complément VSTO et le modèle objet COM dans PowerPoint. Tous les types de l'assembly PIA PowerPoint sont définis dans l'espace de noms <xref:Microsoft.Office.Interop.PowerPoint> . Pour plus d’informations sur les assemblys PIA, consultez [présentation du développement de Solutions Office &#40;VSTO&#41; ](../vsto/office-solutions-development-overview-vsto.md) et [assemblys PIA Office](../vsto/office-primary-interop-assemblies.md).  
  
##  <a name="WordOMDocumentation"></a> Utilisation de la documentation du modèle objet PowerPoint  
 Pour obtenir des informations complètes sur le modèle objet PowerPoint, vous pouvez vous reporter à la documentation de référence de l'assembly PIA (Primary Interop Assembly) PowerPoint et à la documentation de référence du modèle objet VBA.  
  
### <a name="primary-interop-assembly-reference"></a>Documentation de référence de l'assembly PIA (Primary Interop Assembly)  
 La documentation de référence de l'assembly PIA PowerPoint décrit les types de l'assembly PIA pour PowerPoint. Cette documentation est disponible à l’emplacement suivant : [Documentation de référence de l’assembly PIA (Primary Interop Assembly) PowerPoint 2010](http://go.microsoft.com/fwlink/?LinkId=189588).  
  
 Pour plus d’informations sur la conception de l’assembly PIA PowerPoint, telles que les différences entre les classes et les interfaces dans l’assembly PIA, et l’implémentation des événements dans l’assembly PIA, consultez [Vue d’ensemble des classes et des interfaces dans les assemblys PIA (Primary Interop Assembly) Office](http://go.microsoft.com/fwlink/?LinkId=199885).  
  
### <a name="vba-object-model-reference"></a>Documentation de référence du modèle objet VBA  
 La documentation de référence du modèle objet VBA présente le modèle objet PowerPoint tel qu'il est exposé au code VBA (Visual Basic pour Applications). Pour plus d’informations, consultez [Référence du modèle objet PowerPoint 2010](http://go.microsoft.com/fwlink/?LinkId=199770).  
  
 Tous les objets et membres mentionnés dans la documentation de référence du modèle objet VBA correspondent aux types et aux membres de l'assembly PIA PowerPoint. Par exemple, l’objet de la présentation dans la référence du modèle objet VBA correspond à la <xref:Microsoft.Office.Interop.PowerPoint.Presentation> type dans l’assembly PIA PowerPoint. Même si la documentation de référence du modèle objet VBA fournit des exemples de code pour la plupart des propriétés, méthodes et événements, vous devez traduire le code VBA fourni dans cette documentation de référence en Visual Basic ou Visual C# pour pouvoir les utiliser dans un projet de complément VSTO PowerPoint créé à l’aide de Visual Studio.  
  
## <a name="customizing-the-user-interface-of-powerpoint"></a>Personnalisation de l'interface utilisateur de PowerPoint  
 Vous pouvez modifier l'interface utilisateur de PowerPoint comme suit.  
  
|Tâche|Pour plus d'informations|  
|----------|--------------------------|  
|Créer un volet des tâches personnalisé.|[Volets de tâches personnalisés](../vsto/custom-task-panes.md)|  
|Ajouter des onglets personnalisés au ruban.|[Vue d’ensemble du ruban](../vsto/ribbon-overview.md)|  
|Ajouter des groupes personnalisés à un onglet intégré du ruban.|[Guide pratique pour personnaliser un onglet intégré](../vsto/how-to-customize-a-built-in-tab.md)|  
  
 Pour plus d’informations sur la personnalisation de l’interface utilisateur de PowerPoint et autres applications Microsoft Office, consultez [personnalisation de l’interface utilisateur Office](../vsto/office-ui-customization.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure pas à pas : Création de votre complément VSTO pour PowerPoint](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)   
 [Getting Started Programming VSTO Add-ins](../vsto/getting-started-programming-vsto-add-ins.md)   
 [Présentation du développement de Solutions Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Architecture des Compléments VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)   
 [Écriture de Code dans les Solutions Office](../vsto/writing-code-in-office-solutions.md)   
 [Assemblys PIA Office](../vsto/office-primary-interop-assemblies.md)   
 [Personnalisation de l’interface utilisateur Office](../vsto/office-ui-customization.md)   
 [PowerPoint 2010 dans le développement Office](http://go.microsoft.com/fwlink/?LinkId=199015)  
  
  