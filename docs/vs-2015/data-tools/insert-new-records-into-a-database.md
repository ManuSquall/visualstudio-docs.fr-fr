---
title: Insérer de nouveaux enregistrements dans une base de données | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- TableAdapters, inserting new records into
- data [Visual Studio], saving
- databases, inserting new records into
- records, inserting
- saving data
ms.assetid: ea118fff-69b1-4675-b79a-e33374377f04
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3c686a764f42f50a3e59da3e8b37b219ddb7b11c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651558"
---
# <a name="insert-new-records-into-a-database"></a>Insérer de nouveaux enregistrements dans une base de données
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pour insérer de nouveaux enregistrements dans une base de données, vous pouvez utiliser la `TableAdapter.Update` méthode ou l’une des méthodes DBDirect du TableAdapter (en particulier la `TableAdapter.Insert` méthode).

 Si votre application n’utilise pas de TableAdapters, vous pouvez utiliser des objets de commande (par exemple,  <xref:System.Data.SqlClient.SqlCommand> ) pour insérer de nouveaux enregistrements dans votre base de données.

 Si votre application utilise des jeux de données pour stocker des données, utilisez la `TableAdapter.Update` méthode. La `Update` méthode envoie toutes les modifications (mises à jour, insertions et suppressions) à la base de données.

 Si votre application utilise des objets pour stocker des données, ou si vous souhaitez un contrôle plus fin sur la création d’enregistrements dans la base de données, utilisez la `TableAdapter.Insert` méthode.

 Si votre TableAdapter n’a pas de `Insert` méthode, cela signifie que le TableAdapter est configuré pour utiliser des procédures stockées ou que sa `GenerateDBDirectMethods` propriété a la valeur `false` . Essayez de définir la propriété du TableAdapter `GenerateDBDirectMethods` à `true` partir de dans le concepteur de DataSet, puis enregistrez le jeu de données. Cela permet de régénérer le TableAdapter. Si le TableAdapter n’a toujours `Insert` pas de méthode, il est probable que la table ne fournisse pas suffisamment d’informations de schéma pour faire la distinction entre des lignes individuelles (par exemple, il se peut qu’il n’y ait pas de clé primaire définie sur la table).

## <a name="insert-new-records-by-using-tableadapters"></a>Insérer de nouveaux enregistrements à l’aide de TableAdapters
 Les TableAdapters offrent différentes façons d’insérer de nouveaux enregistrements dans une base de données, en fonction des exigences de votre application.

 Si votre application utilise des jeux de données pour stocker des données, vous pouvez simplement ajouter de nouveaux enregistrements aux souhaités <xref:System.Data.DataTable> dans le DataSet, puis appeler la `TableAdapter.Update` méthode. La `TableAdapter.Update` méthode envoie toutes les modifications apportées <xref:System.Data.DataTable> à la base de données (y compris les enregistrements modifiés et supprimés).

#### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterupdate-method"></a>Pour insérer de nouveaux enregistrements dans une base de données à l’aide de la méthode TableAdapter. Update

1. Ajoutez de nouveaux enregistrements au souhaité <xref:System.Data.DataTable> en créant un nouveau <xref:System.Data.DataRow> et en l’ajoutant à la <xref:System.Data.DataTable.Rows%2A> collection. Pour plus d’informations, consultez [Comment : ajouter des lignes à un DataTable](https://msdn.microsoft.com/library/78ebbb43-c402-49cf-81da-0715289487bf).

2. Une fois les nouvelles lignes ajoutées au <xref:System.Data.DataTable> , appelez la `TableAdapter.Update` méthode. Vous pouvez contrôler la quantité de données à mettre à jour en passant une valeur entière <xref:System.Data.DataSet> , un <xref:System.Data.DataTable> , un tableau de ou <xref:System.Data.DataRow> un unique <xref:System.Data.DataRow> .

    Le code suivant montre comment ajouter un nouvel enregistrement à un <xref:System.Data.DataTable> , puis appeler la `TableAdapter.Update` méthode pour enregistrer la nouvelle ligne dans la base de données. (Cet exemple utilise la `Region` table de la base de données Northwind.)

    [!code-csharp[VbRaddataSaving#14](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form5.cs#14)]
    [!code-vb[VbRaddataSaving#14](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form5.vb#14)]

   Si votre application utilise des objets pour stocker des données, vous pouvez utiliser la `TableAdapter.Insert` méthode pour créer des lignes directement dans la base de données. La `Insert` méthode accepte les valeurs individuelles pour chaque colonne en tant que paramètres. L’appel de la méthode insère un nouvel enregistrement dans la base de données avec les valeurs de paramètres passées.

   La procédure suivante utilise la `Region` table de la base de données Northwind comme exemple.

#### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterinsert-method"></a>Pour insérer de nouveaux enregistrements dans une base de données à l’aide de la méthode TableAdapter. Insert

- Appelez la méthode du TableAdapter en `Insert` passant les valeurs de chaque colonne en tant que paramètres.

    > [!NOTE]
    > Si vous n’avez pas d’instance disponible, instanciez le TableAdapter que vous souhaitez utiliser.

     [!code-csharp[VbRaddataSaving#15](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#15)]
     [!code-vb[VbRaddataSaving#15](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#15)]

## <a name="insert-new-records-by-using-command-objects"></a>Insérer de nouveaux enregistrements à l’aide d’objets de commande
 L’exemple suivant insère de nouveaux enregistrements directement dans une base de données à l’aide d’objets de commande.

 La procédure suivante utilise la `Region` table de la base de données Northwind comme exemple.

#### <a name="to-insert-new-records-into-a-database-by-using-command-objects"></a>Pour insérer de nouveaux enregistrements dans une base de données à l’aide d’objets de commande

- Créez un nouvel objet de commande, puis définissez ses `Connection` `CommandType` Propriétés, et `CommandText` .

     [!code-csharp[VbRaddataSaving#16](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#16)]
     [!code-vb[VbRaddataSaving#16](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#16)]

## <a name="net-framework-security"></a>Sécurité du .NET Framework
 Vous devez avoir accès à la base de données à laquelle vous essayez de vous connecter, ainsi qu’à l’autorisation d’effectuer des insertions dans la table souhaitée.

## <a name="see-also"></a>Voir aussi
 [Enregistrer les données dans la base de données](../data-tools/save-data-back-to-the-database.md)
