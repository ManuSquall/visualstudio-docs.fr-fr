---
title: 'Comment : créer et modifier des propriétés de document personnalisées'
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: 6dd4f4ada36be4ef7b70f4f32d659abb10c8a62a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547210"
---
# <a name="how-to-create-and-modify-custom-document-properties"></a>Comment : créer et modifier des propriétés de document personnalisées
  Les applications Microsoft Office répertoriées ci-dessus fournissent des propriétés intégrées qui sont stockées avec les documents. En outre, vous pouvez créer et modifier des propriétés de document personnalisées si vous souhaitez stocker des informations supplémentaires avec le document.

 [!INCLUDE[appliesto_docprops](../vsto/includes/appliesto-docprops-md.md)]

 Utilisez la propriété CustomDocumentProperties d’un document pour travailler avec des propriétés personnalisées. Par exemple, dans un projet au niveau du document pour Microsoft Office Excel, utilisez la propriété <xref:Microsoft.Office.Tools.Excel.Workbook.CustomDocumentProperties%2A> de la classe `ThisWorkbook` . Dans un projet de complément VSTO pour Excel, utilisez la propriété <xref:Microsoft.Office.Interop.Excel._Workbook.CustomDocumentProperties%2A> d'un objet <xref:Microsoft.Office.Interop.Excel.Workbook> . Ces propriétés retournent un objet <xref:Microsoft.Office.Core.DocumentProperties> , qui est une collection d'objets <xref:Microsoft.Office.Core.DocumentProperty> . Vous pouvez utiliser la propriété `Item` de la collection pour récupérer une propriété particulière, par nom ou par index dans la collection.

 L'exemple suivant illustre l'ajout d'une propriété personnalisée dans une personnalisation au niveau du document pour Excel et l'affectation d'une valeur à cette propriété.

## <a name="example"></a>Exemple
 [!code-vb[Trin_VstcoreProgramming#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/ThisWorkbook.vb#6)]
 [!code-csharp[Trin_VstcoreProgramming#6](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/ThisWorkbook.cs#6)]

## <a name="robust-programming"></a>Programmation fiable
 Toute tentative d'accès à la propriété `Value` pour des propriétés non définies lève une exception.

## <a name="see-also"></a>Voir aussi
- [Programmer les compléments VSTO](../vsto/programming-vsto-add-ins.md)
- [Personnaliser les personnalisations au niveau du document](../vsto/programming-document-level-customizations.md)
- [Comment : lire et écrire dans les propriétés d’un document](../vsto/how-to-read-from-and-write-to-document-properties.md)
