---
title: Enregistrer un jeu de données au format XML | Documents Microsoft
ms.custom: ''
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
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: b9d91e964ddade89c8bce8f0519517995b7d75a0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="save-a-dataset-as-xml"></a>Enregistrer un jeu de données au format XML
Les données XML dans un jeu de données est accessible en appelant les méthodes XML disponibles sur le jeu de données. Pour enregistrer les données au format XML, vous pouvez appeler la <xref:System.Data.DataSet.GetXml%2A> (méthode) ou le <xref:System.Data.DataSet.WriteXml%2A> méthode d’un <xref:System.Data.DataSet>.  
  
 Appel de la <xref:System.Data.DataSet.GetXml%2A> méthode retourne une chaîne qui contient les données de toutes les tables de données dans le jeu de données au format XML.  
  
 Appel de la <xref:System.Data.DataSet.WriteXml%2A> méthode envoie les données au format XML dans un fichier que vous spécifiez.  
  
### <a name="to-save-the-data-in-a-dataset-as-xml-to-a-variable"></a>Pour enregistrer les données dans un jeu de données au format XML à une variable  
  
-   Le <xref:System.Data.DataSet.GetXml%2A> méthode retourne un <xref:System.String>. Cela signifie que vous déclarez une variable de type <xref:System.String> et affecter les résultats de la <xref:System.Data.DataSet.GetXml%2A> (méthode).  
  
     [!code-vb[VbRaddataSaving#12](../data-tools/codesnippet/VisualBasic/save-a-dataset-as-xml_1.vb)]
     [!code-csharp[VbRaddataSaving#12](../data-tools/codesnippet/CSharp/save-a-dataset-as-xml_1.cs)]  
  
### <a name="to-save-the-data-in-a-dataset-as-xml-to-a-file"></a>Pour enregistrer les données dans un jeu de données au format XML dans un fichier  
  
-   Le <xref:System.Data.DataSet.WriteXml%2A> méthode a plusieurs surcharges. Le code suivant montre comment enregistrer les données dans un fichier. Déclarez une variable et l’assigner à un chemin d’accès valide pour enregistrer le fichier.  
  
     [!code-vb[VbRaddataSaving#13](../data-tools/codesnippet/VisualBasic/save-a-dataset-as-xml_2.vb)]
     [!code-csharp[VbRaddataSaving#13](../data-tools/codesnippet/CSharp/save-a-dataset-as-xml_2.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 [Enregistrer les données dans la base de données](../data-tools/save-data-back-to-the-database.md)