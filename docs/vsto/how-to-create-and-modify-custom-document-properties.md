---
title: "Comment : créer et modifier les propriétés de Document personnalisées | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom document properties
- documents [Office development in Visual Studio], properties
- document properties [Office development in Visual Studio]
ms.assetid: 99d9dfaf-891f-4f3b-a580-67362afdaf34
caps.latest.revision: "47"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 78cf27b7d58e85217c770abee1dc6a4151cc1eb1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-create-and-modify-custom-document-properties"></a>Comment : créer et modifier des propriétés de document personnalisées
  Les applications Microsoft Office répertoriées ci-dessus fournissent des propriétés intégrées qui sont stockées avec les documents. En outre, vous pouvez créer et modifier des propriétés de document personnalisées si vous souhaitez stocker des informations supplémentaires avec le document.  
  
 [!INCLUDE[appliesto_docprops](../vsto/includes/appliesto-docprops-md.md)]  
  
 Utilisez la propriété CustomDocumentProperties d’un document pour travailler avec les propriétés personnalisées. Par exemple, dans un projet au niveau du document pour Microsoft Office Excel, utilisez la propriété <xref:Microsoft.Office.Tools.Excel.Workbook.CustomDocumentProperties%2A> de la classe `ThisWorkbook` . Dans un projet de complément VSTO pour Excel, utilisez la propriété <xref:Microsoft.Office.Interop.Excel._Workbook.CustomDocumentProperties%2A> d'un objet <xref:Microsoft.Office.Interop.Excel.Workbook> . Ces propriétés retournent un objet <xref:Microsoft.Office.Core.DocumentProperties> , qui est une collection d'objets <xref:Microsoft.Office.Core.DocumentProperty> . Vous pouvez utiliser la propriété `Item` de la collection pour récupérer une propriété particulière, par nom ou par index dans la collection.  
  
 L'exemple suivant illustre l'ajout d'une propriété personnalisée dans une personnalisation au niveau du document pour Excel et l'affectation d'une valeur à cette propriété.  
  
 ![lien vers la vidéo](../vsto/media/playvideo.gif "lien vidéo") pour une démonstration vidéo connexe, consultez [comment faire pour accéder et manipuler des propriétés de Document personnalisées dans Microsoft Word ?](http://go.microsoft.com/fwlink/?LinkId=136772).  
  
## <a name="example"></a>Exemple  
 [!code-vb[Trin_VstcoreProgramming#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/ThisWorkbook.vb#6)]
 [!code-csharp[Trin_VstcoreProgramming#6](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/ThisWorkbook.cs#6)]  
  
## <a name="robust-programming"></a>Programmation fiable  
 Toute tentative d'accès à la propriété `Value` pour des propriétés non définies lève une exception.  
  
## <a name="see-also"></a>Voir aussi  
 [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)   
 [Programmation des personnalisations au niveau du Document](../vsto/programming-document-level-customizations.md)   
 [Guide pratique pour lire des propriétés de document et en écrire](../vsto/how-to-read-from-and-write-to-document-properties.md)  
  
  