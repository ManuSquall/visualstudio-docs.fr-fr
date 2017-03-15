---
title: "Proc&#233;dure pas &#224; pas&#160;: cr&#233;ation d&#39;un DataTable dans le Concepteur de DataSet | Microsoft Docs"
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
  - "données (Visual Studio), Concepteur de DataSet"
  - "Concepteur de DataSet, créer des tables de données"
  - "objets DataTable, créer"
  - "tables (Visual Studio), créer"
ms.assetid: abf0a2b5-e4e5-422e-97ef-55a0e35a82df
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Proc&#233;dure pas &#224; pas&#160;: cr&#233;ation d&#39;un DataTable dans le Concepteur de DataSet
Cette procédure pas à pas explique comment créer un <xref:System.Data.DataTable> \(sans TableAdapter\) à l'aide du **Concepteur de DataSet**.  Pour plus d'informations sur la création de tables de données comprenant des TableAdapters, consultez [Comment : créer des TableAdapters](../data-tools/create-and-configure-tableadapters.md).  
  
 Cette procédure pas à pas illustre les tâches suivantes :  
  
-   Création d'un nouveau projet Application Windows  
  
-   Ajout d'un nouveau groupe de données à l'application  
  
-   Ajout d'une nouvelle table de données au groupe de données  
  
-   Ajout de colonnes à la table de données  
  
-   Définition de la clé primaire pour la table  
  
## Création d'une nouvelle application Windows  
  
#### Pour créer un projet d'application Windows  
  
1.  Dans le menu **Fichier**, créez un nouveau projet.  
  
2.  Choisissez un langage de programmation dans le volet **Types de projets**.  
  
3.  Cliquez sur **Application Windows** dans le volet **Modèles**.  
  
4.  Nommez le projet `DataTableWalkthrough`, puis cliquez sur **OK**.  
  
     Visual Studio ajoute le projet à l'**Explorateur de solutions** et affiche **Form1** dans le concepteur.  
  
## Ajout d'un nouveau groupe de données à l'application  
  
#### Pour ajouter un nouvel élément de groupe de données au projet  
  
1.  Dans le menu **Projet**, cliquez sur **Ajouter un nouvel élément**.  
  
     La boîte de dialogue Ajouter un nouvel élément apparaît.  
  
2.  Dans la zone **Modèles**, sélectionnez **DataSet**.  
  
3.  Cliquez sur **Ajouter**.  
  
     Visual Studio ajoute un fichier appelé **DataSet1.xsd** au projet et l'ouvre dans le **Concepteur de DataSet**.  
  
## Ajout d'un nouveau DataTable au groupe de données  
  
#### Pour ajouter une nouvelle table de données au groupe de données  
  
1.  Faites glisser un **DataTable** depuis l'onglet **DataSet** de la **Boîte à outils** jusqu'au **Concepteur de DataSet**.  
  
     Une table nommée **DataTable1** est ajoutée au groupe de données.  
  
    > [!NOTE]
    >  Pour créer une table de données qui comprend un TableAdapter, consultez [Procédure pas à pas : création d'un TableAdapter avec plusieurs requêtes](../data-tools/walkthrough-creating-a-tableadapter-with-multiple-queries.md).  
  
2.  Cliquez sur la barre de titre de **DataTable1** et renommez\-le `Music`.  
  
## Ajout de colonnes à la table de données  
  
#### Pour ajouter des colonnes à la table de données  
  
1.  Cliquez avec le bouton droit sur la table **Music**.  Pointez sur **Ajouter**, puis cliquez sur **Colonne**.  
  
2.  Nommez la colonne `SongID`.  
  
3.  Dans la fenêtre **Propriétés**, affectez à la propriété <xref:System.Data.DataColumn.DataType%2A> la valeur <xref:System.Int16?displayProperty=fullName>.  
  
4.  Répétez ce processus pour ajouter les colonnes suivantes :  
  
     `SongTitle` : <xref:System.String?displayProperty=fullName>  
  
     `Artist` : <xref:System.String?displayProperty=fullName>  
  
     `Genre` : <xref:System.String?displayProperty=fullName>  
  
## Définition de la clé primaire pour la table  
 Toutes les tables de données doivent posséder une clé primaire.  Une clé primaire identifie de manière unique un enregistrement spécifique dans une table de données.  
  
#### Pour définir la clé primaire de la table de données  
  
-   Cliquez avec le bouton droit sur la colonne **SongID**, puis cliquez sur **Définir la clé primaire**.  
  
     Une icône en forme de clé apparaît en regard de la colonne **SongID**.  
  
## Enregistrement de votre projet  
  
#### Pour enregistrer le projet DataTableWalkthrough  
  
-   Dans le menu **Fichier**, cliquez sur **Enregistrer tout**.  
  
## Étapes suivantes  
 Maintenant que vous avez créé la table, vous pouvez exécuter l'une des actions suivantes :  
  
|Pour|Consultez|  
|----------|---------------|  
|Créer un formulaire d'entrée de données|[Procédure pas à pas : affichage de données sur un Windows Form](../data-tools/walkthrough-displaying-data-on-a-windows-form.md).|  
|Ajouter des données à la table|[Ajout de données à un objet DataTable](../Topic/Adding%20Data%20to%20a%20DataTable.md).|  
|Afficher les données dans une table|[Visualisation de données dans un DataTable](../Topic/Viewing%20Data%20in%20a%20DataTable.md).|  
|Modifier les données|[Modifications d'un DataTable](../Topic/DataTable%20Edits.md)|  
|Supprimer une ligne d'une table|[Suppresion d'un objet DataRow](../Topic/DataRow%20Deletion.md)|  
  
## Voir aussi  
 [Connexion aux données dans Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Préparation de votre application pour recevoir des données](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Extraction de données dans votre application](../data-tools/fetching-data-into-your-application.md)   
 [Liaison de contrôles à des données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modification des données dans votre application](../data-tools/editing-data-in-your-application.md)   
 [Validation des données](../Topic/Validating%20Data.md)   
 [Enregistrement des données](../data-tools/saving-data.md)   
 [Procédures pas à pas relatives aux données](../Topic/Data%20Walkthroughs.md)