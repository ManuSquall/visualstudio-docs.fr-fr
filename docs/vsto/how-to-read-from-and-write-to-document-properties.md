---
title: 'Comment : lire et écrire dans les propriétés d’un document'
description: Découvrez comment vous pouvez utiliser Visual Studio pour obtenir ou définir des propriétés de document dans Microsoft Excel et Microsoft Word.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word [Office development in Visual Studio], document properties
- documents [Office development in Visual Studio], properties
- document properties [Office development in Visual Studio]
- Excel [Office development in Visual Studio], document properties
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 3474d86a7408e841d383c82e5ab38da90253dbbf
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826679"
---
# <a name="how-to-read-from-and-write-to-document-properties"></a>Comment : lire et écrire dans les propriétés d’un document
  Vous pouvez stocker des propriétés de document avec un document. Les applications Office fournissent plusieurs propriétés intégrées, telles que l'auteur, le titre et l'objet. Cette rubrique indique comment définir des propriétés de document dans Microsoft Office Excel et Microsoft Office Word.

 [!INCLUDE[appliesto_docprops](../vsto/includes/appliesto-docprops-md.md)]

## <a name="set-document-properties-in-excel"></a>Définir des propriétés de document dans Excel
 Pour travailler avec des propriétés intégrées dans Excel, utilisez les propriétés suivantes :

- Dans un projet au niveau du document, utilisez la propriété <xref:Microsoft.Office.Tools.Excel.Workbook.BuiltinDocumentProperties%2A> de la classe `ThisWorkbook` .

- Dans un projet de complément VSTO, utilisez la propriété <xref:Microsoft.Office.Interop.Excel._Workbook.BuiltinDocumentProperties%2A> d'un objet <xref:Microsoft.Office.Interop.Excel.Workbook> .

  Ces propriétés retournent un objet <xref:Microsoft.Office.Core.DocumentProperties> , qui est une collection d'objets <xref:Microsoft.Office.Core.DocumentProperty> . Vous pouvez utiliser la propriété `Item` de la collection pour récupérer une propriété particulière, par nom ou par index dans la collection.

  L'exemple de code suivant indique comment modifier la propriété intégrée **Revision Number** dans un projet au niveau du document.

### <a name="to-change-the-revision-number-property-in-excel"></a>Pour modifier la propriété Revision Number dans Excel

1. Assignez les propriétés de document intégrées à une variable.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/ThisWorkbook.vb" id="Snippet7":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/ThisWorkbook.cs" id="Snippet7":::

2. Incrémentez la propriété `Revision Number` de un.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/ThisWorkbook.vb" id="Snippet8":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/ThisWorkbook.cs" id="Snippet8":::

## <a name="set-document-properties-in-word"></a>Définir les propriétés de document dans Word
 Pour travailler avec des propriétés intégrées dans Word, utilisez les propriétés suivantes :

- Dans un projet au niveau du document, utilisez la propriété <xref:Microsoft.Office.Tools.Word.Document.BuiltInDocumentProperties%2A> de la classe `ThisDocument` .

- Dans un projet de complément VSTO, utilisez la propriété <xref:Microsoft.Office.Interop.Word._Document.BuiltInDocumentProperties%2A> d'un objet <xref:Microsoft.Office.Interop.Word.Document> .

  Ces propriétés retournent un objet <xref:Microsoft.Office.Core.DocumentProperties> , qui est une collection d'objets <xref:Microsoft.Office.Core.DocumentProperty> . Vous pouvez utiliser la propriété `Item` de la collection pour récupérer une propriété particulière, par nom ou par index dans la collection.

  L'exemple de code suivant indique comment modifier la propriété intégrée **Subject** dans un projet au niveau du document.

### <a name="to-change-the-subject-property"></a>Pour modifier la propriété Subject

1. Assignez les propriétés de document intégrées à une variable.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingWordCS/ThisDocument.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingWordVB/ThisDocument.vb" id="Snippet1":::

2. Remplacez la valeur de la propriété `Subject` par « Whitepaper ».

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingWordCS/ThisDocument.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingWordVB/ThisDocument.vb" id="Snippet2":::

## <a name="robust-programming"></a>Programmation fiable
 Les exemples supposent que vous avez écrit le code dans la classe `ThisWorkbook` dans un projet au niveau du document pour Excel et dans la classe `ThisDocument` dans un projet au niveau du document pour Word.

 Bien que vous utilisiez Word et Excel ainsi que leurs objets, Microsoft Office fournit la liste des propriétés de document intégrées disponibles. Toute tentative d'accès à une propriété non définie lève une exception.

## <a name="see-also"></a>Voir aussi
- [Programmer les compléments VSTO](../vsto/programming-vsto-add-ins.md)
- [Personnaliser les personnalisations au niveau du document](../vsto/programming-document-level-customizations.md)
- [Comment : créer et modifier des propriétés de document personnalisées](../vsto/how-to-create-and-modify-custom-document-properties.md)
