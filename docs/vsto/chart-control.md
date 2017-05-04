---
title: "Chart, contr&#244;le | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VST.ProjectItem.ExcelChart"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Chart (contrôle) (développement Office dans Visual Studio)"
  - "Chart (contrôle) (développement Office dans Visual Studio), liaison de données"
  - "Chart (contrôle) (développement Office dans Visual Studio), événements"
ms.assetid: 64f1a7cc-cc66-47da-aaeb-44a62ae53909
caps.latest.revision: 51
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 50
---
# Chart, contr&#244;le
  Le contrôle <xref:Microsoft.Office.Tools.Excel.Chart> est un objet de graphique qui expose des événements.  Quand vous ajoutez un graphique à une feuille de calcul, Visual Studio crée un objet <xref:Microsoft.Office.Tools.Excel.Chart> que vous pouvez programmer directement, sans devoir parcourir le modèle objet Microsoft Office Excel.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## Création du contrôle  
 Vous pouvez ajouter des contrôles <xref:Microsoft.Office.Tools.Excel.Chart> à une feuille de calcul Microsoft Office Excel au moment du design ou au moment de l'exécution dans un projet au niveau du document.  
  
 Vous pouvez ajouter des contrôles <xref:Microsoft.Office.Tools.Excel.Chart> à une feuille de calcul au moment de l'exécution dans un complément VSTO.  Pour plus d'informations, consultez [Comment : ajouter des contrôles Chart aux feuilles de calcul](../vsto/how-to-add-chart-controls-to-worksheets.md).  
  
> [!NOTE]  
>  Les objets de graphique créés dynamiquement ne sont pas persistants dans la feuille de calcul en tant que contrôles hôtes, une fois la feuille de calcul fermée.  Pour plus d'informations, consultez [Ajout de contrôles à des documents Office au moment de l'exécution](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
## Mise en forme  
 La mise en forme qui peut être appliquée à <xref:Microsoft.Office.Interop.Excel.Chart> peut l'être également à un contrôle <xref:Microsoft.Office.Tools.Excel.Chart>.  Cela inclut les bordures, les polices, le type de graphique, le quadrillage, la légende et les étiquettes de données.  
  
## Événements  
 Les événements suivants sont disponibles pour le contrôle <xref:Microsoft.Office.Tools.Excel.Chart> :  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.ActivateEvent>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.BeforeDoubleClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.BeforeRightClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.BindingContextChanged>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.Calculate>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.Deactivate>  
  
-   <xref:System.ComponentModel.Component.Disposed>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.DragOver>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.DragPlot>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.MouseDown>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.MouseMove>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.MouseUp>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.Resize>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.SelectEvent>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.SeriesChange>  
  
## Voir aussi  
 [Exemples et procédures pas à pas relatifs au développement Office](../vsto/office-development-samples-and-walkthroughs.md)   
 [Extension de documents Word et de classeurs Excel dans des compléments VSTO au moment de l'exécution](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Contrôles sur des documents Office](../vsto/controls-on-office-documents.md)   
 [Ajout de contrôles à des documents Office au moment de l'exécution](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Automatisation d'Excel à l'aide d'objets étendus](../vsto/automating-excel-by-using-extended-objects.md)   
 [Comment : ajouter des contrôles Chart aux feuilles de calcul](../vsto/how-to-add-chart-controls-to-worksheets.md)   
 [Liaison de données aux contrôles dans les solutions Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Limitations de programmation des éléments hôtes et des contrôles hôtes](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  