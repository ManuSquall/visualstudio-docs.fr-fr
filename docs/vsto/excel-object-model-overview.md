---
title: Vue d’ensemble du modèle objet Excel
description: Découvrez que vous pouvez interagir avec les objets fournis par le modèle objet Excel pour développer des solutions qui utilisent Microsoft Office Excel.
ms.custom: SEO-VS-2020
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Worksheet object
- Range object
- object models [Office development in Visual Studio], Excel
- object models [Office development in Visual Studio], Office
- Workbook class
- objects [Office development in Visual Studio], Office object models
- Excel object model
- Office object models
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: a49dcc36d4079a6a945806b3112e3949ddcd79e2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99910298"
---
# <a name="excel-object-model-overview"></a>Vue d’ensemble du modèle objet Excel
  Pour développer des solutions qui utilisent Microsoft Office Excel, vous pouvez interagir avec les objets fournis par le modèle objet Excel. Cette rubrique présente les objets les plus importants :

- <xref:Microsoft.Office.Interop.Excel.Application>

- <xref:Microsoft.Office.Interop.Excel.Workbook>

- <xref:Microsoft.Office.Interop.Excel.Worksheet>

- <xref:Microsoft.Office.Interop.Excel.Range>

  [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

  Le modèle objet suit étroitement l'interface utilisateur. L’objet <xref:Microsoft.Office.Interop.Excel.Application> représente l’application entière et chaque objet <xref:Microsoft.Office.Interop.Excel.Workbook> contient une collection d’objets `Worksheet`. À partir de là, l'abstraction principale représentant les cellules est l'objet <xref:Microsoft.Office.Interop.Excel.Range>, qui vous permet d'utiliser des cellules individuelles ou des groupes de cellules.

  Outre le modèle objet Excel, les projets Office dans Visual Studio fournissent des *éléments hôtes* et des *contrôles hôtes* qui étendent certains objets dans le modèle objet Excel. Les éléments hôtes et les contrôles hôtes se comportent comme les objets Excel qu’ils étendent, mais ils possèdent également des fonctionnalités supplémentaires telles que la liaison de données et des événements supplémentaires. Pour plus d’informations, consultez [automatisation d’Excel à l’aide d’objets étendus](../vsto/automating-excel-by-using-extended-objects.md) et [vue d’ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md).

  Cette rubrique propose une vue d'ensemble succincte du modèle objet Excel. Pour obtenir des ressources qui vous permettent d’en savoir plus sur l’ensemble du modèle objet Excel, consultez [utiliser la documentation du modèle objet Excel](#ExcelOMDocumentation).

## <a name="access-objects-in-an-excel-project"></a>Accéder aux objets dans un projet Excel
 Quand vous créez un projet de complément VSTO pour Excel, Visual Studio crée automatiquement un fichier de code *ThisAddIn. vb* ou *ThisAddIn.cs* . Vous pouvez accéder à l'objet Application à l'aide de `Me.Application` ou de `this.Application`.

 Lorsque vous créez un projet de niveau document pour Excel, vous avez la possibilité de créer un projet Classeur Excel ou Modèle Excel. Visual Studio crée automatiquement les fichiers de code suivants dans votre nouveau projet Excel à la fois pour les projets de classeur et les projets de modèle.

|Visual Basic|C#|
|------------------|---------|
|ThisWorkbook.vb|ThisWorkbook.cs|
|Sheet1.vb|Sheet1.cs|
|Sheet2.vb|Sheet2.cs|
|Sheet3.vb|Sheet3.cs|

 Vous pouvez utiliser la classe `Globals` dans votre projet pour accéder à `ThisWorkbook`, `Sheet1`, `Sheet2` ou `Sheet3` depuis l'extérieur de la classe respective. Pour plus d’informations, consultez [accès global aux objets dans les projets Office](../vsto/global-access-to-objects-in-office-projects.md). L’exemple suivant appelle la <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A> méthode `Sheet1` , que le code soit placé dans une des `Sheet` *n* classes ou dans la `ThisWorkbook` classe.

 [!code-csharp[Trin_VstcoreExcelAutomation#82](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#82)]
 [!code-vb[Trin_VstcoreExcelAutomation#82](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#82)]

 Comme les données dans un document Excel sont hautement structurées, le modèle objet est hiérarchique et simple. Excel fournit des centaines d’objets avec lesquels vous pouvez interagir, mais vous pouvez commencer à utiliser le modèle objet en vous concentrant sur un petit sous-ensemble des objets disponibles. Ces objets incluent les quatre éléments suivants :

- Application

- Classeur

- Feuille de calcul

- Plage

  La majeure partie du travail effectué avec Excel tourne autour de ces quatre objets et de leurs membres.

### <a name="application-object"></a>Objet application
 L'objet <xref:Microsoft.Office.Interop.Excel.Application> d'Excel représente l'application Excel. L'objet <xref:Microsoft.Office.Interop.Excel.Application> contient une grande quantité d'informations sur l'application en cours d'exécution, les options appliquées à cette instance et les objets utilisateur actuels ouverts dans l'instance.

> [!NOTE]
> Vous ne devez pas attribuer la valeur <xref:Microsoft.Office.Interop.Excel.ApplicationClass.EnableEvents%2A> à la propriété <xref:Microsoft.Office.Interop.Excel.Application> de l'objet **T:Microsoft.Office.Interop.Excel.Application**. Si cette propriété a la valeur false, Excel ne peut pas déclencher d'événements, y compris les événements de contrôles hôtes.

### <a name="workbook-object"></a>Workbook (objet)
 L'objet <xref:Microsoft.Office.Interop.Excel.Workbook> représente un classeur unique dans l'application Excel.

 Les outils de développement Office dans Visual Studio étendent l'objet <xref:Microsoft.Office.Interop.Excel.Workbook> en fournissant le type <xref:Microsoft.Office.Tools.Excel.Workbook> . Ce type vous donne accès à toutes les fonctionnalités d'un objet <xref:Microsoft.Office.Interop.Excel.Workbook>. Pour plus d’informations, consultez [élément hôte de classeur](../vsto/workbook-host-item.md).

### <a name="worksheet-object"></a>Worksheet (objet)
 L'objet <xref:Microsoft.Office.Interop.Excel.Worksheet> est membre de la collection <xref:Microsoft.Office.Interop.Excel.Worksheets>. La plupart des propriétés, méthodes et événements de l'objet <xref:Microsoft.Office.Interop.Excel.Worksheet> sont strictement identiques, ou similaires, aux membres fournis par les objets <xref:Microsoft.Office.Interop.Excel.Application> ou <xref:Microsoft.Office.Interop.Excel.Workbook>.

 Excel fournit une collection <xref:Microsoft.Office.Interop.Excel.Sheets> en tant que propriété d’un objet <xref:Microsoft.Office.Interop.Excel.Workbook>. Chaque membre de la collection <xref:Microsoft.Office.Interop.Excel.Sheets> est un objet <xref:Microsoft.Office.Interop.Excel.Worksheet> ou <xref:Microsoft.Office.Interop.Excel.Chart>.

 Les outils de développement Office dans Visual Studio étendent l'objet <xref:Microsoft.Office.Interop.Excel.Worksheet> en fournissant le type <xref:Microsoft.Office.Tools.Excel.Worksheet> . Ce type vous donne accès à toutes les fonctionnalités d’un objet <xref:Microsoft.Office.Interop.Excel.Worksheet>, ainsi qu’à de nouvelles fonctionnalités telles que la capacité d’héberger des contrôles managés et de gérer de nouveaux événements. Pour plus d’informations, consultez [élément hôte de feuille de calcul](../vsto/worksheet-host-item.md).

### <a name="range-object"></a>Range (objet)
 L'objet <xref:Microsoft.Office.Interop.Excel.Range> est l'objet que vous utiliserez le plus fréquemment dans vos applications Excel. Avant de pouvoir manipuler une zone dans Excel, vous devez la spécifier comme étant un objet <xref:Microsoft.Office.Interop.Excel.Range> et travailler avec les méthodes et les propriétés de ce dernier. Un objet <xref:Microsoft.Office.Interop.Excel.Range> représente une cellule, une ligne, une colonne, une sélection des cellules contenant un ou plusieurs blocs de cellules, qui peuvent ou non être contiguës, ou même un groupe de cellules dans plusieurs feuilles.

 Visual Studio étend l'objet <xref:Microsoft.Office.Interop.Excel.Range> en fournissant les types <xref:Microsoft.Office.Tools.Excel.NamedRange> et <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>. Ces types possèdent la plupart des fonctionnalités d’un objet <xref:Microsoft.Office.Interop.Excel.Range>, ainsi que de nouvelles fonctionnalités telles que la fonction de liaison de données et de nouveaux événements. Pour plus d’informations, consultez contrôle [NamedRange](../vsto/namedrange-control.md) et [contrôle XmlMappedRange](../vsto/xmlmappedrange-control.md).

## <a name="use-the-excel-object-model-documentation"></a><a name="ExcelOMDocumentation"></a> Utiliser la documentation du modèle objet Excel
 Pour obtenir des informations complètes sur le modèle objet Excel, vous pouvez vous reporter à la documentation de référence de l'assembly PIA (Primary Interop Assembly) Excel et à la documentation de référence du modèle objet VBA.

### <a name="primary-interop-assembly-reference"></a>Référence d’assembly PIA (Primary Interop Assembly)
 La documentation de référence de l'assembly PIA Excel décrit les types de l'assembly PIA pour Excel. Cette documentation est disponible à partir de l’emplacement suivant : référence de l' [assembly PIA Excel 2010](office-primary-interop-assemblies.md).

 Pour plus d’informations sur la conception de l’assembly PIA Excel, notamment les différences entre les classes et les interfaces dans l’assembly PIA et le mode d’implémentation des événements dans l’ASSEMBLy Pia, consultez [vue d’ensemble des classes et des interfaces dans les assemblys PIA (Primary Interop Assembly](/previous-versions/office/office-12/ms247299(v=office.12))) d’Office.

### <a name="vba-object-model-reference"></a>Référence du modèle objet VBA
 La documentation de référence du modèle objet VBA présente le modèle objet Excel tel qu'il est exposé au code VBA (Visual Basic pour Applications). Pour plus d’informations, consultez [Référence du modèle objet Excel 2010](/office/vba/api/overview/Excel/object-model).

 Tous les objets et membres mentionnés dans la documentation de référence du modèle objet VBA correspondent aux types et aux membres de l'assembly PIA Excel. Par exemple, l’objet de feuille de calcul dans la documentation de référence du modèle objet VBA correspond à l' <xref:Microsoft.Office.Interop.Excel.Worksheet> objet dans l’assembly PIA Excel. Même si la documentation de référence du modèle objet VBA fournit des exemples de code pour la plupart des propriétés, méthodes et événements, vous devez traduire le code VBA fourni dans documentation de référence en Visual Basic ou Visual C# pour pouvoir les utiliser dans un projet Excel créé à l'aide de Visual Studio.

### <a name="related-topics"></a>Rubriques connexes

|Titre|Description|
|-----------|-----------------|
|[Solutions Excel](../vsto/excel-solutions.md)|Explique comment créer des personnalisations au niveau du document et des compléments VSTO pour Microsoft Office Excel.|
|[Utiliser des plages](../vsto/working-with-ranges.md)|Fournit des exemples montrant comment effectuer des tâches courantes avec des plages.|
|[Utiliser des feuilles de calcul](../vsto/working-with-worksheets.md)|Fournit des exemples montrant comment effectuer des tâches courantes avec des feuilles de calcul.|
|[Utiliser des classeurs](../vsto/working-with-workbooks.md)|Fournit des exemples montrant comment effectuer des tâches courantes avec des classeurs.|
