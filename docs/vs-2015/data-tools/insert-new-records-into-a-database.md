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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 001f3a3c74f792fbe3028b6915cb350d359221a1
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60043134"
---
# <a name="insert-new-records-into-a-database"></a>Insérer de nouveaux enregistrements dans une base de données
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pour insérer de nouveaux enregistrements dans une base de données, vous pouvez utiliser la `TableAdapter.Update` (méthode), ou l’une des méthodes DBDirect du TableAdapter (en particulier le `TableAdapter.Insert` méthode).
  
 Si votre application n’utilise pas les TableAdapters, vous pouvez utiliser des objets de commande (par exemple, <xref:System.Data.SqlClient.SqlCommand>) pour insérer de nouveaux enregistrements dans votre base de données.  
  
 Si votre application utilise des jeux de données pour stocker des données, utilisez le `TableAdapter.Update` (méthode). Le `Update` méthode envoie toutes les modifications (mises à jour, insertions et suppressions) à la base de données.  
  
 Si votre application utilise des objets pour stocker des données, ou si vous souhaitez mieux contrôler la création de nouveaux enregistrements dans la base de données, utilisez le `TableAdapter.Insert` (méthode).  
  
 Si votre TableAdapter n’a pas un `Insert` (méthode), cela signifie que le TableAdapter est configuré pour utiliser des procédures stockées ou son `GenerateDBDirectMethods` propriété est définie sur `false`. Essayez de définir le TableAdapter `GenerateDBDirectMethods` propriété `true` à partir de dans le Concepteur de Dataset, puis enregistrez le jeu de données. Cette opération va regénérer le TableAdapter. Si le TableAdapter n’est pas encore un `Insert` (méthode), puis la table ne fournit probablement pas suffisamment schéma d’informations pour faire la distinction entre des lignes individuelles (par exemple, il ne peut être aucun jeu de clé primaire sur la table).  
  
## <a name="insert-new-records-by-using-tableadapters"></a>Insérer de nouveaux enregistrements à l’aide de TableAdapters  
 Les TableAdapters fournissent différentes façons d’insérer de nouveaux enregistrements dans une base de données, selon les besoins de votre application.  
  
 Si votre application utilise des jeux de données pour stocker des données, vous pouvez simplement ajouter des enregistrements à souhaité <xref:System.Data.DataTable> dans le jeu de données, puis appelez le `TableAdapter.Update` (méthode). Le `TableAdapter.Update` méthode envoie toutes les modifications le <xref:System.Data.DataTable> à la base de données (y compris les enregistrements modifiés et supprimés).  
  
#### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterupdate-method"></a>Pour insérer de nouveaux enregistrements dans une base de données à l’aide de la méthode TableAdapter.Update  
  
1. Ajouter des enregistrements à souhaité <xref:System.Data.DataTable> en créant un nouveau <xref:System.Data.DataRow> et en l’ajoutant à la <xref:System.Data.DataTable.Rows%2A> collection. Pour plus d'informations, voir [Procédure : Ajouter des lignes à un DataTable](http://msdn.microsoft.com/library/78ebbb43-c402-49cf-81da-0715289487bf).  
  
2. Une fois que les nouvelles lignes sont ajoutées à la <xref:System.Data.DataTable>, appelez le `TableAdapter.Update` (méthode). Vous pouvez contrôler la quantité de données pour mettre à jour en passant l’intégralité d’un <xref:System.Data.DataSet>, un <xref:System.Data.DataTable>, un tableau de <xref:System.Data.DataRow>s ou un seul <xref:System.Data.DataRow>.  
  
    Le code suivant montre comment ajouter un nouvel enregistrement à un <xref:System.Data.DataTable> , puis appelez le `TableAdapter.Update` méthode pour enregistrer la nouvelle ligne dans la base de données. (Cet exemple utilise le `Region` table dans la base de données Northwind.)  
  
    [!code-csharp[VbRaddataSaving#14](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form5.cs#14)]
    [!code-vb[VbRaddataSaving#14](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form5.vb#14)]  
  
   Si votre application utilise des objets pour stocker des données, vous pouvez utiliser la `TableAdapter.Insert` méthode pour créer des lignes directement dans la base de données. Le `Insert` méthode accepte les valeurs individuelles pour chaque colonne en tant que paramètres. Appel de la méthode insère un nouvel enregistrement dans la base de données avec les valeurs de paramètre passées.  
  
   La procédure suivante utilise le `Region` table dans la base de données Northwind comme exemple.  
  
#### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterinsert-method"></a>Pour insérer de nouveaux enregistrements dans une base de données à l’aide de la méthode TableAdapter.Insert  
  
- Appelez le TableAdapter `Insert` méthode, en passant les valeurs pour chaque colonne en tant que paramètres.  
  
    > [!NOTE]
    >  Si vous n’avez pas d’instance disponible, instanciez le TableAdapter que vous souhaitez utiliser.  
  
     [!code-csharp[VbRaddataSaving#15](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#15)]
     [!code-vb[VbRaddataSaving#15](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#15)]  
  
## <a name="insert-new-records-by-using-command-objects"></a>Insérer de nouveaux enregistrements à l’aide des objets de commande  
 L’exemple suivant insère de nouveaux enregistrements directement dans une base de données à l’aide des objets de commande.
  
 La procédure suivante utilise le `Region` table dans la base de données Northwind comme exemple.  
  
#### <a name="to-insert-new-records-into-a-database-by-using-command-objects"></a>Pour insérer de nouveaux enregistrements dans une base de données à l’aide des objets de commande  
  
- Créez un nouvel objet de commande et définissez son `Connection`, `CommandType`, et `CommandText` propriétés.  
  
     [!code-csharp[VbRaddataSaving#16](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#16)]
     [!code-vb[VbRaddataSaving#16](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#16)]  
  
## <a name="net-framework-security"></a>Sécurité .NET Framework  
 Vous devez avoir accès à la base de données que vous essayez de vous connecter, mais aussi autorisé à effectuer des insertions dans la table souhaitée.  
  
## <a name="see-also"></a>Voir aussi  
 [Enregistrer les données dans la base de données](../data-tools/save-data-back-to-the-database.md)
