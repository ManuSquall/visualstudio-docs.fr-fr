---
title: "Comment&#160;: valider des donn&#233;es lorsqu&#39;une nouvelle ligne est ajout&#233;e &#224; un contr&#244;le ListObject | Microsoft Docs"
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
  - "contrôles (développement Office dans Visual Studio), valider des données"
  - "ListObject (contrôle), nouvelle ligne"
  - "ListObject (contrôle), valider des données"
ms.assetid: 107bce92-e5ef-40be-8c05-cd6861d39d75
caps.latest.revision: 43
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 42
---
# Comment&#160;: valider des donn&#233;es lorsqu&#39;une nouvelle ligne est ajout&#233;e &#224; un contr&#244;le ListObject
  Les utilisateurs peuvent ajouter de nouvelles lignes à un contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> qui est lié aux données. Vous pouvez valider les données de l’utilisateur avant d’approuver les modifications apportées à la source de données.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## Validation de données  
 Chaque fois qu’une ligne est ajoutée à un <xref:Microsoft.Office.Tools.Excel.ListObject> qui est lié aux données, l’événement <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeAddDataBoundRow> est déclenché. Vous pouvez gérer cet événement pour effectuer la validation de vos données. Par exemple, si votre application requiert que seuls les employés âgés de 18 à 65 ans puissent être ajoutés à la source de données, vous pouvez vérifier que l’âge entré est compris dans cette plage avant que la ligne ne soit ajoutée.  
  
> [!NOTE]  
>  Vous devez toujours vérifier l’entrée d’utilisateur sur le client, mais aussi sur le serveur. Pour plus d'informations, consultez [Applications clientes sécurisées](http://msdn.microsoft.com/library/6239592e-fa7d-4dea-9f00-d296d0048b01).  
  
#### Pour valider des données lorsqu’une nouvelle ligne est ajoutée à un ListObject lié aux données  
  
1.  Créez des variables pour l’ID et <xref:System.Data.DataTable> au niveau de la classe.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#8](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#8)]
     [!code-vb[Trin_VstcoreHostControlsExcel#8](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet1.vb#8)]  
  
2.  Créez un <xref:System.Data.DataTable> puis ajoutez des exemples de colonnes et de données dans le gestionnaire d’événements `Startup` de la classe `Sheet1` \(dans un projet au niveau du document\) ou de la classe `ThisAddIn` \(dans un projet complément VSTO\).  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#9](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#9)]
     [!code-vb[Trin_VstcoreHostControlsExcel#9](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet1.vb#9)]  
  
3.  Ajoutez du code au gestionnaire d’événements `list1_BeforeAddDataBoundRow` pour vérifier si l’âge entré est compris dans la plage autorisée.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#10)]
     [!code-vb[Trin_VstcoreHostControlsExcel#10](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet1.vb#10)]  
  
## Compilation du code  
 Cet exemple de code suppose qu’un <xref:Microsoft.Office.Tools.Excel.ListObject> nommé `list1` existe dans la feuille de calcul dans laquelle ce code apparaît.  
  
## Voir aussi  
 [Extension de documents Word et de classeurs Excel dans des compléments VSTO au moment de l'exécution](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Contrôles sur des documents Office](../vsto/controls-on-office-documents.md)   
 [Ajout de contrôles à des documents Office au moment de l'exécution](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [ListObject, contrôle](../vsto/listobject-control.md)   
 [Automatisation d'Excel à l'aide d'objets étendus](../vsto/automating-excel-by-using-extended-objects.md)   
 [Comment : mapper des colonnes ListObject aux données](../vsto/how-to-map-listobject-columns-to-data.md)  
  
  