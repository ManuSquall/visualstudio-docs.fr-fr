---
title: "Utilisation de groupes de donn&#233;es dans des applications multicouches | Microsoft Docs"
ms.custom: ""
ms.date: "12/13/2016"
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
  - "données (Visual Basic), applications multicouches"
  - "projet DataSet (différence avec applications multicouches)"
  - "groupes de données (Visual Basic), applications multicouches"
  - "applications distribuées (différence avec applications multicouches)"
  - "applications sur plusieurs niveaux"
  - "applications de bases de données multicouches"
  - "applications multicouches"
  - "TableAdapters, applications multicouches"
  - "couches, applications multicouches"
  - "datasets typés, applications multicouches"
ms.assetid: f6ae2ee0-ea5f-4a79-8f4b-e21c115afb20
caps.latest.revision: 22
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Utilisation de groupes de donn&#233;es dans des applications multicouches
Les *applications de données multicouches* sont des applications centrées sur les données divisées en plusieurs *couches* logiques.  En d'autres termes, une application de données multicouche est une application divisée en plusieurs projets, avec une couche d'accès aux données, une couche de logique métier et une couche Présentation dans son propre projet.  Pour plus d'informations, consultez [Vue d'ensemble des applications de données multicouches](../data-tools/n-tier-data-applications-overview.md).  
  
 Les datasets typés ont été améliorés de sorte que les TableAdapters et les classes DataSet puissent être générés dans des projets distincts.  Cela permet de rapidement séparer les couches de l'application et de générer des applications de données multicouches.  
  
 La prise en charge du multicouche dans les datasets typés permet le développement itératif de l'architecture de l'application vers une conception multicouche et élimine la nécessité de séparer manuellement le code en plusieurs projets.  Commencez par concevoir la couche Données à l'aide du [Création et modification de Datasets typés](../data-tools/creating-and-editing-typed-datasets.md).  Quand vous êtes prêt à faire évoluer l'architecture de l'application vers une conception multicouche, définissez la propriété **DataSet Project** d'un dataset pour qu'elle génère la classe DataSet dans un projet distinct.  
  
## Dans cette section  
 [Comment : séparer les Datasets et les TableAdapters dans différents projets](../data-tools/separate-datasets-and-tableadapters-into-different-projects.md)  
 Décrit comment déplacer la classe DataSet générée du projet qui contient les classes TableAdapter générées dans un nouveau projet.  
  
 [Comment : ajouter du code aux TableAdapters dans des applications multicouches](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)  
 Décrit comment générer une classe partielle dans laquelle le code peut être ajouté pour un TableAdapter multicouche.  
  
 [Comment : ajouter du code aux groupes de données dans des applications multicouches](../data-tools/add-code-to-datasets-in-n-tier-applications.md)  
 Décrit comment générer une classe partielle dans laquelle le code peut être ajouté pour un dataset multicouche.  
  
 [Comment : ajouter la validation à un groupe de données multicouche](../data-tools/add-validation-to-an-n-tier-dataset.md)  
 Décrit où ajouter le code pour effectuer une validation pendant la modification des données.  
  
 [Procédure pas à pas : création d'une application de données multicouche](../data-tools/walkthrough-creating-an-n-tier-data-application.md)  
 Fournit des instructions pas à pas pour créer un dataset typé et diviser le code du TableAdapter et du dataset en plusieurs projets.  
  
 [Procédure pas à pas : ajout d'une validation à une application de données multicouche](../Topic/Walkthrough:%20Adding%20Validation%20to%20an%20N-Tier%20Data%20Application.md)  
 Fournit des instructions pas à pas pour ajouter une validation à l'application créée dans la procédure pas à pas sur l'application de données multicouche.  
  
## Référence  
 <xref:System.Data.DataSet>  
  
 <xref:System.Data.TypedTableBase%601>  
  
## Rubriques connexes  
 [Vue d'ensemble des applications de données multicouches](../data-tools/n-tier-data-applications-overview.md)  
  
 [Mise à jour hiérarchique](../data-tools/hierarchical-update.md)  
  
 [Utilisation de groupes de données dans Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)  
  
 [Accès aux données dans Visual Studio](../data-tools/accessing-data-in-visual-studio.md)  
  
 [Vue d'ensemble de TableAdapter](../data-tools/tableadapter-overview.md)  
  
 [Applications multicouches et distantes avec LINQ to SQL](../Topic/N-Tier%20and%20Remote%20Applications%20with%20LINQ%20to%20SQL.md)