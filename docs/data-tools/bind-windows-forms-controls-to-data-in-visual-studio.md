---
title: "Liaison de contr&#244;les Windows Forms &#224; des donn&#233;es dans Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "données (Windows Forms), sources de données"
  - "données (Windows Forms), afficher"
  - "sources de données, afficher les données"
  - "afficher des données sur des formulaires"
  - "afficher les données, Windows Forms"
  - "formulaires, afficher les données"
  - "Windows Forms, liaison de données"
  - "Windows Forms, afficher les données"
ms.assetid: 243338ef-41af-4cc5-aff7-1e830236f0ec
caps.latest.revision: 37
caps.handback.revision: 31
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Liaison de contr&#244;les Windows Forms &#224; des donn&#233;es dans Visual Studio
Vous pouvez afficher des données pour les utilisateurs de votre application en liant les données à des Windows Forms.  Pour créer ces contrôles liés aux données, vous pouvez faire glisser des éléments de la fenêtre **Sources de données** sur le Concepteur Windows Forms dans Visual Studio.  Cette rubrique décrit quelques tâches, outils et classes les plus courants utilisés pour la création d'applications Windows Forms liées aux données.  
  
 Pour plus d'informations sur la création de contrôles liés aux données dans Visual Studio, consultez [Liaison de contrôles à des données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).  Pour plus d'informations sur la liaison de données dans les Windows Forms, consultez [Liaison de données Windows Forms](../Topic/Windows%20Forms%20Data%20Binding.md).  
  
## Tâches impliquées dans l'affichage de données sur un formulaire dans une application Windows  
 Le tableau suivant répertorie les tâches courantes liées à l'affichage des données sur un formulaire dans une application Windows.  
  
|Tâche|Complément d'information|  
|-----------|------------------------------|  
|Créer des contrôles liés aux données.<br /><br /> Lier des contrôles existants à des données.|[Comment : lier des contrôles Windows Forms à des données](../data-tools/bind-windows-forms-controls-to-data.md)|  
|Créer des contrôles qui affichent les données connexes d'une relation parent\-enfant : lorsque l'utilisateur sélectionne un enregistrement de données dans un contrôle, un autre contrôle affiche les données connexes pour l'enregistrement sélectionné.|[Comment : afficher des données connexes dans une application Windows Forms](../Topic/How%20to:%20Display%20Related%20Data%20in%20a%20Windows%20Forms%20Application.md)|  
|Créer une *table de correspondance*.  Une table de correspondance affiche les informations d'une table en fonction de la valeur du champ de clé étrangère d'une autre table.|[Comment : créer des tables de correspondance dans des applications Windows Forms](../data-tools/create-lookup-tables-in-windows-forms-applications.md)|  
|Mettre en forme la façon dont les contrôles affichent les données.|[Formatting and Advanced Binding Dialog Box](http://msdn.microsoft.com/fr-fr/42638120-9e6f-436b-985f-4036664230fd)|  
|Modifier le comportement de la fonctionnalité de retouche des légendes dans la fenêtre **Sources de données**.|[Comment : personnaliser la façon dont Visual Studio crée des légendes pour les contrôles liés aux données](../data-tools/customize-how-visual-studio-creates-captions-for-data-bound-controls.md)|  
|Ajouter des contrôles qui exécutent une requête paramétrable.|[Comment : ajouter une requête paramétrable à une application Windows Forms](../Topic/How%20to:%20Add%20a%20Parameterized%20Query%20to%20a%20Windows%20Forms%20Application.md)|  
|Définir une colonne de façon à utiliser un contrôle d'image pour afficher des images dans une base de données.|[Comment : lier des contrôles à des images d'une base de données](../data-tools/bind-controls-to-pictures-from-a-database.md)|  
|Filtrer ou trier des données dans un groupe de données.|[Comment : filtrer et trier des données connexes dans une application Windows Forms](../data-tools/filter-and-sort-data-in-a-windows-forms-application.md)|  
  
 Les rubriques suivantes fournissent des exemples de liaisons de contrôles Windows Forms à des données.  
  
 [Procédure pas à pas : affichage de données sur un Windows Form](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)  
 Fournit des détails pas à pas sur l'interrogation de données provenant d'une base de données et leur affichage sur un Windows Form.  
  
 [Procédure pas à pas : affichage de données liées sur un Windows Form](../Topic/Walkthrough:%20Displaying%20Related%20Data%20on%20a%20Windows%20Form.md)  
 Fournit des détails pas à pas sur l'affichage de données provenant de deux tables connexes et leur affichage sur un Windows Form.  
  
 [Procédure pas à pas : création d'un Windows Form pour rechercher des données](../data-tools/create-a-windows-form-to-search-data.md)  
 Fournit des détails pas à pas sur la façon de créer un Windows Form qui effectue une recherche dans une base de données en fonction de l'entrée utilisateur.  
  
 [Procédure pas à pas : création d'une table de correspondance dans une application Windows Forms](../Topic/Walkthrough:%20Creating%20a%20Lookup%20Table%20in%20a%20Windows%20Forms%20Application.md)  
 Fournit des détails pas à pas sur la façon d'afficher des données d'une table basée sur les données sélectionnées dans une autre table.  
  
 [Procédure pas à pas : passage de données entre Windows Forms](../data-tools/pass-data-between-forms.md)  
 Fournit des détails pas à pas sur la façon de passer des valeurs d'un formulaire à un autre formulaire dans une application.  
  
 [Procédure pas à pas : création d'un contrôle utilisateur Windows Forms prenant en charge la liaison de données simple](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md)  
 Fournit des détails pas à pas sur la création d'un contrôle personnalisé qui peut être utilisé dans la fenêtre **Sources de données**.  
  
 [Procédure pas à pas : création d'un contrôle utilisateur Windows Forms prenant en charge la liaison de données complexe](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md)  
 Fournit des détails pas à pas sur la création d'un contrôle personnalisé qui peut être utilisé dans la fenêtre **Sources de données**.  
  
 [Procédure pas à pas : création d'un contrôle utilisateur Windows Forms prenant en charge la liaison de données de recherche](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md)  
 Fournit des détails pas à pas sur la création d'un contrôle personnalisé qui peut être utilisé dans la fenêtre **Sources de données**.  
  
## Balises actives de données  
 Les balises actives spécifiques à l'utilisation de données sont disponibles sur de nombreux contrôles.  Lorsque certains contrôles sont ajoutés à un formulaire, un jeu d'actions possible lié aux données est disponible sur la balise active.  
  
## Composant BindingSource  
 Le composant <xref:System.Windows.Forms.BindingSource> remplit deux fonctions.  Il fournit une couche d'abstraction lors de la liaison des contrôles figurant sur votre formulaire aux données.  Les contrôles sur le formulaire sont liés au composant <xref:System.Windows.Forms.BindingSource> \(au lieu d'être lié directement à une source de données\).  
  
 Il permet de gérer une collection d'objets.  L'ajout d'un type au composant <xref:System.Windows.Forms.BindingSource> crée une liste de ce type.  
  
 Pour plus d'informations sur le composant <xref:System.Windows.Forms.BindingSource>, consultez :  
  
-   [Composant BindingSource](../Topic/BindingSource%20Component.md)  
  
-   [Vue d'ensemble du composant BindingSource](../Topic/BindingSource%20Component%20Overview.md)  
  
-   [Architecture du composant BindingSource](../Topic/BindingSource%20Component%20Architecture.md)  
  
## Contrôle BindingNavigator  
 Ce composant fournit une interface utilisateur pour la navigation dans des données affichées par une application Windows.  Pour plus d'informations, consultez [BindingNavigator, contrôle](../Topic/BindingNavigator%20Control%20\(Windows%20Forms\).md).  
  
## Contrôle DataGridView  
 Le contrôle <xref:System.Windows.Forms.DataGridView> vous permet d'afficher et de modifier les données sous forme de tableau provenant de nombreux types de sources de données différents.  Vous pouvez lier des données à un <xref:System.Windows.Forms.DataGridView> à l'aide de la propriété <xref:System.Windows.Forms.DataGridView.DataSource%2A>.  Pour plus d'informations, consultez [Vue d'ensemble du contrôle DataGridView](../Topic/DataGridView%20Control%20Overview%20\(Windows%20Forms\).md).  
  
## Voir aussi  
 [Procédures pas à pas relatives aux données](../Topic/Data%20Walkthroughs.md)   
 [Sources de données \(fenêtre\)](../Topic/Data%20Sources%20Window.md)   
 [Liaison de contrôles à des données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Procédure pas à pas : affichage de données sur un Windows Form](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)   
 [Création et modification de Datasets typés](../data-tools/creating-and-editing-typed-datasets.md)   
 [Vue d'ensemble des sources de données](../data-tools/add-new-data-sources.md)   
 [Procédure pas à pas : création d'un contrôle utilisateur Windows Forms prenant en charge la liaison de données simple](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md)   
 [Procédure pas à pas : création d'un contrôle utilisateur Windows Forms prenant en charge la liaison de données complexe](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md)   
 [Procédure pas à pas : création d'un contrôle utilisateur Windows Forms prenant en charge la liaison de données de recherche](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md)