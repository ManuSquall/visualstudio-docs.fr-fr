---
title: "Comment&#160;: mettre en cache par programmation une source de donn&#233;es dans un document Office | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "données (développement Office dans Visual Studio), mettre en cache"
  - "mise en cache de données (développement Office dans Visual Studio), par programmation"
  - "groupes de données (développement Office dans Visual Studio), mettre en cache"
  - "applications Office (développement Office dans Visual Studio), données"
  - "StartCaching (méthode)"
ms.assetid: 70b3fc06-7534-407e-898b-36f84e9a7516
caps.latest.revision: 43
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 43
---
# Comment&#160;: mettre en cache par programmation une source de donn&#233;es dans un document Office
  Vous pouvez ajouter par programmation un objet de données dans le cache de données d'un document en appelant la méthode `StartCaching` d'un élément hôte, tel qu'un <xref:Microsoft.Office.Tools.Word.Document>, <xref:Microsoft.Office.Tools.Excel.Workbook> ou <xref:Microsoft.Office.Tools.Excel.Worksheet>.  Supprimez un objet de données du cache de données en appelant la méthode `StopCaching` d'un élément hôte.  
  
 Les méthodes `StartCaching` et `StopCaching` sont privées mais apparaissent dans IntelliSense.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Lorsque vous utilisez la méthode `StartCaching` pour ajouter un objet de données dans le cache de données, il n'est pas nécessaire que l'objet de données soit déclaré avec l'attribut <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute>.  Toutefois, l'objet de données doit satisfaire à certaines exigences pour être ajouté au cache de données.  Pour plus d’informations, consultez [Mise en cache des données](../vsto/caching-data.md).  
  
### Pour mettre en cache un objet de données par programmation  
  
1.  Déclarez l'objet de données au niveau de la classe, et non au sein d'une méthode.  Cet exemple suppose que vous déclarez un <xref:System.Data.DataSet> nommé `dataSet1` que vous souhaitez mettre en cache par programmation.  
  
     [!code-csharp[Trin_VstcoreDataExcel#12](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#12)]
     [!code-vb[Trin_VstcoreDataExcel#12](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet1.vb#12)]  
  
2.  Instanciez l'objet de données, puis appelez la méthode `StartCaching` de l'instance du document ou de la feuille de calcul et passez le nom de l'objet de données.  
  
     [!code-csharp[Trin_VstcoreDataExcel#13](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#13)]
     [!code-vb[Trin_VstcoreDataExcel#13](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet1.vb#13)]  
  
### Pour arrêter la mise en cache d'un objet de données  
  
1.  Appelez la méthode `StopCaching` de l'instance du document ou de la feuille de calcul et passez le nom de l'objet de données.  Cet exemple suppose que vous avez un <xref:System.Data.DataSet> nommé `dataSet1` dont vous souhaitez arrêter la mise en cache.  
  
     [!code-csharp[Trin_VstcoreDataExcel#14](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#14)]
     [!code-vb[Trin_VstcoreDataExcel#14](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet1.vb#14)]  
  
    > [!NOTE]  
    >  N'appelez pas `StopCaching` à partir du gestionnaire d'événements pour l'événement `Shutdown` d'un document ou d'une feuille de calcul.  Lorsque l'événement `Shutdown` est déclenché, il est trop tard pour modifier le cache de données.  Pour plus d'informations sur l'événement `Shutdown`, consultez [Événements dans les projets Office](../vsto/events-in-office-projects.md).  
  
## Voir aussi  
 [Mise en cache des données](../vsto/caching-data.md)   
 [Comment : mettre en cache des données pour une utilisation hors connexion ou sur un serveur](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)   
 [Comment : mettre en cache des données dans un document protégé par un mot de passe](../vsto/how-to-cache-data-in-a-password-protected-document.md)   
 [Accès aux données des documents sur le serveur](../vsto/accessing-data-in-documents-on-the-server.md)   
 [Enregistrement des données](../data-tools/saving-data.md)  
  
  