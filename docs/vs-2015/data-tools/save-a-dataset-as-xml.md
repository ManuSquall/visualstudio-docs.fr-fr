---
title: Enregistrer un jeu de données au format XML | Microsoft Docs
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 2e4331b59c532e681c7e10ab8e43b953e9f72b18
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62559555"
---
# <a name="save-a-dataset-as-xml"></a>Enregistrer un dataset au format XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les données XML dans un jeu de données sont accessible en appelant les méthodes XML disponibles sur le jeu de données. Pour enregistrer les données au format XML, vous pouvez appeler soit la <xref:System.Data.DataSet.GetXml%2A> (méthode) ou le <xref:System.Data.DataSet.WriteXml%2A> méthode d’un <xref:System.Data.DataSet>.  
  
 Appel de la <xref:System.Data.DataSet.GetXml%2A> méthode retourne une chaîne qui contient les données de toutes les tables de données dans le jeu de données est au format XML.  
  
 Appel de la <xref:System.Data.DataSet.WriteXml%2A> méthode envoie les données au format XML dans un fichier que vous spécifiez.  
  
### <a name="to-save-the-data-in-a-dataset-as-xml-to-a-variable"></a>Pour enregistrer les données dans un jeu de données au format XML à une variable  
  
- Le <xref:System.Data.DataSet.GetXml%2A> méthode retourne un <xref:System.String>. Cela signifie que vous déclarez une variable de type <xref:System.String> et affecter les résultats de la <xref:System.Data.DataSet.GetXml%2A> (méthode).  
  
     [!code-csharp[VbRaddataSaving#12](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#12)]
     [!code-vb[VbRaddataSaving#12](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#12)]  
  
### <a name="to-save-the-data-in-a-dataset-as-xml-to-a-file"></a>Pour enregistrer les données dans un jeu de données au format XML dans un fichier  
  
- Le <xref:System.Data.DataSet.WriteXml%2A> méthode a plusieurs surcharges. Le code suivant montre comment enregistrer les données dans un fichier. Déclarez une variable et attribuez-lui un chemin d’accès valide pour enregistrer le fichier.  
  
     [!code-csharp[VbRaddataSaving#13](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#13)]
     [!code-vb[VbRaddataSaving#13](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#13)]  
  
## <a name="see-also"></a>Voir aussi  
 [Enregistrer les données dans la base de données](../data-tools/save-data-back-to-the-database.md)
