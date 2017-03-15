---
title: "Proc&#233;dure pas &#224; pas&#160;: cr&#233;ation d&#39;un groupe de donn&#233;es avec le Concepteur de DataSet | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "Concepteur de DataSet, procédures pas à pas"
  - "groupes de données (Visual Basic), créer"
  - "groupes de données (Visual Basic), procédures pas à pas"
  - "schémas XML, créer des groupes de données"
ms.assetid: 12360f54-db6c-45d2-a91f-fee43214b555
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Proc&#233;dure pas &#224; pas&#160;: cr&#233;ation d&#39;un groupe de donn&#233;es avec le Concepteur de DataSet
Dans cette procédure pas à pas, vous allez créer un groupe de données à l'aide du **Concepteur de DataSet**.  Elle vous guidera à travers le processus consistant à créer un nouveau projet et à y ajouter un nouvel élément **DataSet**.  Vous apprendrez à créer des tables basées sur des tables d'une base de données sans utiliser d'Assistant.  
  
 Cette procédure pas à pas illustre les tâches suivantes :  
  
-   Création d'un nouveau projet **Application Windows**.  
  
-   Ajout d'un élément **DataSet** vide au projet.  
  
-   Création et configuration d'une source de données dans votre application en générant un groupe de données avec le **Concepteur de DataSet**.  
  
-   Création d'une connexion à la base de données Northwind dans l'**Explorateur de serveurs**.  
  
-   Création dans le groupe de données de tables avec des TableAdapters basées sur les tables contenues dans la base de données.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## Composants requis  
 Pour exécuter cette procédure pas à pas, vous devez :  
  
-   avoir accès à l'exemple de base de données Northwind \(versions SQL Server ou Access\).  Pour plus d'informations, consultez [Comment : installer des exemples de bases de données](../data-tools/how-to-install-sample-databases.md).  
  
## Création d'un projet d'application Windows  
  
#### Pour créer un projet d'application Windows  
  
1.  Dans le menu **Fichier**, créez un nouveau projet.  
  
2.  Choisissez un langage de programmation dans le volet **Types de projets**.  
  
3.  Cliquez sur **Application Windows** dans le volet **Modèles**.  
  
4.  Nommez le projet `DatasetDesignerWalkthrough`, puis cliquez sur **OK**.  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ajoutera le projet à l'**Explorateur de solutions** et affichera un nouveau formulaire dans le concepteur.  
  
## Ajout d'un nouveau groupe de données à l'application  
  
#### Pour ajouter un nouvel élément de groupe de données au projet  
  
1.  Dans le menu **Projet**, cliquez sur **Ajouter un nouvel élément**.  
  
     La boîte de dialogue **Ajouter un nouvel élément** s'affiche alors.  
  
2.  Dans la zone **Modèles** de la boîte de dialogue **Ajouter un nouvel élément**, cliquez sur **DataSet**.  
  
3.  Nommez le groupe de données `NorthwindDataset`, puis cliquez sur **Ajouter**.  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ajoutera un fichier appelé **NorthwindDataset.xsd** au projet et l'ouvrira dans le **Concepteur de DataSet**.  
  
## Création d'une connexion de données dans l'Explorateur de serveurs  
  
#### Pour créer une connexion à la base de données Northwind  
  
1.  Dans le menu **Affichage**, cliquez sur **Explorateur de serveurs**.  
  
2.  Dans l'**Explorateur de serveurs**, cliquez le bouton **Se connecter à la base de données**.  
  
3.  Créez une connexion à l'exemple de base de données Northwind.  
  
    > [!NOTE]
    >  Vous pouvez vous connecter à la version SQL Server ou Access de Northwind pour exécuter cette procédure pas à pas.  
  
## Création des tables dans le groupe de données  
 Cette section explique l'ajout de tables au groupe de données.  
  
#### Pour créer la table Customers  
  
1.  Développez la connexion de données que vous avez créée dans l'**Explorateur de serveurs**, puis développez le nœud **Tables**.  
  
2.  Faites glisser la table **Customers** depuis l'**Explorateur de serveurs** jusqu'au **Concepteur de DataSet**.  
  
     Une table de données **Customers** et un **CustomersTableAdapter** sont ajoutés au groupe de données.  
  
#### Pour créer la table Orders  
  
-   Faites glisser la table **Orders** depuis l'**Explorateur de serveurs** jusqu'au **Concepteur de DataSet**.  
  
     Une table de données **Orders**, un **OrdersTableAdapter** et une relation de données entre les tables **Customers** et **Orders** sont ajoutés au groupe de données.  
  
#### Pour créer la table OrderDetails  
  
-   Faites glisser la table **Order Details** depuis l'**Explorateur de serveurs** jusqu'au **Concepteur de DataSet**.  
  
     Une table de données **Order Details**, un **Order DetailsTableAdapter** et une relation de données entre les tables **Orders** et **Order Details** sont ajoutés au groupe de données.  
  
## Étapes suivantes  
  
### Pour ajouter des fonctionnalités à votre application  
  
-   Enregistrez le groupe de données.  
  
-   Sélectionnez des éléments dans la fenêtre **Sources de données** et faites\-les glisser jusqu'à un formulaire.  Pour plus d'informations, consultez [Liaison de contrôles Windows Forms à des données dans Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md).  
  
-   Ajoutez d'autres requêtes aux TableAdapters.  Pour plus d'informations, consultez [Comment : créer des requêtes TableAdapter](../data-tools/how-to-create-tableadapter-queries.md).  
  
-   Ajoutez une logique de validation aux événements <xref:System.Data.DataTable.ColumnChanging> ou <xref:System.Data.DataTable.RowChanging> des tables de données dans le groupe de données.  Pour plus d'informations, consultez [Validation de données dans des groupes de données](../data-tools/validate-data-in-datasets.md).  
  
## Voir aussi  
 [Procédures pas à pas relatives aux données](../Topic/Data%20Walkthroughs.md)   
 [Liaison de contrôles Windows Forms à des données dans Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Connexion aux données dans Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Préparation de votre application pour recevoir des données](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Extraction de données dans votre application](../data-tools/fetching-data-into-your-application.md)   
 [Liaison de contrôles à des données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modification des données dans votre application](../data-tools/editing-data-in-your-application.md)   
 [Validation des données](../Topic/Validating%20Data.md)   
 [Enregistrement des données](../data-tools/saving-data.md)