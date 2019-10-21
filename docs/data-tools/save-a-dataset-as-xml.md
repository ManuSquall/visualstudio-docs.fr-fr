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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 5b3aa23cb0fde98b4da4225b8e255b7cd6e7aef5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72641353"
---
# <a name="save-a-dataset-as-xml"></a>Enregistrer un dataset au format XML

Accédez aux données XML d’un DataSet en appelant les méthodes XML disponibles sur le DataSet. Pour enregistrer les données au format XML, vous pouvez appeler la méthode <xref:System.Data.DataSet.GetXml%2A> ou la méthode <xref:System.Data.DataSet.WriteXml%2A> d’un <xref:System.Data.DataSet>.

L’appel de la méthode <xref:System.Data.DataSet.GetXml%2A> retourne une chaîne qui contient les données de toutes les tables de données du DataSet au format XML.

L’appel de la méthode <xref:System.Data.DataSet.WriteXml%2A> envoie les données au format XML à un fichier que vous spécifiez.

## <a name="to-save-the-data-in-a-dataset-as-xml-to-a-variable"></a>Pour enregistrer les données d’un DataSet au format XML dans une variable

- La méthode <xref:System.Data.DataSet.GetXml%2A> retourne un <xref:System.String>. Déclarez une variable de type <xref:System.String> et assignez-lui les résultats de la méthode <xref:System.Data.DataSet.GetXml%2A>.

     [!code-vb[VbRaddataSaving#12](../data-tools/codesnippet/VisualBasic/save-a-dataset-as-xml_1.vb)]
     [!code-csharp[VbRaddataSaving#12](../data-tools/codesnippet/CSharp/save-a-dataset-as-xml_1.cs)]

## <a name="to-save-the-data-in-a-dataset-as-xml-to-a-file"></a>Pour enregistrer les données d’un DataSet au format XML dans un fichier

- La méthode <xref:System.Data.DataSet.WriteXml%2A> a plusieurs surcharges. Déclarez une variable et attribuez-lui un chemin d’accès valide pour enregistrer le fichier. Le code suivant montre comment enregistrer les données dans un fichier :

     [!code-vb[VbRaddataSaving#13](../data-tools/codesnippet/VisualBasic/save-a-dataset-as-xml_2.vb)]
     [!code-csharp[VbRaddataSaving#13](../data-tools/codesnippet/CSharp/save-a-dataset-as-xml_2.cs)]

## <a name="see-also"></a>Voir aussi

- [Enregistrer les données dans la base de données](../data-tools/save-data-back-to-the-database.md)