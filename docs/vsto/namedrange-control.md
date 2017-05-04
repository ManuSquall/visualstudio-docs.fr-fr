---
title: "NamedRange, contr&#244;le | Microsoft Docs"
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
  - "VST.Toolbox.Range"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "plages nommées"
  - "NamedRange (contrôle), événements"
  - "NamedRange (contrôle), liaison de données"
  - "NamedRange (contrôle)"
ms.assetid: 07878c7c-cb5a-4f98-95c4-e828de25dae5
caps.latest.revision: 56
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 55
---
# NamedRange, contr&#244;le
  Le contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange> est une plage qui possède un nom unique, qui expose des événements et qui peut être liée à des données. Pour plus d'informations, consultez [Vue d'ensemble du modèle objet Excel](../vsto/excel-object-model-overview.md).  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## Création du contrôle  
 Vous pouvez ajouter des contrôles <xref:Microsoft.Office.Tools.Excel.NamedRange> à une feuille de calcul Microsoft Office Excel au moment du design ou de l’exécution dans des projets au niveau du document.  
  
 Vous pouvez ajouter des contrôles <xref:Microsoft.Office.Tools.Excel.NamedRange> à une feuille de calcul au moment de l’exécution dans un complément VSTO. Pour plus d'informations, consultez [Comment : ajouter des contrôles NamedRange aux feuilles de calcul](../vsto/how-to-add-namedrange-controls-to-worksheets.md).  
  
> [!NOTE]  
>  Par défaut, les plages nommées créées dynamiquement ne sont pas persistantes dans la feuille de calcul en tant que contrôles hôtes lorsque la feuille de calcul est fermée. Pour plus d'informations, consultez [Ajout de contrôles à des documents Office au moment de l'exécution](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
 Les contrôles <xref:Microsoft.Office.Tools.Excel.NamedRange> peuvent uniquement se composer de plages sur des feuilles spécifiques. Les contrôles <xref:Microsoft.Office.Tools.Excel.NamedRange> ne peuvent pas avoir de noms relatifs qui s’appliquent à toutes les feuilles et ne peuvent pas se composer de plages qui couvrent plusieurs feuilles de calcul d’un classeur \(plages 3D\).  
  
## Liaison de données au contrôle  
 Une plage nommée peut sembler un bon candidat pour la liaison de données complexe dans la mesure où elle peut comporter de nombreuses cellules ; toutefois, une plage est une simple collection de cellules qui ne peuvent pas être facilement mappées à une colonne particulière d’un dataset. Par conséquent, les contrôles <xref:Microsoft.Office.Tools.Excel.NamedRange> prennent uniquement en charge la liaison de données simple. Le contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> peut être utilisé pour la liaison de données complexes. Pour plus d'informations, consultez [ListObject, contrôle](../vsto/listobject-control.md).  
  
 Le contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange> peut être lié à une source de données à l’aide des propriétés <xref:System.Windows.Forms.Control.DataBindings%2A>. La propriété de liaison de données par défaut du contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange> est <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A>.  
  
 Si les données du dataset lié sont mises à jour via un mécanisme quelconque, le contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange> reflète les modifications.  
  
## Mise en forme  
 Une mise en forme qui peut être appliquée à un <xref:Microsoft.Office.Interop.Excel.Range> peut également être appliquée à un contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange>. Cela inclut les bordures, les polices, le format de nombre et les styles.  
  
## Changement de nom du contrôle  
 Lorsque vous ajoutez un contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange> à votre feuille de calcul à partir de la **boîte à outils**, Visual Studio génère automatiquement un nom pour ce contrôle. Vous pouvez modifier ce nom dans la fenêtre **Propriétés**.  
  
## Événements  
 Les événements suivants sont disponibles pour le contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange> :  
  
-   <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeRightClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.NamedRange.BindingContextChanged>  
  
-   <xref:Microsoft.Office.Tools.Excel.NamedRange.Change>  
  
-   <xref:Microsoft.Office.Tools.Excel.NamedRange.Deselected>  
  
-   <xref:System.ComponentModel.Component.Disposed>  
  
-   <xref:Microsoft.Office.Tools.Excel.NamedRange.Selected>  
  
-   <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange>  
  
## Voir aussi  
 [Automatisation d'Excel à l'aide d'objets étendus](../vsto/automating-excel-by-using-extended-objects.md)   
 [Exemples et procédures pas à pas relatifs au développement Office](../vsto/office-development-samples-and-walkthroughs.md)   
 [Liaison de données aux contrôles dans les solutions Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Extension de documents Word et de classeurs Excel dans des compléments VSTO au moment de l'exécution](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Contrôles sur des documents Office](../vsto/controls-on-office-documents.md)   
 [Ajout de contrôles à des documents Office au moment de l'exécution](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Comment : ajouter des contrôles NamedRange aux feuilles de calcul](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [Comment : redimensionner les contrôles NamedRange](../vsto/how-to-resize-namedrange-controls.md)   
 [Liaison de données aux contrôles dans les solutions Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Procédure pas à pas : programmation d'événements d'un contrôle NamedRange](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md)   
 [Limitations de programmation des éléments hôtes et des contrôles hôtes](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  