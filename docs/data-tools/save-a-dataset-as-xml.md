---
title: Enregistrer un dataset au format XML
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XML [Visual Basic], datasets
- data [Visual Studio], saving as XML
- datasets [Visual Basic], saving as XML
- saving data
ms.assetid: 68b8327c-ae05-49ff-b9ba-99183e70b52c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 3c993ac8703468a24a99e114563fec1bdc817581
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55913117"
---
# <a name="save-a-dataset-as-xml"></a>Enregistrer un dataset au format XML

Accéder aux données XML dans un jeu de données en appelant les méthodes XML disponibles sur le jeu de données. Pour enregistrer les données au format XML, vous pouvez appeler soit la <xref:System.Data.DataSet.GetXml%2A> (méthode) ou le <xref:System.Data.DataSet.WriteXml%2A> méthode d’un <xref:System.Data.DataSet>.

Appel de la <xref:System.Data.DataSet.GetXml%2A> méthode retourne une chaîne qui contient les données de toutes les tables de données dans le jeu de données est au format XML.

Appel de la <xref:System.Data.DataSet.WriteXml%2A> méthode envoie les données au format XML dans un fichier que vous spécifiez.

## <a name="to-save-the-data-in-a-dataset-as-xml-to-a-variable"></a>Pour enregistrer les données dans un jeu de données au format XML à une variable

- La méthode <xref:System.Data.DataSet.GetXml%2A> retourne un <xref:System.String>. Déclarez une variable de type <xref:System.String> et affecter les résultats de la <xref:System.Data.DataSet.GetXml%2A> (méthode).

     [!code-vb[VbRaddataSaving#12](../data-tools/codesnippet/VisualBasic/save-a-dataset-as-xml_1.vb)]
     [!code-csharp[VbRaddataSaving#12](../data-tools/codesnippet/CSharp/save-a-dataset-as-xml_1.cs)]

## <a name="to-save-the-data-in-a-dataset-as-xml-to-a-file"></a>Pour enregistrer les données dans un jeu de données au format XML dans un fichier

- Le <xref:System.Data.DataSet.WriteXml%2A> méthode a plusieurs surcharges. Déclarez une variable et attribuez-lui un chemin d’accès valide pour enregistrer le fichier. Le code suivant montre comment enregistrer les données dans un fichier :

     [!code-vb[VbRaddataSaving#13](../data-tools/codesnippet/VisualBasic/save-a-dataset-as-xml_2.vb)]
     [!code-csharp[VbRaddataSaving#13](../data-tools/codesnippet/CSharp/save-a-dataset-as-xml_2.cs)]

## <a name="see-also"></a>Voir aussi

- [Enregistrer les données dans la base de données](../data-tools/save-data-back-to-the-database.md)