---
title: Solutions PowerPoint
ms.date: 02/02/2017
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
ms.openlocfilehash: 0f264cd7382ea16a7c4cfa5896241f4359b0cd67
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53906044"
---
# <a name="powerpoint-solutions"></a>Solutions PowerPoint
  Visual Studio fournit des modèles de projet que vous pouvez utiliser pour créer des compléments VSTO pour Microsoft Office PowerPoint. Vous pouvez utiliser les compléments VSTO pour automatiser PowerPoint, étendre les fonctionnalités PowerPoint ou personnaliser l’interface utilisateur PowerPoint.  
  
 Pour plus d’informations sur les Compléments VSTO, consultez [commencer à programmer des Compléments VSTO](../vsto/getting-started-programming-vsto-add-ins.md) et [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md). Si vous êtes novice en programmation avec Microsoft Office, consultez [prise en main &#40;développement Office dans Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md).  
  
 [!INCLUDE[appliesto_pptallapp](../vsto/includes/appliesto-pptallapp-md.md)]  
  
> [!NOTE]  
>  Vous souhaitez développer des solutions qui étendent l’expérience Office sur [plusieurs plateformes](https://dev.office.com/add-in-availability)? Découvrez le nouvel [modèle de compléments Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Compléments Office peu encombrantes par rapport aux compléments VSTO et de solutions, et vous pouvez les créer à l’aide de presque toutes les technologies, telles que HTML5, JavaScript, CSS3 et XML de programmation web.  
  
 ![lien vers la vidéo](../vsto/media/playvideo.gif "lien vers la vidéo") pour une démonstration vidéo connexe, consultez [How do I: Créer un complément pour Microsoft PowerPoint ? ](http://go.microsoft.com/fwlink/?LinkId=132767).  
  
## <a name="automate-powerpoint-by-using-the-powerpoint-object-model"></a>Automatiser PowerPoint à l’aide du modèle objet PowerPoint  
 Le modèle objet PowerPoint expose de nombreux types que vous pouvez utiliser pour automatiser PowerPoint. Ces types permettent d'écrire le code pour accomplir les tâches courantes :  
  
- créer et mettre en forme les présentations par programmation ;  
  
- ajouter ou supprimer des diapositives des présentations ;  
  
- ajouter ou modifier des formes sur une diapositive.  
  
  Pour accéder au modèle objet PowerPoint à partir d’un complément, VSTO, utilisez le `Application` champ la `ThisAddIn` classe dans votre projet. Le champ `Application` retourne un objet <xref:Microsoft.Office.Interop.PowerPoint.Application> qui représente l'instance actuelle de PowerPoint. Pour plus d’informations, consultez [programme VSTO Add-Ins](../vsto/programming-vsto-add-ins.md).  
  
  Quand vous appelez le modèle objet PowerPoint, vous utilisez des types fournis dans l'assembly PIA (Primary Interop Assembly) pour PowerPoint. L’assembly PIA fait office de pont entre le code managé du complément VSTO et le modèle objet COM dans PowerPoint. Tous les types de l'assembly PIA PowerPoint sont définis dans l'espace de noms <xref:Microsoft.Office.Interop.PowerPoint> . Pour plus d’informations sur les assemblys PIA, consultez [présentation du développement de solutions Office &#40;VSTO&#41; ](../vsto/office-solutions-development-overview-vsto.md) et [assemblys PIA Office](../vsto/office-primary-interop-assemblies.md).  
  
##  <a name="WordOMDocumentation"></a> Utilisez la documentation du modèle objet PowerPoint  
 Pour obtenir des informations complètes sur le modèle objet PowerPoint, vous pouvez vous reporter à la documentation de référence de l'assembly PIA (Primary Interop Assembly) PowerPoint et à la documentation de référence du modèle objet VBA.  
  
### <a name="primary-interop-assembly-reference"></a>Référence d’assembly PIA  
 La documentation de référence de l'assembly PIA PowerPoint décrit les types de l'assembly PIA pour PowerPoint. Cette documentation est disponible à partir de l’emplacement suivant : [Référence d’assembly PIA PowerPoint 2010](http://go.microsoft.com/fwlink/?LinkId=189588).  
  
 Pour plus d’informations sur la conception de l’assembly PIA PowerPoint, telles que les différences entre les classes et interfaces dans l’assembly PIA, et comment les événements dans l’assembly PIA, consultez [vue d’ensemble des classes et interfaces dans les assemblys PIA Office ](http://go.microsoft.com/fwlink/?LinkId=199885).  
  
### <a name="vba-object-model-reference"></a>Référence du modèle objet VBA  
 La documentation de référence du modèle objet VBA présente le modèle objet PowerPoint tel qu'il est exposé au code VBA (Visual Basic pour Applications). Pour plus d’informations, consultez [référence du modèle objet PowerPoint 2010](http://go.microsoft.com/fwlink/?LinkId=199770)  
  
 Tous les objets et membres mentionnés dans la documentation de référence du modèle objet VBA correspondent aux types et aux membres de l'assembly PIA PowerPoint. Par exemple, l’objet de présentation de la référence du modèle objet VBA correspond à la <xref:Microsoft.Office.Interop.PowerPoint.Presentation> type dans l’assembly PIA PowerPoint. Même si la documentation de référence du modèle objet VBA fournit des exemples de code pour la plupart des propriétés, méthodes et événements, vous devez traduire le code VBA fourni dans cette documentation de référence en Visual Basic ou Visual C# pour pouvoir les utiliser dans un projet de complément VSTO PowerPoint créé à l’aide de Visual Studio.  
  
## <a name="customize-the-user-interface-of-powerpoint"></a>Personnaliser l’interface utilisateur de PowerPoint  
 Vous pouvez modifier l'interface utilisateur de PowerPoint comme suit.  
  
|Tâche|Pour plus d'informations|  
|----------|--------------------------|  
|Créer un volet des tâches personnalisé.|[Volets Office personnalisés](../vsto/custom-task-panes.md)|  
|Ajouter des onglets personnalisés au ruban.|[Vue d’ensemble du ruban](../vsto/ribbon-overview.md)|  
|Ajouter des groupes personnalisés à un onglet intégré du ruban.|[Guide pratique pour Personnaliser un onglet intégré](../vsto/how-to-customize-a-built-in-tab.md)|  
  
 Pour plus d’informations sur la personnalisation de l’interface utilisateur de PowerPoint et d’autres applications Microsoft Office, consultez [personnalisation de l’interface utilisateur Office](../vsto/office-ui-customization.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure pas à pas : Créer votre premier complément pour PowerPoint](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)   
 [Commencer à programmer des Compléments VSTO](../vsto/getting-started-programming-vsto-add-ins.md)   
 [Vue d’ensemble du développement de solutions Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md)   
 [Guide pratique pour Créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Programmer des Compléments VSTO](../vsto/programming-vsto-add-ins.md)   
 [Écrire du code dans les solutions Office](../vsto/writing-code-in-office-solutions.md)   
 [Assemblys PIA Office](../vsto/office-primary-interop-assemblies.md)   
 [Personnalisation de l’interface utilisateur Office](../vsto/office-ui-customization.md)   
 [PowerPoint 2010 dans le développement Office](http://go.microsoft.com/fwlink/?LinkId=199015)  
