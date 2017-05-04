---
title: "Comment&#160;: ajouter des contr&#244;les NamedRange aux feuilles de calcul | Microsoft Docs"
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
  - "plages, ajouter à des feuilles de calcul"
  - "contrôle NamedRange, ajouter à des feuilles de calcul"
  - "contrôles (développement Office dans Visual Studio), ajouter à des feuilles de calcul"
ms.assetid: da7ec48f-92cb-4fa3-b3e2-447c238d17a8
caps.latest.revision: 54
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 53
---
# Comment&#160;: ajouter des contr&#244;les NamedRange aux feuilles de calcul
  Vous pouvez ajouter des contrôles <xref:Microsoft.Office.Tools.Excel.NamedRange> à une feuille de calcul Microsoft Office Excel au moment de la conception et au moment de l’exécution dans des projets au niveau du document.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Vous pouvez aussi ajouter des contrôles <xref:Microsoft.Office.Tools.Excel.NamedRange> au moment de l’exécution dans des projets de complément VSTO.  
  
 Cette rubrique décrit les tâches suivantes :  
  
-   [Ajout de contrôles NamedRange au moment de la conception](#designtime)  
  
-   [Ajout de contrôles NamedRange au moment de l’exécution dans un projet au niveau du document](#runtimedoclevel)  
  
-   [Ajout de contrôles NamedRange au moment de l’exécution dans un projet de complément VSTO](#runtimeaddin)  
  
 Pour plus d’informations sur les contrôles <xref:Microsoft.Office.Tools.Excel.NamedRange>, consultez [NamedRange, contrôle](../vsto/namedrange-control.md).  
  
##  <a name="designtime"></a> Ajout de contrôles NamedRange au moment de la conception  
 Il existe plusieurs façons d’ajouter des contrôles <xref:Microsoft.Office.Tools.Excel.NamedRange> à une feuille de calcul dans un projet au niveau du document au moment de la conception : dans Excel, à partir de la **Boîte à outils** Visual Studio, et à partir de la fenêtre **Sources de données**.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
#### Pour ajouter un contrôle NamedRange à une feuille de calcul via la Zone Nom d’Excel  
  
1.  Sélectionnez la ou les cellules que vous souhaitez inclure dans l'étendue nommée.  
  
2.  Dans la **Zone Nom**, tapez un nom pour la plage et appuyez sur Entrée.  
  
     La **Zone Nom** se trouve à côté de la barre de formule, juste au\-dessus de la colonne **A** de la feuille de calcul.  
  
#### Pour ajouter un contrôle NamedRange à une feuille de calcul via la Boîte à outils  
  
1.  Ouvrez la **Boîte à outils**, puis cliquez sur l’onglet **Contrôles Excel**.  
  
2.  Cliquez sur <xref:Microsoft.Office.Tools.Excel.NamedRange> et faites\-le glisser vers une feuille de calcul.  
  
     La boîte de dialogue **Ajouter une plage nommée** s’affiche.  
  
3.  Sélectionnez la ou les cellules que vous souhaitez inclure dans l'étendue nommée.  
  
4.  Cliquez sur **OK**.  
  
     Si vous ne voulez pas du nom attribué par défaut au contrôle, vous pouvez le modifier dans la fenêtre **Propriétés**.  
  
#### Pour ajouter un contrôle NamedRange à une feuille de calcul via la fenêtre Sources de données  
  
1.  Ouvrez la fenêtre **Sources de données** et créez une source de données pour votre projet. Pour plus d'informations, consultez [Comment : établir une connexion à des données d'une base de données](~/data-tools/how-to-connect-to-data-in-a-database.md).  
  
2.  Faites glisser un seul champ de la fenêtre **Sources de données** vers votre feuille de calcul.  
  
     Un contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange> lié aux données est ajouté à la feuille de calcul. Pour plus d'informations, consultez [Liaison de données et Windows Forms](http://msdn.microsoft.com/library/419aac5e-819b-4aad-88b0-73a2f8c0bd27).  
  
##  <a name="runtimedoclevel"></a> Ajout de contrôles NamedRange au moment de l’exécution dans un projet au niveau du document  
 Vous pouvez ajouter un <xref:Microsoft.Office.Tools.Excel.NamedRange> contrôle par programmation à votre feuille de calcul au moment de l’exécution. Cela vous permet de créer les contrôles hôtes en réponse à des événements. Les plages nommées créées dynamiquement ne sont pas conservées dans la feuille de calcul en tant que contrôles hôtes au moment où la feuille de calcul est fermée. Pour plus d'informations, consultez [Ajout de contrôles à des documents Office au moment de l'exécution](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
#### Pour ajouter un contrôle NamedRange à une feuille de calcul par programmation  
  
1.  Dans le gestionnaire d’événements <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> de `Sheet1`, insérez le code suivant pour ajouter le contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange> à la cellule **A1** et attribuez à sa propriété <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> la valeur `Hello world!`  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#3)]
     [!code-vb[Trin_VstcoreHostControlsExcel#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet1.vb#3)]  
  
##  <a name="runtimeaddin"></a> Ajout de contrôles NamedRange au moment de l’exécution dans un projet de complément VSTO  
 Vous pouvez ajouter un contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange> par programmation à une feuille de calcul ouverte dans un projet de complément VSTO. Les plages nommées créées dynamiquement ne sont pas conservées dans la feuille de calcul en tant que contrôles hôtes au moment où la feuille de calcul est fermée. Pour plus d'informations, consultez [Extension de documents Word et de classeurs Excel dans des compléments VSTO au moment de l'exécution](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
#### Pour ajouter un contrôle NamedRange à une feuille de calcul par programmation  
  
1.  Le code suivant génère un élément hôte de feuille de calcul basé sur la feuille de calcul ouverte, puis ajoute un contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange> à la cellule **A1** et attribue à sa propriété <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> la valeur `Hello world`.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#7](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/CS/ThisAddIn.cs#7)]
     [!code-vb[Trin_Excel_Dynamic_Controls#7](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/VB/ThisAddIn.vb#7)]  
  
## Voir aussi  
 [Extension de documents Word et de classeurs Excel dans des compléments VSTO au moment de l'exécution](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Contrôles sur des documents Office](../vsto/controls-on-office-documents.md)   
 [NamedRange, contrôle](../vsto/namedrange-control.md)   
 [Automatisation d'Excel à l'aide d'objets étendus](../vsto/automating-excel-by-using-extended-objects.md)   
 [Vue d'ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)   
 [Comment : redimensionner les contrôles NamedRange](../vsto/how-to-resize-namedrange-controls.md)   
 [Limitations de programmation des éléments hôtes et des contrôles hôtes](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  