---
title: Élément hôte de classeur
description: Découvrez que l’élément hôte de classeur est un type qui étend le type de classeur à partir de l’assembly PIA (Primary Interop Assembly) pour Microsoft Excel.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel workbooks
- Workbook host items
- host items [Office development in Visual Studio], Workbook
- workbooks, Excel
- Workbook host items, events
- workbooks
- Excel [Office development in Visual Studio], workbooks
- workbooks, events
- events [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 24f32f8799d2bac5c23a0f8a2ef92857d2a6f7c7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99847594"
---
# <a name="workbook-host-item"></a>Élément hôte de classeur
  L’élément hôte <xref:Microsoft.Office.Tools.Excel.Workbook> est un type qui étend le type <xref:Microsoft.Office.Interop.Excel.Workbook> à partir de l’assembly PIA (Primary Interop Assembly) pour Excel. L’élément hôte <xref:Microsoft.Office.Tools.Excel.Workbook> fournit les mêmes propriétés, méthodes et événements qu’un objet <xref:Microsoft.Office.Interop.Excel.Workbook> , mais il offre également d’autres fonctionnalités.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Dans les projets au niveau du document se trouve un élément hôte <xref:Microsoft.Office.Tools.Excel.Workbook> par défaut qui représente le classeur dans votre projet. Dans les projets de compléments VSTO, vous pouvez générer des éléments hôtes <xref:Microsoft.Office.Tools.Excel.Workbook> au moment de l'exécution.

## <a name="understand-the-workbook-host-item-in-document-level-projects"></a>Comprendre l’élément hôte de classeur dans les projets au niveau du document
 Pour accéder au classeur dans votre projet, utilisez la classe `ThisWorkbook` . La classe `ThisWorkbook` vous permet d’accéder aux membres de l’élément hôte <xref:Microsoft.Office.Tools.Excel.Workbook> pour effectuer des tâches de base dans votre personnalisation, comme l’exécution de code à l’ouverture ou la fermeture du classeur. Pour plus d’informations, consultez [programmes personnalisations au niveau du document](../vsto/programming-document-level-customizations.md).

 La classe `ThisWorkbook` fournit un emplacement dans lequel vous pouvez commencer à écrire du code dans votre projet. Étant donné que la classe fournit les mêmes propriétés, méthodes et événements que l’objet <xref:Microsoft.Office.Interop.Excel.Workbook> dans l’assembly PIA pour Excel, vous pouvez aussi utiliser `ThisWorkbook` pour accéder au modèle objet d’Excel. Pour plus d’informations, consultez [vue d’ensemble du modèle objet Excel](../vsto/excel-object-model-overview.md).

 Double-cliquez sur l’élément de projet **ThisWorkbook** dans l’ **Explorateur de solutions** pour afficher le Concepteur de classeurs et afficher les propriétés et événements du classeur dans la fenêtre **Propriétés** .

### <a name="limitations-of-the-workbook-host-item-in-document-level-projects"></a>Limitations de l’élément hôte de classeur dans les projets au niveau du document
 Un projet au niveau du document peut contenir un seul élément hôte <xref:Microsoft.Office.Tools.Excel.Workbook> (autrement dit, la classe `ThisWorkbook` ). Vous ne pouvez pas ajouter de nouveaux éléments hôtes <xref:Microsoft.Office.Tools.Excel.Workbook> à votre projet au moment du design. Vous ne pouvez pas non plus créer des éléments hôtes <xref:Microsoft.Office.Tools.Excel.Workbook> au moment de l’exécution à partir d’une personnalisation au niveau du document.

 Si vous créez un classeur Excel au moment de l’exécution, son type est <xref:Microsoft.Office.Interop.Excel.Workbook>. Comme il ne s’agit pas d’un élément hôte, il ne peut pas contenir de contrôles hôtes ni de contrôles Windows Forms. Pour plus d’informations sur la création de classeurs au moment de l’exécution, consultez [Comment : créer des classeurs par programmation](../vsto/how-to-programmatically-create-new-workbooks.md).

 L’élément hôte <xref:Microsoft.Office.Tools.Excel.Workbook> n’agit pas comme un conteneur pour les contrôles hôtes. Ainsi, vous ne pouvez pas ajouter de contrôles visibles au classeur, mais vous pouvez ajouter des composants, comme <xref:System.Data.DataSet>, pour pouvoir les partager dans toutes les feuilles de calcul. Dans un projet au niveau du document, les composants disponibles pour le classeur se trouvent sous les onglets **Composant** , **Données** et **Tous les Windows Forms** de la **Boîte à outils**.

> [!NOTE]
> Les outils de développement Office dans Visual Studio ne prennent pas en charge les classeurs partagés.

## <a name="understand-workbook-host-items-in-vsto-add-in-projects"></a>Comprendre les éléments hôtes de classeur dans les projets de complément VSTO
 Dans les projets complément VSTO, vous pouvez générer un élément hôte <xref:Microsoft.Office.Tools.Excel.Workbook> au moment de l’exécution pour tout classeur ouvert dans Excel. Pour générer un élément hôte <xref:Microsoft.Office.Tools.Excel.Workbook>, utilisez la méthode `GetVstoObject`. Pour plus d’informations, consultez [extension de documents Word et de classeurs Excel dans des compléments VSTO au moment](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)de l’exécution.

## <a name="see-also"></a>Voir aussi
- [Exemples et procédures pas à pas relatifs au développement Office](../vsto/office-development-samples-and-walkthroughs.md)
- [Étendre des documents Word et des classeurs Excel dans des compléments VSTO au moment de l’exécution](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Vue d’ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)
- [Élément hôte de feuille de calcul](../vsto/worksheet-host-item.md)
- [Automatiser Excel à l’aide d’objets étendus](../vsto/automating-excel-by-using-extended-objects.md)
- [Limitations de programmation des éléments hôtes et des contrôles hôtes](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
