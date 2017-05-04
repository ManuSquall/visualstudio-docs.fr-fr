---
title: "Comment&#160;: remplir des documents avec les donn&#233;es d&#39;une base de donn&#233;es | Microsoft Docs"
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
  - "données, ajouter à des documents"
  - "documents, remplir de données"
ms.assetid: 1eb5b13d-7359-407e-8be8-e42c1829f10c
caps.latest.revision: 48
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 47
---
# Comment&#160;: remplir des documents avec les donn&#233;es d&#39;une base de donn&#233;es
  Vous pouvez accéder aux projets au niveau du document pour Microsoft Office de la même façon que vous accédez aux données des projets Windows Forms.  Vous utilisez les mêmes outils et le même code pour importer les données à partir d'une base de données dans votre solution, et vous pouvez utiliser des contrôles Windows Forms pour afficher les données.  
  
 En outre, vous pouvez afficher les données à l'aide de contrôles hôtes.  Les contrôles hôtes sont des objets natifs dans Microsoft Office Word qui ont été améliorés avec les événements et la fonctionnalité de liaison de données.  Pour plus d'informations, consultez [Vue d'ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md).  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 L'exemple suivant montre comment ajouter des contrôles liés aux données dans les projets au niveau du document à l'aide d'un concepteur.  Pour obtenir un exemple montrant comment ajouter des contrôles liés aux données dans les projets de complément VSTO au moment de l'exécution, consultez [Procédure pas à pas : liaison de données simple dans un projet de complément VSTO](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md).  
  
 ![lien vers la vidéo](../vsto/media/playvideo.png "lien vers la vidéo") Pour une démonstration vidéo connexe, consultez [Liaison de données aux contrôles de contenu Word 2007 à l'aide de Visual Studio Tools pour Office System \(3.0\)](http://go.microsoft.com/fwlink/?LinkId=136785).  
  
## Ajout d'un contrôle à un document au moment du design  
  
#### Remplir un document avec les données d'une base de données  
  
1.  Ouvrez un projet au niveau du document Word dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], avec le document ouvert dans le concepteur.  
  
2.  Ouvrez la fenêtre **Sources de données** et créez une source de données à partir d'une base de données.  Pour plus d'informations, consultez [Comment : établir une connexion à des données d'une base de données](~/data-tools/how-to-connect-to-data-in-a-database.md).  
  
3.  Faites glisser le contrôle que vous souhaitez depuis la fenêtre **Sources de données** vers votre document.  
  
 Un contrôle de contenu est ajouté au document.  Le type de contrôle de contenu dépend du type de données du champ sélectionné.  Pour plus d'informations, consultez [Contrôles de contenu](../vsto/content-controls.md).  
  
 Vous pouvez ajouter un autre contrôle en sélectionnant le champ de données dans la fenêtre **Sources de données**, puis en choisissant un contrôle différent dans la liste déroulante.  
  
## Objets du projet  
 Outre le contrôle, les objets de données suivants sont automatiquement ajoutés à votre projet :  
  
-   Un dataset typé qui encapsule les tables de données auxquelles vous êtes connecté dans la base de données.  Pour plus d'informations, consultez [Utilisation de groupes de données dans Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).  
  
-   Un <xref:System.Windows.Forms.BindingSource> qui connecte le contrôle au dataset typé.  Pour plus d'informations, consultez [Vue d'ensemble du composant BindingSource](http://msdn.microsoft.com/library/be838caf-fcb0-4b68-827f-58b2c04b747f).  
  
-   Un TableAdapter qui connecte le dataset typé à la base de données.  Pour plus d'informations, consultez [Vue d'ensemble de TableAdapter](/visual-studio/data-tools/tableadapter-overview).  
  
-   Un TableAdapterManager, qui permet de coordonner les adaptateurs de table du dataset pour permettre les mises à jour hiérarchiques.  Pour plus d'informations, consultez [Mise à jour hiérarchique](../data-tools/hierarchical-update.md) et [Vue d'ensemble de TableAdapterManager](http://msdn.microsoft.com/library/33076d42-6b41-491a-ac11-6c6339aea650).  
  
 Lorsque vous exécutez le projet, le contrôle affiche le premier enregistrement de la source de données.  Vous pouvez utiliser le <xref:System.Windows.Forms.BindingSource> pour permettre aux utilisateurs de faire défiler les enregistrements.  
  
#### Pour faire défiler les enregistrements  
  
-   Utilisez les méthodes <xref:System.Windows.Forms.BindingSource> telles que <xref:System.Windows.Forms.BindingSource.MoveNext%2A> et <xref:System.Windows.Forms.BindingSource.MovePrevious%2A>.  
  
 Pour plus d'informations sur l'envoi de mises à jour au dataset typé et à la base de données, consultez [Comment : mettre à jour une source de données avec les données d'un contrôle hôte](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md).  
  
## Voir aussi  
 [Liaison de données aux contrôles dans les solutions Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Vue d'ensemble des sources de données](../data-tools/add-new-data-sources.md)   
 [Liaison de contrôles Windows Forms à des données dans Visual Studio](../Topic/Binding%20Windows%20Forms%20controls%20to%20data%20in%20Visual%20Studio.md)   
 [Comment : remplir des documents avec les données d'objets](../vsto/how-to-populate-documents-with-data-from-objects.md)   
 [Comment : mettre à jour une source de données avec les données d'un contrôle hôte](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)   
 [Vue d'ensemble de l'utilisation de fichiers de base de données locaux dans les solutions Office](../vsto/using-local-database-files-in-office-solutions-overview.md)   
 [Connexion à des données dans des applications Windows Forms](/visual-studio/data-tools/connecting-to-data-in-windows-forms-applications)   
 [Vue d'ensemble du composant BindingSource](http://msdn.microsoft.com/library/be838caf-fcb0-4b68-827f-58b2c04b747f)  
  
  