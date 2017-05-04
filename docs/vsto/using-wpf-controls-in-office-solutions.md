---
title: "Utilisation de contr&#244;les WPF dans les solutions Office | Microsoft Docs"
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
  - "WPF (développement Office dans Visual Studio)"
ms.assetid: 305a212b-0a95-40ad-87aa-22896fe80a04
caps.latest.revision: 25
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 24
---
# Utilisation de contr&#244;les WPF dans les solutions Office
  Bien que les solutions créées à l'aide des outils de développement Office dans Visual Studio soient conçues pour fonctionner directement avec les contrôles Windows Forms, vous pouvez également utiliser des contrôles WPF dans vos solutions.  Windows Presentation Foundation \(WPF\) est une alternative à Windows Forms pour concevoir des interfaces utilisateur.  WPF utilise un langage de balisage appelé XAML \(eXtensible Application Markup Language\) qui offre de nouvelles techniques pour intégrer l'interface utilisateur, les médias et les documents.  Pour plus d'informations, consultez [Présentation de WPF dans Visual Studio 2015](../Topic/Introduction%20to%20WPF%20in%20Visual%20Studio%202015.md).  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Tout élément d'interface utilisateur qui peut héberger des contrôles Windows Forms dans une solution Office peut également héberger des contrôles WPF.  Ces éléments sont entre autres les suivants :  
  
-   Les documents et les feuilles de calcul dans les personnalisations au niveau du document.  
  
-   Les volets Actions dans les personnalisations au niveau du document.  
  
-   Les volets de tâches personnalisés dans les compléments VSTO.  
  
-   Les zones de formulaire dans les compléments VSTO pour Outlook.  
  
## Ajout de contrôles WPF aux projets Office au moment du design  
 Vous ne pouvez pas ajouter des contrôles WPF directement aux éléments d'interface utilisateur dans les solutions Office.  À la place, ajoutez un élément **contrôle utilisateur \(WPF\)** à votre projet et utilisez\-le comme aire de conception pour les contrôles WPF.  Puis, ajoutez le contrôle utilisateur WPF à un élément d'interface utilisateur de votre projet.  
  
#### Pour ajouter des contrôles WPF à un volet Actions, un volet des tâches personnalisé ou une zone de formulaire  
  
1.  Ouvrez un projet auquel vous souhaitez ajouter un volet des tâches personnalisé, un volet Actions ou une zone de formulaire.  
  
2.  Ajoutez un élément **Contrôle utilisateur \(WPF\)** à votre projet.  
  
3.  À partir de la **boîte à outils**, ajoutez des contrôles WPF à l'aire de conception des contrôles utilisateur WPF.  
  
     Par défaut, lorsque le Concepteur de contrôles utilisateur WPF est ouvert, la **boîte à outils** contient uniquement des contrôles WPF.  
  
4.  Générez le projet.  
  
5.  Ajoutez un volet Actions, une zone de formulaire ou un volet des tâches personnalisé à votre projet :  
  
    -   Pour les zones de formulaire, ajoutez un élément **zone de formulaire Outlook** au projet.  Pour plus d'informations, consultez [Comment : ajouter une zone de formulaire à un projet de complément Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).  
  
    -   Pour les volets Actions, ajoutez un élément **contrôle de volet Actions** ou **contrôle utilisateur** au projet.  Pour plus d'informations, consultez [Comment : ajouter un volet Actions à des documents Word ou à des classeurs Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md) et [Comment : ajouter un volet Actions à des documents Word ou à des classeurs Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md).  
  
    -   Pour les volets de tâches personnalisés, ajoutez un élément **contrôle utilisateur** au projet.  Pour plus d'informations, consultez [Comment : ajouter un volet de tâches personnalisé à une application](../vsto/how-to-add-a-custom-task-pane-to-an-application.md).  
  
6.  À partir de l'onglet *NomProjet* **Contrôles utilisateur WPF** de la **boîte à outils**, faites glisser le contrôle utilisateur WPF vers le concepteur du volet Actions, de la zone de formulaire ou d'un volet de tâches personnalisé.  
  
     Visual Studio crée automatiquement un objet <xref:System.Windows.Forms.Integration.ElementHost> qui héberge le contrôle utilisateur WPF sur l'élément d'interface utilisateur.  
  
7.  Regénérez le projet.  
  
#### Pour ajouter des contrôles WPF à un document ou à une feuille de calcul d'un projet au niveau du document  
  
1.  Ouvrez un projet au niveau du document pour Word ou Excel.  
  
2.  Ajoutez un élément **Contrôle utilisateur \(WPF\)** à votre projet.  
  
3.  À partir de la **boîte à outils**, ajoutez des contrôles WPF à l'aire de conception des contrôles utilisateur WPF.  
  
4.  Générez le projet.  
  
5.  Ajouter un élément **Contrôle utilisateur** \(autrement dit, un contrôle utilisateur Windows Forms\) au projet.  
  
6.  Ouvrez le concepteur pour le contrôle utilisateur Windows Forms.  
  
7.  À partir de l'onglet *NomProjet* **Contrôles utilisateur WPF** de la **boîte à outils**, faites glisser le contrôle utilisateur WPF vers le concepteur.  
  
     Visual Studio crée automatiquement un objet <xref:System.Windows.Forms.Integration.ElementHost> qui héberge le contrôle utilisateur WPF dans le contrôle utilisateur Windows Forms.  
  
8.  Écrivez le code qui ajoute par programmation le contrôle utilisateur Windows Forms au document ou au classeur.  Pour plus d'informations, consultez [Ajout de contrôles à des documents Office au moment de l'exécution](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
    > [!NOTE]  
    >  Vous ne pouvez pas faire glisser le contrôle utilisateur Windows Forms vers le document ou la feuille de calcul du concepteur .  
  
9. Regénérez le projet.  
  
## Hébergement des contrôles WPF à l'aide de la classe ElementHost  
 Visual Studio fournit des fonctionnalités qui vous aident à utiliser les contrôles Windows Forms dans vos solutions Office, mais il ne fournit pas de fonctionnalités similaires pour les contrôles WPF.  Par exemple, vous pouvez ajouter des contrôles Windows Forms aux documents et aux feuilles de calcul au moment du design en faisant glisser des contrôles à partir de la **boîte à outils** ou au moment de l'exécution à l'aide des méthodes d'assistance.  Cependant, ces outils ne sont pas disponibles pour les contrôles WPF.  
  
 Les contrôles WPF utilisent la classe <xref:System.Windows.Forms.Integration.ElementHost> comme couche d'intégration entre un formulaire ou contrôle Windows Forms et les contrôles WPF.  Lorsque vous ajoutez des contrôles WPF à votre solution au moment du design, Visual Studio génère automatiquement un objet <xref:System.Windows.Forms.Integration.ElementHost>.  
  
## Ressources WPF  
 Pour plus d'informations sur les problèmes d'architecture ou de conception d'hébergement des contrôles WPF sur les formulaires et les contrôles Windows Forms, consultez les rubriques suivantes :  
  
-   [Architecture d'entrée pour l'interopérabilité entre Windows Forms et WPF](../Topic/Windows%20Forms%20and%20WPF%20Interoperability%20Input%20Architecture.md)  
  
-   [Mappage de propriétés Windows Forms et WPF](../Topic/Windows%20Forms%20and%20WPF%20Property%20Mapping.md)  
  
-   [Interopérabilité WPF et Windows Forms](../Topic/WPF%20and%20Windows%20Forms%20Interoperation.md)  
  
-   [Contrôles Windows Forms et contrôles WPF équivalents](../Topic/Windows%20Forms%20Controls%20and%20Equivalent%20WPF%20Controls.md)  
  
 Pour plus d'informations sur l'ajout de contrôles WPF à des formulaires et contrôles Windows Forms dans Visual Studio au moment du design, consultez les rubriques suivantes :  
  
-   [Procédure pas à pas : création de contenu WPF sur les Windows Forms au moment du design](../Topic/Walkthrough:%20Creating%20New%20WPF%20Content%20on%20Windows%20Forms%20at%20Design%20Time.md)  
  
-   [Procédure pas à pas : réorganisation du contenu WPF sur les Windows Forms au moment du design](../Topic/Walkthrough:%20Arranging%20WPF%20Content%20on%20Windows%20Forms%20at%20Design%20Time.md)  
  
-   [Procédure pas à pas : application de styles au contenu WPF](../Topic/Walkthrough:%20Styling%20WPF%20Content.md).  
  
## Voir aussi  
 [Personnalisation de l'interface utilisateur Office](../vsto/office-ui-customization.md)   
 [Vue d'ensemble des contrôles Windows Forms dans les documents Office](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Vue d'ensemble du volet Actions](../vsto/actions-pane-overview.md)   
 [Volets de tâches personnalisés](../vsto/custom-task-panes.md)   
 [Création de zones de formulaire Outlook](../vsto/creating-outlook-form-regions.md)   
 [Comment : ajouter un volet Actions à des documents Word ou à des classeurs Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [Comment : ajouter un volet Actions à des documents Word ou à des classeurs Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [Comment : ajouter un volet de tâches personnalisé à une application](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)   
 [Comment : ajouter une zone de formulaire à un projet de complément Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)  
  
  