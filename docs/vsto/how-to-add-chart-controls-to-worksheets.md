---
title: "Comment&#160;: ajouter des contr&#244;les Chart aux feuilles de calcul | Microsoft Docs"
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
  - "Chart (contrôle) (développement Office dans Visual Studio), ajouter à des feuilles de calcul"
  - "contrôles (développement Office dans Visual Studio), ajouter à des feuilles de calcul"
ms.assetid: f02568e7-5caa-45b4-aa2a-4f73b0565d4e
caps.latest.revision: 44
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 42
---
# Comment&#160;: ajouter des contr&#244;les Chart aux feuilles de calcul
  Vous pouvez ajouter des contrôles <xref:Microsoft.Office.Tools.Excel.Chart> à une feuille de calcul Microsoft Office Excel au moment du design et au moment de l'exécution dans des personnalisations au niveau du document.  Vous pouvez également ajouter des contrôles <xref:Microsoft.Office.Tools.Excel.Chart> au moment de l'exécution dans des compléments VSTO.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Cette rubrique décrit les tâches suivantes :  
  
-   [Ajout de contrôles Chart au moment du design](#designtime)  
  
-   [Ajout de contrôles Chart au moment de l'exécution dans un projet au niveau du document](#runtimedoclevel)  
  
-   [Ajout de contrôles Chart au moment de l'exécution dans un projet de complément VSTO](#runtimeaddin)  
  
 Pour plus d'informations sur les contrôles <xref:Microsoft.Office.Tools.Excel.Chart>, consultez [Chart, contrôle](../vsto/chart-control.md).  
  
##  <a name="designtime"></a> Ajout de contrôles Chart au moment du design  
 Vous pouvez ajouter le contrôle <xref:Microsoft.Office.Tools.Excel.Chart> à votre feuille de calcul de la même manière que vous ajouteriez un graphique à partir de l'application.  
  
> [!NOTE]  
>  Le contrôle <xref:Microsoft.Office.Tools.Excel.Chart> n'est pas disponible à partir de la **boîte à outils** ou de la fenêtre **Sources de données**.  
  
#### Pour ajouter un contrôle hôte Chart à une feuille de calcul dans Excel  
  
1.  Sous l'onglet **Insérer**, dans le groupe **Graphiques**, cliquez sur **Colonne**, cliquez sur une catégorie de graphiques, puis cliquez sur le type de graphique souhaité.  
  
2.  Dans la boîte de dialogue **Insérer un graphique**, cliquez sur **OK**.  
  
3.  Sous l'onglet **Création**, dans le groupe **Données**, cliquez sur **Sélectionner des données**.  
  
4.  Dans la boîte de dialogue **Sélectionner une source de données**, cliquez dans la zone **Plage de données dugraphique** et effacez toutes les sélections par défaut.  
  
5.  Dans la feuille **Données pour Graphique**, sélectionnez la plage de cellules qui contient les données du graphique \(cellules **A5** à **D8**\).  
  
6.  Dans la boîte de dialogue **Sélectionner une source de données**, cliquez sur **OK**.  
  
##  <a name="runtimedoclevel"></a> Ajout de contrôles Chart au moment de l'exécution dans un projet au niveau du document  
 Vous pouvez ajouter dynamiquement le contrôle <xref:Microsoft.Office.Tools.Excel.Chart> au moment de l'exécution.  Les graphiques créés dynamiquement ne sont pas persistants dans le document en tant que contrôles hôtes lorsque le document est fermé.  Pour plus d'informations, consultez [Ajout de contrôles à des documents Office au moment de l'exécution](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
#### Pour ajouter par programmation un contrôle Chart à une feuille de calcul  
  
1.  Dans le gestionnaire d'événements <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> de `Sheet1`, insérez le code suivant pour ajouter le contrôle <xref:Microsoft.Office.Tools.Excel.Chart>  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#1)]
     [!code-vb[Trin_VstcoreHostControlsExcel#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet1.vb#1)]  
  
##  <a name="runtimeaddin"></a> Ajout de contrôles Chart au moment de l'exécution dans un projet de complément VSTO  
 Vous pouvez ajouter par programmation un contrôle <xref:Microsoft.Office.Tools.Excel.Chart> à une feuille de calcul ouverte dans un projet de complément VSTO.  Pour plus d'informations, consultez [Extension de documents Word et de classeurs Excel dans des compléments VSTO au moment de l'exécution](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
 Les contrôles Chart créés dynamiquement ne sont pas persistants dans la feuille de calcul en tant que contrôles hôtes lorsque la feuille de calcul est fermée.  Pour plus d'informations, consultez [Ajout de contrôles à des documents Office au moment de l'exécution](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
#### Pour ajouter par programmation un contrôle Chart à une feuille de calcul  
  
1.  Le code suivant génère un élément hôte de feuille de calcul basé sur la feuille de calcul ouverte, puis ajoute un contrôle <xref:Microsoft.Office.Tools.Excel.Chart>.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#9](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/CS/ThisAddIn.cs#9)]
     [!code-vb[Trin_Excel_Dynamic_Controls#9](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/VB/ThisAddIn.vb#9)]  
  
## Compilation du code  
 Cet exemple exige les éléments suivants :  
  
-   les données à représenter sur le graphique, stockées dans la plage comprenant les cellules A5 à D8 de la feuille de calcul.  
  
## Voir aussi  
 [Extension de documents Word et de classeurs Excel dans des compléments VSTO au moment de l'exécution](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Contrôles sur des documents Office](../vsto/controls-on-office-documents.md)   
 [Chart, contrôle](../vsto/chart-control.md)   
 [Automatisation d'Excel à l'aide d'objets étendus](../vsto/automating-excel-by-using-extended-objects.md)   
 [Vue d'ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)   
 [Liaison de données aux contrôles dans les solutions Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Limitations de programmation des éléments hôtes et des contrôles hôtes](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  