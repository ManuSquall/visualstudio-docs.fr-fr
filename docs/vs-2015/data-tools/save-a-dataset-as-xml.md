---
title: Enregistrer un jeu de données au format XML | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
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
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a91bc594f2f028f7dfc7a11263b7aac23150b7f5
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49287571"
---
# <a name="save-a-dataset-as-xml"></a>Enregistrer un dataset au format XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Les données XML dans un jeu de données sont accessible en appelant les méthodes XML disponibles sur le jeu de données. Pour enregistrer les données au format XML, vous pouvez appeler soit la <xref:System.Data.DataSet.GetXml%2A> (méthode) ou le <xref:System.Data.DataSet.WriteXml%2A> méthode d’un <xref:System.Data.DataSet>.  
  
 Appel de la <xref:System.Data.DataSet.GetXml%2A> méthode retourne une chaîne qui contient les données de toutes les tables de données dans le jeu de données est au format XML.  
  
 Appel de la <xref:System.Data.DataSet.WriteXml%2A> méthode envoie les données au format XML dans un fichier que vous spécifiez.  
  
### <a name="to-save-the-data-in-a-dataset-as-xml-to-a-variable"></a>Pour enregistrer les données dans un jeu de données au format XML à une variable  
  
-   Le <xref:System.Data.DataSet.GetXml%2A> méthode retourne un <xref:System.String>. Cela signifie que vous déclarez une variable de type <xref:System.String> et affecter les résultats de la <xref:System.Data.DataSet.GetXml%2A> (méthode).  
  
     [!code-csharp[VbRaddataSaving#12](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#12)]
     [!code-vb[VbRaddataSaving#12](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#12)]  
  
### <a name="to-save-the-data-in-a-dataset-as-xml-to-a-file"></a>Pour enregistrer les données dans un jeu de données au format XML dans un fichier  
  
-   Le <xref:System.Data.DataSet.WriteXml%2A> méthode a plusieurs surcharges. Le code suivant montre comment enregistrer les données dans un fichier. Déclarez une variable et attribuez-lui un chemin d’accès valide pour enregistrer le fichier.  
  
     [!code-csharp[VbRaddataSaving#13](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#13)]
     [!code-vb[VbRaddataSaving#13](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#13)]  
  
## <a name="see-also"></a>Voir aussi  
 [Enregistrer les données dans la base de données](../data-tools/save-data-back-to-the-database.md)

