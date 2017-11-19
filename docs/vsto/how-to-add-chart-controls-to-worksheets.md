---
title: "Comment : ajouter des contrôles Chart aux feuilles de calcul | Documents Microsoft"
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
- Chart control [Office development in Visual Studio], adding to worksheets
- controls [Office development in Visual Studio], adding to worksheets
ms.assetid: f02568e7-5caa-45b4-aa2a-4f73b0565d4e
caps.latest.revision: "44"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1ba31b5577090c3aef01ad974ba51a72e6f9980e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-add-chart-controls-to-worksheets"></a>Comment : ajouter des contrôles Chart aux feuilles de calcul
  Vous pouvez ajouter des contrôles <xref:Microsoft.Office.Tools.Excel.Chart> à une feuille de calcul Microsoft Office Excel au moment du design et au moment de l'exécution dans des personnalisations au niveau du document. Vous pouvez également ajouter des contrôles <xref:Microsoft.Office.Tools.Excel.Chart> au moment de l'exécution dans des compléments VSTO.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Cette rubrique décrit les tâches suivantes :  
  
-   [Ajout de contrôles Chart au moment du design](#designtime)  
  
-   [Ajout de contrôles Chart au moment de l’exécution dans un projet au niveau du document](#runtimedoclevel)  
  
-   [Ajout de contrôles Chart au moment de l’exécution dans un projet de complément VSTO](#runtimeaddin)  
  
 Pour plus d’informations sur <xref:Microsoft.Office.Tools.Excel.Chart> contrôles, consultez [contrôle Chart](../vsto/chart-control.md).  
  
##  <a name="designtime"></a>Ajout de contrôles Chart au moment du Design  
 Vous pouvez ajouter le contrôle <xref:Microsoft.Office.Tools.Excel.Chart> à votre feuille de calcul de la même manière que vous ajouteriez un graphique à partir de l'application.  
  
> [!NOTE]  
>  Le <xref:Microsoft.Office.Tools.Excel.Chart> contrôle n’est pas disponible à partir de la **boîte à outils** ou **des Sources de données** fenêtre.  
  
#### <a name="to-add-a-chart-host-control-to-a-worksheet-in-excel"></a>Pour ajouter un contrôle hôte Chart à une feuille de calcul dans Excel  
  
1.  Sur le **insérer** sous l’onglet du **graphiques** , cliquez sur **colonne**et cliquez sur une catégorie de graphiques, puis cliquez sur le type de graphique souhaité.  
  
2.  Dans le **insérer un graphique** boîte de dialogue, cliquez sur **OK**.  
  
3.  Sur le **conception** sous l’onglet du **données** , cliquez sur **sélectionner les données**.  
  
4.  Dans le **sélectionner une Source de données** boîte de dialogue, cliquez dans le **graphique** **plage de données** zone, puis désactivez toutes les sélections par défaut.  
  
5.  Dans le **les données de graphique** feuille, sélectionnez la plage de cellules qui contient les données pour le graphique (cellules **A5** via **D8**).  
  
6.  Dans le **sélectionner une Source de données** boîte de dialogue, cliquez sur **OK**.  
  
##  <a name="runtimedoclevel"></a>Ajout de contrôles Chart au moment de l’exécution dans un projet au niveau du Document  
 Vous pouvez ajouter dynamiquement le contrôle <xref:Microsoft.Office.Tools.Excel.Chart> au moment de l'exécution. Les graphiques créés dynamiquement ne sont pas persistants dans le document en tant que contrôles hôtes lorsque le document est fermé. Pour plus d'informations, consultez [Adding Controls to Office Documents at Run Time](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
#### <a name="to-add-a-chart-control-to-a-worksheet-programmatically"></a>Pour ajouter par programmation un contrôle Chart à une feuille de calcul  
  
1.  Dans le gestionnaire d'événements <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> de `Sheet1`, insérez le code suivant pour ajouter le contrôle <xref:Microsoft.Office.Tools.Excel.Chart>  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#1](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#1)]
     [!code-vb[Trin_VstcoreHostControlsExcel#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#1)]  
  
##  <a name="runtimeaddin"></a>Ajout de contrôles Chart au moment de l’exécution dans un projet de complément VSTO  
 Vous pouvez ajouter par programmation un contrôle <xref:Microsoft.Office.Tools.Excel.Chart> à une feuille de calcul ouverte dans un projet de complément VSTO. Pour plus d'informations, consultez [Extending Word Documents and Excel Workbooks in VSTO Add-ins at Run Time](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
 Les contrôles Chart créés dynamiquement ne sont pas persistants dans la feuille de calcul en tant que contrôles hôtes lorsque la feuille de calcul est fermée. Pour plus d'informations, consultez [Adding Controls to Office Documents at Run Time](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
#### <a name="to-add-a-chart-control-to-a-worksheet-programmatically"></a>Pour ajouter par programmation un contrôle Chart à une feuille de calcul  
  
1.  Le code suivant génère un élément hôte de feuille de calcul basé sur la feuille de calcul ouverte, puis ajoute un contrôle <xref:Microsoft.Office.Tools.Excel.Chart>.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#9](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#9)]
     [!code-vb[Trin_Excel_Dynamic_Controls#9](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#9)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple exige les éléments suivants :  
  
-   les données à représenter sur le graphique, stockées dans la plage comprenant les cellules A5 à D8 de la feuille de calcul.  
  
## <a name="see-also"></a>Voir aussi  
 [Extension de Documents Word et classeurs Excel dans des Compléments VSTO au moment de l’exécution](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Contrôles sur des Documents Office](../vsto/controls-on-office-documents.md)   
 [Chart (contrôle)](../vsto/chart-control.md)   
 [Automatisation d’Excel à l’aide d’objets étendus](../vsto/automating-excel-by-using-extended-objects.md)   
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)   
 [Liaison de données aux contrôles dans les Solutions Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Limitations de programmation des éléments hôtes et des contrôles hôtes](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  