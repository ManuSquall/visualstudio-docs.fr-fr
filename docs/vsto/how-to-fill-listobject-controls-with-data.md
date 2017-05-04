---
title: "Comment&#160;: remplir de donn&#233;es des contr&#244;les ListObject | Microsoft Docs"
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
  - "déconnecter de sources de données"
  - "ListObject (contrôle), déconnecter d’une source de données"
  - "ListObject (contrôle), remplir avec des données"
  - "données (développement Office dans Visual Studio), ajouter à des feuilles de calcul"
  - "liaison de données, contrôles ListObject"
  - "feuilles de calcul, remplir avec des données"
ms.assetid: bf692c77-f5cc-456a-9a5c-84ed3067d7eb
caps.latest.revision: 27
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 26
---
# Comment&#160;: remplir de donn&#233;es des contr&#244;les ListObject
  Vous pouvez utiliser la liaison de données comme moyen pour ajouter rapidement des données à votre document. Après avoir lié les données à un objet de liste, vous pouvez déconnecter celui\-ci de manière à ce qu’il affiche les données mais ne soit plus lié à leur source.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 ![lien vers la vidéo](../vsto/media/playvideo.png "lien vers la vidéo") Pour visionner une démonstration vidéo associée, consultez [Comment faire pour créer, dans Excel, une liste qui soit connectée à une liste SharePoint ?](http://go.microsoft.com/fwlink/?LinkID=130263).  
  
### Pour lier des données à un contrôle ListObject  
  
1.  Créez un <xref:System.Data.DataTable> au niveau de la classe.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#20](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet4.cs#20)]
     [!code-vb[Trin_VstcoreHostControlsExcel#20](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet4.vb#20)]  
  
2.  Ajoutez des exemples de colonnes et de données dans le gestionnaire d’événements `Startup` de la classe `Sheet1` \(dans un projet au niveau du document\) ou de la classe `ThisAddIn` \(dans un projet au niveau de l’application\).  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#21](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet4.cs#21)]
     [!code-vb[Trin_VstcoreHostControlsExcel#21](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet4.vb#21)]  
  
3.  Appelez la méthode <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> et passez les noms des colonnes dans l’ordre dans lequel elles doivent apparaître. L’ordre des colonnes dans l’objet de liste peut différer de l’ordre dans lequel elles apparaissent dans le <xref:System.Data.DataTable>.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#22](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet4.cs#22)]
     [!code-vb[Trin_VstcoreHostControlsExcel#22](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet4.vb#22)]  
  
### Pour déconnecter le contrôle ListObject de la source de données  
  
1.  Appelez la méthode <xref:Microsoft.Office.Tools.Excel.ListObject.Disconnect%2A> de `List1`.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#23](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet4.cs#23)]
     [!code-vb[Trin_VstcoreHostControlsExcel#23](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet4.vb#23)]  
  
## Compilation du code  
 Cet exemple de code suppose qu’un <xref:Microsoft.Office.Tools.Excel.ListObject> nommé `list1` existe dans la feuille de calcul dans laquelle ce code apparaît.  
  
## Voir aussi  
 [Extension de documents Word et de classeurs Excel dans des compléments VSTO au moment de l'exécution](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Contrôles sur des documents Office](../vsto/controls-on-office-documents.md)   
 [Ajout de contrôles à des documents Office au moment de l'exécution](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Comment : mapper des colonnes ListObject aux données](../vsto/how-to-map-listobject-columns-to-data.md)   
 [Automatisation d'Excel à l'aide d'objets étendus](../vsto/automating-excel-by-using-extended-objects.md)   
 [ListObject, contrôle](../vsto/listobject-control.md)   
 [Liaison de données aux contrôles dans les solutions Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Comment : remplir des feuilles de calcul avec des données provenant d'une base de données](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)   
 [Comment : remplir des documents avec les données de services](../vsto/how-to-populate-documents-with-data-from-services.md)  
  
  