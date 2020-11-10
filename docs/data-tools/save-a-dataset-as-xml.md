---
title: Enregistrer un dataset au format XML
description: Enregistrez un DataSet au format XML. Accédez aux données XML d’un DataSet en appelant les méthodes XML disponibles sur le DataSet, telles que GetXml ou WriteXml.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XML [Visual Basic], datasets
- data [Visual Studio], saving as XML
- datasets [Visual Basic], saving as XML
- saving data
ms.assetid: 68b8327c-ae05-49ff-b9ba-99183e70b52c
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: e454aca47f9bf6425ef2dfd98747869c27523f2c
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94434621"
---
# <a name="save-a-dataset-as-xml"></a>Enregistrer un dataset au format XML

Accédez aux données XML d’un DataSet en appelant les méthodes XML disponibles sur le DataSet. Pour enregistrer les données au format XML, vous pouvez appeler la <xref:System.Data.DataSet.GetXml%2A> méthode ou la <xref:System.Data.DataSet.WriteXml%2A> méthode d’un <xref:System.Data.DataSet> .

L’appel de la <xref:System.Data.DataSet.GetXml%2A> méthode retourne une chaîne qui contient les données de toutes les tables de données du DataSet au format XML.

L’appel de la <xref:System.Data.DataSet.WriteXml%2A> méthode envoie les données au format XML à un fichier que vous spécifiez.

## <a name="to-save-the-data-in-a-dataset-as-xml-to-a-variable"></a>Pour enregistrer les données d’un DataSet au format XML dans une variable

- La méthode <xref:System.Data.DataSet.GetXml%2A> retourne un <xref:System.String>. Déclarez une variable de type <xref:System.String> et assignez-lui les résultats de la <xref:System.Data.DataSet.GetXml%2A> méthode.

     [!code-vb[VbRaddataSaving#12](../data-tools/codesnippet/VisualBasic/save-a-dataset-as-xml_1.vb)]
     [!code-csharp[VbRaddataSaving#12](../data-tools/codesnippet/CSharp/save-a-dataset-as-xml_1.cs)]

## <a name="to-save-the-data-in-a-dataset-as-xml-to-a-file"></a>Pour enregistrer les données d’un DataSet au format XML dans un fichier

- La <xref:System.Data.DataSet.WriteXml%2A> méthode a plusieurs surcharges. Déclarez une variable et attribuez-lui un chemin d’accès valide pour enregistrer le fichier. Le code suivant montre comment enregistrer les données dans un fichier :

     [!code-vb[VbRaddataSaving#13](../data-tools/codesnippet/VisualBasic/save-a-dataset-as-xml_2.vb)]
     [!code-csharp[VbRaddataSaving#13](../data-tools/codesnippet/CSharp/save-a-dataset-as-xml_2.cs)]

## <a name="see-also"></a>Voir aussi

- [Enregistrer les données dans la base de données](../data-tools/save-data-back-to-the-database.md)
