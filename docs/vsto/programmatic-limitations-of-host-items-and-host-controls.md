---
title: "Limitations de programmation des &#233;l&#233;ments h&#244;tes et des contr&#244;les h&#244;tes"
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
  - "documents Office (développement Office dans Visual Studio), contrôles hôtes"
  - "développement d’applications (développement Office dans Visual Studio), éléments hôtes"
  - "applications Office (développement Office dans Visual Studio), éléments hôtes"
  - "éléments hôtes (développement Office dans Visual Studio), limitations par programmation"
  - "Excel (développement Office dans Visual Studio), éléments hôtes"
  - "contrôles hôtes (développement Office dans Visual Studio), création"
  - "personnalisations au niveau du document (développement Office dans Visual Studio), contrôles hôtes"
  - "applications Office (développement Office dans Visual Studio), contrôles hôtes"
  - "documents (développement Office dans Visual Studio), contrôles hôtes"
  - "contrôles (développement Office dans Visual Studio), contrôles hôtes"
  - "contrôles hôtes (développement Office dans Visual Studio), passage aux méthodes et propriétés"
  - "développement d’applications (développement Office dans Visual Studio), contrôles hôtes"
  - "Excel (développement Office dans Visual Studio), contrôles hôtes"
  - "contrôles hôtes (développement Office dans Visual Studio), limitations par programmation"
  - "documents (développement Office dans Visual Studio), éléments hôtes"
  - "documents Office (développement Office dans Visual Studio), éléments hôtes"
  - "Word (développement Office dans Visual Studio), éléments hôtes"
  - "personnalisations au niveau du document (développement Office dans Visual Studio), éléments hôtes"
  - "Word (développement Office dans Visual Studio), contrôles hôtes"
ms.assetid: 88487946-6f3d-4ea6-8de0-dd219b8002df
caps.latest.revision: 67
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 63
---
# Limitations de programmation des &#233;l&#233;ments h&#244;tes et des contr&#244;les h&#244;tes
  Chaque élément hôte et contrôle hôte est conçu pour se comporter comme un objet Microsoft Office Word ou Microsoft Office Excel natif correspondant, avec des fonctionnalités supplémentaires. Toutefois, il existe des différences fondamentales entre le comportement des éléments hôtes ou contrôles hôtes, et celui des objets Office natifs au moment de l’exécution.  
  
 Pour obtenir des informations générales sur les éléments hôtes et contrôles hôtes, consultez [Vue d'ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md).  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
## Création d’éléments hôtes par programmation  
 Quand vous créez ou ouvrez par programmation un document, un classeur ou une feuille de calcul au moment de l’exécution via le modèle objet Word ou Excel, l’élément n’est pas un élément hôte. À la place, le nouvel objet est un objet Office natif. Par exemple, si vous utilisez la méthode <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> pour créer un document Word au moment de l’exécution, il correspond à un objet <xref:Microsoft.Office.Interop.Word.Document> natif au lieu d’un élément hôte <xref:Microsoft.Office.Tools.Word.Document>. De même, quand vous créez une feuille de calcul au moment de l’exécution à l’aide de la méthode <xref:Microsoft.Office.Interop.Excel.Worksheets.Add%2A>, vous obtenez un objet <xref:Microsoft.Office.Interop.Excel.Worksheet> natif au lieu d’un élément hôte <xref:Microsoft.Office.Tools.Excel.Worksheet>.  
  
 Dans les projets au niveau du document, vous ne pouvez pas créer d’éléments hôtes au moment de l’exécution. Vous ne pouvez créer les éléments hôtes qu’au moment du design dans les projets au niveau du document. Pour plus d'informations, consultez [Élément hôte de document](../vsto/document-host-item.md), [Élément hôte de classeur](../vsto/workbook-host-item.md) et [Élément hôte de feuille de calcul](../vsto/worksheet-host-item.md).  
  
 Dans les projets de compléments VSTO, vous pouvez créer des éléments hôtes <xref:Microsoft.Office.Tools.Word.Document>, <xref:Microsoft.Office.Tools.Excel.Workbook> ou <xref:Microsoft.Office.Tools.Excel.Worksheet> au moment de l’exécution. Pour plus d'informations, consultez [Extension de documents Word et de classeurs Excel dans des compléments VSTO au moment de l'exécution](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
## Création de contrôles hôtes par programmation  
 Vous pouvez ajouter par programmation des contrôles hôtes à un élément hôte <xref:Microsoft.Office.Tools.Word.Document> ou <xref:Microsoft.Office.Tools.Excel.Worksheet> au moment de l’exécution. Pour plus d'informations, consultez [Ajout de contrôles à des documents Office au moment de l'exécution](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
 Vous ne pouvez pas ajouter de contrôles hôtes à un <xref:Microsoft.Office.Interop.Word.Document> ou <xref:Microsoft.Office.Interop.Excel.Worksheet> natif.  
  
> [!NOTE]  
>  Vous ne pouvez pas ajouter les contrôles hôtes suivants par programmation aux feuilles de calcul ou aux documents : <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>, <xref:Microsoft.Office.Tools.Word.XMLNode>, et <xref:Microsoft.Office.Tools.Word.XMLNodes>.  
  
## Présentation des différences de type entre les éléments hôtes, les contrôles hôtes et les objets Office natifs  
 Pour chaque élément hôte et contrôle hôte, il existe un objet Microsoft Office Word ou Microsoft Office Excel natif sous\-jacent. Vous pouvez accéder à l’objet sous\-jacent à l’aide de la propriété InnerObject de l’élément hôte ou du contrôle hôte. Toutefois, il n’existe aucun moyen d’effectuer un cast d’un objet Office natif vers son élément hôte ou contrôle hôte correspondant. Si vous essayez d’effectuer un cast d’un objet Office natif vers le type d’un élément hôte ou contrôle hôte, <xref:System.InvalidCastException> est levé.  
  
 Il existe plusieurs scénarios où les différences entre les types des éléments hôtes ou contrôles hôtes, et ceux des objets Office natifs sous\-jacents peuvent affecter votre code.  
  
### Passage de contrôles hôtes aux méthodes et propriétés  
 Dans Word, vous ne pouvez pas passer un contrôle hôte à une méthode ou une propriété qui nécessite un objet Word natif en tant que paramètre. Vous devez utiliser la propriété InnerObject du contrôle hôte pour retourner l’objet Word natif sous\-jacent. Par exemple, vous pouvez passer un objet <xref:Microsoft.Office.Interop.Word.Bookmark> à une méthode en passant la propriété <xref:Microsoft.Office.Tools.Word.Bookmark.InnerObject%2A> du contrôle hôte <xref:Microsoft.Office.Tools.Word.Bookmark> à la méthode.  
  
 Dans Excel, vous devez utiliser la propriété InnerObject du contrôle hôte pour passer ce dernier à une méthode ou une propriété quand la méthode ou la propriété attend l’objet Excel sous\-jacent.  
  
 L’exemple suivant crée un contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange> et le passe à la méthode <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A>. Le code utilise la propriété <xref:Microsoft.Office.Tools.Excel.NamedRange.InnerObject%2A> de la plage nommée pour retourner le <xref:Microsoft.Office.Interop.Excel.Range> Office sous\-jacent nécessaire à la méthode <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A>.  
  
 [!code-csharp[Trin_VstcoreHostControlsExcel#28](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#28)]
 [!code-vb[Trin_VstcoreHostControlsExcel#28](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet1.vb#28)]  
  
### Types de retour des méthodes et propriétés Office natives  
 La plupart des méthodes et propriétés des éléments hôtes retournent l’objet Office natif sous\-jacent sur lequel l’élément hôte est basé. Par exemple, la propriété <xref:Microsoft.Office.Tools.Excel.NamedRange.Parent%2A> d’un contrôle hôte <xref:Microsoft.Office.Tools.Excel.NamedRange> dans Excel retourne un objet <xref:Microsoft.Office.Interop.Excel.Worksheet> à la place d’un élément hôte <xref:Microsoft.Office.Tools.Excel.Worksheet>. De même, la propriété <xref:Microsoft.Office.Tools.Word.RichTextContentControl.Parent%2A> d’un contrôle hôte <xref:Microsoft.Office.Tools.Word.RichTextContentControl> dans Word retourne un objet <xref:Microsoft.Office.Interop.Word.Document> à la place d’un élément hôte <xref:Microsoft.Office.Tools.Word.Document>.  
  
### Accès aux collections de contrôles hôtes  
 Le [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] ne fournit pas de collections individuelles pour chaque type de contrôle hôte. Utilisez plutôt la propriété Controls d’un élément hôte pour itérer dans tous les contrôles managés \(contrôles hôtes et contrôles Windows Forms\) du document ou de la feuille de calcul, puis recherchez les éléments qui correspondent au type du contrôle hôte souhaité. L’exemple de code suivant permet d’examiner chaque contrôle d’un document Word et de déterminer si le contrôle correspond à <xref:Microsoft.Office.Tools.Word.Bookmark>.  
  
 [!code-csharp[Trin_VstcoreHostControlsWord#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsWord/CS/ThisDocument.cs#10)]
 [!code-vb[Trin_VstcoreHostControlsWord#10](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsWord/VB/ThisDocument.vb#10)]  
  
 Pour plus d’informations sur la propriété Controls des éléments hôtes, consultez [Ajout de contrôles à des documents Office au moment de l'exécution](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
 Les modèles objet Word et Excel incluent des propriétés qui exposent des collections de contrôles natifs sur des documents et des feuilles de calcul. Vous ne pouvez pas accéder aux contrôles managés à l’aide de ces propriétés. Par exemple, il n’est pas possible d’énumérer chaque contrôle hôte <xref:Microsoft.Office.Tools.Word.Bookmark> d’un document à l’aide de la propriété <xref:Microsoft.Office.Interop.Word._Document.Bookmarks%2A> de <xref:Microsoft.Office.Interop.Word.Document> ou de la propriété <xref:Microsoft.Office.Tools.Word.Document.Bookmarks%2A> de <xref:Microsoft.Office.Tools.Word.Document>. Ces propriétés incluent uniquement les contrôles <xref:Microsoft.Office.Interop.Word.Bookmark> dans le document ; elles ne contiennent pas les contrôles hôtes <xref:Microsoft.Office.Tools.Word.Bookmark> dans le document.  
  
## Voir aussi  
 [Vue d'ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)   
 [Automatisation de Word à l'aide d'objets étendus](../vsto/automating-word-by-using-extended-objects.md)   
 [Automatisation d'Excel à l'aide d'objets étendus](../vsto/automating-excel-by-using-extended-objects.md)   
 [Élément hôte de feuille de calcul](../vsto/worksheet-host-item.md)   
 [Élément hôte de classeur](../vsto/workbook-host-item.md)   
 [Élément hôte de document](../vsto/document-host-item.md)  
  
  