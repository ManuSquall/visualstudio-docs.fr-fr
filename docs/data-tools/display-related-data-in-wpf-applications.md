---
title: "Comment&#160;: afficher des donn&#233;es connexes dans des applications WPF | Microsoft Docs"
ms.custom: ""
ms.date: "09/21/2016"
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
  - "données (WPF), afficher"
  - "liaison de données, WPF"
  - "afficher les données, WPF"
  - "WPF (WPF), données"
  - "liaison de données WPF (Visual Studio)"
  - "concepteur WPF, liaison de données"
  - "WPF, liaison de données dans Visual Studio"
ms.assetid: 3aa80194-0191-474d-9d28-5ec05654b426
caps.latest.revision: 16
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Comment&#160;: afficher des donn&#233;es connexes dans des applications WPF
Dans certaines applications, vous pouvez utiliser des données qui viennent de plusieurs tables ou entités mises en rapport les unes avec les autres dans une relation parent\-enfant.  Par exemple, vous pouvez afficher une grille qui montre les clients d'une table `Customers`.  Lorsque l'utilisateur sélectionne un client spécifique, une autre grille affiche les commandes pour ce client à partir d'une table `Orders` connexe.  
  
 Vous pouvez créer des contrôles liés aux données qui affichent les données connexes en faisant glisser des éléments de la fenêtre **Sources de données** vers le Concepteur WPF.  
  
### Pour créer des contrôles qui affichent des enregistrements connexes  
  
1.  Dans le menu **Données**, cliquez sur **Afficher les sources de données** pour ouvrir la fenêtre **Sources de données**.  
  
2.  Cliquez sur **Ajouter une nouvelle source de données**, puis exécutez l'**Assistant Configuration de source de données**.  
  
3.  Ouvrez le Concepteur WPF et assurez\-vous qu'il inclut un conteneur étant une cible de déplacement valide pour les éléments de la fenêtre **Sources de données**.  
  
     Pour plus d'informations sur les cibles de déplacement valides, consultez [Liaison de contrôles WPF avec des données dans Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
4.  Dans la fenêtre **Sources de données**, développez le nœud qui représente la table ou l'objet parent dans la relation.  La table ou l'objet parent représente la partie « un » d'une relation un\-à\-plusieurs.  
  
5.  Faites glisser le nœud parent \(ou les éléments un par un dans le nœud parent\) de la fenêtre **Sources de données** vers une cible valide de déplacement dans le concepteur.  
  
     Visual Studio génère du code XAML qui crée des contrôles liés aux données pour chaque élément que vous faites glisser.  Le code XAML ajoute également une nouvelle <xref:System.Windows.Data.CollectionViewSource> pour la table ou l'objet parent aux ressources de la cible de déplacement.  Pour certaines sources de données, Visual Studio génère également du code permettant de charger les données dans la table ou l'objet parent.  Pour plus d'informations, consultez [Liaison de contrôles WPF avec des données dans Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
6.  Dans la fenêtre **Sources de données**, localisez la table ou l'objet enfant connexe.  Les tables et objets enfants connexes apparaissent sous forme de nœuds extensibles en bas de la liste des colonnes du nœud parent.  
  
7.  Faites glisser le nœud enfant \(ou les éléments un par un dans le nœud enfant\) de la fenêtre **Sources de données** vers une cible valide de déplacement dans le concepteur.  
  
     Visual Studio génère du code XAML qui crée des contrôles liés aux données pour chaque élément que vous faites glisser.  Le code XAML ajoute également une nouvelle <xref:System.Windows.Data.CollectionViewSource> pour la table ou l'objet enfant aux ressources de la cible de déplacement.  Cette nouvelle <xref:System.Windows.Data.CollectionViewSource> est liée à la propriété de la table ou de l'objet parent que vous venez de faire glisser vers le concepteur.  Pour certaines sources de données, Visual Studio génère également du code permettant de charger les données dans la table ou l'objet enfant.  
  
     L'illustration suivante montre la table **Orders** connexe de la table **Customers** dans un groupe de données \(dataset\) dans la fenêtre **Sources de données**.  
  
     ![Fenêtre Sources de données montrant des relations](~/docs/data-tools/media/datasources2.gif "DataSources2")  
  
## Voir aussi  
 [Liaison de contrôles WPF avec des données dans Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)   
 [Comment : lier des contrôles WPF à des données dans Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md)   
 [Comment : créer des tables de correspondance dans des applications WPF](../data-tools/create-lookup-tables-in-wpf-applications.md)   
 [Procédure pas à pas : affichage de données connexes dans une application WPF](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md)