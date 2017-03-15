---
title: "Comment&#160;: cr&#233;er un groupe de donn&#233;es typ&#233; | Microsoft Docs"
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
  - "groupes de données (Visual Basic), créer"
  - "datasets typés, créer"
ms.assetid: 58f33b43-24e1-43b1-b08b-b74329960bd6
caps.latest.revision: 36
caps.handback.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Comment&#160;: cr&#233;er un groupe de donn&#233;es typ&#233;
Vous créez un <xref:System.Data.DataSet> typé à l'aide de l'**Assistant Configuration de source de données** ou du [Création et modification de Datasets typés](../data-tools/creating-and-editing-typed-datasets.md).  
  
> [!NOTE]
>  Pour plus d'informations sur la création de groupes de données par programme, consultez [Création d'un DataSet](../Topic/Creating%20a%20DataSet.md).  
  
## Création de groupes de données typés à l'aide de l'Assistant Configuration de source de données ou du Concepteur de DataSet  
  
#### Pour créer un groupe de données avec l'Assistant Configuration de source de données  
  
1.  Dans le menu **Données**, cliquez sur **Ajouter une nouvelle source de données** pour lancer l'**Assistant Configuration de source de données**.  
  
2.  Sélectionnez **Base de données** dans la page **Choisir un type de source de données**.  
  
3.  Lorsque vous exécutez l'Assistant, un groupe de données typé est ajouté à votre projet.  Pour plus d'informations, consultez [Configuration de source de données \(Assistant\)](../data-tools/media/data-source-configuration-wizard.png).  
  
#### Pour créer un groupe de données avec le Concepteur de DataSet  
  
1.  Dans le menu **Projet**, cliquez sur **Ajouter un nouvel élément**.  
  
2.  Sélectionnez **DataSet** dans la boîte de dialogue **Ajouter un nouvel élément**.  
  
3.  Tapez le nom à affecter au groupe de données.  
  
4.  Cliquez sur **Ajouter**.  
  
     Le groupe de données est ajouté au projet et s'ouvre dans le **Concepteur de DataSet**.  
  
5.  Faites glisser des éléments depuis l'onglet **DataSet** de la **Boîte à outils** jusqu'au concepteur.  Pour plus d'informations, consultez [Comment : modifier un groupe de données](../Topic/How%20to:%20Edit%20a%20Dataset.md).  
  
     ou  
  
     Faites glisser des éléments depuis une connexion active dans l'**Explorateur de serveurs**\/**Explorateur de bases de données** jusqu'au **Concepteur de DataSet**.  
  
## Voir aussi  
 [Procédure pas à pas : connexion à des données dans une base de données \(Windows Forms\)](../Topic/Walkthrough:%20Connecting%20to%20Data%20in%20a%20Database%20\(Windows%20Forms\).md)   
 [Création et modification de Datasets typés](../data-tools/creating-and-editing-typed-datasets.md)   
 [Comment : modifier un groupe de données](../Topic/How%20to:%20Edit%20a%20Dataset.md)   
 [TableAdapters](../Topic/TableAdapters.md)   
 [Relations dans les groupes de données](../data-tools/relationships-in-datasets.md)   
 [Utilisation de groupes de données dans Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)   
 [Préparation de votre application pour recevoir des données](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Connexion aux données dans Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Extraction de données dans votre application](../data-tools/fetching-data-into-your-application.md)