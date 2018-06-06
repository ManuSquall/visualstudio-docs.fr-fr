---
title: Limitations de programmation des éléments hôtes et des contrôles hôtes
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office documents [Office development in Visual Studio, host controls
- application development [Office development in Visual Studio], host items
- Office applications [Office development in Visual Studio], host items
- host items [Office development in Visual Studio], programmatic limitations
- Excel [Office development in Visual Studio], host items
- host controls [Office development in Visual Studio], creating
- document-level customizations [Office development in Visual Studio], host controls
- Office applications [Office development in Visual Studio], host controls
- documents [Office development in Visual Studio], host controls
- controls [Office development in Visual Studio], host controls
- host controls [Office development in Visual Studio], passing to methods and properties
- application development [Office development in Visual Studio], host controls
- Excel [Office development in Visual Studio], host controls
- host controls [Office development in Visual Studio], programmatic limitations
- documents [Office development in Visual Studio], host items
- Office documents [Office development in Visual Studio, host items
- Word [Office development in Visual Studio], host items
- document-level customizations [Office development in Visual Studio], host items
- Word [Office development in Visual Studio], host controls
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 0b7e45ed9ba8e9fcd42d57a1cc6aaf34ce3e3711
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34693381"
---
# <a name="programmatic-limitations-of-host-items-and-host-controls"></a>Limitations de programmation des éléments hôtes et des contrôles hôtes
  Chaque élément hôte et contrôle hôte est conçu pour se comporter comme un objet Microsoft Office Word ou Microsoft Office Excel natif correspondant, avec des fonctionnalités supplémentaires. Toutefois, il existe des différences fondamentales entre le comportement des éléments hôtes ou contrôles hôtes, et celui des objets Office natifs au moment de l’exécution.  
  
 Pour obtenir des informations générales sur les éléments hôtes et des contrôles hôtes, consultez [éléments hôtes et héberger la vue d’ensemble des contrôles](../vsto/host-items-and-host-controls-overview.md).  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
## <a name="programmatically-create-host-items"></a>Créer par programmation des éléments hôtes  
 Quand vous créez ou ouvrez par programmation un document, un classeur ou une feuille de calcul au moment de l’exécution via le modèle objet Word ou Excel, l’élément n’est pas un élément hôte. À la place, le nouvel objet est un objet Office natif. Par exemple, si vous utilisez la méthode <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> pour créer un document Word au moment de l’exécution, il correspond à un objet <xref:Microsoft.Office.Interop.Word.Document> natif au lieu d’un élément hôte <xref:Microsoft.Office.Tools.Word.Document> . De même, quand vous créez une feuille de calcul au moment de l’exécution à l’aide de la méthode <xref:Microsoft.Office.Interop.Excel.Worksheets.Add%2A> , vous obtenez un objet <xref:Microsoft.Office.Interop.Excel.Worksheet> natif au lieu d’un élément hôte <xref:Microsoft.Office.Tools.Excel.Worksheet> .  
  
 Dans les projets au niveau du document, vous ne pouvez pas créer des éléments hôtes lors de l’exécution. Vous ne pouvez créer les éléments hôtes qu’au moment du design dans les projets au niveau du document. Pour plus d’informations, consultez [élément hôte de Document](../vsto/document-host-item.md), [élément hôte de classeur](../vsto/workbook-host-item.md), et [élément hôte de feuille de calcul](../vsto/worksheet-host-item.md).  
  
 Dans les projets de complément VSTO, vous pouvez créer <xref:Microsoft.Office.Tools.Word.Document>, <xref:Microsoft.Office.Tools.Excel.Workbook>, ou <xref:Microsoft.Office.Tools.Excel.Worksheet> héberger des éléments lors de l’exécution. Pour plus d’informations, consultez [documents Word d’étendre et classeurs Excel dans des Compléments VSTO lors de l’exécution](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
## <a name="programmatically-create-host-controls"></a>Créer par programmation des contrôles hôtes  
 Vous pouvez ajouter par programmation des contrôles hôtes à un <xref:Microsoft.Office.Tools.Word.Document> ou <xref:Microsoft.Office.Tools.Excel.Worksheet> élément hôte lors de l’exécution. Pour plus d’informations, consultez [ajouter des contrôles aux documents Office au moment de l’exécution](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
 Vous ne pouvez pas ajouter de contrôles hôtes à un <xref:Microsoft.Office.Interop.Word.Document> ou <xref:Microsoft.Office.Interop.Excel.Worksheet>natif.  
  
> [!NOTE]  
>  Vous ne pouvez pas ajouter les contrôles hôtes suivants par programmation aux feuilles de calcul ou aux documents : <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>, <xref:Microsoft.Office.Tools.Word.XMLNode>, et <xref:Microsoft.Office.Tools.Word.XMLNodes>.  
  
## <a name="understand-type-differences-between-host-items-host-controls-and-native-office-objects"></a>Comprendre les différences de type entre les éléments hôtes, contrôles hôtes et les objets Office natifs  
 Pour chaque élément hôte et contrôle hôte, il existe un objet Microsoft Office Word ou Microsoft Office Excel natif sous-jacent. Vous pouvez accéder à l’objet sous-jacent à l’aide de la propriété InnerObject de l’élément hôte ou contrôle hôte. Toutefois, il n’existe aucun moyen d’effectuer un cast d’un objet Office natif vers son élément hôte ou contrôle hôte correspondant. Si vous essayez d’effectuer un cast d’un objet Office natif vers le type d’un élément hôte ou contrôle hôte, <xref:System.InvalidCastException> est levé.  
  
 Il existe plusieurs scénarios où les différences entre les types des éléments hôtes ou contrôles hôtes, et ceux des objets Office natifs sous-jacents peuvent affecter votre code.  
  
### <a name="pass-host-controls-to-methods-and-properties"></a>Passer des contrôles hôtes aux méthodes et propriétés  
 Dans Word, vous ne pouvez pas passer un contrôle hôte à une méthode ou une propriété qui nécessite un objet Word natif en tant que paramètre. Vous devez utiliser la propriété InnerObject du contrôle hôte pour retourner l’objet Word natif sous-jacent. Par exemple, vous pouvez passer un objet <xref:Microsoft.Office.Interop.Word.Bookmark> à une méthode en passant la propriété <xref:Microsoft.Office.Tools.Word.Bookmark.InnerObject%2A> du contrôle hôte <xref:Microsoft.Office.Tools.Word.Bookmark> à la méthode.  
  
 Dans Excel, vous devez utiliser la propriété InnerObject du contrôle hôte pour passer le contrôle hôte à une méthode ou propriété lorsque la méthode ou propriété attend l’objet Excel sous-jacent.  
  
 L’exemple suivant crée un contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange> et le passe à la méthode <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> . Le code utilise la propriété <xref:Microsoft.Office.Tools.Excel.NamedRange.InnerObject%2A> de la plage nommée pour retourner le <xref:Microsoft.Office.Interop.Excel.Range> Office sous-jacent nécessaire à la méthode <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> .  
  
 [!code-csharp[Trin_VstcoreHostControlsExcel#28](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#28)]
 [!code-vb[Trin_VstcoreHostControlsExcel#28](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#28)]  
  
### <a name="return-types-of-native-office-methods-and-properties"></a>Types de retour des propriétés et méthodes Office natives  
 La plupart des méthodes et propriétés des éléments hôtes retournent l’objet Office natif sous-jacent sur lequel l’élément hôte est basé. Par exemple, la propriété <xref:Microsoft.Office.Tools.Excel.NamedRange.Parent%2A> d’un contrôle hôte <xref:Microsoft.Office.Tools.Excel.NamedRange> dans Excel retourne un objet <xref:Microsoft.Office.Interop.Excel.Worksheet> à la place d’un élément hôte <xref:Microsoft.Office.Tools.Excel.Worksheet> . De même, la propriété <xref:Microsoft.Office.Tools.Word.RichTextContentControl.Parent%2A> d’un contrôle hôte <xref:Microsoft.Office.Tools.Word.RichTextContentControl> dans Word retourne un objet <xref:Microsoft.Office.Interop.Word.Document> à la place d’un élément hôte <xref:Microsoft.Office.Tools.Word.Document> .  
  
### <a name="access-collections-of-host-controls"></a>Collections d’accès de contrôles hôtes  
 Le [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] ne fournit pas de collections individuelles pour chaque type de contrôle hôte. Au lieu de cela, utilisez la propriété de contrôles d’un élément hôte pour itérer sur tous les contrôles managés (contrôles hôtes et contrôles Windows Forms) sur le document ou la feuille de calcul, puis rechercher les éléments qui correspondent au type du contrôle hôte qui que vous intéressez. L’exemple de code suivant permet d’examiner chaque contrôle d’un document Word et de déterminer si le contrôle correspond à <xref:Microsoft.Office.Tools.Word.Bookmark>.  
  
 [!code-csharp[Trin_VstcoreHostControlsWord#10](../vsto/codesnippet/CSharp/trin_vstcorehostcontrolsword/ThisDocument.cs#10)]
 [!code-vb[Trin_VstcoreHostControlsWord#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsWordVB/ThisDocument.vb#10)]  
  
 Pour plus d’informations sur la propriété de contrôles des éléments hôtes, consultez [ajouter des contrôles aux documents Office au moment de l’exécution](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
 Les modèles objet Word et Excel incluent des propriétés qui exposent des collections de contrôles natifs sur des documents et des feuilles de calcul. Vous ne pouvez pas accéder aux contrôles managés à l’aide de ces propriétés. Par exemple, il n’est pas possible d’énumérer chaque contrôle hôte <xref:Microsoft.Office.Tools.Word.Bookmark> d’un document à l’aide de la propriété <xref:Microsoft.Office.Interop.Word._Document.Bookmarks%2A> de <xref:Microsoft.Office.Interop.Word.Document> ou de la propriété <xref:Microsoft.Office.Tools.Word.Document.Bookmarks%2A> de <xref:Microsoft.Office.Tools.Word.Document>. Ces propriétés incluent uniquement les contrôles <xref:Microsoft.Office.Interop.Word.Bookmark> dans le document ; elles ne contiennent pas les contrôles hôtes <xref:Microsoft.Office.Tools.Word.Bookmark> dans le document.  
  
## <a name="see-also"></a>Voir aussi  
 [Éléments hôtes et vue d’ensemble des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)   
 [Automatisation de Word à l’aide d’objets étendus](../vsto/automating-word-by-using-extended-objects.md)   
 [Automatisation d’Excel à l’aide d’objets étendus](../vsto/automating-excel-by-using-extended-objects.md)   
 [Élément hôte de feuille de calcul](../vsto/worksheet-host-item.md)   
 [Élément hôte de classeur](../vsto/workbook-host-item.md)   
 [Élément hôte de document](../vsto/document-host-item.md)  
  
  