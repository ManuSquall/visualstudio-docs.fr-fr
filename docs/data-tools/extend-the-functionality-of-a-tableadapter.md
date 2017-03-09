---
title: "Comment&#160;: &#233;tendre les fonctionnalit&#233;s d&#39;un TableAdapter | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
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
  - "données (Visual Studio), étendre des TableAdapters"
  - "données (Visual Studio), TableAdapters"
  - "TableAdapters, ajouter une fonctionnalité"
ms.assetid: 418249c8-c7f3-47ef-a94c-744cb6fe6aaf
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Comment&#160;: &#233;tendre les fonctionnalit&#233;s d&#39;un TableAdapter
Vous pouvez étendre les fonctionnalités d'un TableAdapter en ajoutant du code au fichier de classe partielle du TableAdapter.  
  
 Le code qui définit un TableAdapter est régénéré lorsque des modifications sont apportées au TableAdapter \(dans le **Concepteur de Dataset**\) ou lorsque des modifications sont apportées lors de l'exécution d'un Assistant qui modifie la configuration d'un TableAdapter.  Pour empêcher la suppression de votre code pendant la régénération d'un TableAdapter, ajoutez le code au fichier de classe partielle de ce dernier.  
  
 \(Les classes partielles permettent la répartition du code pour une classe spécifique parmi plusieurs fichiers physiques.  Pour plus d'informations, consultez [Partial](/dotnet/visual-basic/language-reference/modifiers/partial) ou [partiel, Type](/dotnet/csharp/language-reference/keywords/partial-type).\)  
  
## Localisation de TableAdapters dans le code  
 Alors que les TableAdapters sont créés à l'aide du **Concepteur de DataSet**, les classes TableAdapter générées ne sont pas créées en tant que classes imbriquées du <xref:System.Data.DataSet>.  Les TableAdapters se trouvent dans un espace de noms basé sur le nom du groupe de données associé du TableAdapter.  Par exemple, si votre application contient un groupe de données nommé `HRDataSet`, les TableAdapters se trouvent dans l'espace de noms `HRDataSetTableAdapters`.  \(La convention d'affectation de noms suit ce modèle : *NomGroupeDonnées* \+ `TableAdapters`\).  
  
 L'exemple suivant suppose un TableAdapter nommé `CustomersTableAdapter` dans un projet avec un `NorthwindDataSet`.  
  
#### Pour créer une classe partielle pour un TableAdapter  
  
1.  Ajoutez une nouvelle classe à votre projet en sélectionnant **Ajouter une classe** dans le menu **Projet**.  
  
2.  Nommez la classe `CustomersTableAdapterExtended`.  
  
3.  Cliquez sur **Ajouter**.  
  
4.  Remplacez le code par l'espace de noms adéquat et le nom de classe partiel de votre projet.  Par exemple :  
  
     [!CODE [VbRaddataTableAdapters#2](../CodeSnippet/VS_Snippets_VBCSharp/VbRaddataTableAdapters#2)]  
  
## Voir aussi  
 [Vue d'ensemble de TableAdapter](../data-tools/tableadapter-overview.md)   
 [Comment : créer des TableAdapters](../data-tools/create-and-configure-tableadapters.md)   
 [Comment : créer des requêtes TableAdapter](../data-tools/how-to-create-tableadapter-queries.md)   
 [Comment : étendre les fonctionnalités d'un groupe de données](../Topic/How%20to:%20Extend%20the%20Functionality%20of%20a%20Dataset.md)   
 [Procédures pas à pas relatives aux données](../Topic/Data%20Walkthroughs.md)   
 [Liaison de contrôles Windows Forms à des données dans Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Vue d'ensemble d'applications de données dans Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Connexion aux données dans Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Préparation de votre application pour recevoir des données](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Extraction de données dans votre application](../data-tools/fetching-data-into-your-application.md)   
 [Liaison de contrôles à des données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modification des données dans votre application](../data-tools/editing-data-in-your-application.md)   
 [Validation des données](../Topic/Validating%20Data.md)   
 [Enregistrement des données](../data-tools/saving-data.md)