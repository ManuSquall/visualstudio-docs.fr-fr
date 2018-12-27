---
title: Vue d’ensemble du modèle objet Excel
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
manager: douge
ms.workload:
- office
ms.openlocfilehash: eb5b930df90f36395a22461ad0f26e82548afb6f
ms.sourcegitcommit: a205ff1b389fba1803acd32c54df7feb0ef7a203
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/20/2018
ms.locfileid: "53647523"
---
# <a name="excel-object-model-overview"></a>Vue d’ensemble du modèle d’objet Excel
  Pour développer des solutions qui utilisent Microsoft Office Excel, vous pouvez interagir avec les objets fournis par le modèle objet Excel. Cette rubrique présente les objets les plus importants :  
  
- <xref:Microsoft.Office.Interop.Excel.Application>  
  
- <xref:Microsoft.Office.Interop.Excel.Workbook>  
  
- <xref:Microsoft.Office.Interop.Excel.Worksheet>  
  
- <xref:Microsoft.Office.Interop.Excel.Range>  
  
  [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
  Le modèle objet suit étroitement l'interface utilisateur. L'objet <xref:Microsoft.Office.Interop.Excel.Application> représente l'application entière et chaque objet <xref:Microsoft.Office.Interop.Excel.Workbook> contient une collection d'objets `Worksheet`. À partir de là, l'abstraction principale représentant les cellules est l'objet <xref:Microsoft.Office.Interop.Excel.Range>, qui vous permet d'utiliser des cellules individuelles ou des groupes de cellules.  
  
  Outre le modèle objet Excel, les projets Office dans Visual Studio fournissent *éléments hôtes* et *contrôles hôtes* qui étendent certains objets dans le modèle objet Excel. Les éléments hôtes et les contrôles hôtes se comportent comme les objets Excel qu’ils étendent, mais ils possèdent également des fonctionnalités supplémentaires telles que la liaison de données et des événements supplémentaires. Pour plus d’informations, consultez [automatisation d’Excel à l’aide d’objets étendus](../vsto/automating-excel-by-using-extended-objects.md) et [éléments hôtes et héberger de vue d’ensemble des contrôles](../vsto/host-items-and-host-controls-overview.md).  
  
  Cette rubrique propose une vue d'ensemble succincte du modèle objet Excel. Pour les ressources où vous pouvez en savoir plus sur le modèle objet Excel complet, consultez [utiliser la documentation du modèle objet Excel](#ExcelOMDocumentation).  
  
  ![lien vers la vidéo](../vsto/media/playvideo.gif "lien vers la vidéo") pour une démonstration vidéo connexe, consultez [How do I: Utilisez les gestionnaires d’événements dans un complément Excel 2007 ? ](http://go.microsoft.com/fwlink/?LinkID=130291), et [How do I: Utiliser des formes pour créer un graphique en bulles dans Excel ? ](http://go.microsoft.com/fwlink/?LinkID=130313).  
  
## <a name="access-objects-in-an-excel-project"></a>Accéder aux objets dans un projet Excel  
 Lorsque vous créez un nouveau projet de complément VSTO pour Excel, Visual Studio crée automatiquement un *ThisAddIn.vb* ou *ThisAddIn.cs* fichier de code. Vous pouvez accéder à l'objet Application à l'aide de `Me.Application` ou de `this.Application`.  
  
 Lorsque vous créez un projet de niveau document pour Excel, vous avez la possibilité de créer un projet Classeur Excel ou Modèle Excel. Visual Studio crée automatiquement les fichiers de code suivants dans votre nouveau projet Excel à la fois pour les projets de classeur et les projets de modèle.  
  
|Visual Basic|C#|  
|------------------|---------|  
|ThisWorkbook.vb|ThisWorkbook.cs|  
|Sheet1.vb|Sheet1.cs|  
|Sheet2.vb|Sheet2.cs|  
|Sheet3.vb|Sheet3.cs|  
  
 Vous pouvez utiliser la classe `Globals` dans votre projet pour accéder à `ThisWorkbook`, `Sheet1`, `Sheet2` ou `Sheet3` depuis l'extérieur de la classe respective. Pour plus d’informations, consultez [d’accès Global aux objets dans les projets Office](../vsto/global-access-to-objects-in-office-projects.md). L’exemple suivant appelle la <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A> méthode de `Sheet1` , quel que soit le code est placé dans un de la `Sheet` *n* classes ou les `ThisWorkbook` classe.  
  
 [!code-csharp[Trin_VstcoreExcelAutomation#82](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#82)]
 [!code-vb[Trin_VstcoreExcelAutomation#82](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#82)]  
  
 Comme les données dans un document Excel sont hautement structurées, le modèle objet est hiérarchique et simple. Excel fournit des centaines d’objets avec lesquels vous pouvez souhaiter interagir, mais vous pouvez obtenir un bon départ avec le modèle objet en se concentrant sur un petit sous-ensemble des objets disponibles. Ces objets incluent les quatre éléments suivants :  
  
- Application  
  
- Workbook  
  
- Worksheet  
  
- Plage  
  
  La majeure partie du travail effectué avec Excel tourne autour de ces quatre objets et de leurs membres.  
  
### <a name="application-object"></a>Objet Application  
 L'objet <xref:Microsoft.Office.Interop.Excel.Application> d'Excel représente l'application Excel. L'objet <xref:Microsoft.Office.Interop.Excel.Application> contient une grande quantité d'informations sur l'application en cours d'exécution, les options appliquées à cette instance et les objets utilisateur actuels ouverts dans l'instance.  
  
> [!NOTE]  
>  Vous ne devez pas attribuer la valeur <xref:Microsoft.Office.Interop.Excel.ApplicationClass.EnableEvents%2A> à la propriété <xref:Microsoft.Office.Interop.Excel.Application> de l'objet **T:Microsoft.Office.Interop.Excel.Application**. Si cette propriété a la valeur false, Excel ne peut pas déclencher d'événements, y compris les événements de contrôles hôtes.  
  
### <a name="workbook-object"></a>Objet de classeur  
 L'objet <xref:Microsoft.Office.Interop.Excel.Workbook> représente un classeur unique dans l'application Excel.  
  
 Les outils de développement Office dans Visual Studio étendent l'objet <xref:Microsoft.Office.Interop.Excel.Workbook> en fournissant le type <xref:Microsoft.Office.Tools.Excel.Workbook> . Ce type vous donne accès à toutes les fonctionnalités d’un objet <xref:Microsoft.Office.Interop.Excel.Workbook>. Pour plus d’informations, consultez [élément hôte de classeur](../vsto/workbook-host-item.md).  
  
### <a name="worksheet-object"></a>Worksheet (objet)  
 L’objet <xref:Microsoft.Office.Interop.Excel.Worksheet> est membre de la collection <xref:Microsoft.Office.Interop.Excel.Worksheets>. La plupart des propriétés, méthodes et événements de l'objet <xref:Microsoft.Office.Interop.Excel.Worksheet> sont strictement identiques, ou similaires, aux membres fournis par les objets <xref:Microsoft.Office.Interop.Excel.Application> ou <xref:Microsoft.Office.Interop.Excel.Workbook>.  
  
 Excel fournit une collection <xref:Microsoft.Office.Interop.Excel.Sheets> en tant que propriété d'un objet <xref:Microsoft.Office.Interop.Excel.Workbook>. Chaque membre de la collection <xref:Microsoft.Office.Interop.Excel.Sheets> est un objet <xref:Microsoft.Office.Interop.Excel.Worksheet> ou <xref:Microsoft.Office.Interop.Excel.Chart>.  
  
 Les outils de développement Office dans Visual Studio étendent l'objet <xref:Microsoft.Office.Interop.Excel.Worksheet> en fournissant le type <xref:Microsoft.Office.Tools.Excel.Worksheet> . Ce type vous donne accès à toutes les fonctionnalités d’un objet <xref:Microsoft.Office.Interop.Excel.Worksheet>, ainsi qu’à de nouvelles fonctionnalités telles que la capacité d’héberger des contrôles managés et de gérer de nouveaux événements. Pour plus d’informations, consultez [élément hôte de feuille de calcul](../vsto/worksheet-host-item.md).  
  
### <a name="range-object"></a>Range (objet)  
 L'objet <xref:Microsoft.Office.Interop.Excel.Range> est l'objet que vous utiliserez le plus fréquemment dans vos applications Excel. Avant de pouvoir manipuler une zone dans Excel, vous devez la spécifier comme étant un objet <xref:Microsoft.Office.Interop.Excel.Range> et travailler avec les méthodes et les propriétés de ce dernier. Un objet <xref:Microsoft.Office.Interop.Excel.Range> représente une cellule, une ligne, une colonne, une sélection des cellules contenant un ou plusieurs blocs de cellules, qui peuvent ou non être contiguës, ou même un groupe de cellules dans plusieurs feuilles.  
  
 Visual Studio étend l'objet <xref:Microsoft.Office.Interop.Excel.Range> en fournissant les types <xref:Microsoft.Office.Tools.Excel.NamedRange> et <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>. Ces types possèdent la plupart des fonctionnalités d’un objet <xref:Microsoft.Office.Interop.Excel.Range>, ainsi que de nouvelles fonctionnalités telles que la fonction de liaison de données et de nouveaux événements. Pour plus d’informations, consultez [contrôle NamedRange](../vsto/namedrange-control.md) et [XmlMappedRange, contrôle](../vsto/xmlmappedrange-control.md).  
  
##  <a name="ExcelOMDocumentation"></a> Utilisez la documentation du modèle objet Excel  
 Pour obtenir des informations complètes sur le modèle objet Excel, vous pouvez vous reporter à la documentation de référence de l'assembly PIA (Primary Interop Assembly) Excel et à la documentation de référence du modèle objet VBA.  
  
### <a name="primary-interop-assembly-reference"></a>Référence d’assembly PIA  
 La documentation de référence de l'assembly PIA Excel décrit les types de l'assembly PIA pour Excel. Cette documentation est disponible à partir de l’emplacement suivant : [Référence d’assembly PIA Excel 2010](http://go.microsoft.com/fwlink/?LinkId=189585).  
  
 Pour plus d’informations sur la conception de l’assembly PIA Excel, telles que les différences entre les classes et interfaces dans l’assembly PIA, et comment les événements dans l’assembly PIA, consultez [vue d’ensemble des classes et interfaces dans les assemblys PIA Office](http://go.microsoft.com/fwlink/?LinkId=189592).  
  
### <a name="vba-object-model-reference"></a>Référence du modèle objet VBA  
 La documentation de référence du modèle objet VBA présente le modèle objet Excel tel qu'il est exposé au code VBA (Visual Basic pour Applications). Pour plus d’informations, consultez [référence du modèle objet Excel 2010](http://go.microsoft.com/fwlink/?LinkId=199768).  
  
 Tous les objets et membres mentionnés dans la documentation de référence du modèle objet VBA correspondent aux types et aux membres de l'assembly PIA Excel. Par exemple, l’objet de feuille de calcul dans la référence du modèle objet VBA correspond à la <xref:Microsoft.Office.Interop.Excel.Worksheet> objet dans l’assembly PIA Excel. Même si la documentation de référence du modèle objet VBA fournit des exemples de code pour la plupart des propriétés, méthodes et événements, vous devez traduire le code VBA fourni dans documentation de référence en Visual Basic ou Visual C# pour pouvoir les utiliser dans un projet Excel créé à l'aide de Visual Studio.  
  
### <a name="related-topics"></a>Rubriques connexes  
  
|Titre|Description|  
|-----------|-----------------|  
|[Solutions Excel](../vsto/excel-solutions.md)|Explique comment créer des personnalisations au niveau du document et des compléments VSTO pour Microsoft Office Excel.|  
|[Travailler avec des plages](../vsto/working-with-ranges.md)|Fournit des exemples montrant comment effectuer des tâches courantes avec des plages.|  
|[Travailler avec des feuilles de calcul](../vsto/working-with-worksheets.md)|Fournit des exemples montrant comment effectuer des tâches courantes avec des feuilles de calcul.|  
|[Travailler avec des classeurs](../vsto/working-with-workbooks.md)|Fournit des exemples montrant comment effectuer des tâches courantes avec des classeurs.|  
  
  