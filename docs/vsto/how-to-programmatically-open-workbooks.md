---
title: "Comment : ouvrir des classeurs par programmation | Documents Microsoft"
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
- workbooks, opening
- Excel [Office development in Visual Studio], opening workbooks
ms.assetid: 06c0ac87-a2c6-4cc1-87be-39be0cb81c71
caps.latest.revision: "36"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e7768aec2684e95c0201c88713e4a342737ce3cd
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-open-workbooks"></a>Comment : ouvrir des classeurs par programmation
  Le <xref:Microsoft.Office.Interop.Excel.Workbooks> collection dans Microsoft Office Excel permet de travailler avec tous les classeurs ouverts et d’ouvrir des classeurs.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
### <a name="to-open-an-existing-workbook"></a>Pour ouvrir un classeur existant  
  
1.  Utilisez le <xref:Microsoft.Office.Interop.Excel.Workbooks.Open%2A> méthode de la <xref:Microsoft.Office.Interop.Excel.Workbooks> collection, en passant le chemin d’accès au classeur.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#2](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#2)]
     [!code-vb[Trin_VstcoreExcelAutomation#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#2)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple de code doit respecter la condition suivante :  
  
-   Un classeur nommé `YourWorkbook.xls` doit exister dans un répertoire nommé `Test` sur le lecteur C.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation des classeurs](../vsto/working-with-workbooks.md)   
 [Comment : ouvrir des fichiers texte en tant que classeurs par programmation](../vsto/how-to-programmatically-open-text-files-as-workbooks.md)   
 [Comment : créer des classeurs par programmation](../vsto/how-to-programmatically-create-new-workbooks.md)   
 [Comment : enregistrer des classeurs par programmation](../vsto/how-to-programmatically-save-workbooks.md)   
 [Comment : fermer des classeurs par programmation](../vsto/how-to-programmatically-close-workbooks.md)   
 [Programmatic Limitations of Host Items and Host Controls](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Paramètres optionnels dans les Solutions Office](../vsto/optional-parameters-in-office-solutions.md)   
 [Vue d’ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)  
  
  