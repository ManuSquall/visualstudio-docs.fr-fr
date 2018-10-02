---
title: 'Comment : supprimer des enregistrements dans une base de données | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [Visual Studio], saving
- records, deleting
- TableAdapter.Delete method
- databases, deleting records
- deleting data
- TableAdapter.Update method
- saving data
ms.assetid: d74d2130-9732-4648-abea-241059c4a372
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: e594a7c131d7e571a0919a9b96fa368f35cf18d7
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47504096"
---
# <a name="how-to-delete-records-in-a-database"></a>Comment : supprimer les enregistrements dans une base de données
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pour supprimer des enregistrements à partir d’une base de données, utilisez le `TableAdapter.Update` méthode ou le `TableAdapter.Delete` (méthode). Ou, si votre application n’utilise pas les TableAdapters, vous pouvez utiliser des objets de commande pour supprimer des enregistrements d’une base de données (par exemple, <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A>).  
  
 Le `TableAdapter.Update` méthode est généralement utilisée lorsque votre application utilise des jeux de données pour stocker des données, tandis que le `TableAdapter.Delete` méthode est généralement utilisée lorsque votre application utilise des objets pour stocker des données.  
  
 Si votre TableAdapter n’a pas un `Delete` (méthode), cela signifie que le TableAdapter est configuré pour utiliser des procédures stockées, ou son `GenerateDBDirectMethods` propriété est définie sur `false`. Essayez de définir le TableAdapter `GenerateDBDirectMethods` propriété `true` depuis le [Concepteur de Dataset](../data-tools/creating-and-editing-typed-datasets.md) puis enregistrez le jeu de données pour régénérer le TableAdapter. Si le TableAdapter n’a pas encore un `Delete` (méthode), puis la table ne fournit probablement pas suffisamment schéma d’informations pour faire la distinction entre des lignes individuelles (par exemple, aucune clé primaire n’est définie sur la table).  
  
## <a name="delete-records-using-tableadapters"></a>Supprimer des enregistrements à l’aide de TableAdapters  
 Les TableAdapters fournissent différentes façons de supprimer des enregistrements d’une base de données selon les besoins de votre application.  
  
 Si votre application utilise des jeux de données pour stocker des données vous pouvez simplement supprimer des enregistrements de souhaité <xref:System.Data.DataTable> dans le <xref:System.Data.DataSet>, puis appelez le `TableAdapter.Update` (méthode). Le `TableAdapter.Update` méthode accepte toutes les modifications dans la table de données et envoie ces modifications à la base de données (y compris les enregistrements insérés, mis à jour et supprimés).  
  
#### <a name="to-delete-records-from-a-database-using-the-tableadapterupdate-method"></a>Pour supprimer des enregistrements à partir d’une base de données à l’aide de la méthode TableAdapter.Update  
  
-   Supprimer des enregistrements de souhaité <xref:System.Data.DataTable> en supprimant <xref:System.Data.DataRow> objets à partir de la table. Pour plus d’informations, consultez [Comment : supprimer des lignes dans un DataTable](http://msdn.microsoft.com/library/add481e5-08c7-4923-9276-f036ae29d31e). Une fois que les lignes sont supprimées de la <xref:System.Data.DataTable>, appelez le `TableAdapter.Update` (méthode). Vous pouvez contrôler la quantité de données pour mettre à jour en passant l’intégralité d’un <xref:System.Data.DataSet>, un <xref:System.Data.DataTable>, un tableau de <xref:System.Data.DataRow>s ou un seul <xref:System.Data.DataRow>. Le code suivant montre comment supprimer un enregistrement à partir d’un <xref:System.Data.DataTable> , puis appelez le `TableAdapter.Update` méthode pour communiquer les modifications et supprimer la ligne de la base de données. (Cet exemple utilise la base de données Northwind `Region` table.)  
  
     [!code-csharp[VbRaddataSaving#20](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form5.cs#20)]
     [!code-vb[VbRaddataSaving#20](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form5.vb#20)]  
  
 Si votre application utilise des objets pour stocker les données dans votre application, vous pouvez utiliser les méthodes DBDirect du TableAdapter pour supprimer des données directement à partir de la base de données. Appel de la `Delete` méthode supprime les enregistrements à partir de la base de données selon les valeurs de paramètre passées.  
  
#### <a name="to-delete-records-from-a-database-using-the-tableadapterdelete-method"></a>Pour supprimer des enregistrements à partir d’une base de données à l’aide de la méthode TableAdapter.Delete  
  
-   Appelez le TableAdapter `Delete` méthode, en passant les valeurs pour chaque colonne en tant que paramètres de la `Delete` (méthode). (Cet exemple utilise la base de données Northwind `Region` table.)  
  
    > [!NOTE]
    >  Si vous n’avez pas d’instance disponible, instanciez le TableAdapter que vous souhaitez utiliser.  
  
     [!code-csharp[VbRaddataSaving#21](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#21)]
     [!code-vb[VbRaddataSaving#21](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#21)]  
  
## <a name="delete-records-using-command-objects"></a>Supprimer des enregistrements à l’aide des objets de commande  
 L’exemple suivant supprime des enregistrements directement à partir d’une base de données à l’aide des objets de commande. Pour plus d’informations sur l’utilisation des objets de commande pour exécuter des commandes et des procédures stockées, consultez [l’extraction des données dans votre Application](../data-tools/fetching-data-into-your-application.md).  
  
#### <a name="to-delete-records-from-a-database-using-command-objects"></a>Pour supprimer des enregistrements à partir d’une base de données à l’aide des objets de commande  
  
-   Créez un nouvel objet de commande, définissez son `Connection`, `CommandType`, et `CommandText` propriétés. (Cet exemple utilise la base de données Northwind `Region` table.)  
  
     [!code-csharp[VbRaddataSaving#22](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#22)]
     [!code-vb[VbRaddataSaving#22](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#22)]  
  
## <a name="net-framework-security"></a>Sécurité .NET Framework  
 Vous devez avoir accès à la base de données que vous essayez de vous connecter, ainsi que les autorisations de suppression des enregistrements à partir de la table souhaitée.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de TableAdapter](../data-tools/tableadapter-overview.md)   
 [Insérer de nouveaux enregistrements dans une base de données](../data-tools/insert-new-records-into-a-database.md)   
 [Comment : mettre à jour des enregistrements dans une base de données](../data-tools/how-to-update-records-in-a-database.md)   
 [Enregistrer les données à partir d’un objet dans une base de données](../data-tools/save-data-from-an-object-to-a-database.md)   
 [Vue d’ensemble des Applications de données dans Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Connexion aux données dans Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Préparation de votre Application à recevoir des données](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Récupération de données dans votre Application](../data-tools/fetching-data-into-your-application.md)   
 [Lier des contrôles à des données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modification des données dans votre Application](../data-tools/editing-data-in-your-application.md)   
 [Validation des données](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Enregistrer des données](../data-tools/saving-data.md)