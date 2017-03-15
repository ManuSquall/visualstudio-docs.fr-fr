---
title: "Comment&#160;: mettre &#224; jour les enregistrements dans une base de donn&#233;es | Microsoft Docs"
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
  - "données (Visual Studio), enregistrer"
  - "bases de données, mettre à jour"
  - "enregistrements, modifier"
  - "enregistrements, mettre à jour"
  - "TableAdapter.Update (méthode)"
ms.assetid: cdc8a8e4-a5fa-40dd-9221-97b8571d802a
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Comment&#160;: mettre &#224; jour les enregistrements dans une base de donn&#233;es
Vous pouvez utiliser la méthode `TableAdapter.Update` pour mettre à jour \(modifier\) les enregistrements d'une base de données.  La méthode `TableAdapter.Update` fournit plusieurs surcharges qui exécutent des opérations différentes selon les paramètres passées dans.  Il est important de comprendre les résultats de l'appel de ces signatures de méthode différentes.  
  
> [!NOTE]
>  Si votre application n'utilise pas de TableAdapters, vous pouvez utiliser des objets de commande pour mettre à jour des enregistrements dans votre base de données \(par exemple, <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A>\).  Pour plus d'informations sur la mise à jour de données avec des objets de commande, consultez « Mettre à jour des enregistrements à l'aide d'objets de commande » ci\-dessous.  
  
 Le tableau suivant décrit le comportement des diverses méthodes `TableAdapter.Update` :  
  
|Méthode|Description|  
|-------------|-----------------|  
|`TableAdapter.Update(DataTable)`|Essaie d'enregistrer toutes les modifications apportées à la <xref:System.Data.DataTable> dans la base de données.  \(Cela inclut la suppression des lignes supprimées de la table, l'ajout de lignes insérées à la table et la mise à jour de lignes de la table qui ont changé.\)|  
|`TableAdapter.Update(DataSet)`|Bien que le paramètre prenne un groupe de données, le TableAdapter essaie d'enregistrer toutes les modifications du TableAdapter <xref:System.Data.DataTable> associé dans la base de données.  \(Cela inclut la suppression des lignes supprimées de la table, l'ajout de lignes insérées à la table et la mise à jour de lignes de la table qui ont changé.\) **Note:**  La <xref:System.Data.DataTable> associée d'un TableAdapter est la <xref:System.Data.DataTable> créée lors de la configuration initiale du TableAdapter.|  
|`TableAdapter.Update(DataRow)`|Tente d'enregistrer les modifications dans l'objet <xref:System.Data.DataRow> indiqué dans la base de données.|  
|`TableAdapter.Update(DataRows())`|Tente d'enregistrer les modifications apportées à une ligne du tableau de <xref:System.Data.DataRow> dans la base de données.|  
|`TableAdapter.Update("new column values", "original column values")`|Tente d'enregistrer les modifications apportées à une seule ligne qui est identifiée par les valeurs des colonnes d'origine.|  
  
 Vous utilisez en général la méthode `TableAdapter.Update` qui prend un <xref:System.Data.DataSet>, <xref:System.Data.DataTable> ou <xref:System.Data.DataRow> lorsque votre application utilise des groupes de données exclusivement pour stocker des données.  
  
 Vous utilisez en général la méthode `TableAdapter.Update` qui prend des valeurs de colonne lorsque votre application utilise des objets pour stocker des données.  
  
 Si votre TableAdapter n'a pas une méthode `Update` qui prend des valeurs de colonne, cela signifie que le TableAdapter est configuré pour utiliser des procédures stockées ou que sa propriété `GenerateDBDirectMethods` a la valeur `false`.  Essayez de donner à la propriété `GenerateDBDirectMethods` du TableAdapter la valeur `true` à partir du [Concepteur de Dataset](../data-tools/creating-and-editing-typed-datasets.md) puis enregistrez le groupe de données pour régénérer le TableAdapter.  Si le TableAdapter n'a pas encore une méthode `Update` qui prend des valeurs de colonne, la table ne fournit probablement pas assez d'informations de schéma pour faire la distinction entre des lignes individuelles \(par exemple, aucune clé primaire n'est définie sur la table\).  
  
## Mise à jour d'enregistrements existants à l'aide de TableAdapters  
 Les TableAdapters offrent des moyens différents de mettre à jour les enregistrements d'une base de données en fonction des besoins de votre application.  
  
 Si votre application utilise des datasets pour stocker des données, il vous suffit de mettre à jour les enregistrements dans la <xref:System.Data.DataTable> voulue, puis d'appeler la méthode `TableAdapter.Update` et de passer <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, <xref:System.Data.DataRow> ou un tableau de <xref:System.Data.DataRow>.  Le tableau ci\-dessus décrit les méthodes `Update` différentes.  
  
#### Pour mettre à jour des enregistrements dans une base de données avec la méthode TableAdapter.Update qui prend DataSet, DataTable, DataRow ou DataRows \(\)  
  
1.  Modifiez les enregistrements dans la <xref:System.Data.DataTable> voulue en modifiant directement <xref:System.Data.DataRow> dans <xref:System.Data.DataTable>.  Pour plus d'informations, consultez [Comment : modifier des lignes dans un DataTable](../Topic/How%20to:%20Edit%20Rows%20in%20a%20DataTable.md).  
  
2.  Après avoir modifié les lignes de <xref:System.Data.DataTable>, appelez la méthode `TableAdapter.Update`.  Vous pouvez contrôler la quantité de données à mettre à jour en passant un  <xref:System.Data.DataSet> entier, un <xref:System.Data.DataTable>, un tableau de <xref:System.Data.DataRow>, ou une seule <xref:System.Data.DataRow>.  
  
     Le code suivant indique comment modifier un enregistrement dans une <xref:System.Data.DataTable> puis appeler la méthode `TableAdapter.Update` pour enregistrer les modifications dans la base de données.  \(Cet exemple utilise la table Region de la base de données Northwind.\)  
  
     [!code-vb[VbRaddataSaving#17](../data-tools/codesnippet/VisualBasic/how-to-update-records-in-a-database_1.vb)]
     [!code-cs[VbRaddataSaving#17](../data-tools/codesnippet/CSharp/how-to-update-records-in-a-database_1.cs)]  
  
 Si votre application utilise des objets pour stocker les données de votre application, vous pouvez utiliser les méthodes `DBDirect` du TableAdapter pour envoyer des données directement de vos objets à la base de données.  Ces méthodes vous permettent de passer des valeurs individuelles pour chaque colonne en tant que paramètres de méthode.  L'appel à cette méthode met à jour un enregistrement existant dans la base de données avec les valeurs de colonne passées dans la méthode.  
  
 La procédure suivante utilise la table `Region` de Northwind en tant qu'exemple.  
  
#### Pour mettre à jour des enregistrements d'une base de données à l'aide de la méthode TableAdapter.Update qui prend des valeurs de colonne  
  
-   Appelez la méthode `Update` du TableAdapter, en passant les valeurs nouvelles et d'origine pour chaque colonne en tant que paramètres.  
  
    > [!NOTE]
    >  Si vous n'avez pas d'instance disponible, instanciez le TableAdapter que vous voulez utiliser.  
  
     [!code-vb[VbRaddataSaving#18](../data-tools/codesnippet/VisualBasic/how-to-update-records-in-a-database_2.vb)]
     [!code-cs[VbRaddataSaving#18](../data-tools/codesnippet/CSharp/how-to-update-records-in-a-database_2.cs)]  
  
## Mettre à jour des enregistrements à l'aide d'objets de commande  
 L'exemple suivant met à jour des enregistrements existants directement dans une base de données à l'aide d'objets de commande.  Pour plus d'informations concernant l'utilisation d'objets de commande pour exécuter des commandes et des procédures stockées, consultez [Extraction de données dans votre application](../data-tools/fetching-data-into-your-application.md).  
  
 La procédure suivante utilise la table `Region` de Northwind en tant qu'exemple.  
  
#### Pour mettre à jour des enregistrements existants dans une base de données à l'aide d'objets de commande  
  
-   Créez un objet de commande ; définissez ses propriétés `Connection`, `CommandType` et `CommandText`, puis ouvrez une connexion et exécutez la commande.  
  
     [!code-vb[VbRaddataSaving#19](../data-tools/codesnippet/VisualBasic/how-to-update-records-in-a-database_3.vb)]
     [!code-cs[VbRaddataSaving#19](../data-tools/codesnippet/CSharp/how-to-update-records-in-a-database_3.cs)]  
  
## Sécurité .NET Framework  
 Vous devez avoir accès à la base de données à laquelle vous essayez de vous connecter, et détenir les autorisations permettant de mettre à jour des enregistrements dans la table voulue.  
  
## Voir aussi  
 [Vue d'ensemble de TableAdapter](../data-tools/tableadapter-overview.md)   
 [Comment : supprimer les enregistrements dans une base de données](../Topic/How%20to:%20Delete%20Records%20in%20a%20Database.md)   
 [Comment : insérer de nouveaux enregistrements dans une base de données](../data-tools/insert-new-records-into-a-database.md)   
 [Comment : enregistrer les données d'un objet dans une base de données](../data-tools/save-data-from-an-object-to-a-database.md)   
 [Vue d'ensemble d'applications de données dans Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Connexion aux données dans Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Préparation de votre application pour recevoir des données](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Extraction de données dans votre application](../data-tools/fetching-data-into-your-application.md)   
 [Liaison de contrôles à des données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modification des données dans votre application](../data-tools/editing-data-in-your-application.md)   
 [Validation des données](../Topic/Validating%20Data.md)   
 [Enregistrement des données](../data-tools/saving-data.md)