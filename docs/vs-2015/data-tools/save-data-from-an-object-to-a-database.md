---
title: Enregistrer les données à partir d’un objet dans une base de données | Microsoft Docs
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
- data [Visual Studio], saving
- data access [Visual Studio], objects
- saving data
ms.assetid: efd6135a-40cf-4b0d-8f8b-41a5aaea7057
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 6980ecc7676afd978f8dfd243ef8f383413ad83d
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60074881"
---
# <a name="save-data-from-an-object-to-a-database"></a>Enregistrer les données d’un objet dans une base de données
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez enregistrer des données dans des objets à une base de données en passant les valeurs à partir de votre objet à une des méthodes DBDirect du TableAdapter (par exemple, `TableAdapter.Insert`).
  
 Pour enregistrer des données à partir d’une collection d’objets, parcourez la collection d’objets (par exemple, une boucle for-next) et envoyez les valeurs pour chaque objet à la base de données à l’aide d’une des méthodes DBDirect du TableAdapter.  
  
 Par défaut, les méthodes DBDirect sont créés sur un TableAdapter qui peut être exécuté directement par rapport à la base de données. Ces méthodes peuvent être appelées directement et ne nécessitent pas <xref:System.Data.DataSet> ou <xref:System.Data.DataTable> pour rapprocher des modifications pour envoyer des mises à jour à une base de données.  
  
> [!NOTE]
>  Lorsque vous configurez un TableAdapter, la requête principale doit fournir suffisamment d’informations pour les méthodes DBDirect doit être créé. Par exemple, si un TableAdapter est configuré pour interroger des données à partir d’une table qui n’a pas une colonne de clé primaire définie, il ne génère pas de méthodes DBDirect.  
  
|Méthode DBDirect du TableAdapter|Description|  
|----------------------------------|-----------------|  
|`TableAdapter.Insert`|Ajoute de nouveaux enregistrements à une base de données et vous permet de passer des valeurs de colonne individuels en tant que paramètres de méthode.|  
|`TableAdapter.Update`|Mises à jour les enregistrements dans une base de données existants. Le `Update` méthode accepte des valeurs d’origine et de la nouvelle colonne en tant que paramètres de méthode. Les valeurs d’origine sont utilisées pour rechercher l’enregistrement d’origine et les nouvelles valeurs sont utilisées pour mettre à jour cet enregistrement.<br /><br /> Le `TableAdapter.Update` méthode est également utilisée pour rapprocher les modifications dans un jeu de données dans la base de données en prenant un <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, <xref:System.Data.DataRow>, ou un tableau de <xref:System.Data.DataRow>s en tant que paramètres de méthode.|  
|`TableAdapter.Delete`|Supprime les enregistrements existants de la base de données en fonction des valeurs de colonne d’origine passés en tant que paramètres de méthode.|  
  
### <a name="to-save-new-records-from-an-object-to-a-database"></a>Pour enregistrer les nouveaux enregistrements à partir d’un objet dans une base de données  
  
- Créer les enregistrements en passant les valeurs pour le `TableAdapter.Insert` (méthode).  
  
     L’exemple suivant crée un nouvel enregistrement de client dans le `Customers` table en passant les valeurs dans le `currentCustomer` de l’objet à le `TableAdapter.Insert` (méthode).  
  
     [!code-csharp[VbRaddataSaving#23](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#23)]
     [!code-vb[VbRaddataSaving#23](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#23)]  
  
### <a name="to-update-existing-records-from-an-object-to-a-database"></a>Pour mettre à jour les enregistrements existants à partir d’un objet à une base de données  
  
- Modifier les enregistrements en appelant le `TableAdapter.Update` (méthode), en passant les nouvelles valeurs à mettre à jour l’enregistrement et en passant les valeurs d’origine pour rechercher l’enregistrement.  
  
    > [!NOTE]
    >  Votre objet doit conserver les valeurs d’origine afin de les passer à la `Update` (méthode). Cet exemple utilise des propriétés avec un `orig` préfixe pour stocker les valeurs d’origine.  
  
     L’exemple suivant met à jour un enregistrement existant dans le `Customers` table en passant les valeurs nouvelles et originale de la `Customer` de l’objet à le `TableAdapter.Update` (méthode).  
  
     [!code-csharp[VbRaddataSaving#24](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#24)]
     [!code-vb[VbRaddataSaving#24](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#24)]  
  
### <a name="to-delete-existing-records-from-a-database"></a>Pour supprimer des enregistrements existants à partir d’une base de données  
  
- Supprimer les enregistrements en appelant le `TableAdapter.Delete` (méthode) et en passant les valeurs d’origine pour rechercher l’enregistrement.  
  
    > [!NOTE]
    >  Votre objet doit conserver les valeurs d’origine afin de les passer à la `Delete` (méthode). Cet exemple utilise des propriétés avec un `orig` préfixe pour stocker les valeurs d’origine.  
  
     L’exemple suivant supprime un enregistrement à partir de la `Customers` table en passant les valeurs d’origine dans le `Customer` de l’objet à le `TableAdapter.Delete` (méthode).  
  
     [!code-csharp[VbRaddataSaving#25](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#25)]
     [!code-vb[VbRaddataSaving#25](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#25)]  
  
## <a name="net-framework-security"></a>Sécurité .NET Framework  
 Vous devez être autorisé à exécuter les instructions INSERT, UPDATE ou DELETE sur la table dans la base de données.  
  
## <a name="see-also"></a>Voir aussi  
 [Enregistrer les données dans la base de données](../data-tools/save-data-back-to-the-database.md)
