---
title: "Comment&#160;: ins&#233;rer de nouveaux enregistrements dans une base de donn&#233;es | Microsoft Docs"
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
  - "données (Visual Studio), enregistrer"
  - "bases de données, insérer de nouveaux enregistrements dans"
  - "enregistrements, insérer"
  - "enregistrer les données"
  - "TableAdapters, insérer de nouveaux enregistrements dans"
ms.assetid: ea118fff-69b1-4675-b79a-e33374377f04
caps.latest.revision: 11
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Comment&#160;: ins&#233;rer de nouveaux enregistrements dans une base de donn&#233;es
Pour insérer de nouveaux enregistrements dans une base de données, vous pouvez utiliser la méthode `TableAdapter.Update`, ou l'une des méthodes DBDirect \(spécifiquement la méthode `TableAdapter.Insert`\) du TableAdapter.  Pour plus d'informations, consultez [Vue d'ensemble de TableAdapter](../data-tools/tableadapter-overview.md).  
  
 Si votre application n'utilise pas de TableAdapters, vous pouvez faire appel à des objets de commande pour interagir et insérer de nouveaux enregistrements dans votre base de données \(par exemple, <xref:System.Data.SqlClient.SqlCommand>\).  
  
 Utilisez la méthode `TableAdapter.Update` lorsque votre application utilise des groupes de données pour stocker des données.  La méthode `Update` envoie toutes les modifications \(mises à jour, insertions et suppressions\) à la base de données.  
  
 Utilisez la méthode `TableAdapter.Insert` lorsque votre application utilise des objets pour stocker des données ou lorsque vous voulez mieux maîtriser la création d'enregistrements dans la base de données.  
  
 Si votre TableAdapter n'a pas de méthode `Insert`, cela signifie soit qu'il est configuré pour utiliser des procédures stockées soit que sa propriété `GenerateDBDirectMethods` a la valeur `false`.  Essayez de donner à la propriété `GenerateDBDirectMethods` du TableAdapter la valeur `true` à partir du [Concepteur de Dataset](../data-tools/creating-and-editing-typed-datasets.md) puis enregistrez le groupe de données pour régénérer le TableAdapter.  Si le TableAdapter n'a toujours pas de méthode `Insert`, la table ne fournit probablement pas assez d'informations de schéma pour faire la distinction entre des lignes individuelles \(par exemple, aucune clé primaire n'est définie sur la table\).  
  
## Insérer de nouveaux enregistrements à l'aide de TableAdapters  
 Les TableAdapters proposent différents moyens d'insérer de nouveaux enregistrements dans une base de données, selon les besoins de votre application.  
  
 Si votre application utilise des groupes de données pour stocker des données, il vous suffit d'ajouter de nouveaux enregistrements à la <xref:System.Data.DataTable> voulue dans le groupe de données, puis d'appeler la méthode `TableAdapter.Update`.  La méthode `TableAdapter.Update` prend tous les changements dans la <xref:System.Data.DataTable> et les envoie à la base de données \(y compris les enregistrements modifiés et supprimés\).  
  
#### Pour insérer de nouveaux enregistrements dans une base de données à l'aide de la méthode TableAdapter.Update  
  
1.  Ajoutez de nouveaux enregistrements à la <xref:System.Data.DataTable> voulue en créant un objet <xref:System.Data.DataRow> et en l'ajoutant à la collection <xref:System.Data.DataTable.Rows%2A>.  Pour plus d'informations, consultez [Comment : ajouter des lignes à un DataTable](../Topic/How%20to:%20Add%20Rows%20to%20a%20DataTable.md).  
  
2.  Après avoir ajouté à la <xref:System.Data.DataTable> les nouvelles lignes, appelez la méthode `TableAdapter.Update`.  Vous pouvez contrôler la quantité de données à mettre à jour en passant un  <xref:System.Data.DataSet> entier, un <xref:System.Data.DataTable>, un tableau de <xref:System.Data.DataRow>, ou une seule <xref:System.Data.DataRow>.  
  
     Le code suivant indique comment ajouter un nouvel enregistrement à une <xref:System.Data.DataTable> et appeler la méthode `TableAdapter.Update` pour enregistrer la nouvelle ligne dans la base de données.  \(Cet exemple utilise la table `Region` de la base de données Northwind.\)  
  
     [!code-vb[VbRaddataSaving#14](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_1.vb)]
     [!code-cs[VbRaddataSaving#14](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_1.cs)]  
  
 Si votre application utilise des objets pour stocker les données dans votre application, vous pouvez utiliser la méthode `TableAdapter.Insert` pour créer des lignes directement dans la base de données.  La méthode `Insert` accepte les valeurs individuelles pour chaque colonne en tant que paramètres.  L'appel à la méthode insère un nouvel enregistrement dans la base de données avec les valeurs de paramètre passées.  
  
 La procédure suivante utilise la table `Region` de la base de données Northwind en tant qu'exemple.  
  
#### Pour insérer de nouveaux enregistrements dans une base de données à l'aide de la méthode TableAdapter.Insert  
  
-   Appelez la méthode `Insert` du TableAdapter, en passant les valeurs pour chaque colonne en tant que paramètres.  
  
    > [!NOTE]
    >  Si vous n'avez pas d'instance disponible, instanciez le TableAdapter que vous voulez utiliser.  
  
     [!code-vb[VbRaddataSaving#15](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_2.vb)]
     [!code-cs[VbRaddataSaving#15](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_2.cs)]  
  
## Insérer de nouveaux enregistrements à l'aide d'objets de commande  
 L'exemple suivant insère de nouveaux enregistrements directement dans une base de données à l'aide d'objets de commande.  Pour plus d'informations concernant l'utilisation d'objets de commande pour exécuter des commandes et des procédures stockées, consultez [Extraction de données dans votre application](../data-tools/fetching-data-into-your-application.md).  
  
 La procédure suivante utilise la table `Region` de la base de données Northwind en tant qu'exemple.  
  
#### Pour insérer de nouveaux enregistrements dans une base de données à l'aide d'objets de commande  
  
-   Créez un objet de commande, définissez ses propriétés `Connection`, `CommandType` et `CommandText`.  
  
     [!code-vb[VbRaddataSaving#16](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_3.vb)]
     [!code-cs[VbRaddataSaving#16](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_3.cs)]  
  
## Sécurité .NET Framework  
 Vous devez avoir accès à la base de données à laquelle vous essayez de vous connecter, et détenir les autorisations permettant d'insérer des enregistrements dans la table voulue.  
  
## Voir aussi  
 [Comment : supprimer les enregistrements dans une base de données](../Topic/How%20to:%20Delete%20Records%20in%20a%20Database.md)   
 [Comment : mettre à jour les enregistrements dans une base de données](../data-tools/how-to-update-records-in-a-database.md)   
 [Comment : enregistrer les données d'un objet dans une base de données](../data-tools/save-data-from-an-object-to-a-database.md)   
 [Vue d'ensemble d'applications de données dans Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Connexion aux données dans Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Préparation de votre application pour recevoir des données](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Extraction de données dans votre application](../data-tools/fetching-data-into-your-application.md)   
 [Liaison de contrôles à des données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modification des données dans votre application](../data-tools/editing-data-in-your-application.md)   
 [Validation des données](../Topic/Validating%20Data.md)   
 [Enregistrement des données](../data-tools/saving-data.md)   
 [Extraction des valeurs de champs Identité ou NuméroAuto](../Topic/Retrieving%20Identity%20or%20Autonumber%20Values.md)