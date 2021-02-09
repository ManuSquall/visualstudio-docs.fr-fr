---
title: Enregistrer les données d’un objet dans une base de données
description: Enregistrer des données à partir d’un objet dans une base de données à l’aide des outils de DataSet dans Visual Studio. Découvrez comment enregistrer de nouveaux enregistrements, mettre à jour des enregistrements existants et supprimer des enregistrements existants.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Visual Studio], saving
- data access [Visual Studio], objects
- saving data
ms.assetid: efd6135a-40cf-4b0d-8f8b-41a5aaea7057
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 52bd4f95160165ee67c0a35816d094238786bc38
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99866565"
---
# <a name="save-data-from-an-object-to-a-database"></a>Enregistrer les données d’un objet dans une base de données

Vous pouvez enregistrer des données dans des objets dans une base de données en passant les valeurs de votre objet à l’une des méthodes DBDirect du TableAdapter (par exemple, `TableAdapter.Insert` ). Pour plus d’informations, consultez [TableAdapter](../data-tools/create-and-configure-tableadapters.md).

Pour enregistrer des données à partir d’une collection d’objets, parcourez la collection d’objets (par exemple, une boucle for-Next) et envoyez les valeurs de chaque objet à la base de données à l’aide de l’une des méthodes du TableAdapter `DBDirect` .

Par défaut, `DBDirect` les méthodes sont créées sur un TableAdapter qui peut être exécuté directement sur la base de données. Ces méthodes peuvent être appelées directement et ne nécessitent pas <xref:System.Data.DataSet> <xref:System.Data.DataTable> d’objets ou pour harmoniser les modifications afin d’envoyer des mises à jour à une base de données.

> [!NOTE]
> Quand vous configurez un TableAdapter, la requête principale doit fournir suffisamment d’informations pour que les `DBDirect` méthodes soient créées. Par exemple, si un TableAdapter est configuré pour interroger les données d’une table qui n’a pas de colonne de clé primaire définie, il ne génère pas de `DBDirect` méthodes.

|Méthode DBDirect du TableAdapter|Description|
| - |-----------------|
|`TableAdapter.Insert`|Ajoute de nouveaux enregistrements à une base de données et vous permet de transmettre des valeurs de colonne individuelles en tant que paramètres de méthode.|
|`TableAdapter.Update`|Met à jour les enregistrements existants dans une base de données. La `Update` méthode accepte les valeurs de colonne d’origine et nouvelles en tant que paramètres de méthode. Les valeurs d’origine sont utilisées pour localiser l’enregistrement d’origine, et les nouvelles valeurs sont utilisées pour mettre à jour cet enregistrement.<br /><br /> La `TableAdapter.Update` méthode est également utilisée pour réconcilier les modifications apportées à un DataSet dans la base de données en acceptant un <xref:System.Data.DataSet> ,, <xref:System.Data.DataTable> <xref:System.Data.DataRow> ou un tableau de <xref:System.Data.DataRow> s comme paramètres de méthode.|
|`TableAdapter.Delete`|Supprime les enregistrements existants de la base de données en fonction des valeurs de colonne d’origine passées en tant que paramètres de méthode.|

## <a name="to-save-new-records-from-an-object-to-a-database"></a>Pour enregistrer de nouveaux enregistrements d’un objet dans une base de données

- Créez les enregistrements en passant les valeurs à la `TableAdapter.Insert` méthode.

     L’exemple suivant crée un nouvel enregistrement Customer dans la `Customers` table en passant les valeurs de l' `currentCustomer` objet à la `TableAdapter.Insert` méthode.

     [!code-csharp[VbRaddataSaving#23](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_1.cs)]
     [!code-vb[VbRaddataSaving#23](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_1.vb)]

## <a name="to-update-existing-records-from-an-object-to-a-database"></a>Pour mettre à jour des enregistrements existants d’un objet vers une base de données

- Modifiez les enregistrements en appelant la `TableAdapter.Update` méthode, en passant les nouvelles valeurs pour mettre à jour l’enregistrement et en passant les valeurs d’origine pour localiser l’enregistrement.

    > [!NOTE]
    > Votre objet doit conserver les valeurs d’origine afin de les passer à la `Update` méthode. Cet exemple utilise des propriétés avec un `orig` préfixe pour stocker les valeurs d’origine.

     L’exemple suivant met à jour un enregistrement existant dans la `Customers` table en passant les valeurs nouvelles et d’origine de l' `Customer` objet à la `TableAdapter.Update` méthode.

     [!code-csharp[VbRaddataSaving#24](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_2.cs)]
     [!code-vb[VbRaddataSaving#24](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_2.vb)]

## <a name="to-delete-existing-records-from-a-database"></a>Pour supprimer des enregistrements existants d’une base de données

- Supprimez les enregistrements en appelant la `TableAdapter.Delete` méthode et en passant les valeurs d’origine pour localiser l’enregistrement.

    > [!NOTE]
    > Votre objet doit conserver les valeurs d’origine afin de les passer à la `Delete` méthode. Cet exemple utilise des propriétés avec un `orig` préfixe pour stocker les valeurs d’origine.

     L’exemple suivant supprime un enregistrement de la `Customers` table en passant les valeurs d’origine de l' `Customer` objet à la `TableAdapter.Delete` méthode.

     [!code-csharp[VbRaddataSaving#25](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_3.cs)]
     [!code-vb[VbRaddataSaving#25](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_3.vb)]

## <a name="net-security"></a>Sécurité .NET

Vous devez être autorisé à effectuer l’option sélectionnée, `INSERT` `UPDATE` ou `DELETE` sur la table dans la base de données.

## <a name="see-also"></a>Voir aussi

- [Enregistrer les données dans la base de données](../data-tools/save-data-back-to-the-database.md)
