---
title: "Personnalisation de l&#39;interface utilisateur Office | Microsoft Docs"
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
  - "volets Actions (développement Office dans Visual Studio), créer"
  - "menus (développement Office dans Visual Studio), personnaliser"
  - "applications Office (développement Office dans Visual Studio), personnalisation de l'interface utilisateur"
  - "barres d'outils (développement Office dans Visual Studio), personnaliser"
  - "WPF (développement Office dans Visual Studio)"
ms.assetid: 3d7c7b88-2053-4ada-bfe7-e7bb202c430b
caps.latest.revision: 74
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 73
---
# Personnalisation de l&#39;interface utilisateur Office
  Vous pouvez personnaliser l'interface utilisateur des applications Microsoft Office à l'aide des outils de développement Office dans Visual Studio.  Cette rubrique répertorie les fonctionnalités de l'interface utilisateur que vous pouvez personnaliser, comme décrit dans les sections suivantes :  
  
-   [Comparaison des fonctionnalités de l'interface utilisateur](#Comparison)  
  
-   [Volets Actions et volets de tâches personnalisés](#Actions)  
  
-   [Interface utilisateur du ruban personnalisée](#Ribbon)  
  
-   [Mode Backstage](#Backstage)  
  
-   [Zones de formulaire Outlook](#FormRegion)  
  
-   [Contrôles dans des documents](#Controls)  
  
-   [Menus contextuels](#Shortcut)  
  
##  <a name="Comparison"></a> Comparaison des fonctionnalités de l'interface utilisateur  
 Le tableau suivant compare les principales fonctionnalités de l'interface utilisateur que vous pouvez personnaliser dans les projets Microsoft Office.  
  
|Fonctionnalité|Types de projet pris en charge|Applications Microsoft Office prises en charge|  
|--------------------|------------------------------------|----------------------------------------------------|  
|Volet Actions|Personnalisations au niveau du document|Excel<br /><br /> Word|  
|Volets de tâches personnalisés|Compléments VSTO|Excel<br /><br /> [!INCLUDE[InfoPath_15_short](../vsto/includes/infopath-15-short-md.md)]<br /><br /> [!INCLUDE[InfoPath_14_short](../vsto/includes/infopath-14-short-md.md)]<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Word<br /><br /> Excel|  
|Interface utilisateur du ruban personnalisée|Personnalisations au niveau du document<br /><br /> Compléments VSTO|Excel<br /><br /> [!INCLUDE[InfoPath_15_short](../vsto/includes/infopath-15-short-md.md)]<br /><br /> [!INCLUDE[InfoPath_14_short](../vsto/includes/infopath-14-short-md.md)]<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Projet<br /><br /> Word<br /><br /> Visio|  
|Mode Backstage|Personnalisations au niveau du document<br /><br /> Compléments VSTO|Excel<br /><br /> [!INCLUDE[InfoPath_15_short](../vsto/includes/infopath-15-short-md.md)].<br /><br /> [!INCLUDE[InfoPath_14_short](../vsto/includes/infopath-14-short-md.md)]<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Projet<br /><br /> Word<br /><br /> Visio|  
|Zones de formulaire Outlook|Compléments VSTO|Outlook|  
|Contrôles dans des documents|Personnalisations au niveau du document<br /><br /> Compléments VSTO|Excel<br /><br /> Word|  
|Menus contextuels|Personnalisations au niveau du document<br /><br /> Compléments VSTO|Excel<br /><br /> [!INCLUDE[InfoPath_15_short](../vsto/includes/infopath-15-short-md.md)]<br /><br /> [!INCLUDE[InfoPath_14_short](../vsto/includes/infopath-14-short-md.md)]<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Projet<br /><br /> Word<br /><br /> Visio<br /><br /> Excel|  
  
##  <a name="Actions"></a> Volets Actions et volets de tâches personnalisés  
 Les volets de tâches sont des panneaux d'interface utilisateur généralement ancrés à l'un des côtés d'une fenêtre dans une application Microsoft Office.  Presque toutes les applications Microsoft Office intègrent des volets de tâches,  tels que le volet Aide dans Word.  
  
 Les outils de développement Office dans Visual Studio offrent deux façons de personnaliser des volets de tâches :  
  
-   Vous pouvez ajouter un volet Actions à une personnalisation au niveau du document.  Par défaut, ce volet s'affiche sur le côté droit de l'application, à droite du document.  Il peut aussi s'afficher à gauche, en haut ou en bas du document.  
  
-   Vous pouvez ajouter un volet de tâches personnalisé à un complément VSTO.  Les utilisateurs peuvent ancrer les volets de tâches personnalisés aux différents côtés de la fenêtre d'application ou les faire glisser n'importe où dans la fenêtre.  
  
 Les volets Actions et les volets de tâches personnalisés fournissent des fonctionnalités en hébergeant divers contrôles qui facilitent l'exécution de certaines tâches, telles que la saisie de données.  Par rapport à un groupe Ruban, les volets Actions et les volets de tâches personnalisés proposent une zone beaucoup plus grande pour inclure le texte et les contrôles.  
  
 Pour plus d'informations sur les volets Actions, consultez [Vue d'ensemble du volet Actions](../vsto/actions-pane-overview.md).  Pour plus d'informations sur les volets de tâches personnalisés, consultez [Volets de tâches personnalisés](../vsto/custom-task-panes.md).  
  
##  <a name="Ribbon"></a> Interface utilisateur du ruban personnalisée  
 Vous pouvez personnaliser l'interface utilisateur du ruban pour exposer les fonctionnalités que vous ajoutez aux applications Office.  Le ruban est une façon d'organiser les commandes associées \(sous forme de contrôles\) pour les retrouver plus facilement.  Vous pouvez créer vos propres groupes et onglets de ruban pour permettre aux utilisateurs d'accéder aux fonctionnalités fournies dans votre solution.  La plupart des fonctionnalités accessibles via les menus et les barres d'outils dans les versions antérieures de Microsoft Office System sont maintenant accessibles à partir du ruban.  
  
 Pour plus d'informations, consultez [Vue d'ensemble du ruban](../vsto/ribbon-overview.md).  
  
##  <a name="Backstage"></a> Mode Backstage  
 Dans les applications Office, un clic sur l'onglet **Fichier** ouvre le mode Backstage.  Le mode Backstage fournit une interface utilisateur qui combine des actions et des tâches de niveau fichier, et remplace les fonctionnalités similaires disponibles via le bouton Microsoft Office dans Microsoft Office System version 2007.  Ce mode est intégralement extensible à l'aide de XML.  
  
 Visual Studio ne fournit pas de concepteur ni d'API pour personnaliser le mode Backstage.  Toutefois, si vous ajoutez un élément **Ruban \(XML\)** à votre projet Office, vous pouvez inclure du code XML dans le fichier XML du ruban pour personnaliser le mode Backstage.  Pour plus d'informations sur les éléments **Ruban \(XML\)**, consultez [Élément XML Ribbon](../vsto/ribbon-xml.md).  
  
 Pour plus d'informations sur la personnalisation du mode Backstage, consultez [Introduction au mode Backstage Office 2010 pour les développeurs](http://go.microsoft.com/fwlink/?LinkId=182189) et [Personnalisation du mode Backstage Office 2010 pour les développeurs](http://go.microsoft.com/fwlink/?LinkId=182188).  
  
##  <a name="FormRegion"></a> Zones de formulaire Outlook  
 Utilisez des zones de formulaire pour ajouter des fonctionnalités personnalisées aux formulaires Microsoft Office Outlook standard.  Vous pouvez créer des zones de formulaire qui étendent tout formulaire existant avec des champs ou contrôles supplémentaires.  Si vous créez une zone de formulaire à l'aide des outils de développement Office dans Visual Studio, vous pouvez utiliser uniquement des contrôles Windows Forms dans cette zone de formulaire.  Si vous importez une zone de formulaire conçue dans Outlook, vous pouvez alors utiliser des contrôles Outlook natifs uniquement.  
  
 Vous pouvez créer des zones de formulaire qui occupent différents endroits de l'interface utilisateur d'Outlook.  Par exemple, ces zones de formulaire adjacentes s'affichent en bas de la première page d'un formulaire et sont toutes réductibles.  Vous pouvez aussi ajouter une zone de formulaire distincte qui s'affiche comme page de formulaire supplémentaire complète et peut apparaître sur tout formulaire standard ou personnalisé existant.  
  
 Pour plus d'informations, consultez [Création de zones de formulaire Outlook](../vsto/creating-outlook-form-regions.md).  
  
##  <a name="Controls"></a> Contrôles dans des documents  
 Vous pouvez ajouter divers contrôles aux documents Word et aux feuilles de calcul Excel.  Par exemple, ajoutez un contrôle sélecteur de dates à un document pour permettre à l'utilisateur d'entrer des dates dans un format standard, ou placez un bouton dans une feuille de calcul pour envoyer des données vers une base de données.  
  
 Quand vous développez un projet de niveau document pour Excel ou Word, vous pouvez utiliser le concepteur Visual Studio pour ajouter des contrôles au document ou au classeur dans votre projet au moment du design, ou les ajouter par programmation au moment de l'exécution.  Quand vous développez des projets de complément VSTO pour Excel ou Word, vous pouvez ajouter des contrôles par programmation à n'importe quel document ou classeur ouvert au moment de l'exécution.  
  
 Pour plus d'informations, consultez [Vue d'ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md) et [Vue d'ensemble des contrôles Windows Forms dans les documents Office](../vsto/windows-forms-controls-on-office-documents-overview.md).  
  
##  <a name="Shortcut"></a> Menus contextuels  
 Un menu contextuel s'affiche lorsque vous cliquez avec le bouton droit dans un document ou une fenêtre d'application.  Vous pouvez définir un menu contextuel pour qu'il apparaisse quand un événement se produit \(par exemple, quand un utilisateur clique avec le bouton droit sur un document, un classeur ou un contrôle hôte\).  Vous avez la possibilité d'ajouter divers contrôles ou commandes de menu à un menu contextuel,  et créer des menus contextuels à l'aide de XML.  Si vous ajoutez un élément **Ruban \(XML\)** à votre projet Office, vous pouvez ajouter le code XML dans le fichier XML du ruban pour créer des menus contextuels.  Pour plus d'informations sur l'utilisation de XML pour créer des menus contextuels, consultez [Comment : ajouter des commandes à des menus contextuels](../vsto/how-to-add-commands-to-shortcut-menus.md).  
  
## Voir aussi  
 [Vue d'ensemble du ruban](../vsto/ribbon-overview.md)   
 [Vue d'ensemble des contrôles Windows Forms dans les documents Office](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Vue d'ensemble du volet Actions](../vsto/actions-pane-overview.md)   
 [Création de zones de formulaire Outlook](../vsto/creating-outlook-form-regions.md)   
 [Volets de tâches personnalisés](../vsto/custom-task-panes.md)   
 [Utilisation de contrôles WPF dans les solutions Office](../vsto/using-wpf-controls-in-office-solutions.md)   
 [Comment : afficher l'onglet Développeur sur le ruban](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)   
 [Comment : afficher les erreurs de l'interface utilisateur du complément](../vsto/how-to-show-add-in-user-interface-errors.md)   
 [Procédure pas à pas : collecte de données à l'aide d'un Windows Form](../vsto/walkthrough-collecting-data-using-a-windows-form.md)  
  
  