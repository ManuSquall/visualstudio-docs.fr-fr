---
title: "Comment&#160;: ajouter des contr&#244;les ListObject aux feuilles de calcul | Microsoft Docs"
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
  - "ListObject (contrôle), ajout à des feuilles de calcul"
  - "contrôles (développement Office dans Visual Studio), ajout à des feuilles de calcul"
ms.assetid: 40788ecb-937f-4d2a-90ba-9c938e495b74
caps.latest.revision: 44
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 43
---
# Comment&#160;: ajouter des contr&#244;les ListObject aux feuilles de calcul
  Vous pouvez ajouter des contrôles <xref:Microsoft.Office.Tools.Excel.ListObject> à une feuille de calcul Microsoft Office Excel au moment du design et au moment de l’exécution dans des projets au niveau du document.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Vous pouvez également ajouter des contrôles <xref:Microsoft.Office.Tools.Excel.ListObject> au moment de l’exécution dans des projets de complément VSTO.  
  
 Cette rubrique décrit les tâches suivantes :  
  
-   [Ajout de contrôles ListObject au moment du design](#designtime)  
  
-   [Ajout de contrôles ListObject au moment de l’exécution dans un projet au niveau du document](#runtimedoclevel)  
  
-   [Ajout de contrôles ListObject au moment de l’exécution dans un projet de complément VSTO](#runtimeaddin)  
  
 Pour plus d’informations sur les contrôles <xref:Microsoft.Office.Tools.Excel.ListObject>, consultez [ListObject, contrôle](../vsto/listobject-control.md).  
  
##  <a name="designtime"></a> Ajout de contrôles ListObject au moment du design  
 Il existe plusieurs manières d’ajouter des contrôles <xref:Microsoft.Office.Tools.Excel.ListObject> à une feuille de calcul Excel dans un projet au niveau du document au moment du design : dans Excel, à partir de la **Boîte à outils** Visual Studio, et à partir de la fenêtre **Sources de données**.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
#### Pour utiliser le ruban dans Excel  
  
1.  Sous l’onglet **Insérer** du groupe **Tableaux**, cliquez sur **Tableau**.  
  
2.  Sélectionnez la ou les cellules que vous souhaitez inclure dans la liste, puis cliquez sur **OK**.  
  
#### Pour utiliser la Boîte à outils  
  
1.  À partir de l’onglet **Contrôles Excel**  de la **boîte à outils**, faites glisser un <xref:Microsoft.Office.Tools.Excel.ListObject> sur la feuille de calcul.  
  
     La boîte de dialogue **Ajouter un contrôle ListObject** s’affiche.  
  
2.  Sélectionnez la ou les cellules que vous souhaitez inclure dans la liste, puis cliquez sur **OK**.  
  
     Si vous ne souhaitez pas conserver le nom par défaut, vous pouvez le modifier dans la fenêtre **Propriétés**.  
  
#### Pour utiliser la fenêtre Sources de données  
  
1.  Ouvrez la fenêtre **Sources de données** et créez une source de données pour votre projet. Pour plus d'informations, consultez [Comment : établir une connexion à des données d'une base de données](~/data-tools/how-to-connect-to-data-in-a-database.md).  
  
2.  Faites glisser un tableau de la fenêtre **Sources de données** vers votre feuille de calcul.  
  
     Un contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> lié aux données est ajouté à la feuille de calcul. Pour plus d'informations, consultez [Liaison de données et Windows Forms](http://msdn.microsoft.com/library/419aac5e-819b-4aad-88b0-73a2f8c0bd27).  
  
##  <a name="runtimedoclevel"></a> Ajout de contrôles ListObject au moment de l’exécution dans un projet au niveau du document  
 Vous pouvez ajouter dynamiquement le contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> au moment de l'exécution. Cela vous permet de créer les contrôles hôtes en réponse à des événements. Les objets de liste créés de manière dynamique ne sont pas persistants dans la feuille de calcul en tant que contrôles hôtes, une fois la feuille de calcul fermée. Pour plus d'informations, consultez [Ajout de contrôles à des documents Office au moment de l'exécution](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
#### Pour ajouter par programmation un contrôle ListObject à une feuille de calcul  
  
1.  Dans le gestionnaire d’événements <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> de `Sheet1`, insérez le code suivant pour ajouter un contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> aux cellules **A1** à **A4**.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#2)]
     [!code-vb[Trin_VstcoreHostControlsExcel#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet1.vb#2)]  
  
##  <a name="runtimeaddin"></a> Ajout de contrôles ListObject au moment de l’exécution dans un projet de complément VSTO  
 Vous pouvez ajouter par programmation un contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> à une feuille de calcul ouverte dans un projet de complément VSTO. Les objets de liste créés de manière dynamique ne sont pas persistants dans la feuille de calcul en tant que contrôles hôtes, une fois la feuille de calcul enregistrée puis fermée. Pour plus d'informations, consultez [Extension de documents Word et de classeurs Excel dans des compléments VSTO au moment de l'exécution](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
#### Pour ajouter par programmation un contrôle ListObject à une feuille de calcul  
  
1.  Le code suivant génère un élément hôte de feuille de calcul basé sur la feuille de calcul ouverte, puis ajoute un contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> aux cellules **A1** à **A4**.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#8](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/CS/ThisAddIn.cs#8)]
     [!code-vb[Trin_Excel_Dynamic_Controls#8](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/VB/ThisAddIn.vb#8)]  
  
## Voir aussi  
 [Extension de documents Word et de classeurs Excel dans des compléments VSTO au moment de l'exécution](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Contrôles sur des documents Office](../vsto/controls-on-office-documents.md)   
 [ListObject, contrôle](../vsto/listobject-control.md)   
 [Automatisation d'Excel à l'aide d'objets étendus](../vsto/automating-excel-by-using-extended-objects.md)   
 [Vue d'ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)   
 [Comment : redimensionner les contrôles ListObject](../vsto/how-to-resize-listobject-controls.md)   
 [Liaison de données aux contrôles dans les solutions Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Limitations de programmation des éléments hôtes et des contrôles hôtes](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  