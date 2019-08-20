---
title: Enregistrer les données d’un objet dans une base de données
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Visual Studio], saving
- data access [Visual Studio], objects
- saving data
ms.assetid: efd6135a-40cf-4b0d-8f8b-41a5aaea7057
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: b15776b67ded2fc813f1b8bcf82d8aa91f212346
ms.sourcegitcommit: 5483e399f14fb01f528b3b194474778fd6f59fa6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66715028"
---
# <a name="save-data-from-an-object-to-a-database"></a>Enregistrer les données d’un objet dans une base de données

Vous pouvez enregistrer des données dans des objets à une base de données en passant les valeurs à partir de votre objet à une des méthodes DBDirect du TableAdapter (par exemple, `TableAdapter.Insert`). Pour plus d’informations, consultez [TableAdapter](../data-tools/create-and-configure-tableadapters.md).

Pour enregistrer des données à partir d’une collection d’objets, parcourez la collection d’objets (par exemple, une boucle for-next) et envoyez les valeurs pour chaque objet à la base de données à l’aide d’une de du TableAdapter `DBDirect` méthodes.

Par défaut, `DBDirect` méthodes sont créées sur un TableAdapter qui peut être exécuté directement par rapport à la base de données. Ces méthodes peuvent être appelées directement et ne nécessitent pas <xref:System.Data.DataSet> ou <xref:System.Data.DataTable> pour rapprocher des modifications pour envoyer des mises à jour à une base de données.

> [!NOTE]
> Lorsque vous configurez un TableAdapter, la requête principale doit fournir suffisamment d’informations pour le `DBDirect` méthodes doit être créé. Par exemple, si un TableAdapter est configuré pour interroger des données à partir d’une table qui n’a pas une colonne de clé primaire définie, il ne génère pas `DBDirect` méthodes.

|Méthode DBDirect du TableAdapter|Description|
| - |-----------------|
|`TableAdapter.Insert`|Ajoute de nouveaux enregistrements à une base de données et vous permet de passer des valeurs de colonne individuels en tant que paramètres de méthode.|
|`TableAdapter.Update`|Mises à jour les enregistrements dans une base de données existants. Le `Update` méthode accepte des valeurs d’origine et de la nouvelle colonne en tant que paramètres de méthode. Les valeurs d’origine sont utilisées pour rechercher l’enregistrement d’origine et les nouvelles valeurs sont utilisées pour mettre à jour cet enregistrement.<br /><br /> Le `TableAdapter.Update` méthode est également utilisée pour rapprocher les modifications dans un jeu de données dans la base de données en prenant un <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, <xref:System.Data.DataRow>, ou un tableau de <xref:System.Data.DataRow>s en tant que paramètres de méthode.|
|`TableAdapter.Delete`|Supprime les enregistrements existants de la base de données en fonction des valeurs de colonne d’origine passés en tant que paramètres de méthode.|

## <a name="to-save-new-records-from-an-object-to-a-database"></a>Pour enregistrer les nouveaux enregistrements à partir d’un objet dans une base de données

- Créer les enregistrements en passant les valeurs pour le `TableAdapter.Insert` (méthode).

     L’exemple suivant crée un nouvel enregistrement de client dans le `Customers` table en passant les valeurs dans le `currentCustomer` de l’objet à le `TableAdapter.Insert` (méthode).

     [!code-csharp[VbRaddataSaving#23](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_1.cs)]
     [!code-vb[VbRaddataSaving#23](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_1.vb)]

## <a name="to-update-existing-records-from-an-object-to-a-database"></a>Pour mettre à jour les enregistrements existants à partir d’un objet à une base de données

- Modifier les enregistrements en appelant le `TableAdapter.Update` (méthode), en passant les nouvelles valeurs à mettre à jour l’enregistrement et en passant les valeurs d’origine pour rechercher l’enregistrement.

    > [!NOTE]
    > Votre objet doit conserver les valeurs d’origine afin de les passer à la `Update` (méthode). Cet exemple utilise des propriétés avec un `orig` préfixe pour stocker les valeurs d’origine.

     L’exemple suivant met à jour un enregistrement existant dans le `Customers` table en passant les valeurs nouvelles et originale de la `Customer` de l’objet à le `TableAdapter.Update` (méthode).

     [!code-csharp[VbRaddataSaving#24](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_2.cs)]
     [!code-vb[VbRaddataSaving#24](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_2.vb)]

## <a name="to-delete-existing-records-from-a-database"></a>Pour supprimer des enregistrements existants à partir d’une base de données

- Supprimer les enregistrements en appelant le `TableAdapter.Delete` (méthode) et en passant les valeurs d’origine pour rechercher l’enregistrement.

    > [!NOTE]
    > Votre objet doit conserver les valeurs d’origine afin de les passer à la `Delete` (méthode). Cet exemple utilise des propriétés avec un `orig` préfixe pour stocker les valeurs d’origine.

     L’exemple suivant supprime un enregistrement à partir de la `Customers` table en passant les valeurs d’origine dans le `Customer` de l’objet à le `TableAdapter.Delete` (méthode).

     [!code-csharp[VbRaddataSaving#25](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_3.cs)]
     [!code-vb[VbRaddataSaving#25](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_3.vb)]

## <a name="net-security"></a>Sécurité de .NET

Vous devez être autorisé à effectuer sélectionné `INSERT`, `UPDATE`, ou `DELETE` sur la table dans la base de données.

## <a name="see-also"></a>Voir aussi

- [Enregistrer les données dans la base de données](../data-tools/save-data-back-to-the-database.md)