---
title: "Comment : ajouter des contrôles ListObject aux feuilles de calcul | Documents Microsoft"
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
- ListObject control, adding to worksheets
- controls [Office development in Visual Studio], adding to worksheets
ms.assetid: 40788ecb-937f-4d2a-90ba-9c938e495b74
caps.latest.revision: "44"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 8c22c8aa98ab2b1522b2cd9094738dd251708aee
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-add-listobject-controls-to-worksheets"></a>Comment : ajouter des contrôles ListObject aux feuilles de calcul
  Vous pouvez ajouter des contrôles <xref:Microsoft.Office.Tools.Excel.ListObject> à une feuille de calcul Microsoft Office Excel au moment du design et au moment de l’exécution dans des projets au niveau du document.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Vous pouvez également ajouter des contrôles <xref:Microsoft.Office.Tools.Excel.ListObject> au moment de l’exécution dans des projets de complément VSTO.  
  
 Cette rubrique décrit les tâches suivantes :  
  
-   [Ajout de contrôles ListObject au moment du design](#designtime)  
  
-   [Ajout de contrôles ListObject au moment de l’exécution dans un projet au niveau du document](#runtimedoclevel)  
  
-   [Ajout de contrôles ListObject au moment de l’exécution dans un projet de complément VSTO](#runtimeaddin)  
  
 Pour plus d’informations sur les contrôles <xref:Microsoft.Office.Tools.Excel.ListObject> , consultez [ListObject Control](../vsto/listobject-control.md).  
  
##  <a name="designtime"></a> Adding ListObject Controls at Design Time  
 Il existe plusieurs manières d’ajouter des contrôles <xref:Microsoft.Office.Tools.Excel.ListObject> à une feuille de calcul Excel dans un projet au niveau du document au moment du design : dans Excel, à partir de la **Boîte à outils**Visual Studio, et à partir de la fenêtre **Sources de données** .  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
#### <a name="to-use-the-ribbon-in-excel"></a>Pour utiliser le ruban dans Excel  
  
1.  Sous l’onglet **Insérer** du groupe **Tableaux** , cliquez sur **Tableau**.  
  
2.  Sélectionnez la ou les cellules que vous souhaitez inclure dans la liste, puis cliquez sur **OK**.  
  
#### <a name="to-use-the-toolbox"></a>Pour utiliser la Boîte à outils  
  
1.  À partir de l’onglet **Contrôles Excel** de la **boîte à outils**, faites glisser un <xref:Microsoft.Office.Tools.Excel.ListObject> sur la feuille de calcul.  
  
     La boîte de dialogue **Ajouter un contrôle ListObject** s’affiche.  
  
2.  Sélectionnez la ou les cellules que vous souhaitez inclure dans la liste, puis cliquez sur **OK**.  
  
     Si vous ne souhaitez pas conserver le nom par défaut, vous pouvez le modifier dans la fenêtre **Propriétés** .  
  
#### <a name="to-use-the-data-sources-window"></a>Pour utiliser la fenêtre Sources de données  
  
1.  Ouvrez la fenêtre **Sources de données** et créez une source de données pour votre projet. Pour plus d’informations, consultez [ajouter de nouvelles connexions](../data-tools/add-new-connections.md).  
  
2.  Faites glisser un tableau de la fenêtre **Sources de données** vers votre feuille de calcul.  
  
     Un contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> lié aux données est ajouté à la feuille de calcul. Pour plus d'informations, consultez [Data Binding and Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms).  
  
##  <a name="runtimedoclevel"></a> Adding ListObject Controls at Run Time in a Document-Level Project  
 Vous pouvez ajouter dynamiquement le contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> au moment de l'exécution. Cela vous permet de créer les contrôles hôtes en réponse à des événements. Les objets de liste créés de manière dynamique ne sont pas persistants dans la feuille de calcul en tant que contrôles hôtes, une fois la feuille de calcul fermée. Pour plus d'informations, consultez [Adding Controls to Office Documents at Run Time](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
#### <a name="to-add-a-listobject-control-to-a-worksheet-programmatically"></a>Pour ajouter par programmation un contrôle ListObject à une feuille de calcul  
  
1.  Dans le gestionnaire d’événements <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> de `Sheet1`, insérez le code suivant pour ajouter un contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> aux cellules **A1** à **A4**.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#2](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#2)]
     [!code-vb[Trin_VstcoreHostControlsExcel#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#2)]  
  
##  <a name="runtimeaddin"></a> Adding ListObject Controls at Run Time in an VSTO Add-in project  
 Vous pouvez ajouter par programmation un contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> à une feuille de calcul ouverte dans un projet de complément VSTO. Les objets de liste créés de manière dynamique ne sont pas persistants dans la feuille de calcul en tant que contrôles hôtes, une fois la feuille de calcul enregistrée puis fermée. Pour plus d'informations, consultez [Extending Word Documents and Excel Workbooks in VSTO Add-ins at Run Time](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
#### <a name="to-add-a-listobject-control-to-a-worksheet-programmatically"></a>Pour ajouter par programmation un contrôle ListObject à une feuille de calcul  
  
1.  Le code suivant génère un élément hôte de feuille de calcul basé sur la feuille de calcul ouverte, puis ajoute un contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> aux cellules **A1** à **A4**.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#8](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#8)]
     [!code-vb[Trin_Excel_Dynamic_Controls#8](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#8)]  
  
## <a name="see-also"></a>Voir aussi  
 [Extension de Documents Word et classeurs Excel dans des Compléments VSTO au moment de l’exécution](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Contrôles sur des Documents Office](../vsto/controls-on-office-documents.md)   
 [ListObject (contrôle)](../vsto/listobject-control.md)   
 [Automatisation d’Excel à l’aide d’objets étendus](../vsto/automating-excel-by-using-extended-objects.md)   
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)   
 [Comment : redimensionner les contrôles ListObject](../vsto/how-to-resize-listobject-controls.md)   
 [Liaison de données aux contrôles dans les Solutions Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Limitations de programmation des éléments hôtes et des contrôles hôtes](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  