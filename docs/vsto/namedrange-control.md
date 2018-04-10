---
title: Contrôle NamedRange | Documents Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.reviewer: ''
ms.suite: ''
ms.technology:
- office-development
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VST.Toolbox.Range
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, named
- NamedRange control, events
- NamedRange control, data binding
- NamedRange control
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 22adc003c10e95de0e701eb3f382d9e530b28acf
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2018
---
# <a name="namedrange-control"></a>NamedRange (contrôle)
  Le contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange> est une plage qui possède un nom unique, qui expose des événements et qui peut être liée à des données. Pour plus d'informations, consultez [Excel Object Model Overview](../vsto/excel-object-model-overview.md).  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="creating-the-control"></a>Création du contrôle  
 Vous pouvez ajouter des contrôles <xref:Microsoft.Office.Tools.Excel.NamedRange> à une feuille de calcul Microsoft Office Excel au moment du design ou de l’exécution dans des projets au niveau du document.  
  
 Vous pouvez ajouter des contrôles <xref:Microsoft.Office.Tools.Excel.NamedRange> à une feuille de calcul au moment de l’exécution dans un complément VSTO. Pour plus d'informations, consultez [How to: Add NamedRange Controls to Worksheets](../vsto/how-to-add-namedrange-controls-to-worksheets.md).  
  
> [!NOTE]  
>  Par défaut, les plages nommées créées dynamiquement ne sont pas persistantes dans la feuille de calcul en tant que contrôles hôtes lorsque la feuille de calcul est fermée. Pour plus d'informations, consultez [Ajout de contrôles à des documents Office au moment de l'exécution](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
 Les contrôles<xref:Microsoft.Office.Tools.Excel.NamedRange> peuvent uniquement se composer de plages sur des feuilles spécifiques. Les contrôles<xref:Microsoft.Office.Tools.Excel.NamedRange> ne peuvent pas avoir de noms relatifs qui s’appliquent à toutes les feuilles et ne peuvent pas se composer de plages qui couvrent plusieurs feuilles de calcul d’un classeur (plages 3D).  
  
## <a name="binding-data-to-the-control"></a>Liaison de données au contrôle  
 Une plage nommée peut sembler un bon candidat pour la liaison de données complexe dans la mesure où elle peut comporter de nombreuses cellules ; toutefois, une plage est une simple collection de cellules qui ne peuvent pas être facilement mappées à une colonne particulière d’un dataset. Par conséquent, les contrôles <xref:Microsoft.Office.Tools.Excel.NamedRange> prennent uniquement en charge la liaison de données simple. Le contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> peut être utilisé pour la liaison de données complexes. Pour plus d'informations, consultez [ListObject Control](../vsto/listobject-control.md).  
  
 Le contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange> peut être lié à une source de données à l’aide des propriétés <xref:System.Windows.Forms.Control.DataBindings%2A> . La propriété de liaison de données par défaut du contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange> est <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A>.  
  
 Si les données du dataset lié sont mises à jour via un mécanisme quelconque, le contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange> reflète les modifications.  
  
## <a name="formatting"></a>Mise en forme  
 Une mise en forme qui peut être appliquée à un <xref:Microsoft.Office.Interop.Excel.Range> peut également être appliquée à un contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange> . Cela inclut les bordures, les polices, le format de nombre et les styles.  
  
## <a name="renaming-the-control"></a>Changement de nom du contrôle  
 Lorsque vous ajoutez un contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange> à votre feuille de calcul à partir de la **boîte à outils**, Visual Studio génère automatiquement un nom pour ce contrôle. Vous pouvez modifier ce nom dans la fenêtre **Propriétés** .  
  
## <a name="events"></a>Événements  
 Les événements suivants sont disponibles pour le contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange> :  
  
-   <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeRightClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.NamedRange.BindingContextChanged>  
  
-   <xref:Microsoft.Office.Tools.Excel.NamedRange.Change>  
  
-   <xref:Microsoft.Office.Tools.Excel.NamedRange.Deselected>  
  
-   <xref:System.ComponentModel.Component.Disposed>  
  
-   <xref:Microsoft.Office.Tools.Excel.NamedRange.Selected>  
  
-   <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange>  
  
## <a name="see-also"></a>Voir aussi  
 [Automatisation d’Excel à l’aide d’objets étendus](../vsto/automating-excel-by-using-extended-objects.md)   
 [Procédures pas à pas et des exemples de développement office](../vsto/office-development-samples-and-walkthroughs.md)   
 [Liaison de données aux contrôles dans les Solutions Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Extension de Documents Word et classeurs Excel dans des Compléments VSTO au moment de l’exécution](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Contrôles sur des Documents Office](../vsto/controls-on-office-documents.md)   
 [Ajout de contrôles aux Documents Office au moment de l’exécution](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Comment : ajouter des contrôles NamedRange aux feuilles de calcul](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [Comment : redimensionner les contrôles NamedRange](../vsto/how-to-resize-namedrange-controls.md)   
 [Liaison de données aux contrôles dans les Solutions Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Procédure pas à pas : Programmation d’événements d’un contrôle NamedRange](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md)   
 [Limitations de programmation des éléments hôtes et des contrôles hôtes](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  