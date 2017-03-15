---
title: "D&#233;finir le contr&#244;le &#224; cr&#233;er lors d’une op&#233;ration de glisser-d&#233;placer &#224; partir de la fen&#234;tre Sources de donn&#233;es | Microsoft Docs"
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
  - "Sources de données (fenêtre), sélectionner des contrôles"
  - "Windows Forms, affichage de données"
  - "données (Visual Studio), affichage dans les Windows Forms"
  - "données (Visual Studio), fenêtre Sources de données"
ms.assetid: 20597ff8-0c98-43ec-8fb1-05376804ba48
caps.latest.revision: 31
caps.handback.revision: 28
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# D&#233;finir le contr&#244;le &#224; cr&#233;er lors d’une op&#233;ration de glisser-d&#233;placer &#224; partir de la fen&#234;tre Sources de donn&#233;es
Vous pouvez créer des contrôles liés aux données en faisant glisser des éléments de la fenêtre **Sources de données** vers le Concepteur WPF ou le Concepteur Windows Forms.  Chaque élément de la fenêtre **Sources de données** possède un contrôle par défaut qui est créé lorsque vous faites glisser l'élément vers le concepteur.  Toutefois, vous pouvez choisir de créer un contrôle différent.  
  
## Définition des contrôles à créer pour des tables de données ou des objets  
 Avant de faire glisser des éléments qui représentent des tables de données ou des objets de la fenêtre **Sources de données**, vous pouvez choisir d'afficher toutes les données dans un seul contrôle ou d'afficher chaque colonne ou propriété dans un contrôle distinct.  
  
 Dans ce contexte, le terme *objet* fait référence à un objet métier personnalisé, une entité \(dans un Entity Data Model\) ou un objet retourné par un service.  
  
#### Pour définir les contrôles à créer pour des tables de données ou des objets  
  
1.  Assurez\-vous que le Concepteur WPF ou le Concepteur Windows Forms est ouvert.  
  
2.  Dans la fenêtre **Sources de données**, sélectionnez l'élément qui représente la table de données ou l'objet que vous voulez définir.  
  
3.  Cliquez sur le menu déroulant de l'élément, puis sur l'un des éléments suivants dans le menu :  
  
    -   Pour afficher chaque champ de données dans un contrôle distinct, cliquez sur **Détails**.  Lorsque vous faites glisser l'élément de données vers le concepteur, cette action crée un contrôle lié aux données différent pour chaque colonne ou propriété de la table de données ou de l'objet parent, avec des étiquettes pour chaque contrôle.  
  
    -   Pour afficher toutes les données dans un seul contrôle, sélectionnez un contrôle différent dans la liste, tel que **DataGrid** ou **List** dans une application WPF, ou **DataGridView** dans une application Windows Forms.  
  
     La liste des contrôles disponibles dépend du concepteur que vous avez ouvert, de la version .NET Framework que votre projet cible, et si vous avez ajouté à la **Boîte à outils** des contrôles personnalisés qui prennent en charge la liaison de données.  Si le contrôle que vous voulez créer se trouve dans la liste des contrôles disponibles, vous pouvez l'ajouter à la liste.  Pour plus d'informations, consultez [Ajouter des contrôles personnalisés à la fenêtre Sources de données](../data-tools/add-custom-controls-to-the-data-sources-window.md).  
  
     Pour apprendre à créer un contrôle Windows Forms personnalisé qui peut être ajouté à la liste de contrôles pour les tables de données ou les objets dans la fenêtre **Sources de données**, consultez [Procédure pas à pas : création d'un contrôle utilisateur Windows Forms prenant en charge la liaison de données complexe](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md).  
  
## Définition des contrôles à créer pour des colonnes de données ou des propriétés  
 Avant de faire glisser un élément qui représente une colonne ou une propriété d'un objet de la fenêtre **Sources de données** vers le concepteur, vous pouvez définir le contrôle à créer.  
  
#### Pour définir les contrôles à créer pour des colonnes ou des propriétés  
  
1.  Assurez\-vous que le Concepteur WPF ou le Concepteur Windows Forms est ouvert.  
  
2.  Dans la fenêtre **Sources de données**, développez la table ou l'objet souhaité pour afficher ses colonnes ou propriétés.  
  
3.  Sélectionnez chaque colonne ou propriété pour laquelle vous voulez définir le contrôle à créer.  
  
4.  Cliquez sur le menu déroulant de la colonne ou de la propriété, puis sélectionnez le contrôle que vous voulez créer après avoir fait glisser l'élément vers le concepteur.  
  
     La liste des contrôles disponibles dépend du concepteur que vous avez ouvert, de la version .NET Framework que votre projet cible et des contrôles personnalisés qui prennent en charge la liaison de données que vous avez ajoutés à la **Boîte à outils** .  Si le contrôle que vous voulez créer se trouve dans la liste des contrôles disponibles, vous pouvez l'ajouter à la liste.  Pour plus d'informations, consultez [Ajouter des contrôles personnalisés à la fenêtre Sources de données](../data-tools/add-custom-controls-to-the-data-sources-window.md).  
  
     Pour apprendre comment créer un contrôle personnalisé qui peut être ajouté à la liste de contrôles pour les colonnes de données ou les propriétés dans la fenêtre **Sources de données**, consultez [Procédure pas à pas : création d'un contrôle utilisateur Windows Forms prenant en charge la liaison de données simple](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).  
  
     Si vous ne souhaitez pas créer de contrôle pour la colonne ou la propriété, sélectionnez **Aucun** dans le menu déroulant.  Cela est utile si vous voulez faire glisser la table ou l'objet parent vers le concepteur, mais ne voulez pas inclure la colonne ou la propriété spécifique.  
  
## Voir aussi  
 [Procédures pas à pas relatives aux données](../Topic/Data%20Walkthroughs.md)   
 [Procédure pas à pas : affichage de données sur un Windows Form](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)   
 [Liaison de contrôles Windows Forms à des données dans Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Création et modification de Datasets typés](../data-tools/creating-and-editing-typed-datasets.md)   
 [Vue d'ensemble des sources de données](../data-tools/add-new-data-sources.md)   
 [Sources de données \(fenêtre\)](../Topic/Data%20Sources%20Window.md)   
 [Ajouter des contrôles personnalisés à la fenêtre Sources de données](../data-tools/add-custom-controls-to-the-data-sources-window.md)