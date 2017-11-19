---
title: "Comment : valider des données lorsqu’une nouvelle ligne est ajoutée à un contrôle ListObject | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], validating data
- ListObject control, new row
- ListObject control, validating data
ms.assetid: 107bce92-e5ef-40be-8c05-cd6861d39d75
caps.latest.revision: "43"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4c4eb8446f26267eb0c3d5d9b2f5cdb5cfa02a78
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-validate-data-when-a-new-row-is-added-to-a-listobject-control"></a>Comment : valider des données lorsqu'une nouvelle ligne est ajoutée à un contrôle ListObject
  Les utilisateurs peuvent ajouter de nouvelles lignes à un contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> qui est lié aux données. Vous pouvez valider les données de l’utilisateur avant d’approuver les modifications apportées à la source de données.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="data-validation"></a>Validation de données  
 Chaque fois qu’une ligne est ajoutée à un <xref:Microsoft.Office.Tools.Excel.ListObject> qui est lié aux données, l’événement <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeAddDataBoundRow> est déclenché. Vous pouvez gérer cet événement pour effectuer la validation de vos données. Par exemple, si votre application requiert que seuls les employés âgés de 18 à 65 ans puissent être ajoutés à la source de données, vous pouvez vérifier que l’âge entré est compris dans cette plage avant que la ligne ne soit ajoutée.  
  
> [!NOTE]  
>  Vous devez toujours vérifier l’entrée d’utilisateur sur le client, mais aussi sur le serveur. Pour plus d’informations, consultez [sécuriser les Applications clientes](/dotnet/framework/data/adonet/secure-client-applications).  
  
#### <a name="to-validate-data-when-a-new-row-is-added-to-data-bound-listobject"></a>Pour valider des données lorsqu’une nouvelle ligne est ajoutée à un ListObject lié aux données  
  
1.  Créez des variables pour l’ID et <xref:System.Data.DataTable> au niveau de la classe.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#8](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#8)]
     [!code-vb[Trin_VstcoreHostControlsExcel#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#8)]  
  
2.  Créez un <xref:System.Data.DataTable> puis ajoutez des exemples de colonnes et de données dans le gestionnaire d’événements `Startup` de la classe `Sheet1` (dans un projet au niveau du document) ou de la classe `ThisAddIn` (dans un projet complément VSTO).  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#9](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#9)]
     [!code-vb[Trin_VstcoreHostControlsExcel#9](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#9)]  
  
3.  Ajoutez du code au gestionnaire d’événements `list1_BeforeAddDataBoundRow` pour vérifier si l’âge entré est compris dans la plage autorisée.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#10)]
     [!code-vb[Trin_VstcoreHostControlsExcel#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#10)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple de code suppose qu’un <xref:Microsoft.Office.Tools.Excel.ListObject> nommé `list1` existe dans la feuille de calcul dans laquelle ce code apparaît.  
  
## <a name="see-also"></a>Voir aussi  
 [Extension de Documents Word et classeurs Excel dans des Compléments VSTO au moment de l’exécution](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Contrôles sur des Documents Office](../vsto/controls-on-office-documents.md)   
 [Ajout de contrôles aux Documents Office au moment de l’exécution](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [ListObject (contrôle)](../vsto/listobject-control.md)   
 [Automatisation d’Excel à l’aide d’objets étendus](../vsto/automating-excel-by-using-extended-objects.md)   
 [Guide pratique pour mapper des colonnes ListObject aux données](../vsto/how-to-map-listobject-columns-to-data.md)  
  
  