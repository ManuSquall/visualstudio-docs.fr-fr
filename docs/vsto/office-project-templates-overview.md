---
title: "Vue d&#39;ensemble des mod&#232;les de projet Office"
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
  - "modèles (développement Office dans Visual Studio), à propos des modèles de projet"
  - "classeur Excel (modèle de projet)"
  - "modèle Word (modèle de projet)"
  - "Excel (développement Office dans Visual Studio), modèles de projet"
  - "Project (développement Office dans Visual Studio), modèles de projet"
  - "modèles de projet (développement Office dans Visual Studio)"
  - "modèles de projet, Word"
  - "InfoPath (développement Office dans Visual Studio), modèles de projet"
  - "modèle Excel (modèle de projet)"
  - "modèles de projet, Microsoft Office System 2007"
  - "modèles de projet, Excel"
  - "PowerPoint (développement Office dans Visual Studio), modèles de projet"
  - "Word (développement Office dans Visual Studio), modèles de projet Word"
  - "projets Office (développement Office dans Visual Studio), modèles"
  - "projets Excel dans Visual Studio"
  - "document Word (modèle de projet)"
  - "Visio (développement Office dans Visual Studio), modèles de projet"
  - "projets Word dans Visual Studio"
  - "Outlook (développement Office dans Visual Studio), modèles de projet"
ms.assetid: 2f86546b-307f-48ea-b01c-5f5a242fce17
caps.latest.revision: 68
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 66
---
# Vue d&#39;ensemble des mod&#232;les de projet Office
  Les Outils de développement Microsoft Office dans Visual Studio incluent des modèles de projet pour la création des types suivants de solutions Office :  
  
-   [Personnalisations au niveau du document](#DocLevel)  
  
-   [Compléments VSTO](#AppLevel)  
  
 Pour obtenir une comparaison détaillée de ces types de solutions Office, consultez [Vue d'ensemble du développement des solutions Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
 Les modèles de projet Office sont disponibles dans la boîte de dialogue **Nouveau projet**, sous le nœud **Office** des nœuds de langage **Visual C\#** et **Visual Basic**. Chaque modèle génère un projet avec la configuration appropriée pour l'application cible, y compris les références d'assembly et les paramètres de débogage.  
  
 Chaque projet fournit des fichiers et du code qui vous aident à démarrer sur un genre de solution spécifique. Le code généré pour chaque projet inclut le démarrage et l'arrêt des gestionnaires d'événements. Vous pouvez ajouter du code à ces gestionnaires pour initialiser votre solution lorsqu'elle est chargée et pour la nettoyer lorsqu'elle est déchargée. Pour plus d’informations, consultez [Projets Office dans l'environnement Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md) et [Événements dans les projets Office](../vsto/events-in-office-projects.md).  
  
> [!NOTE]  
>  Les Outils de développement Office sont inclus avec certaines éditions de Visual Studio. Pour plus d'informations, consultez [Configuration d'un ordinateur pour développer des solutions Office](../vsto/configuring-a-computer-to-develop-office-solutions.md).  
  
##  <a name="DocLevel"></a> Personnalisations au niveau du document  
 Le nœud **Office** dans la boîte de dialogue **Nouveau projet** fournit les modèles de projet suivants pour vous aider à créer des personnalisations au niveau du document pour Word et Excel :  
  
-   **Document VSTO pour Word 2013 et 2016**  
  
-   **Modèle VSTO pour Word 2013 et 2016**  
  
-   **Classeur VSTO pour Excel 2013 et 2016**  
  
-   **Modèle VSTO pour Excel 2013 et 2016**  
  
-   **Document VSTO pour Word 2010**  
  
-   **Modèle VSTO pour Word 2010**  
  
-   **Classeur VSTO pour Excel 2010**  
  
-   **Modèle VSTO pour Excel 2010**  
  
 Les modèles de projet Document Word et Classeur Excel fournissent le code qui vous permet de commencer à créer une solution basée sur un document ou classeur spécifique. Dans ces types de solutions, votre code s'exécute uniquement lorsque le document associé est ouvert dans Word ou Excel.  
  
 Les modèles de projet Modèle Word et Modèle Excel se comportent de la même façon que les modèles Document Word et Classeur Excel. Toutefois, les modèles de projet Modèle Word et Modèle Excel permettent aux utilisateurs de créer facilement un document local ou des copies de classeur du modèle personnalisé dans votre solution. Les fonctionnalités de votre solution sont disponibles dans le nouveau document que l'utilisateur crée à partir du modèle.  
  
> [!NOTE]  
>  Vous ne pouvez pas utiliser des modèles Word qui font référence à des extensions de code managé comme compléments VSTO globaux. L'assembly n'est pas appelé si le modèle est chargé à partir du répertoire Startup de Word. Pour plus d'informations, consultez [Limitations des modèles globaux et des compléments Excel \(fichiers .xla\)](#Limitations)  
  
 Pour plus d'informations sur la mise en route avec ces types de projet, consultez les rubriques suivantes :  
  
-   [Programmation de personnalisations au niveau du document](../vsto/programming-document-level-customizations.md)  
  
-   [Solutions Word](../vsto/word-solutions.md)  
  
-   [Solutions Excel](../vsto/excel-solutions.md)  
  
-   [Procédure pas à pas : création de votre première personnalisation au niveau du document pour Word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)  
  
-   [Procédure pas à pas : création de votre première personnalisation au niveau du document pour Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)  
  
##  <a name="AppLevel"></a> Compléments VSTO  
 Le nœud **Office\/SharePoint** dans la boîte de dialogue **Nouveau projet** fournit les modèles de projets suivants pour vous aider à créer des compléments VSTO.  
  
-   **Complément VSTO pour Excel 2013 et 2016**  
  
-   **Complément VSTO pour InfoPath 2013**  
  
-   **Complément VSTO pour Outlook 2013 et 2016**  
  
-   **Complément VSTO pour PowerPoint 2013 et 2016**  
  
-   **Complément pour Project 2013 et 2016**  
  
-   **Complément pour Visio 2013 et 2016**  
  
-   **Complément pour Word 2013 et 2016**  
  
-   **Complément pour Excel 2010**  
  
-   **Complément pour InfoPath 2010**  
  
-   **Complément pour Outlook 2010**  
  
-   **Complément pour PowerPoint 2010**  
  
-   **Complément pour Project 2010**  
  
-   **Complément pour Visio 2010**  
  
-   **Complément pour Word 2010**  
  
 Lorsque vous créez un projet basé sur l'un de ces modèles de projet, le code de votre solution s'exécute lorsque l'application associée est ouverte. Contrairement aux projets au niveau du document, le code n'est pas associé à un document unique.  
  
 Pour plus d'informations sur la mise en route avec ces types de projet, consultez les rubriques suivantes :  
  
-   [Prise en main de la programmation de compléments VSTO](../vsto/getting-started-programming-vsto-add-ins.md)  
  
-   [Programmation de compléments VSTO](../vsto/programming-vsto-add-ins.md)  
  
-   [Procédure pas à pas : création de votre premier complément VSTO pour Excel](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md)  
  
-   [Procédure pas à pas : création de votre premier complément VSTO pour Outlook](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)  
  
-   [Procédure pas à pas : création de votre premier complément VSTO pour PowerPoint](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)  
  
-   [Procédure pas à pas : création de votre premier complément VSTO pour Project](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)  
  
-   [Procédure pas à pas : création de votre premier complément VSTO pour Word](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)  
  
## Solutions basées sur un document ou sur un modèle  
 Lorsque vous concevez une solution basée sur un document Word ou un classeur Excel, vous devez déterminer la meilleure façon de rendre ce document accessible aux utilisateurs.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Dans certains cas, il est possible de donner une copie d'un document à chaque utilisateur. Dans ce cas, créez votre solution à l'aide d'un projet de document Excel ou Word.  
  
 Dans d'autres cas, vous pouvez rendre un modèle disponible sur un serveur, de sorte que chaque utilisateur puisse l'ouvrir et enregistrer une copie locale sous forme de document. Dans ce cas, créez votre solution à l'aide d'un projet de modèle Excel ou Word.  
  
## Comparaison  
 Le tableau suivant souligne les différences entre les documents et les modèles.  
  
|Documents|Modèles|  
|---------------|-------------|  
|Les utilisateurs peuvent ouvrir et modifier un document, sauf s'il est en lecture seule. Les modifications enregistrées sont conservées dans l'original.|Les utilisateurs peuvent ouvrir un modèle pour créer une copie locale sous forme de nouveau document. Ils ne peuvent pas modifier l'original à moins qu'ils ne disposent d'autorisations particulières.|  
|Une fois le document ouvert, il déclenche l'événement <xref:Microsoft.Office.Tools.Word.Document.Open>.|Une fois le modèle ouvert, il déclenche l'événement <xref:Microsoft.Office.Tools.Word.Document.New>.|  
  
##  <a name="Limitations"></a> Limitations des modèles globaux et des compléments Excel \(fichiers .xla\)  
 Les documents, classeurs et modèles peuvent ne pas fonctionner correctement en tant que modèles globaux ou compléments VSTO Excel \(fichiers .xla\).  
  
## Modèles Word  
 Si un modèle Microsoft Office Word a des extensions de code managé, l'assembly de projet n'est pas appelé si le modèle est attaché en tant que modèle global ou chargé à partir du répertoire de démarrage de Word. En outre, le document ne reconnaît pas le format d'un modèle faisant partie d'une solution Office.  
  
## Compléments Excel \(fichiers .xla\)  
 Il n’existe aucun projet Office permettant de créer un complément VSTO Excel \(fichier .xla\). Il est possible d'enregistrer un classeur en tant que fichier .xla, mais cette opération, qui n'est pas prise en charge, n'est pas recommandée. Si vous enregistrez un classeur qui a des extensions de code managé au format de fichier **Macro complémentaire Microsoft Office Excel \(\*.xla\)**, vous pouvez le sélectionner dans la boîte de dialogue **Compléments** pour l'appliquer à un autre classeur. Parfois, le code s’exécute dans le classeur cible après l’application du complément VSTO, mais une telle utilisation de la solution Office n’est pas prise en charge.  
  
## Voir aussi  
 [Conception et création de solutions Office](../vsto/designing-and-creating-office-solutions.md)   
 [Développement de solutions Office](../vsto/developing-office-solutions.md)   
 [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Mise en route de la programmation des personnalisations au niveau du document pour Excel](../vsto/getting-started-programming-document-level-customizations-for-excel.md)   
 [Mise en route de la programmation des personnalisations au niveau du document pour Word](../vsto/getting-started-programming-document-level-customizations-for-word.md)   
 [Prise en main de la programmation de compléments VSTO](../vsto/getting-started-programming-vsto-add-ins.md)  
  
  