---
title: "Comment&#160;: d&#233;marrer l&#39;Assistant Configuration de TableAdapter | Microsoft Docs"
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
  - "Configuration de TableAdapter (Assistant)"
  - "TableAdapters, Assistant Configuration"
ms.assetid: 301f2dcd-ed72-4229-80ef-3b59cb062d5d
caps.latest.revision: 11
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Comment&#160;: d&#233;marrer l&#39;Assistant Configuration de TableAdapter
L'**Assistant Configuration de TableAdapter** crée et modifie les TableAdapters dans les datasets fortement typés.  L'Assistant crée des TableAdapters basés sur des instructions SQL que vous entrez dans l'Assistant ou sur des procédures stockées existantes dans la base de données.  L'Assistant peut également créer des procédures stockées dans la base de données en fonction des instructions SQL que vous y entrez.  
  
### Pour démarrer l'Assistant Configuration de TableAdapter afin de créer un TableAdapter  
  
1.  Ouvrez votre dataset dans le **Concepteur de DataSet**.  Pour plus d'informations, consultez [Comment : ouvrir un groupe de données dans le Concepteur de DataSet](../Topic/How%20to:%20Open%20a%20Dataset%20in%20the%20Dataset%20Designer.md).  
  
    > [!NOTE]
    >  Si vous ne disposez pas de dataset dans votre projet, consultez [Comment : créer un groupe de données typé](../data-tools/create-and-configure-datasets-in-visual-studio.md).  
  
2.  Si vous créez un TableAdapter, faites glisser un objet **TableAdapter** depuis l'onglet **DataSet** de la **Boîte à outils** vers le **Concepteur de DataSet**.  
  
3.  Dans la page **Choisir votre connexion de données**, sélectionnez une connexion de données dans la liste de connexions actuellement disponibles ou sélectionnez **Nouvelle connexion** pour en créer une.  
  
### Pour démarrer l'Assistant Configuration de TableAdapter afin de modifier un TableAdapter existant  
  
1.  Ouvrez votre dataset dans le **Concepteur de DataSet**.  Pour plus d'informations, consultez [Comment : ouvrir un groupe de données dans le Concepteur de DataSet](../Topic/How%20to:%20Open%20a%20Dataset%20in%20the%20Dataset%20Designer.md).  
  
2.  Cliquez avec le bouton droit sur le TableAdapter dans le **Concepteur de DataSet** et choisissez **Configurer**.  L'Assistant s'ouvre sur la page **Générer les instructions SQL** ou la page **Lier des commandes aux procédures stockées existantes**, selon la façon dont le TableAdapter a été initialement configuré.  
  
3.  Terminez l'Assistant.  
  
## Voir aussi  
 [Procédures pas à pas relatives aux données](../Topic/Data%20Walkthroughs.md)   
 [Liaison de contrôles Windows Forms à des données dans Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Vue d'ensemble de TableAdapter](../data-tools/tableadapter-overview.md)   
 [Création et modification de Datasets typés](../data-tools/creating-and-editing-typed-datasets.md)   
 [Vue d'ensemble des sources de données](../data-tools/add-new-data-sources.md)   
 [Comment : établir une connexion à des données d'une base de données](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [Validation des données](../Topic/Validating%20Data.md)   
 [Comment : trier et filtrer des données ADO.NET avec le composant BindingSource Windows Forms](../Topic/How%20to:%20Sort%20and%20Filter%20ADO.NET%20Data%20with%20the%20Windows%20Forms%20BindingSource%20Component.md)   
 [Comment : créer une table de correspondance avec le composant BindingSource Windows Forms](../Topic/How%20to:%20Create%20a%20Lookup%20Table%20with%20the%20Windows%20Forms%20BindingSource%20Component.md)   
 [Procédure pas à pas : affichage de données sur un Windows Form](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)