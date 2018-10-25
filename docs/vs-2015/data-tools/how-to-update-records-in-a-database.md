---
title: 'Comment : mettre à jour des enregistrements dans une base de données | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
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
- records, updating
- data [Visual Studio], saving
- records, editing
- databases, updating
- TableAdapter.Update method
ms.assetid: cdc8a8e4-a5fa-40dd-9221-97b8571d802a
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: b62dc86425dcbebb225c66eecd51505f674e20ec
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49949030"
---
# <a name="how-to-update-records-in-a-database"></a>Comment : mettre à jour les enregistrements dans une base de données
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez utiliser la `TableAdapter.Update` méthode pour mettre à jour (modifier) des enregistrements dans une base de données. Le `TableAdapter.Update` méthode fournit plusieurs surcharges qui effectuent des opérations différentes selon les paramètres transmis. Il est important de comprendre les résultats de l’appel de ces signatures de méthode différente.  
  
> [!NOTE]
>  Si votre application n’utilise pas les TableAdapters, vous pouvez utiliser des objets de commande pour mettre à jour des enregistrements dans votre base de données (par exemple, <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A>). Pour plus d’informations sur la mise à jour des données avec des objets de commande, consultez « Mise à jour des enregistrements à l’aide des objets de commande » ci-dessous.  
  
 Le tableau suivant décrit le comportement des différents `TableAdapter.Update` méthodes :  
  
|Méthode|Description|  
|------------|-----------------|  
|`TableAdapter.Update(DataTable)`|Tente d’enregistrer toutes les modifications dans le <xref:System.Data.DataTable> à la base de données. (Cela inclut la suppression des lignes supprimées de la table, l’ajout de lignes insérées à la table et la mise à jour toutes les lignes dans la table qui ont été modifiés.)|  
|`TableAdapter.Update(DataSet)`|Bien que le paramètre prend un jeu de données, le TableAdapter essaie d’enregistrer toutes les modifications dans le TableAdapter associé au <xref:System.Data.DataTable> à la base de données. (Cela inclut la suppression des lignes supprimées de la table, l’ajout de lignes insérées dans la table et la mise à jour toutes les lignes dans la table qui ont été modifiés.) **Remarque :** associée d’un TableAdapter <xref:System.Data.DataTable> est le <xref:System.Data.DataTable> créé lors de la configuration du TableAdapter à l’origine.|  
|`TableAdapter.Update(DataRow)`|Tente d’enregistrer les modifications dans le texte indiqué <xref:System.Data.DataRow> à la base de données.|  
|`TableAdapter.Update(DataRows())`|Tente d’enregistrer les modifications dans n’importe quelle ligne dans le tableau de <xref:System.Data.DataRow>s pour la base de données.|  
|`TableAdapter.Update("new column values", "original column values")`|Tente d’enregistrer les modifications dans une seule ligne qui est identifiée par les valeurs de colonne d’origine.|  
  
 Vous utilisez généralement le `TableAdapter.Update` méthode qui prend un <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, ou <xref:System.Data.DataRow>(s) de votre application utilise des jeux de données exclusivement pour stocker des données.  
  
 Vous utilisez généralement le `TableAdapter.Update` méthode qui accepte des valeurs de colonne lorsque votre application utilise des objets pour stocker les données.  
  
 Si votre TableAdapter n’a pas un `Update` méthode qui prend des valeurs de colonne, cela signifie que le TableAdapter est configuré pour utiliser des procédures stockées ou son `GenerateDBDirectMethods` propriété est définie sur `false`. Essayez de définir le TableAdapter `GenerateDBDirectMethods` propriété `true` depuis le [Concepteur de Dataset](../data-tools/creating-and-editing-typed-datasets.md) puis enregistrez le jeu de données pour régénérer le TableAdapter. Si le TableAdapter n’a pas encore un `Update` méthode qui prend des valeurs de colonne, la table probablement ne fournit pas suffisamment d’informations pour faire la distinction entre des lignes individuelles schéma (par exemple, aucune clé primaire n’est définie sur la table).  
  
## <a name="update-existing-records-using-tableadapters"></a>Mettre à jour les enregistrements existants à l’aide de TableAdapters  
 Les TableAdapters fournissent différentes façons de mettre à jour des enregistrements dans une base de données selon les besoins de votre application.  
  
 Si votre application utilise des jeux de données pour stocker des données, vous pouvez simplement mettre à jour les enregistrements dans le texte souhaité <xref:System.Data.DataTable> , puis appelez le `TableAdapter.Update` (méthode) et passer le <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, <xref:System.Data.DataRow>, ou un tableau de <xref:System.Data.DataRow>s. Le tableau ci-dessus décrit les différents `Update` méthodes.  
  
#### <a name="to-update-records-in-a-database-with-the-tableadapterupdate-method-that-takes-dataset-datatable-datarow-or-datarows"></a>Pour mettre à jour des enregistrements dans une base de données avec la méthode TableAdapter.Update qui prend le DataSet, DataTable, DataRow ou DataRows ()  
  
1. Modifier les enregistrements de souhaité <xref:System.Data.DataTable> en modifiant directement le <xref:System.Data.DataRow> dans le <xref:System.Data.DataTable>. Pour plus d’informations, consultez [Comment : modifier les lignes dans un DataTable](http://msdn.microsoft.com/library/d5eea200-9bfa-4956-bf7c-08dd6fb6663c).  
  
2. Après avoir modifié les lignes dans le <xref:System.Data.DataTable>, appelez le `TableAdapter.Update` (méthode). Vous pouvez contrôler la quantité de données pour mettre à jour en passant l’intégralité d’un <xref:System.Data.DataSet>, un <xref:System.Data.DataTable>, un tableau de <xref:System.Data.DataRow>s ou un seul <xref:System.Data.DataRow>.  
  
    Le code suivant montre comment modifier un enregistrement dans un <xref:System.Data.DataTable> , puis appelez le `TableAdapter.Update` méthode pour enregistrer les modifications apportées à la base de données. (Cet exemple utilise la table de région de base de données Northwind.)  
  
    [!code-csharp[VbRaddataSaving#17](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form5.cs#17)]
    [!code-vb[VbRaddataSaving#17](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form5.vb#17)]  
  
   Si votre application utilise des objets pour stocker les données dans votre application, vous pouvez utiliser le TableAdapter `DBDirect` des méthodes pour envoyer des données à partir de vos objets directement à la base de données. Ces méthodes vous permettent de vous permettent de transmettre des valeurs individuelles pour chaque colonne en tant que paramètres de méthode. Appel de cette méthode met à jour un enregistrement existant dans la base de données avec les valeurs de colonne passées dans la méthode.  
  
   La procédure suivante utilise Northwind `Region` table comme exemple.  
  
#### <a name="to-update-records-in-a-database-using-the-tableadapterupdate-method-that-takes-column-values"></a>Pour mettre à jour des enregistrements dans une base de données à l’aide de la méthode TableAdapter.Update qui prend des valeurs de colonne  
  
-   Appelez le TableAdapter `Update` méthode, en passant les valeurs nouvelles et originale pour chaque colonne en tant que paramètres.  
  
    > [!NOTE]
    >  Si vous n’avez pas d’instance disponible, instanciez le TableAdapter que vous souhaitez utiliser.  
  
     [!code-csharp[VbRaddataSaving#18](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#18)]
     [!code-vb[VbRaddataSaving#18](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#18)]  
  
## <a name="update-records-using-command-objects"></a>Mettre à jour des enregistrements à l’aide des objets de commande  
 L’exemple suivant met à jour les enregistrements existants directement dans une base de données à l’aide des objets de commande. Pour plus d’informations sur l’utilisation des objets de commande pour exécuter des commandes et des procédures stockées, consultez [l’extraction des données dans votre Application](../data-tools/fetching-data-into-your-application.md).  
  
 La procédure suivante utilise Northwind `Region` table comme exemple.  
  
#### <a name="to-update-existing-records-in-a-database-using-command-objects"></a>Pour mettre à jour des enregistrements existants dans une base de données à l’aide des objets de commande  
  
-   Créez un nouvel objet de commande ; Définissez ses `Connection`, `CommandType`, et `CommandText` propriétés ; ouvrir une connexion et exécutez la commande.  
  
     [!code-csharp[VbRaddataSaving#19](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#19)]
     [!code-vb[VbRaddataSaving#19](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#19)]  
  
## <a name="net-framework-security"></a>Sécurité .NET Framework  
 Vous devez avoir accès à la base de données que vous essayez de vous connecter, mais aussi autorisé à mettre à jour des enregistrements dans la table souhaitée.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de TableAdapter](../data-tools/tableadapter-overview.md)   
 [Comment : supprimer des enregistrements dans une base de données](../data-tools/how-to-delete-records-in-a-database.md)   
 [Insérer de nouveaux enregistrements dans une base de données](../data-tools/insert-new-records-into-a-database.md)   
 [Enregistrer les données à partir d’un objet dans une base de données](../data-tools/save-data-from-an-object-to-a-database.md)   
 [Vue d’ensemble des Applications de données dans Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Connexion aux données dans Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Préparation de votre Application à recevoir des données](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Récupération de données dans votre Application](../data-tools/fetching-data-into-your-application.md)   
 [Lier des contrôles à des données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modification des données dans votre Application](../data-tools/editing-data-in-your-application.md)   
 [Validation des données](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Enregistrer des données](../data-tools/saving-data.md)