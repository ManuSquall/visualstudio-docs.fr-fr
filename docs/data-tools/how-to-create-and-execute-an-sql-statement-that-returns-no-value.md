---
title: "Comment&#160;: cr&#233;er et ex&#233;cuter une instruction SQL qui ne retourne aucune valeur | Microsoft Docs"
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
  - "appeler des méthodes, exemples"
  - "appels de méthode, exemples"
  - "instructions SQL, créer"
  - "instructions SQL, exécuter"
ms.assetid: 612d3046-0cfa-4d90-be6e-c4d6bcbd5aee
caps.latest.revision: 23
caps.handback.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Comment&#160;: cr&#233;er et ex&#233;cuter une instruction SQL qui ne retourne aucune valeur
Pour exécuter une instruction SQL qui ne retourne aucune valeur, vous pouvez lancer une requête TableAdapter configurée pour exécuter une instruction SQL \(par exemple, `CustomersTableAdapter.UpdateTableData(CustomersDataTable)`\).  
  
 Si votre application n'utilise pas de TableAdapters, appelez la méthode `ExecuteNonQuery` sur un objet de commande en affectant à sa propriété `CommandType` la valeur <xref:System.Data.CommandType>.  \(L'« objet de commande » fait référence à la commande spécifique au [fournisseur de données .NET Framework](../Topic/.NET%20Framework%20Data%20Providers.md) que votre application utilise.  Par exemple, si votre application utilise le fournisseur de données .NET Framework pour SQL Server, l'objet de commande est <xref:System.Data.SqlClient.SqlCommand>.\)  
  
 Les exemples suivants illustrent l'exécution d'instructions SQL qui ne retournent aucune valeur provenant d'une base de données à l'aide de TableAdapters ou d'objets de commande.  Pour plus d'informations sur la façon d'interroger à l'aide de TableAdapters et de commandes, consultez [Remplissage de groupes de données avec des données](../data-tools/fill-datasets-by-using-tableadapters.md).  
  
## Exécution d'instructions SQL qui ne retournent aucune valeur à l'aide d'un TableAdapter  
 Cet exemple illustre la création d'une requête TableAdapter à l'aide de l'[Configuration de requête TableAdapter \(Assistant\)](../data-tools/editing-tableadapters.md), puis fournit des informations sur la manière de déclarer une instance de TableAdapter et d'exécuter la requête.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### Pour créer une instruction SQL qui ne renvoie aucune valeur à l'aide d'un TableAdapter  
  
1.  Ouvrez un groupe de données dans le **Concepteur de DataSet**.  Pour plus d'informations, consultez [Comment : ouvrir un groupe de données dans le Concepteur de DataSet](../Topic/How%20to:%20Open%20a%20Dataset%20in%20the%20Dataset%20Designer.md).  
  
2.  S'il n'existe pas encore de TableAdapter, créez\-en un.  Pour plus d'informations sur la création de TableAdapters, consultez [Comment : créer des TableAdapters](../data-tools/create-and-configure-tableadapters.md).  
  
3.  Si vous disposez déjà dans votre TableAdapter d'une requête qui utilise une instruction SQL qui ne retourne aucune valeur, passez à la procédure suivante, « Pour déclarer une instance du TableAdapter et exécuter la requête ». Sinon, passez à l'étape 4 pour créer une nouvelle requête qui ne retourne aucune valeur.  
  
4.  Cliquez avec le bouton droit sur le TableAdapter de votre choix et utilisez le menu contextuel pour ajouter une requête.  
  
     L'**Assistant Configuration de requêtes TableAdapter** s'ouvre.  
  
5.  Conservez la valeur par défaut \(**Utiliser des instructions SQL**\), puis cliquez sur **Suivant**.  
  
6.  Choisissez l'option **UPDATE**, **INSERT** ou **DELETE**, puis cliquez sur **Suivant**.  
  
7.  Tapez votre instruction SQL ou utilisez le **Générateur de requêtes** pour vous aider à la créer, puis cliquez sur **Suivant**.  
  
8.  Spécifiez le nom de la requête.  
  
9. Une fois l'Assistant terminé, la requête est ajoutée au TableAdapter.  
  
10. Générez votre projet.  
  
#### Pour déclarer une instance du TableAdapter et exécuter la requête  
  
1.  Déclarez une instance du TableAdapter qui contient la requête que vous souhaitez exécuter.  
  
    -   Pour créer une instance qui utilise des outils de conception, faites glisser le TableAdapter de votre choix de la **Boîte à outils**.  \(Les composants contenus dans votre projet apparaissent maintenant dans la **Boîte à outils** sous un titre qui correspond à votre nom de projet.\) Si le TableAdapter n'est pas affiché dans la **Boîte à outils**, il se peut que vous deviez générer votre projet.  
  
         ou  
  
    -   Pour créer une instance dans du code, remplacez le code suivant par les noms de votre <xref:System.Data.DataSet> et de votre TableAdapter.  
  
         `Dim tableAdapter As New DataSetTableAdapters.TableAdapter`  
  
        > [!NOTE]
        >  Les TableAdapters ne se trouvent pas réellement à l'intérieur de leurs classes DataSet associées.  Chaque groupe de données possède une collection correspondante de TableAdapters dans son propre espace de noms.  Par exemple, si vous disposez d'un groupe de données nommé `SalesDataSet`, il existe un espace de noms `SalesDataSetTableAdapters` contenant ses TableAdapters.  
  
2.  Appelez votre requête comme s'il s'agissait de toute autre méthode dans du code.  Votre requête est une méthode sur le TableAdapter.  Remplacez le code suivant par les noms de votre TableAdapter et de votre requête.  Vous devez également passer tous les paramètres requis par votre requête.  Si vous ne savez pas si votre requête exige des paramètres, ni quels paramètres sont nécessaires, recherchez dans IntelliSense la signature nécessaire à la requête.  Selon que votre requête prend ou non des paramètres, le code peut se présenter comme l'un des exemples suivants :  
  
     `TableAdapter.Query()`  
  
     `TableAdapter.Query(Parameters)`  
  
     Les requêtes, dont nous pensons qu'elles ne retournent aucune valeur, retournent en réalité une valeur : un entier contenant le nombre de lignes affectées par la requête.  Le code complet permettant de déclarer une instance d'un TableAdapter et d'exécuter une requête doit se présenter sous la forme suivante :  
  
     [!code-cs[VbRaddataFillingAndExecuting#11](../data-tools/codesnippet/CSharp/how-to-create-and-execute-an-sql-statement-that-returns-no-value_1.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#11](../data-tools/codesnippet/VisualBasic/how-to-create-and-execute-an-sql-statement-that-returns-no-value_1.vb)]  
  
## Exécution d'instructions SQL qui ne retournent aucune valeur à l'aide d'un objet de commande  
 L'exemple suivant illustre la création d'une commande et l'exécution d'une instruction SQL qui ne retourne aucune valeur.  Pour plus d'informations sur la définition et l'obtention des valeurs de paramètre pour une commande, consultez [Comment : définir et obtenir des paramètres pour des objets de commande](../Topic/How%20to:%20Set%20and%20Get%20Parameters%20for%20Command%20Objects.md).  
  
 Cet exemple utilise l'objet <xref:System.Data.SqlClient.SqlCommand> et requiert les éléments suivants :  
  
-   des références aux espaces de noms <xref:System>, <xref:System.Data> et <xref:System.Xml> ;  
  
-   une connexion de données nommée `SqlConnection1` ;  
  
-   une table nommée `Customers` dans la source de données à laquelle `SqlConnection1` se connecte  \(sinon, vous avez besoin d'une instruction SQL valide pour votre source de données\).  
  
#### Pour exécuter une instruction SQL qui ne retourne aucune valeur à l'aide d'un DataCommand  
  
-   Ajoutez le code suivant à une méthode à partir de laquelle vous souhaitez exécuter l'instruction SQL.  Appelez la méthode `ExecuteNonQuery` d'une commande pour ne retourner aucune valeur \(par exemple, <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A?displayProperty=fullName>\).  
  
     [!code-cs[VbRaddataFillingAndExecuting#12](../data-tools/codesnippet/CSharp/how-to-create-and-execute-an-sql-statement-that-returns-no-value_2.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#12](../data-tools/codesnippet/VisualBasic/how-to-create-and-execute-an-sql-statement-that-returns-no-value_2.vb)]  
  
## Sécurité .NET Framework  
 L'application requiert l'autorisation d'accéder à la base de données et d'exécuter l'instruction SQL.  
  
## Voir aussi  
 <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A?displayProperty=fullName>   
 <xref:System.Data.OleDb.OleDbCommand.ExecuteNonQuery%2A?displayProperty=fullName>   
 <xref:System.Data.Odbc.OdbcCommand.ExecuteNonQuery%2A?displayProperty=fullName>   
 <xref:System.Data.OracleClient.OracleCommand.ExecuteNonQuery%2A?displayProperty=fullName>   
 [Comment : créer des requêtes TableAdapter](../data-tools/how-to-create-tableadapter-queries.md)   
 [Comment : modifier des requêtes TableAdapter](../data-tools/how-to-edit-tableadapter-queries.md)   
 [Comment : remplir de données un groupe de données](../data-tools/how-to-fill-a-dataset-with-data.md)   
 [Remplissage de groupes de données avec des données](../data-tools/fill-datasets-by-using-tableadapters.md)   
 [Comment : définir et obtenir des paramètres pour des objets de commande](../Topic/How%20to:%20Set%20and%20Get%20Parameters%20for%20Command%20Objects.md)