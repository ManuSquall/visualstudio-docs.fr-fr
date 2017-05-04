---
title: "Comment&#160;: parcourir les enregistrements de base de donn&#233;es dans une feuille de calcul | Microsoft Docs"
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
  - "données (développement Office dans Visual Studio), faire défiler les enregistrements de base de données"
  - "bases de données (développement Office dans Visual Studio), faire défiler des enregistrements"
  - "enregistrements (développement Office dans Visual Studio), défilement"
  - "feuilles de calcul (développement Office dans Visual Studio), faire défiler des enregistrements"
ms.assetid: aea4c86c-9d6d-47dd-8977-066e21945dab
caps.latest.revision: 33
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 32
---
# Comment&#160;: parcourir les enregistrements de base de donn&#233;es dans une feuille de calcul
  Cette procédure explique comment utiliser le concepteur pour afficher un champ à partir d'une table de base de données dans une feuille de calcul Microsoft Office Excel, avec des contrôles qui permettent à l'utilisateur final de faire défiler tous les enregistrements.  
  
 Vous ne pouvez utiliser le concepteur que dans des projets au niveau du document.  Toutefois, vous pouvez également ajouter des contrôles et les lier aux données par programmation au moment de l'exécution.  Pour plus d’informations, consultez [Procédure pas à pas : liaison de données simple dans un projet de complément VSTO](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md).  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
### Pour faire défiler des enregistrements de base de données dans une feuille de calcul  
  
1.  Ouvrez un projet d'application Excel dans Visual Studio.  
  
2.  Ouvrez la fenêtre **Sources de données** et créez une source de données à partir de la base de données.  Pour plus d’informations, consultez [Comment : établir une connexion à des données d'une base de données](../Topic/How%20to:%20Connect%20to%20Data%20in%20a%20Database.md).  
  
3.  Développez la table qui contient les données à afficher et sélectionnez la colonne spécifique.  
  
4.  Ouvrez la liste de contrôles et sélectionnez **NamedRange**.  
  
5.  Faites glisser le contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange> sur la cellule où vous souhaitez que les données apparaissent.  
  
6.  À partir de l'onglet **Windows Forms** de la **Boîte à outils**, ajoutez un contrôle <xref:System.Windows.Forms.BindingNavigator> à votre feuille de calcul et configurez les contrôles que vous souhaitez utiliser.  Pour plus d’informations, consultez [Vue d'ensemble du contrôle BindingNavigator &#40;Windows Forms&#41;](../Topic/BindingNavigator%20Control%20Overview%20(Windows%20Forms).md).  
  
## Voir aussi  
 [Liaison de données aux contrôles dans les solutions Office](../vsto/binding-data-to-controls-in-office-solutions.md)  
  
  