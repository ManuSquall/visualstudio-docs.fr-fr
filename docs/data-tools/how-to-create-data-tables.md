---
title: "Comment&#160;: cr&#233;er des tables de donn&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Microsoft.VSDesigner.DataSource.DesignTable"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "données (Visual Studio), créer des tables de données"
  - "Concepteur de DataSet, créer des tables de données"
  - "tables (Visual Studio), créer"
ms.assetid: 0e8bf4c4-3d05-4b20-9926-9d29914b26ed
caps.latest.revision: 19
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Comment&#160;: cr&#233;er des tables de donn&#233;es
Les données peuvent être stockées en mémoire dans des objets <xref:System.Data.DataTable>. \(Les groupes de données sont composés d'objets <xref:System.Data.DataTable>.\) Vous créez généralement de nouvelles tables à l'aide de TableAdapters avec [Configuration de TableAdapter \(Assistant\)](../Topic/TableAdapter%20Configuration%20Wizard.md) ou en faisant glisser des objets de base de données depuis l'**Explorateur de serveurs** jusqu'au **Concepteur de DataSet**.  
  
 Les tables de données sont créées comme un sous\-produit lorsque vous créez également TableAdapters dans le [Configuration de source de données \(Assistant\)](../data-tools/media/data-source-configuration-wizard.png), mais elles peuvent également être créées indépendamment.  Pour créer une table de données autonome, faites glisser un objet <xref:System.Data.DataTable> depuis l'onglet **Données** de la **Boîte à outils** jusqu'au **Concepteur de DataSet**.  
  
> [!NOTE]
>  Pour créer des tables de données par programme, consultez [Création d'un DataTable](../Topic/Creating%20a%20DataTable.md).  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## Création d'un DataTable avec un TableAdapter  
 Les tables de données avec TableAdapters comprennent des méthodes qui remplissent la table à l'aide de données et écrivent les modifications dans la base de données.  Pour créer des TableAdapters, exécutez l'**Assistant Configuration de TableAdapter** ou faites glisser des objets de base de données depuis l'**Explorateur de serveurs** jusqu'au **Concepteur de DataSet**.  
  
#### Pour créer une nouvelle table de données avec un TableAdapter  
  
1.  Ouvrez votre groupe de données dans le **Concepteur de DataSet**.  Pour plus d'informations, consultez [Comment : ouvrir un groupe de données dans le Concepteur de DataSet](../Topic/How%20to:%20Open%20a%20Dataset%20in%20the%20Dataset%20Designer.md).  
  
2.  Faites glisser un **TableAdapter** depuis l'onglet **DataSet** de la **Boîte à outils** jusqu'au **Concepteur de DataSet**.  
  
     L'**Assistant Configuration de TableAdapter** s'ouvre.  
  
3.  Complétez l'Assistant.  Pour plus d’informations, consultez [Configuration de TableAdapter \(Assistant\)](../Topic/TableAdapter%20Configuration%20Wizard.md)  
  
#### Pour créer une nouvelle table de données avec un TableAdapter à partir de l'Explorateur de serveurs  
  
1.  Ouvrez votre groupe de données dans le **Concepteur de source de données**.  
  
2.  Faites glisser un objet de base de données \(par exemple, une table\) depuis l'**Explorateur de serveurs** jusqu'au **Concepteur de DataSet**.  
  
## Création d'un DataTable autonome  
 La logique `Fill` doit être implémentée dans les tables autonomes pour pouvoir les remplir de données.  Pour plus d'informations sur le remplissage de tables de données autonomes, consultez [Remplissage d'un DataSet à partir d'un DataAdapter](../Topic/Populating%20a%20DataSet%20from%20a%20DataAdapter.md).  
  
#### Pour créer une nouvelle table de données autonome  
  
1.  Ouvrez votre groupe de données dans le **Concepteur de DataSet**.  
  
2.  Faites glisser un <xref:System.Data.DataTable> depuis l'onglet **Données** de la **Boîte à outils** jusqu'au **Concepteur de DataSet**.  
  
3.  Ajoutez des colonnes pour définir votre table de données.  Pour plus d'informations, consultez [Comment : ajouter des colonnes à un DataTable](../Topic/How%20to:%20Add%20Columns%20to%20a%20DataTable.md).  
  
## Voir aussi  
 <xref:System.Data.DataTable>   
 [Procédures pas à pas relatives aux données](../Topic/Data%20Walkthroughs.md)   
 [Procédure pas à pas : affichage de données sur un Windows Form](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)   
 [Vue d'ensemble de TableAdapter](../data-tools/tableadapter-overview.md)   
 [Création et modification de Datasets typés](../data-tools/creating-and-editing-typed-datasets.md)   
 [Vue d'ensemble des sources de données](../data-tools/add-new-data-sources.md)   
 [Sources de données \(fenêtre\)](../Topic/Data%20Sources%20Window.md)   
 [Comment : établir une connexion à des données d'une base de données](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [Validation des données](../Topic/Validating%20Data.md)