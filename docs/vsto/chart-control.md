---
title: Chart, contrôle
description: Apprenez que lorsque vous ajoutez un graphique à une feuille de calcul, Visual Studio crée un objet graphique que vous pouvez programmer directement.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.ProjectItem.ExcelChart
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Chart control [Office development in Visual Studio], events
- Chart control [Office development in Visual Studio]
- Chart control [Office development in Visual Studio], data binding
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 3530e0821d4569381f610f44ae541c04b484b469
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99903772"
---
# <a name="chart-control"></a>Chart, contrôle
  Le contrôle <xref:Microsoft.Office.Tools.Excel.Chart> est un objet de graphique qui expose des événements. Quand vous ajoutez un graphique à une feuille de calcul, Visual Studio crée un objet <xref:Microsoft.Office.Tools.Excel.Chart> que vous pouvez programmer directement, sans devoir parcourir le modèle objet Microsoft Office Excel.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="create-the-control"></a>Créer le contrôle
 Vous pouvez ajouter <xref:Microsoft.Office.Tools.Excel.Chart> des contrôles à une feuille de calcul Microsoft Office Excel au moment du design ou au moment de l’exécution dans un projet au niveau du document.

 Vous pouvez ajouter des contrôles <xref:Microsoft.Office.Tools.Excel.Chart> à une feuille de calcul au moment de l’exécution dans un complément VSTO. Pour plus d’informations, consultez [Comment : ajouter des contrôles Chart à des feuilles de calcul](../vsto/how-to-add-chart-controls-to-worksheets.md).

> [!NOTE]
> Les objets de graphique créés dynamiquement ne sont pas persistants dans la feuille de calcul en tant que contrôles hôtes, une fois la feuille de calcul fermée. Pour plus d’informations, consultez [Ajouter des contrôles aux documents Office au moment de l’exécution](../vsto/adding-controls-to-office-documents-at-run-time.md).

## <a name="formatting"></a>Mise en forme
 La mise en forme qui peut être appliquée à <xref:Microsoft.Office.Interop.Excel.Chart> peut l'être également à un contrôle <xref:Microsoft.Office.Tools.Excel.Chart>. Cela inclut les bordures, les polices, le type de graphique, le quadrillage, la légende et les étiquettes de données.

## <a name="events"></a>Événements
 Les événements suivants sont disponibles pour le contrôle <xref:Microsoft.Office.Tools.Excel.Chart> :

- <xref:Microsoft.Office.Tools.Excel.Chart.ActivateEvent>

- <xref:Microsoft.Office.Tools.Excel.Chart.BeforeDoubleClick>

- <xref:Microsoft.Office.Tools.Excel.Chart.BeforeRightClick>

- <xref:Microsoft.Office.Tools.Excel.Chart.BindingContextChanged>

- <xref:Microsoft.Office.Tools.Excel.Chart.Calculate>

- <xref:Microsoft.Office.Tools.Excel.Chart.Deactivate>

- <xref:System.ComponentModel.Component.Disposed>

- <xref:Microsoft.Office.Tools.Excel.Chart.DragOver>

- <xref:Microsoft.Office.Tools.Excel.Chart.DragPlot>

- <xref:Microsoft.Office.Tools.Excel.Chart.MouseDown>

- <xref:Microsoft.Office.Tools.Excel.Chart.MouseMove>

- <xref:Microsoft.Office.Tools.Excel.Chart.MouseUp>

- <xref:Microsoft.Office.Tools.Excel.Chart.Resize>

- <xref:Microsoft.Office.Tools.Excel.Chart.SelectEvent>

- <xref:Microsoft.Office.Tools.Excel.Chart.SeriesChange>

## <a name="see-also"></a>Voir aussi
- [Exemples et procédures pas à pas relatifs au développement Office](../vsto/office-development-samples-and-walkthroughs.md)
- [Étendre des documents Word et des classeurs Excel dans des compléments VSTO au moment de l’exécution](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Contrôles sur les documents Office](../vsto/controls-on-office-documents.md)
- [Ajouter des contrôles aux documents Office au moment de l’exécution](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Automatiser Excel à l’aide d’objets étendus](../vsto/automating-excel-by-using-extended-objects.md)
- [Comment : ajouter des contrôles Chart à des feuilles de calcul](../vsto/how-to-add-chart-controls-to-worksheets.md)
- [Lier des données à des contrôles dans les solutions Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Limitations de programmation des éléments hôtes et des contrôles hôtes](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
