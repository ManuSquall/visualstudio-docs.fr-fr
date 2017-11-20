---
title: Solutions de projet | Documents Microsoft
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
- projects [Office development in Visual Studio], Project
- Office solutions [Office development in Visual Studio], Project
- Project [Office development in Visual Studio]
- templates [Office development in Visual Studio], Project
- Office projects [Office development in Visual Studio], Project
- solutions [Office development in Visual Studio], Project
ms.assetid: 4ce92269-eb6d-44aa-bee3-6d38ec9995f9
caps.latest.revision: "34"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 584f98e9fbe6a8883039cad03e6b0782d225b8bb
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="project-solutions"></a>Solutions Project
  [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] fournit des modèles de projet que vous pouvez utiliser pour créer des compléments VSTO pour Microsoft Office Project. Vous pouvez utiliser les compléments VSTO pour automatiser Project, étendre les fonctionnalités de Project ou personnaliser l’interface utilisateur de Project.  
  
 Pour plus d’informations sur les compléments VSTO, consultez [Getting Started Programming VSTO Add-ins](../vsto/getting-started-programming-vsto-add-ins.md) et [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md). Si vous débutez en programmation avec Microsoft Office, consultez [mise en route &#40; développement Office dans Visual Studio &#41;](../vsto/getting-started-office-development-in-visual-studio.md).  
  
 [!INCLUDE[appliesto_projallapp](../vsto/includes/appliesto-projallapp-md.md)]  
  
> [!NOTE]  
>  Vous souhaitez développer des solutions qui étendent l’expérience Office sur [plusieurs plateformes](https://dev.office.com/add-in-availability)? Découvrez le nouvel [modèle des compléments Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Compléments Office ont un faible encombrement mémoire par rapport aux compléments VSTO et les solutions, et vous pouvez les créer à l’aide de presque n’importe quel web technologies, telles que HTML5, JavaScript, CSS3 et XML de programmation.  
  
## <a name="automating-project-by-using-the-project-object-model"></a>Automatisation de Project à l’aide du modèle objet Project  
 Le modèle objet Project expose de nombreux types que vous pouvez utiliser pour automatiser Project. Ces types vous permettent d’écrire du code pour accomplir des tâches courantes telles que la création et la modification de tâches dans un projet par programmation.  
  
 Pour accéder au modèle objet Project à partir d’un complément VSTO, utilisez le champ `Application` de la classe `ThisAddIn` dans votre projet. Le `Application` champ retourne un objet Microsoft.Office.Interop.MSProject.application qui représente l’instance actuelle du projet. Pour plus d'informations, consultez [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md).  
  
 Quand vous appelez le modèle objet Project, vous utilisez des types fournis dans l’assembly PIA (Primary Interop Assembly) pour Project. L’assembly PIA fait office de pont entre le code managé du complément VSTO et le modèle objet COM dans Project. Tous les types dans l’assembly PIA Project sont définis dans l’espace de noms Microsoft.Office.Interop.MSProject. Pour plus d’informations sur les assemblys PIA, consultez [présentation du développement de Solutions Office &#40; VSTO &#41; ](../vsto/office-solutions-development-overview-vsto.md) et [assemblys PIA Office](../vsto/office-primary-interop-assemblies.md).  
  
## <a name="using-the-project-object-model-documentation"></a>Utilisation de la documentation du modèle objet Project  
 Pour obtenir des informations complètes sur le modèle objet Project, vous pouvez vous reporter à la référence du modèle objet Project VBA. La documentation de référence du modèle objet VBA présente le modèle objet Project tel qu’il est exposé au code VBA (Visual Basic pour Applications). Pour plus d’informations, consultez [Référence du modèle objet Project 2010](http://go.microsoft.com/fwlink/?LinkId=199771).  
  
 Tous les objets et membres mentionnés dans la documentation de référence du modèle objet VBA correspondent aux types et aux membres de l’assembly PIA Project. Par exemple, l’objet de calendrier dans la référence du modèle objet VBA correspond au type Microsoft.Office.Interop dans l’assembly PIA Project. Même si la documentation de référence du modèle objet VBA fournit des exemples de code pour la plupart des propriétés, méthodes et événements, vous devez traduire le code VBA fourni dans la documentation de référence en Visual Basic ou Visual C# pour pouvoir les utiliser dans un projet de complément Project VSTO créé à l’aide de Visual Studio.  
  
> [!NOTE]  
>  À l’heure actuelle, il n’existe aucune documentation de référence pour l’assembly PIA Project.  
  
### <a name="infrastructure-types-in-the-project-primary-interop-assembly"></a>Types d’infrastructure dans l’assembly PIA Project  
 Lors de l’écriture de code qui utilise l’assembly PIA Project, vous remarquerez peut-être de nombreux types qui ne sont pas décrits dans la référence VBA. Ces types supplémentaires aident à convertir des objets dans le modèle objet COM de Project en code managé. Ils ne sont pas censés être utilisés directement dans votre code.  
  
 Pour plus d’informations, consultez[Vue d’ensemble des classes et des interfaces dans les assemblys PIA (Primary Interop Assembly) d’Office](http://go.microsoft.com/fwlink/?LinkId=189592).  
  
## <a name="customizing-the-user-interface-of-project"></a>Personnalisation de l’interface utilisateur de Project  
 Vous pouvez personnaliser l’interface utilisateur de Project de différentes façons.  
  
|Tâche|Pour plus d'informations|  
|----------|--------------------------|  
|Ajouter des onglets personnalisés au ruban dans Project|[Vue d’ensemble du ruban](../vsto/ribbon-overview.md)|  
  
 Pour plus d’informations sur la personnalisation de l’interface utilisateur de Project et d’autres applications Microsoft Office, consultez [personnalisation de l’interface utilisateur Office](../vsto/office-ui-customization.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure pas à pas : Création de votre complément VSTO pour Project](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)   
 [Getting Started Programming VSTO Add-ins](../vsto/getting-started-programming-vsto-add-ins.md)   
 [Présentation du développement de Solutions Office &#40; VSTO &#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Architecture des Compléments VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)   
 [Écriture de Code dans les Solutions Office](../vsto/writing-code-in-office-solutions.md)   
 [Assemblys PIA Office](../vsto/office-primary-interop-assemblies.md)   
 [Personnalisation de l’interface utilisateur Office](../vsto/office-ui-customization.md)   
 [Project 2010 et Project Server 2010 dans le développement Office](http://go.microsoft.com/fwlink/?LinkId=199016)  
  
  