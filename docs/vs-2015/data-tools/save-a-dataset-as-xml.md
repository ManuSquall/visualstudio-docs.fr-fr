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
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652864"
---
# <a name="save-a-dataset-as-xml"></a>Enregistrer un dataset au format XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez accéder aux données XML d’un DataSet en appelant les méthodes XML disponibles sur le DataSet. Pour enregistrer les données au format XML, vous pouvez appeler la méthode <xref:System.Data.DataSet.GetXml%2A> ou la méthode <xref:System.Data.DataSet.WriteXml%2A> d’un <xref:System.Data.DataSet>.

 L’appel de la méthode <xref:System.Data.DataSet.GetXml%2A> retourne une chaîne qui contient les données de toutes les tables de données du DataSet au format XML.

 L’appel de la méthode <xref:System.Data.DataSet.WriteXml%2A> envoie les données au format XML à un fichier que vous spécifiez.

### <a name="to-save-the-data-in-a-dataset-as-xml-to-a-variable"></a>Pour enregistrer les données d’un DataSet au format XML dans une variable

- La méthode <xref:System.Data.DataSet.GetXml%2A> retourne une <xref:System.String>. cela signifie que vous déclarez une variable de type <xref:System.String> et que vous lui assignez les résultats de la méthode <xref:System.Data.DataSet.GetXml%2A>.

     [!code-csharp[VbRaddataSaving#12](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#12)]
     [!code-vb[VbRaddataSaving#12](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#12)]

### <a name="to-save-the-data-in-a-dataset-as-xml-to-a-file"></a>Pour enregistrer les données d’un DataSet au format XML dans un fichier

- La méthode <xref:System.Data.DataSet.WriteXml%2A> a plusieurs surcharges. Le code suivant montre comment enregistrer les données dans un fichier. Déclarez une variable et attribuez-lui un chemin d’accès valide pour enregistrer le fichier.

     [!code-csharp[VbRaddataSaving#13](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#13)]
     [!code-vb[VbRaddataSaving#13](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#13)]

## <a name="see-also"></a>Voir aussi
 [Enregistrer les données dans la base de données](../data-tools/save-data-back-to-the-database.md)
