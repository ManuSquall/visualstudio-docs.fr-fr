---
title: 'Procédure : Créer et modifier les propriétés de document personnalisées'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom document properties
- documents [Office development in Visual Studio], properties
- document properties [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e890cedb774527ba49c6061ee36c5efc091f3188
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2019
ms.locfileid: "54865812"
---
# <a name="how-to-create-and-modify-custom-document-properties"></a>Procédure : Créer et modifier les propriétés de document personnalisées
  Les applications Microsoft Office répertoriées ci-dessus fournissent des propriétés intégrées qui sont stockées avec les documents. En outre, vous pouvez créer et modifier des propriétés de document personnalisées si vous souhaitez stocker des informations supplémentaires avec le document.  
  
 [!INCLUDE[appliesto_docprops](../vsto/includes/appliesto-docprops-md.md)]  
  
 Utilisez la propriété CustomDocumentProperties d’un document pour travailler avec des propriétés personnalisées. Par exemple, dans un projet au niveau du document pour Microsoft Office Excel, utilisez la propriété <xref:Microsoft.Office.Tools.Excel.Workbook.CustomDocumentProperties%2A> de la classe `ThisWorkbook` . Dans un projet de complément VSTO pour Excel, utilisez la propriété <xref:Microsoft.Office.Interop.Excel._Workbook.CustomDocumentProperties%2A> d'un objet <xref:Microsoft.Office.Interop.Excel.Workbook> . Ces propriétés retournent un objet <xref:Microsoft.Office.Core.DocumentProperties> , qui est une collection d'objets <xref:Microsoft.Office.Core.DocumentProperty> . Vous pouvez utiliser la propriété `Item` de la collection pour récupérer une propriété particulière, par nom ou par index dans la collection.  
  
 L'exemple suivant illustre l'ajout d'une propriété personnalisée dans une personnalisation au niveau du document pour Excel et l'affectation d'une valeur à cette propriété.  
  
 ![lien vers la vidéo](../vsto/media/playvideo.gif "lien vers la vidéo") pour une démonstration vidéo connexe, consultez [How do I: Accéder et manipuler les propriétés de document personnalisées dans Microsoft Word ? ](http://go.microsoft.com/fwlink/?LinkId=136772).  
  
## <a name="example"></a>Exemple  
 [!code-vb[Trin_VstcoreProgramming#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/ThisWorkbook.vb#6)]
 [!code-csharp[Trin_VstcoreProgramming#6](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/ThisWorkbook.cs#6)]  
  
## <a name="robust-programming"></a>Programmation fiable  
 Toute tentative d'accès à la propriété `Value` pour des propriétés non définies lève une exception.  
  
## <a name="see-also"></a>Voir aussi  
 [Programmer des Compléments VSTO](../vsto/programming-vsto-add-ins.md)   
 [Programmer des personnalisations au niveau du document](../vsto/programming-document-level-customizations.md)   
 [Guide pratique pour Lire et écrire dans les propriétés de document](../vsto/how-to-read-from-and-write-to-document-properties.md)  
