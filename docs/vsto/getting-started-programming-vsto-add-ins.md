---
title: "Prise en main de la programmation de compl&#233;ments VSTO | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VST.ProjectItem.Outlook"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "compléments (développement Office dans Visual Studio), prise en main"
  - "compléments de niveau application (développement Office dans Visual Studio), prise en main"
ms.assetid: 9ac1e6ea-9511-4633-80f9-dc7641f22b63
caps.latest.revision: 60
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 59
---
# Prise en main de la programmation de compl&#233;ments VSTO
  Vous pouvez utiliser des compléments VSTO pour automatiser des applications Microsoft Office, étendre les fonctionnalités de l'application et personnaliser son interface utilisateur.  Pour plus d'informations sur les différences entre les compléments VSTO et d'autres types de solutions Office que vous pouvez créer à l'aide de Visual Studio, consultez [Vue d'ensemble du développement des solutions Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
## Création de projets de complément VSTO  
 Créez des projets de complément VSTO en utilisant un des modèles de projet de complément VSTO disponibles dans la boîte de dialogue **Nouveau projet**.  Ces modèles comprennent les références d'assembly et les fichiers projet requis.  Visual Studio fournit des modèles de projet de complément VSTO pour la plupart des applications dans Office.  
  
 Pour plus d'informations sur la création d'un projet de complément VSTO, consultez [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  Pour plus d'informations sur les modèles de projet, consultez [Vue d'ensemble des modèles de projet Office](../vsto/office-project-templates-overview.md).  
  
## Développement de projets de complément VSTO  
 Quand vous créez un projet de complément VSTO, Visual Studio crée automatiquement un fichier de code ThisAddIn.vb \(dans [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]\) ou ThisAddIn.cs \(en C\#\).  Ce fichier contient la classe `ThisAddIn`, qui sert de base à votre complément VSTO.  Vous pouvez utiliser des membres de cette classe pour exécuter le code quand le complément VSTO est chargé ou déchargé, pour accéder au modèle objet de l'application hôte, et pour étendre les fonctionnalités de l'application.  Pour plus d'informations, consultez [Programmation de compléments VSTO](../vsto/programming-vsto-add-ins.md).  
  
## Automatisation d'applications à l'aide des modèles objet  
 Les modèles objet des applications Microsoft Office exposent de nombreux types avec lesquels vous pouvez programmer dans un complément VSTO.  Vous pouvez utiliser ces types pour automatiser l'application.  Par exemple, vous pouvez créer et envoyer par programme un message électronique dans Outlook ou encore ouvrir un document et ajouter du contenu dans Word.  Pour plus d'informations sur l'accès au modèle objet de l'application hôte contenu dans le code, consultez [Programmation de compléments VSTO](../vsto/programming-vsto-add-ins.md).  
  
 Pour plus d'informations sur les modèles objet d'applications Microsoft Office spécifiques, consultez les rubriques suivantes :  
  
-   [Vue d'ensemble du modèle objet Excel](../vsto/excel-object-model-overview.md)  
  
-   [Vue d'ensemble du modèle objet Word](../vsto/word-object-model-overview.md)  
  
-   [Vue d'ensemble du modèle d'objet Outlook](../vsto/outlook-object-model-overview.md)  
  
-   [Solutions InfoPath](../vsto/infopath-solutions.md)  
  
-   [Solutions PowerPoint](../vsto/powerpoint-solutions.md)  
  
-   [Solutions Project](../vsto/project-solutions.md)  
  
-   [Vue d'ensemble du modèle objet Visio](../vsto/visio-object-model-overview.md)  
  
## Personnalisation de l'interface utilisateur des applications  
 Vous pouvez personnaliser l'interface utilisateur de l'application hôte à l'aide d'un complément VSTO de plusieurs manières :  
  
-   Pour Excel et Word, vous pouvez ajouter des contrôles managés aux documents.  Pour plus d'informations, consultez [Extension de documents Word et de classeurs Excel dans des compléments VSTO au moment de l'exécution](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
-   Vous pouvez personnaliser le ruban si l'application le prend en charge.  Pour plus d'informations, consultez [Vue d'ensemble du ruban](../vsto/ribbon-overview.md).  
  
-   Vous pouvez créer un volet de tâches personnalisé si l'application le prend en charge.  Pour plus d'informations, consultez [Volets de tâches personnalisés](../vsto/custom-task-panes.md).  
  
-   Pour Outlook, vous pouvez créer une zone de formulaire personnalisée.  Pour plus d'informations, consultez [Création de zones de formulaire Outlook](../vsto/creating-outlook-form-regions.md).  
  
-   Pour toutes les applications Microsoft Office, vous pouvez afficher Windows Forms dans votre complément VSTO.  
  
 Pour plus d'informations sur la personnalisation de l'interface utilisateur des applications Microsoft Office, consultez [Personnalisation de l'interface utilisateur Office](../vsto/office-ui-customization.md).  
  
## Étapes suivantes  
 Pour savoir comment créer des compléments VSTO, consultez les procédures pas à pas suivantes :  
  
-   [Procédure pas à pas : création de votre premier complément VSTO pour Excel](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md)  
  
-   [Procédure pas à pas : création de votre premier complément VSTO pour Outlook](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)  
  
-   [Procédure pas à pas : création de votre premier complément VSTO pour PowerPoint](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)  
  
-   [Procédure pas à pas : création de votre premier complément VSTO pour Project](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)  
  
-   [Procédure pas à pas : création de votre premier complément VSTO pour Word](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)  
  
 Ces procédures pas à pas vous initient aux Outils de développement Office dans Visual Studio et au modèle de programmation pour les compléments VSTO.  
  
 Pour obtenir la liste des rubriques vous présentant certaines tâches courantes dans les projets Office, consultez [Tâches courantes en matière de programmation Office](../vsto/common-tasks-in-office-programming.md).  
  
## Voir aussi  
 [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Mise en route &#40;Développement Office dans Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)   
 [Écriture de code dans les solutions Office](../vsto/writing-code-in-office-solutions.md)   
 [Architecture des compléments VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Programmation de compléments VSTO](../vsto/programming-vsto-add-ins.md)  
  
  