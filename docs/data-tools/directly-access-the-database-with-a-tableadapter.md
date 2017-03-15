---
title: "Comment&#160;: acc&#233;der directement &#224; la base de donn&#233;es avec un TableAdapter | Microsoft Docs"
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
  - "données (Visual Studio), enregistrer"
  - "bases de données (Visual Basic), accéder avec un TableAdapter"
  - "groupes de données (Visual Basic), ajouter aux projets"
  - "DBDirect (méthodes)"
  - "GenerateDbDirectMethods (propriété)"
  - "enregistrer les données"
  - "TableAdapter.Delete (méthode)"
  - "TableAdapter.GenerateDBDirectMethods (propriété)"
  - "TableAdapter.Insert (méthode)"
  - "TableAdapter.Update (méthode)"
  - "TableAdapters"
ms.assetid: 012c5924-91f7-4790-b2a6-f51402b7014b
caps.latest.revision: 12
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Comment&#160;: acc&#233;der directement &#224; la base de donn&#233;es avec un TableAdapter
Outre `InsertCommand`, `UpdateCommand` et `DeleteCommand`, les TableAdapters sont créés avec des méthodes qui peuvent être exécutées directement sur la base de données.  Ces méthodes \(`TableAdapter.Insert`, `TableAdapter.Update` et `TableAdapter.Delete`\) peuvent être appelées directement pour manipuler des données dans la base de données.  
  
 Si vous ne souhaitez pas créer ces méthodes directes, affectez à la propriété `GenerateDbDirectMethods` du la valeur `false` dans la fenêtre **Propriétés**.  Toutes les requêtes ajoutées à un TableAdapter en plus de la requête de principal du TableAdapter sont des requêtes autonomes \- elles ne génèrent pas ces méthodes DbDirect.  
  
## Envoi direct de la commande à une base de données  
 Appelez la méthode DbDirect du TableAdapter qui exécute la tâche vous tentez d'accomplir.  
  
#### Pour insérer directement de nouveaux enregistrements dans une base de données  
  
-   Appelez la méthode `Insert` du TableAdapter, en passant les valeurs pour chaque colonne en tant que paramètres.  La procédure suivante utilise la table `Region` de la base de données Northwind en tant qu'exemple.  
  
    > [!NOTE]
    >  Si vous n'avez pas d'instance disponible, instanciez le TableAdapter que vous voulez utiliser.  
  
     [!code-vb[VbRaddataSaving#15](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_1.vb)]
     [!code-cs[VbRaddataSaving#15](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_1.cs)]  
  
#### Pour mettre à jour directement des enregistrements dans une base de données  
  
-   Appelez la méthode `Update` du TableAdapter, en passant les valeurs nouvelles et d'origine pour chaque colonne en tant que paramètres.  
  
    > [!NOTE]
    >  Si vous n'avez pas d'instance disponible, instanciez le TableAdapter que vous voulez utiliser.  
  
     [!code-vb[VbRaddataSaving#18](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_2.vb)]
     [!code-cs[VbRaddataSaving#18](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_2.cs)]  
  
#### Pour supprimer directement des enregistrements d'une base de données  
  
-   Appelez la méthode `Delete` du TableAdapter, en passant les valeurs pour chaque colonne en tant que paramètres de la méthode `Delete`.  \(Cet exemple utilise la table `Region` de la base de données Northwind.\)  
  
    > [!NOTE]
    >  Si vous n'avez pas d'instance disponible, instanciez le TableAdapter que vous voulez utiliser.  
  
     [!code-vb[VbRaddataSaving#21](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_3.vb)]
     [!code-cs[VbRaddataSaving#21](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_3.cs)]  
  
## Voir aussi  
 [Vue d'ensemble d'applications de données dans Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Connexion aux données dans Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Préparation de votre application pour recevoir des données](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Extraction de données dans votre application](../data-tools/fetching-data-into-your-application.md)   
 [Liaison de contrôles à des données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modification des données dans votre application](../data-tools/editing-data-in-your-application.md)   
 [Validation des données](../Topic/Validating%20Data.md)   
 [Enregistrement des données](../data-tools/saving-data.md)   
 [Vue d'ensemble de TableAdapter](../data-tools/tableadapter-overview.md)   
 [Commandes et paramètres](../Topic/Commands%20and%20Parameters.md)