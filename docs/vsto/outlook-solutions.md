---
title: "Solutions Outlook | Microsoft Docs"
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
  - "solutions (développement Office dans Visual Studio), Outlook"
  - "projets Office (développement Office dans Visual Studio), Outlook"
  - "solutions Office (développement Office dans Visual Studio), Outlook"
  - "modèles (développement Office dans Visual Studio), Outlook"
  - "projets (développement Office dans Visual Studio), Outlook"
  - "Outlook (développement Office dans Visual Studio)"
  - "messagerie électronique (développement Office dans Visual Studio), solutions Outlook"
ms.assetid: 2ae3cd9c-bf31-4efa-8b18-b6b1c34a8d93
caps.latest.revision: 27
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 23
---
# Solutions Outlook
  Visual Studio fournit des modèles de projet que vous pouvez utiliser pour créer des compléments VSTO pour Microsoft Office Outlook. Vous pouvez utiliser les compléments VSTO pour automatiser Outlook, étendre les fonctionnalités d'Outlook ou personnaliser l'interface utilisateur d'Outlook. Pour plus d’informations sur les compléments VSTO, consultez [Architecture des compléments VSTO](../vsto/architecture-of-vsto-add-ins.md).  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## Création d'un projet de complément VSTO Outlook  
 Créez un projet Outlook à l'aide du modèle de projet **Complément Outlook** de la boîte de dialogue **Nouveau projet**. Ce modèle inclut les références d'assembly et les fichiers projet requis.  
  
 Pour plus d’informations sur la création d’un projet de complément VSTO, consultez [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md). Pour plus d’informations sur les modèles de projet, consultez [Vue d'ensemble des modèles de projet Office](../vsto/office-project-templates-overview.md).  
  
## Modèle de programmation de complément VSTO Outlook  
 Lorsque vous créez un projet de complément VSTO Outlook, Visual Studio génère une classe, appelée `ThisAddIn`, qui est le fondement de votre solution. Cette classe fournit un point de départ pour l'écriture de votre code, et expose également le modèle objet d'Outlook à votre complément.  
  
 Pour plus d’informations sur la classe `ThisAddIn` et d’autres fonctionnalités que vous pouvez utiliser dans un complément VSTO, consultez [Programmation de compléments VSTO](../vsto/programming-vsto-add-ins.md).  
  
## Automatisation d'Outlook à l'aide du modèle objet Outlook  
 Le modèle objet Outlook expose de nombreux types que vous pouvez utiliser pour automatiser Outlook. Ces types permettent d'écrire le code pour accomplir les tâches courantes :  
  
-   Créer et envoyer des messages électroniques par programmation.  
  
-   Envoyer de nouvelles demandes de réunion.  
  
-   Rechercher des éléments dans les dossiers Outlook.  
  
 Pour plus d'informations, consultez [Vue d'ensemble du modèle d'objet Outlook](../vsto/outlook-object-model-overview.md).  
  
## Personnalisation de l'interface utilisateur d'une application Outlook  
  
|Tâche|Pour plus d'informations|  
|-----------|------------------------------|  
|Ajouter des onglets personnalisés au ruban d'un inspecteur Outlook.|[Vue d'ensemble du ruban](../vsto/ribbon-overview.md)|  
|Ajouter des groupes personnalisés à un onglet intégré d'un inspecteur Outlook.|[Comment : personnaliser un onglet intégré](../vsto/how-to-customize-a-built-in-tab.md)|  
|Ajouter un volet des tâches personnalisé qui s'affiche dans un inspecteur Outlook|[Volets de tâches personnalisés](../vsto/custom-task-panes.md).|  
|Ajouter une zone de formulaire qui étend ou remplace des formulaires Outlook existants.|[Création de zones de formulaire Outlook](../vsto/creating-outlook-form-regions.md)|  
  
 Pour plus d’informations sur la personnalisation de l’interface utilisateur d’Outlook et des autres applications Microsoft Office, consultez [Personnalisation de l'interface utilisateur Office](../vsto/office-ui-customization.md).  
  
## Rubriques connexes  
  
|Titre|Description|  
|-----------|-----------------|  
|[Vue d'ensemble du modèle d'objet Outlook](../vsto/outlook-object-model-overview.md)|Fournit une vue d'ensemble des objets qui sont fournis par le modèle objet Outlook.|  
|[Création de zones de formulaire Outlook](../vsto/creating-outlook-form-regions.md)|Décrit les outils fournis par Visual Studio qui simplifient la conception, le développement et le débogage des zones de formulaire.|  
|[Procédure pas à pas : création de votre premier complément VSTO pour Outlook](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)|Explique comment créer un complément VSTO pour Microsoft Office Outlook.|  
|[Outlook 2010 dans le développement Office](http://go.microsoft.com/fwlink/?LinkId=199013)|Zone de MSDN Library où vous pouvez rechercher des articles et de la documentation de référence sur le développement de solutions Outlook \(non spécifiques au développement d'Office à l'aide de Visual Studio\).|  
  
  