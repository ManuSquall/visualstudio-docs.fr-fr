---
title: Enregistrer un DataSet au format XML | Microsoft Docs
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
- XML [Visual Basic], datasets
- data [Visual Studio], saving as XML
- datasets [Visual Basic], saving as XML
- saving data
ms.assetid: 68b8327c-ae05-49ff-b9ba-99183e70b52c
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e64c3c17934e5cdc5d6ca1f510c7164b86a77c1a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72652864"
---
# <a name="save-a-dataset-as-xml"></a>Enregistrer un dataset au format XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez accéder aux données XML d’un DataSet en appelant les méthodes XML disponibles sur le DataSet. Pour enregistrer les données au format XML, vous pouvez appeler la <xref:System.Data.DataSet.GetXml%2A> méthode ou la <xref:System.Data.DataSet.WriteXml%2A> méthode d’un <xref:System.Data.DataSet> .

 L’appel de la <xref:System.Data.DataSet.GetXml%2A> méthode retourne une chaîne qui contient les données de toutes les tables de données du DataSet au format XML.

 L’appel de la <xref:System.Data.DataSet.WriteXml%2A> méthode envoie les données au format XML à un fichier que vous spécifiez.

### <a name="to-save-the-data-in-a-dataset-as-xml-to-a-variable"></a>Pour enregistrer les données d’un DataSet au format XML dans une variable

- La <xref:System.Data.DataSet.GetXml%2A> méthode retourne un <xref:System.String> . Cela signifie que vous déclarez une variable de type et que vous <xref:System.String> lui assignez les résultats de la <xref:System.Data.DataSet.GetXml%2A> méthode.

     [!code-csharp[VbRaddataSaving#12](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#12)]
     [!code-vb[VbRaddataSaving#12](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#12)]

### <a name="to-save-the-data-in-a-dataset-as-xml-to-a-file"></a>Pour enregistrer les données d’un DataSet au format XML dans un fichier

- La <xref:System.Data.DataSet.WriteXml%2A> méthode a plusieurs surcharges. Le code suivant montre comment enregistrer les données dans un fichier. Déclarez une variable et attribuez-lui un chemin d’accès valide pour enregistrer le fichier.

     [!code-csharp[VbRaddataSaving#13](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#13)]
     [!code-vb[VbRaddataSaving#13](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#13)]

## <a name="see-also"></a>Voir aussi
 [Enregistrer les données dans la base de données](../data-tools/save-data-back-to-the-database.md)
