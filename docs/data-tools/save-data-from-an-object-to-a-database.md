---
title: Enregistrer des données à partir d’un objet dans une base de données
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
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 641b598eb855fb1f2c3a7ca38d966630fbac15bb
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31924715"
---
# <a name="save-data-from-an-object-to-a-database"></a>Enregistrer des données à partir d’un objet dans une base de données
Vous pouvez enregistrer des données dans des objets à une base de données en passant les valeurs à partir de votre objet à une des méthodes DBDirect du TableAdapter (par exemple, `TableAdapter.Insert`). Pour plus d’informations, consultez [TableAdapter](../data-tools/create-and-configure-tableadapters.md).

 Pour enregistrer les données à partir d’une collection d’objets, parcourez la collection d’objets (par exemple, une boucle for-next) et envoyer les valeurs pour chaque objet à la base de données à l’aide d’une des méthodes DBDirect du TableAdapter.

 Par défaut, les méthodes DBDirect sont créés sur un TableAdapter qui peut être exécuté directement par rapport à la base de données. Ces méthodes peuvent être appelées directement et ne nécessitent pas <xref:System.Data.DataSet> ou <xref:System.Data.DataTable> pour rapprocher des modifications pour envoyer des mises à jour à une base de données.

> [!NOTE]
>  Lorsque vous configurez un TableAdapter, la requête principale doit fournir suffisamment d’informations pour les méthodes DBDirect doit être créé. Par exemple, si un TableAdapter est configuré pour interroger des données à partir d’une table qui n’a pas de colonne de clé primaire définie, elle ne génère pas de méthodes DBDirect.

|Méthode DBDirect du TableAdapter|Description|
|----------------------------------|-----------------|
|`TableAdapter.Insert`|Ajoute de nouveaux enregistrements dans une base de données et vous permet de passer des valeurs de colonne individuelles comme paramètres de méthode.|
|`TableAdapter.Update`|Mises à jour les enregistrements dans une base de données existants. Le `Update` méthode accepte les valeurs d’origine et de la nouvelle colonne comme paramètres de méthode. Les valeurs d’origine sont utilisées pour rechercher l’enregistrement d’origine et les nouvelles valeurs sont utilisées pour mettre à jour cet enregistrement.<br /><br /> Le `TableAdapter.Update` méthode est également utilisée pour réconcilier les modifications dans un jeu de données à la base de données en effectuant un <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, <xref:System.Data.DataRow>, ou un tableau de <xref:System.Data.DataRow>en tant que paramètres de méthode.|
|`TableAdapter.Delete`|Supprime les enregistrements existants de la base de données selon les valeurs de colonne d’origine passés en tant que paramètres de méthode.|

### <a name="to-save-new-records-from-an-object-to-a-database"></a>Pour enregistrer les nouveaux enregistrements à partir d’un objet dans une base de données

-   Créer les enregistrements en passant les valeurs pour le `TableAdapter.Insert` (méthode).

     L’exemple suivant crée un nouvel enregistrement de client dans le `Customers` table en passant les valeurs dans le `currentCustomer` de l’objet à le `TableAdapter.Insert` (méthode).

     [!code-csharp[VbRaddataSaving#23](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_1.cs)]
     [!code-vb[VbRaddataSaving#23](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_1.vb)]

### <a name="to-update-existing-records-from-an-object-to-a-database"></a>Pour mettre à jour des enregistrements existants à partir d’un objet à une base de données

-   Modifier les enregistrements en appelant le `TableAdapter.Update` méthode, en passant les nouvelles valeurs à mettre à jour l’enregistrement et en passant les valeurs d’origine pour rechercher l’enregistrement.

    > [!NOTE]
    >  Votre objet doit conserver les valeurs d’origine afin de les passer à la `Update` (méthode). Cet exemple utilise des propriétés avec un `orig` préfixe pour stocker les valeurs d’origine.

     L’exemple suivant met à jour un enregistrement existant dans la `Customers` table en passant les valeurs nouvelles et d’origine dans le `Customer` de l’objet à le `TableAdapter.Update` (méthode).

     [!code-csharp[VbRaddataSaving#24](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_2.cs)]
     [!code-vb[VbRaddataSaving#24](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_2.vb)]

### <a name="to-delete-existing-records-from-a-database"></a>Pour supprimer des enregistrements d’une base de données

-   Supprimer les enregistrements en appelant le `TableAdapter.Delete` méthode et en passant les valeurs d’origine pour rechercher l’enregistrement.

    > [!NOTE]
    >  Votre objet doit conserver les valeurs d’origine afin de les passer à la `Delete` (méthode). Cet exemple utilise des propriétés avec un `orig` préfixe pour stocker les valeurs d’origine.

     L’exemple suivant supprime un enregistrement de la `Customers` table en passant les valeurs d’origine dans le `Customer` de l’objet à le `TableAdapter.Delete` (méthode).

     [!code-csharp[VbRaddataSaving#25](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_3.cs)]
     [!code-vb[VbRaddataSaving#25](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_3.vb)]

## <a name="net-framework-security"></a>Sécurité .NET Framework
 Vous devez être autorisé à exécuter les instructions INSERT, UPDATE ou DELETE sur la table dans la base de données.

## <a name="see-also"></a>Voir aussi

- [Enregistrer les données dans la base de données](../data-tools/save-data-back-to-the-database.md)