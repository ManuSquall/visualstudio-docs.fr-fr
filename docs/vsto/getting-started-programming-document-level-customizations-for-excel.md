---
title: "Mise en route de la programmation des personnalisations au niveau du document pour Excel"
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
  - "projets Excel (développement Office dans Visual Studio), mise en route"
  - "solutions Excel dans Visual Studio"
ms.assetid: 8b73cf08-a173-4b49-b20f-2d2456dbe925
caps.latest.revision: 41
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 40
---
# Mise en route de la programmation des personnalisations au niveau du document pour Excel
  Si vous êtes novice dans la création de personnalisations au niveau de le document pour Microsoft Office Excel à l'aide de Visual Studio, voici ce que vous devez connaître.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
## Comprendre le fonctionnement des personnalisations au niveau du document pour Excel  
 Une personnalisation au niveau du document pour Excel est basée sur un classeur unique.  Pour commencer à utiliser la personnalisation, l'utilisateur final ouvre le classeur ou le crée à partir d'un modèle Excel.  Certains événements dans le classeur, par exemple une saisie dans des cellules ou un clic sur des boutons et des éléments de menu, peuvent appeler des méthodes de gestion d'événements dans l'assembly.  Lorsque le classeur est fermé, les fonctionnalités fournies par la personnalisation ne sont plus disponibles dans Excel, uniquement dans le document qui les a contenues.  
  
 Pour plus d’informations, consultez [Architecture des personnalisations au niveau du document](../vsto/architecture-of-document-level-customizations.md).  
  
## Création de projets au niveau du document pour Excel  
 Pour créer une personnalisation au niveau du document pour Excel, utilisez le modèle de projet Classeur Excel ou Modèle Excel dans la boîte de dialogue **Nouveau projet**.  Ces modèles comprennent des références d'assembly et des fichiers projet requis.  
  
 Pour plus d'informations sur la création d'un projet au niveau du document pour Excel, consultez [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  Pour plus d'informations sur les modèles de projet, consultez [Vue d'ensemble des modèles de projet Office](../vsto/office-project-templates-overview.md).  
  
## Programmation de classeurs Excel à l'aide d'éléments hôtes et de contrôles hôtes  
 *Les éléments* hôtes et *contrôles* hôtes sont des classes qui fournissent le modèle de programmation pour les personnalisations au niveau de le document créées à l'aide de Visual Studio.  
  
 Les éléments hôtes fournissent un point d'entrée pour votre code, et ils peuvent également jouer le rôle de conteneurs pour les contrôles hôtes et Windows Forms.  Dans les projets au niveau du document pour Excel, ces éléments hôtes sont représentés par les classes `ThisWorkbook`, `Sheet1`, `Sheet2` et `Sheet3`.  
  
 Les contrôles hôtes sont basés sur des objets Excel natifs, tels que des objets de liste et des plages.  Ils fournissent des fonctionnalités semblables aux objets Excel natifs, mais possèdent également de nouveaux événements, un support concepteur et des fonctions de liaison de données.  Ils apparaissent comme des objets de première classe dans votre code de projet et dans IntelliSense, ce qui facilite les références directes à des objets spécifiques dans votre code, sans devoir parcourir le modèle d'objet Excel.  
  
 Pour plus d’informations, voir les rubriques suivantes :  
  
-   [Programmation de personnalisations au niveau du document](../vsto/programming-document-level-customizations.md)  
  
-   [Automatisation d'Excel à l'aide d'objets étendus](../vsto/automating-excel-by-using-extended-objects.md)  
  
-   [Vue d'ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)  
  
## Personnalisation de l'interface utilisateur d'Excel  
 La plupart des solutions Microsoft Office modifient l'interface utilisateur \(IU\) de l'application Office pour permettre aux utilisateurs d'interagir avec elles.  Vous pouvez modifier de nombreuses manières l'interface utilisateur d'Excel en utilisant une personnalisation au niveau du document.  Par exemple, vous pouvez ajouter des contrôles au ruban, ou vous pouvez afficher un volet Actions.  Pour plus d’informations, consultez [Personnalisation de l'interface utilisateur Office](../vsto/office-ui-customization.md).  
  
 Vous pouvez également ouvrir le classeur associé à votre projet directement dans Visual Studio.  Lorsque le classeur est ouvert dans Visual Studio, vous pouvez le modifier à l'aide de l'interface utilisateur d'Excel.  Vous pouvez également utiliser le classeur comme une aire de conception, ce qui vous permet de faire glisser des contrôles sur des feuilles de calcul.  Pour plus d’informations, consultez [Projets Office dans l'environnement Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md).  
  
## Utilisation de la liaison de données  
 Les contrôles hôtes figurent également dans la liste des contrôles que vous pouvez faire glisser à partir de la fenêtre **Sources de données**.  Cette façon d'ajouter des contrôles hôtes lie automatiquement ces derniers à la source de données configurée à l'aide de la fenêtre.  Sans écrire de code, vous pouvez afficher des données provenant de bases de données, des services Web, et d'objets métiers.  Pour plus d’informations, consultez [Liaison de données aux contrôles dans les solutions Office](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
## Étapes suivantes  
 Pour savoir comment créer une personnalisation au niveau du document pour Excel, consultez [Procédure pas à pas : création de votre première personnalisation au niveau du document pour Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md).  Cette procédure pas à pas vous initie aux outils de développement Office dans Visual Studio et au modèle de programmation pour les personnalisations au niveau du document pour Excel.  
  
 Pour obtenir une liste des rubriques vous présentant les tâches courantes des projets Excel, consultez [Tâches courantes en matière de programmation Office](../vsto/common-tasks-in-office-programming.md).  
  
## Voir aussi  
 [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Programmation de personnalisations au niveau du document](../vsto/programming-document-level-customizations.md)   
 [Solutions Excel](../vsto/excel-solutions.md)   
 [Procédure pas à pas : création de votre première personnalisation au niveau du document pour Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)   
 [Procédures pas à pas utilisant Excel](../vsto/walkthroughs-using-excel.md)   
 [Vue d'ensemble du modèle objet Excel](../vsto/excel-object-model-overview.md)   
 [Écriture de code dans les solutions Office](../vsto/writing-code-in-office-solutions.md)  
  
  