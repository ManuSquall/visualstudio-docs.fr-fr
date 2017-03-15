---
title: "Cr&#233;ation et modification de Datasets typ&#233;s | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Designer_Microsoft.VSDesigner.DataSource.Designer.DataSourceRootDesigner"
  - "vs.data.adddataset"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
  - "aspx"
helpviewer_keywords: 
  - "données (Visual Studio), Concepteur de DataSet"
  - "Concepteur de DataSet"
  - "groupes de données (Visual Basic), concepteur visuel"
ms.assetid: cd0dbe93-be9b-41e4-bc39-e9300678c1f2
caps.latest.revision: 26
caps.handback.revision: 26
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Cr&#233;ation et modification de Datasets typ&#233;s
Le **Concepteur de DataSet** est un jeu d'outils visuels permettant de créer et de modifier des groupes de données typés et les éléments individuels qui les composent.  
  
 Le **Concepteur de DataSet** fournit des représentations visuelles des objets contenus dans des groupes de données typés.  Vous pouvez créer et modifier des [TableAdapters](../data-tools/tableadapter-overview.md), des [requêtes TableAdapter](../data-tools/how-to-create-tableadapter-queries.md), des <xref:System.Data.DataTable>s, des <xref:System.Data.DataColumn>s et des <xref:System.Data.DataRelation>s à l'aide du **Concepteur de DataSet**.  
  
 Pour ouvrir le **Concepteur de DataSet**, double\-cliquez sur un groupe de données dans l'**Explorateur de solutions** ou cliquez avec le bouton droit sur un groupe de données dans la fenêtre **Sources de données** et cliquez sur **Modifier le DataSet à l'aide du Concepteur**.  Pour plus d'informations, consultez [Comment : ouvrir un groupe de données dans le Concepteur de DataSet](../Topic/How%20to:%20Open%20a%20Dataset%20in%20the%20Dataset%20Designer.md).  L'ajout d'un nouvel élément <xref:System.Data.DataSet> avec la boîte de dialogue **Ajouter un nouvel élément** entraîne l'affichage du **Concepteur de DataSet** avec un groupe de données vide que vous pouvez modifier.  
  
> [!NOTE]
>  Le **Concepteur de DataSet** permet d'étendre les fonctionnalités d'un groupe de données.  Double\-cliquez sur l'aire de conception ou cliquez avec le bouton droit et choisissez **Afficher le code** pour créer un fichier de classe partielle dans lequel vous pouvez ajouter au groupe de données du code qui ne sera pas modifié ou supprimé par le concepteur.  Pour plus d'informations sur l'extension des fonctionnalités d'un TableAdapter, consultez [Comment : étendre les fonctionnalités d'un TableAdapter](../data-tools/extend-the-functionality-of-a-tableadapter.md).  
  
 Le tableau suivant répertorie les tâches courantes que vous pouvez exécuter à l'aide du **Concepteur de DataSet**.  
  
|Pour|Consultez|  
|----------|---------------|  
|Créer un TableAdapter|[Comment : créer des TableAdapters](../data-tools/create-and-configure-tableadapters.md)|  
|Modifier un TableAdapter|[Comment : modifier des TableAdapters](../Topic/How%20to:%20Edit%20TableAdapters.md)|  
|Créer une requête TableAdapter|[Comment : créer des requêtes TableAdapter](../data-tools/how-to-create-tableadapter-queries.md)|  
|Modifier une requête TableAdapter|[Comment : modifier des requêtes TableAdapter](../data-tools/how-to-edit-tableadapter-queries.md)|  
|Créer un <xref:System.Data.DataTable>|[Comment : créer des tables de données](../data-tools/how-to-create-data-tables.md)|  
|Modifier un <xref:System.Data.DataTable>|[Conception de DataTables](../data-tools/designing-datatables.md)|  
|Créer un <xref:System.Data.DataColumn>|[Comment : ajouter des colonnes à un DataTable](../Topic/How%20to:%20Add%20Columns%20to%20a%20DataTable.md)|  
|Créer une relation entre deux <xref:System.Data.DataTable>s|[Comment : créer des DataRelations avec le Concepteur de DataSet](../Topic/How%20to:%20Create%20DataRelations%20with%20the%20Dataset%20Designer.md)|  
|Étendre les fonctionnalités du groupe de données|[Comment : étendre les fonctionnalités d'un groupe de données](../Topic/How%20to:%20Extend%20the%20Functionality%20of%20a%20Dataset.md)|  
|Ajouter la validation à l'événement <xref:System.Data.DataTable.ColumnChanging> d'une table de données|[Comment : valider les données au cours des modifications de colonnes](../Topic/How%20to:%20Validate%20Data%20During%20Column%20Changes.md)|  
|Ajouter la validation à l'événement <xref:System.Data.DataTable.RowChanging> d'une table de données|[Comment : valider les données au cours des modifications de lignes](../Topic/How%20to:%20Validate%20Data%20During%20Row%20Changes.md)|  
  
## Création d'objets sur l'aire de conception  
 Vous pouvez créer des groupes de données en ajoutant et en modifiant les objets individuels qui le composent.  Le tableau suivant fournit une explication des différents objets de l'onglet **DataSet** de la **Boîte à outils** qui peuvent être déplacés jusqu'à l'aire de conception:  
  
|Objet|Description|  
|-----------|-----------------|  
|TableAdapter|Contient une collection de commandes de données et une connexion de données permettant de communiquer avec la base de données sous\-jacente et de remplir une table de données.  Pour plus d’informations, consultez [Vue d'ensemble de TableAdapter](../data-tools/tableadapter-overview.md) et [Comment : créer des TableAdapters](../data-tools/create-and-configure-tableadapters.md).|  
|Requête|Les requêtes TableAdapter sont des méthodes fortement typées qui exécutent des instructions SQL et des procédures stockées.  L'exécution d'une requête TableAdapter remplit de données la table de données ou exécute d'autres tâches de base de données.  Pour plus d'informations, consultez [Comment : créer des requêtes TableAdapter](../data-tools/how-to-create-tableadapter-queries.md).  Le déplacement d'une requête jusqu'à une table ajoute la requête à cette table, alors que le déplacement d'une requête jusqu'à une zone vide du **Concepteur de DataSet** crée une requête globale.  Pour plus d'informations, consultez [Comment : ajouter des requêtes globales à un groupe de données](../data-tools/how-to-add-global-queries-to-a-tableadapter.md).|  
|<xref:System.Data.DataTable>|Représente une collection en mémoire des lignes retournées par une base de données.|  
|Relation \(<xref:System.Data.DataRelation>\)|Représente une relation parent\/enfant entre deux objets <xref:System.Data.DataTable>.  Pour plus d’informations, consultez [Introduction aux objets DataRelation](../Topic/Introduction%20to%20DataRelation%20Objects.md) et [Procédure pas à pas : création d'une relation entre des tables de données](../Topic/Walkthrough:%20Creating%20a%20Relationship%20between%20Data%20Tables.md).|  
  
> [!NOTE]
>  Le **Concepteur de DataSet** se connecte à une base de données sous\-jacente uniquement lorsqu'un groupe de données est créé ; le concepteur ne détecte pas automatiquement les modifications faites sur la base de données.  Pour actualiser un .xsd existant, réexécutez l'**Assistant de configuration**.  Si les relations de tableau ont changé, supprimez et rajoutez les tableaux appropriés au .xsd.  
  
## LINQ to DataSet  
 [!INCLUDE[linq_dataset](../data-tools/includes/linq_dataset_md.md)] active [LINQ \(Language\-Integrated Query\)](../Topic/LINQ%20\(Language-Integrated%20Query\).md) sur les données dans un objet <xref:System.Data.DataSet>.  Pour plus d'informations, consultez [LINQ to DataSet](../Topic/LINQ%20to%20DataSet.md).  
  
## Voir aussi  
 [Procédure pas à pas : création d'un groupe de données avec le Concepteur de DataSet](../data-tools/walkthrough-creating-a-dataset-with-the-dataset-designer.md)   
 [Procédure pas à pas : création d'un TableAdapter avec plusieurs requêtes](../data-tools/walkthrough-creating-a-tableadapter-with-multiple-queries.md)   
 [Procédure pas à pas : création d'un DataTable dans le Concepteur de DataSet](../data-tools/walkthrough-creating-a-datatable-in-the-dataset-designer.md)   
 [Procédure pas à pas : création d'une relation entre des tables de données](../Topic/Walkthrough:%20Creating%20a%20Relationship%20between%20Data%20Tables.md)   
 [Procédure pas à pas : affichage de données sur un Windows Form](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)   
 [Sources de données \(fenêtre\)](../Topic/Data%20Sources%20Window.md)   
 [Utilisation de groupes de données dans Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)   
 [Préparation de votre application pour recevoir des données](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Extraction de données dans votre application](../data-tools/fetching-data-into-your-application.md)   
 [Modification des données dans votre application](../data-tools/editing-data-in-your-application.md)   
 [Validation des données](../Topic/Validating%20Data.md)   
 [Enregistrement des données](../data-tools/saving-data.md)