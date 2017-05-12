---
title: "Mise en route de la programmation des personnalisations au niveau du document pour Word"
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
  - "projets Word (développement Office dans Visual Studio), mise en route"
  - "solutions Word dans Visual Studio"
ms.assetid: 30593c47-1658-4fca-b9a9-36fbdf73c901
caps.latest.revision: 44
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 43
---
# Mise en route de la programmation des personnalisations au niveau du document pour Word
  Si vous êtes novice dans la création de personnalisations au niveau de le document pour Microsoft Office Word à l'aide de Visual Studio, voici ce que vous devez connaître.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
## Comprendre le fonctionnement des personnalisations au niveau du document pour Word  
 Chaque personnalisation de Word que vous créez est basée sur un document unique.  Pour commencer à utiliser la personnalisation, l'utilisateur final ouvre le document ou le crée à partir d'un modèle Word.  Certains événements dans le document, par exemple le déplacement du curseur dans des zones spécifiques ou un clic sur des boutons et des éléments de menu, peuvent appeler des méthodes de gestion d'événements dans l'assembly.  Lorsque le document est fermé, les fonctionnalités fournies par la personnalisation ne sont plus disponibles dans Word.  
  
 Pour plus d’informations, consultez [Architecture des personnalisations au niveau du document](../vsto/architecture-of-document-level-customizations.md).  
  
## Création de projets au niveau du document pour Word  
 Pour créer un projet de personnalisation au niveau du document pour Word, utilisez le modèle de projet Document Word ou Modèle Word dans la boîte de dialogue **Nouveau projet** de Visual Studio.  Ces modèles comprennent des références d'assembly et des fichiers projet requis.  
  
 Pour plus d'informations sur la création d'un projet au niveau du document pour Word, consultez [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  Pour plus d'informations sur les modèles de projet, consultez [Vue d'ensemble des modèles de projet Office](../vsto/office-project-templates-overview.md).  
  
## Programmation de documents Word à l'aide d'éléments hôtes et de contrôles hôtes  
 Les *éléments hôtes* et les *contrôles hôtes* sont des classes qui fournissent le modèle de programmation pour les personnalisations au niveau du document.  
  
 Les éléments hôtes fournissent un point d'entrée pour votre code, et ils peuvent également jouer le rôle de conteneurs pour les contrôles hôtes et Windows Forms.  Dans les projets au niveau du document pour Word, l'élément hôte est représenté par la classe `ThisDocument` .  
  
 Les contrôles hôtes sont basés sur des objets Word natifs, tels que les contrôles de contenu, les signets et les nœuds XML.  Les contrôles hôtes fournissent des fonctionnalités semblables aux objets Word natifs, mais ils possèdent également de nouveaux événements, un support concepteur et des fonctions de liaison de données.  Ils apparaissent comme des objets de première classe dans votre code de projet et dans IntelliSense, ce qui facilite les références directes à des objets spécifiques dans votre code, sans devoir parcourir le modèle objet Word.  
  
 Pour plus d’informations, voir les rubriques suivantes :  
  
-   [Programmation de personnalisations au niveau du document](../vsto/programming-document-level-customizations.md)  
  
-   [Automatisation de Word à l'aide d'objets étendus](../vsto/automating-word-by-using-extended-objects.md)  
  
-   [Vue d'ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)  
  
## Personnalisation de l'interface utilisateur de Word  
 La plupart des solutions Microsoft Office modifient l'interface utilisateur \(IU\) de l'application Office pour permettre aux utilisateurs d'interagir avec elles.  Vous pouvez modifier de nombreuses manières l'interface utilisateur de Word en utilisant une personnalisation au niveau du document.  Par exemple, vous pouvez ajouter des contrôles au ruban, et vous pouvez afficher un volet Actions.  Pour plus d’informations, consultez [Personnalisation de l'interface utilisateur Office](../vsto/office-ui-customization.md).  
  
 Vous pouvez également ouvrir le document associé à votre projet directement dans Visual Studio.  Lorsque le document est ouvert dans Visual Studio, vous pouvez modifier le document à l'aide de l'interface utilisateur Word.  Vous pouvez également utiliser le document comme une aire de conception, ce qui vous permet d'y faire glisser des contrôles.  Pour plus d’informations, consultez [Projets Office dans l'environnement Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md).  
  
## Liaison de contrôles aux données  
 Les contrôles de contenu et le contrôle <xref:Microsoft.Office.Tools.Word.Bookmark> figurent dans la liste des contrôles que vous pouvez faire glisser de la fenêtre **Sources de données**.  Ajouter des contrôles de contenu et des signets de cette manière les lie automatiquement à la source de données que vous configurez à l'aide de la fenêtre.  Sans écrire de code, vous pouvez afficher des données provenant de bases de données, de services Web et d'objets métiers.  Pour plus d’informations, consultez [Liaison de données aux contrôles dans les solutions Office](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
## Étapes suivantes  
 Pour savoir comment créer une personnalisation au niveau du document pour Word, consultez [Procédure pas à pas : création de votre première personnalisation au niveau du document pour Word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md).  Cette procédure pas à pas vous initie aux outils de développement Office dans Visual Studio et au modèle de programmation pour les personnalisations au niveau du document pour Word.  
  
 Pour une liste des rubriques vous présentant les tâches courantes des projets Word, consultez [Tâches courantes en matière de programmation Office](../vsto/common-tasks-in-office-programming.md).  
  
## Voir aussi  
 [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Programmation de personnalisations au niveau du document](../vsto/programming-document-level-customizations.md)   
 [Solutions Word](../vsto/word-solutions.md)   
 [Procédure pas à pas : création de votre première personnalisation au niveau du document pour Word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)   
 [Procédures pas à pas utilisant Word](../vsto/walkthroughs-using-word.md)   
 [Vue d'ensemble du modèle objet Word](../vsto/word-object-model-overview.md)   
 [Écriture de code dans les solutions Office](../vsto/writing-code-in-office-solutions.md)  
  
  