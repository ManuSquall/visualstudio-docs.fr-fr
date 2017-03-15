---
title: "Comment&#160;: enregistrer un Dataset au format XML | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "données (Visual Studio), enregistrer comme XML"
  - "groupes de données (Visual Basic), enregistrer comme XML"
  - "enregistrer les données"
  - "XML (Visual Basic), groupes de données"
ms.assetid: 68b8327c-ae05-49ff-b9ba-99183e70b52c
caps.latest.revision: 11
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Comment&#160;: enregistrer un Dataset au format XML
Les données XML d'un groupe de données sont accessibles en appelant les méthodes XML disponibles dans le groupe de données.  Pour enregistrer des données au format XML, vous pouvez appeler soit la méthode <xref:System.Data.DataSet.GetXml%2A> soit la méthode <xref:System.Data.DataSet.WriteXml%2A> d'un <xref:System.Data.DataSet>.  
  
 L'appel à la méthode <xref:System.Data.DataSet.GetXml%2A> retourne une chaîne contenant les données provenant de toutes les tables de données du groupe de données au format XML.  
  
 L'appel à la méthode <xref:System.Data.DataSet.WriteXml%2A> envoie les données au format XML dans un fichier que vous spécifiez.  
  
### Pour enregistrer les données d'un groupe de données en tant que XML dans une variable  
  
-   La méthode <xref:System.Data.DataSet.GetXml%2A> retournant une <xref:System.String>, déclarez une variable de type <xref:System.String> et assignez\-lui les résultats de la méthode <xref:System.Data.DataSet.GetXml%2A>.  
  
     [!code-vb[VbRaddataSaving#12](../data-tools/codesnippet/VisualBasic/save-a-dataset-as-xml_1.vb)]
     [!code-cs[VbRaddataSaving#12](../data-tools/codesnippet/CSharp/save-a-dataset-as-xml_1.cs)]  
  
### Pour enregistrer les données d'un groupe de données en tant que XML dans un fichier  
  
-   La méthode <xref:System.Data.DataSet.WriteXml%2A> a plusieurs surcharges.  Le code suivant indique comment enregistrer les données dans un fichier. Déclarez une variable et assignez\-lui un chemin d'accès valide dans lequel enregistrer le fichier.  
  
     [!code-vb[VbRaddataSaving#13](../data-tools/codesnippet/VisualBasic/save-a-dataset-as-xml_2.vb)]
     [!code-cs[VbRaddataSaving#13](../data-tools/codesnippet/CSharp/save-a-dataset-as-xml_2.cs)]  
  
## Voir aussi  
 [Objets DataSet, DataTable et DataView](../Topic/DataSets,%20DataTables,%20and%20DataViews.md)   
 [Outils XML dans Visual Studio](../xml-tools/xml-tools-in-visual-studio.md)   
 [Préparation de votre application pour recevoir des données](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Connexion aux données dans Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Préparation de votre application pour recevoir des données](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Extraction de données dans votre application](../data-tools/fetching-data-into-your-application.md)   
 [Liaison de contrôles à des données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modification des données dans votre application](../data-tools/editing-data-in-your-application.md)   
 [Validation des données](../Topic/Validating%20Data.md)   
 [Enregistrement des données](../data-tools/saving-data.md)