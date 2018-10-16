---
title: 'Comment : exécuter une procédure stockée qui retourne une valeur unique | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CommandType.StoredProcedure
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- ExecuteReader method example [Visual Basic]
- stored procedures, examples
- stored procedures, executing
ms.assetid: ecf8c262-58ca-4a69-a82c-916c0c061422
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 2c27c8e0fca1393e097f1244a01988052911f73a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49281006"
---
# <a name="how-to-execute-a-stored-procedure-that-returns-a-single-value"></a>Comment : exécuter une procédure stockée qui retourne une seule valeur
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pour exécuter une procédure stockée qui retourne une valeur unique, vous pouvez exécuter la requête de TableAdapter est configuré pour exécuter une procédure stockée (par exemple, `CustomersTableAdapter.CustomerCount()`).  
  
 Si votre application n’utilise pas les TableAdapters, appelez le `ExecuteScalar` méthode sur un objet de commande, en définissant son `CommandType` propriété <xref:System.Data.CommandType>. (« Objet de commande » fait référence à la commande spécifique pour le [.NET Framework Data Provider](http://msdn.microsoft.com/library/03a9fc62-2d24-491a-9fe6-d6bdb6dcb131) à l’aide de votre application. Par exemple, si votre application utilise le fournisseur de données .NET Framework pour SQL Server, l’objet de commande serait <xref:System.Data.SqlClient.SqlCommand>.)  
  
 Les exemples suivants montrent comment exécuter des procédures stockées qui retournent des valeurs uniques à partir d’une base de données à l’aide de TableAdapters ou d’objets de commande. Pour plus d’informations sur l’interrogation avec les TableAdapters et de commandes, consultez [remplir des jeux de données à l’aide de TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md).  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="executing-stored-procedures-that-return-single-values-using-a-tableadapter"></a>L’exécution de procédures stockées qui retournent des valeurs uniques à l’aide d’un TableAdapter  
 Cet exemple montre comment créer une requête TableAdapter en utilisant le [modification des TableAdapters](../data-tools/editing-tableadapters.md), et il fournit des informations sur la façon de déclarer une instance du TableAdapter et exécuter la requête.  
  
#### <a name="to-execute-a-stored-procedure-that-returns-a-single-value-using-a-tableadapter"></a>Pour exécuter une procédure stockée qui retourne une valeur unique à l’aide d’un TableAdapter  
  
1.  Ouvrez un dataset dans le **Concepteur de Dataset**. Pour plus d’informations, consultez [Comment : ouvrir un jeu de données dans le Concepteur de Dataset](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2.  Si vous n’en avez pas déjà, créez un TableAdapter. Pour plus d’informations sur la création des TableAdapters, consultez [créer et configurer des TableAdapters](../data-tools/create-and-configure-tableadapters.md).  
  
3.  Si vous avez déjà une requête sur votre TableAdapter qui utilise une procédure stockée pour retourner une valeur unique, passez à la procédure suivante, « pour déclarer une instance du TableAdapter et exécuter la requête. » Sinon, passez à l’étape 4 pour créer une nouvelle requête qui retourne une valeur unique.  
  
4.  Cliquez sur le TableAdapter que vous souhaitez, puis utilisez le menu contextuel pour ajouter une requête.  
  
     Le **Assistant Configuration de requêtes TableAdapter** s’ouvre.  
  
5.  Sélectionnez **utiliser la procédure stockée existante**, puis cliquez sur **suivant**.  
  
6.  Sélectionnez une procédure stockée dans la liste déroulante, puis cliquez sur **suivant**.  
  
7.  Sélectionnez l’option permettant de retourner **une seule valeur**, puis cliquez sur **suivant**.  
  
8.  Fournissez un nom pour la requête.  
  
9. Cliquez sur **suivant** ou **Terminer** pour terminer l’Assistant ; la requête est ajoutée au TableAdapter.  
  
10. Générez votre projet.  
  
#### <a name="to-declare-an-instance-of-the-tableadapter-and-execute-the-query"></a>Pour déclarer une instance du TableAdapter et exécuter la requête  
  
1.  Déclarez une instance du TableAdapter qui contient la requête que vous souhaitez exécuter.  
  
    -   Pour créer une instance à l’aide des outils de conception, faites glisser le TableAdapter de votre choix à partir de la **boîte à outils**. (Les composants dans votre projet apparaissent maintenant dans le **boîte à outils** sous un titre qui correspond au nom de votre projet.) Si le TableAdapter n’apparaît pas dans le **boîte à outils**, vous pouvez être amené à générer votre projet.  
  
         - ou -  
  
    -   Pour créer une instance dans le code, remplacez le code suivant avec les noms de votre <xref:System.Data.DataSet> et TableAdapter.  
  
         `Dim tableAdapter As New DataSetTableAdapters.TableAdapter`  
  
        > [!NOTE]
        >  Les TableAdapters ne se trouvent pas réellement à l’intérieur de leurs classes de jeu de données associé. Chaque jeu de données possède une collection correspondante de TableAdapters dans son propre espace de noms. Par exemple, si vous disposez d’un dataset nommé `SalesDataSet`, il n’y aurait un `SalesDataSetTableAdapters` espace de noms contenant ses TableAdapters.  
  
2.  Appelez votre requête comme vous appelleriez toute autre méthode dans le code. Votre requête est une méthode sur le TableAdapter. Remplacez le code suivant avec les noms de votre TableAdapter et de requête. Vous devez également passer tous les paramètres requis par votre requête. Si vous ne savez pas si votre requête requiert des paramètres, ou quels paramètres sont nécessaires, puis recherchez IntelliSense la signature requise de la requête. Selon que votre requête prend des paramètres ou non, le code ressemblerait à un des exemples suivants :  
  
     `TableAdapter.Query()`  
  
     `TableAdapter.Query(Parameters)`  
  
     Le code complet pour déclarer une instance du TableAdapter et exécuter la requête doit ressembler à ce qui suit :  
  
     [!code-csharp[VbRaddataFillingAndExecuting#9](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form2.cs#9)]
     [!code-vb[VbRaddataFillingAndExecuting#9](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form2.vb#9)]  
  
## <a name="executing-stored-procedures-that-return-single-values-using-a-command-object"></a>L’exécution de procédures stockées qui retournent des valeurs uniques à l’aide d’un objet de commande  
 L’exemple suivant montre comment créer une commande et exécuter une procédure stockée qui retourne une valeur unique. Pour plus d’informations sur la définition et l’obtention des valeurs de paramètre pour une commande, consultez [Comment : définir et obtenir des paramètres pour les objets de commande](http://msdn.microsoft.com/library/10110ecc-d2ed-4796-bb8f-74f2ecd40787).  
  
 Cet exemple utilise le <xref:System.Data.SqlClient.SqlCommand> de l’objet et nécessite :  
  
-   Fait référence à la <xref:System>, <xref:System.Data>, et <xref:System.Xml> espaces de noms.  
  
-   Une connexion de données nommée `SqlConnection1`.  
  
-   Une table nommée `Customers` dans les données source qui `SqlConnection1` se connecte à. (Sinon, vous avez besoin une instruction SQL valide pour votre source de données).  
  
#### <a name="to-execute-a-stored-procedure-that-returns-a-single-value-using-a-datacommand"></a>Pour exécuter une procédure stockée qui retourne une valeur unique à l’aide d’un DataCommand  
  
-   Ajoutez le code suivant à une méthode que vous souhaitez exécuter le code à partir de. Retourner des valeurs uniques en appelant le `ExecuteScalar` d’une commande (méthode) (par exemple, <xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A>). Les données sont retournées dans un `object`.  
  
     [!code-csharp[VbRaddataFillingAndExecuting#14](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form2.cs#14)]
     [!code-vb[VbRaddataFillingAndExecuting#14](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form2.vb#14)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A?displayProperty=fullName>   
 <xref:System.Data.OleDb.OleDbCommand.ExecuteScalar%2A?displayProperty=fullName>   
 <xref:System.Data.Odbc.OdbcCommand.ExecuteScalar%2A?displayProperty=fullName>   
 <xref:System.Data.OracleClient.OracleCommand.ExecuteScalar%2A?displayProperty=fullName>   
 [Comment : créer des requêtes TableAdapter](../data-tools/how-to-create-tableadapter-queries.md)   
 [Comment : modifier des requêtes TableAdapter](../data-tools/how-to-edit-tableadapter-queries.md)   
 [Comment : remplir un dataset avec des données](../data-tools/how-to-fill-a-dataset-with-data.md)   
 [Remplir des jeux de données à l’aide de TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)   
 [Comment : définir et obtenir des paramètres pour les objets de commande](http://msdn.microsoft.com/library/10110ecc-d2ed-4796-bb8f-74f2ecd40787)