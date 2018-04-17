---
title: Prise en main de programmation des Compléments VSTO | Documents Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VST.ProjectItem.Outlook
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio], getting started
- add-ins [Office development in Visual Studio], getting started
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: fb257a709f2f81f124e2510403a9d6853180a56b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="getting-started-programming-vsto-add-ins"></a>Getting Started Programming VSTO Add-ins
  Vous pouvez utiliser des compléments VSTO pour automatiser des applications Microsoft Office, étendre les fonctionnalités de l’application et personnaliser son interface utilisateur. Pour plus d’informations sur les différences des Compléments VSTO à d’autres types de solutions Office que vous pouvez créer à l’aide de Visual Studio, consultez [présentation du développement de Solutions Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
## <a name="creating-vsto-add-in-projects"></a>Création de projets de complément VSTO  
 Créer des projets de complément VSTO à l’aide d’un des modèles de projet à complément VSTO dans le **nouveau projet** boîte de dialogue. Ces modèles comprennent les références d'assembly et les fichiers projet requis. Visual Studio fournit des modèles de projet de complément VSTO pour la plupart des applications dans Office.  
  
 Pour plus d’informations sur la création d’un projet de complément VSTO, consultez [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md). Pour plus d’informations sur les modèles de projet, consultez [vue d’ensemble des modèles de projet Office](../vsto/office-project-templates-overview.md).  
  
## <a name="developing-vsto-add-in-projects"></a>Développement de projets de complément VSTO  
 Lorsque vous créez un projet de complément VSTO, Visual Studio crée automatiquement un ThisAddIn.vb (dans [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]) ou le fichier de code ThisAddIn.cs (en c#). Ce fichier contient le `ThisAddIn` (classe), qui sert de base pour votre composant complément VSTO. Vous pouvez utiliser des membres de cette classe pour exécuter le code quand le complément VSTO est chargé ou déchargé, pour accéder au modèle objet de l’application hôte, et pour étendre les fonctionnalités de l’application. Pour plus d'informations, consultez [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md).  
  
## <a name="automating-applications-by-using-the-object-models"></a>Automatisation d'applications à l'aide des modèles objet  
 Les modèles objet des applications Microsoft Office exposent de nombreux types avec lesquels vous pouvez programmer dans un complément VSTO. Vous pouvez utiliser ces types pour automatiser l'application. Par exemple, vous pouvez créer et envoyer par programme un message électronique dans Outlook ou encore ouvrir un document et ajouter du contenu dans Word. Pour plus d’informations sur la façon d’accéder au modèle objet de l’application hôte dans le code, consultez [de programmation des Compléments VSTO](../vsto/programming-vsto-add-ins.md).  
  
 Pour plus d'informations sur les modèles objet d'applications Microsoft Office spécifiques, consultez les rubriques suivantes :  
  
-   [Excel Object Model Overview](../vsto/excel-object-model-overview.md)  
  
-   [Word Object Model Overview](../vsto/word-object-model-overview.md)  
  
-   [Outlook Object Model Overview](../vsto/outlook-object-model-overview.md)  
  
-   [Solutions InfoPath](../vsto/infopath-solutions.md)  
  
-   [Solutions PowerPoint](../vsto/powerpoint-solutions.md)  
  
-   [Solutions Project](../vsto/project-solutions.md)  
  
-   [Vue d’ensemble du modèle objet Visio](../vsto/visio-object-model-overview.md)  
  
## <a name="customizing-the-user-interface-of-applications"></a>Personnalisation de l'interface utilisateur des applications  
 Vous pouvez personnaliser l'interface utilisateur de l'application hôte à l'aide d'un complément VSTO de plusieurs manières :  
  
-   Pour Excel et Word, vous pouvez ajouter des contrôles managés aux documents. Pour plus d'informations, consultez [Extension de documents Word et de classeurs Excel dans des compléments VSTO au moment de l'exécution](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
-   Vous pouvez personnaliser le ruban si l'application le prend en charge. Pour plus d’informations, consultez [vue d’ensemble du ruban](../vsto/ribbon-overview.md).  
  
-   Vous pouvez créer un volet de tâches personnalisé si l’application le prend en charge. Pour plus d’informations, consultez [Vue d’ensemble des volets de tâches personnalisés](../vsto/custom-task-panes.md).  
  
-   Pour Outlook, vous pouvez créer une zone de formulaire personnalisée. Pour plus d'informations, consultez [Creating Outlook Form Regions](../vsto/creating-outlook-form-regions.md).  
  
-   Pour toutes les applications Microsoft Office, vous pouvez afficher Windows Forms dans votre complément VSTO.  
  
 Pour plus d’informations sur la façon de personnaliser l’interface utilisateur des applications Microsoft Office, consultez [personnalisation de l’interface utilisateur Office](../vsto/office-ui-customization.md).  
  
## <a name="next-steps"></a>Étapes suivantes  
 Pour savoir comment créer des compléments VSTO, consultez les procédures pas à pas suivantes :  
  
-   [Procédure pas à pas : création de votre premier complément VSTO pour Excel](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md)  
  
-   [Procédure pas à pas : création de votre premier complément VSTO pour Outlook](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)  
  
-   [Procédure pas à pas : création de votre premier complément VSTO pour PowerPoint](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)  
  
-   [Procédure pas à pas : création de votre premier complément VSTO pour Project](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)  
  
-   [Procédure pas à pas : création de votre premier complément VSTO pour Word](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)  
  
 Ces procédures pas à pas vous initient aux Outils de développement Office dans Visual Studio et au modèle de programmation pour les compléments VSTO.  
  
 Pour obtenir la liste des rubriques vous présentant certaines des tâches courantes dans les projets Office, consultez [tâches courantes en matière de programmation Office](../vsto/common-tasks-in-office-programming.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Mise en route &#40;développement Office dans Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)   
 [Écriture de Code dans les Solutions Office](../vsto/writing-code-in-office-solutions.md)   
 [Architecture des Compléments VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)  
  
  