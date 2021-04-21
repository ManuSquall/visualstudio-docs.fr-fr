---
title: 'Comment : ajouter des parties XML personnalisées aux personnalisations au niveau du document'
description: Découvrez comment vous pouvez stocker des données XML dans un classeur Excel Microsoft Office ou un document Word Microsoft Office en créant une partie XML personnalisée dans une personnalisation au niveau du document.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- document-level customizations [Office development in Visual Studio], custom XML parts
- Office documents [Office development in Visual Studio, custom XML parts
- Word [Office development in Visual Studio], custom XML parts
- Excel [Office development in Visual Studio], custom XML parts
- custom XML parts [Office development in Visual Studio], adding
- documents [Office development in Visual Studio], custom XML parts
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 99374a2daded3c4b49b60053a69cd1ff7c4dffe8
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827682"
---
# <a name="how-to-add-custom-xml-parts-to-document-level-customizations"></a>Comment : ajouter des parties XML personnalisées aux personnalisations au niveau du document
  Vous pouvez stocker des données XML dans un classeur Microsoft Office Excel ou un document Microsoft Office Word en créant une partie XML personnalisée dans une personnalisation au niveau du document. Pour plus d’informations, consultez [vue d’ensemble des parties XML personnalisées](../vsto/custom-xml-parts-overview.md).

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

> [!NOTE]
> Visual Studio ne fournit pas de projets au niveau du document pour Microsoft Office PowerPoint. Pour plus d’informations sur l’ajout d’une partie XML personnalisée à une présentation PowerPoint à l’aide d’un complément VSTO, consultez [Comment : ajouter des parties XML personnalisées à des documents à l’aide des compléments VSTO](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md).

### <a name="to-add-a-custom-xml-part-to-an-excel-workbook"></a>Pour ajouter une partie XML personnalisée à un classeur Excel

1. Ajoutez un nouvel objet <xref:Microsoft.Office.Core.CustomXMLPart> à la collection <xref:Microsoft.Office.Core.CustomXMLParts> figurant dans le classeur. <xref:Microsoft.Office.Core.CustomXMLPart> contient la chaîne XML que vous souhaitez stocker dans le classeur.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartExcelDocLevel/ThisWorkbook.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_AddCustomXmlPartExcelDocLevel/ThisWorkbook.vb" id="Snippet1":::

2. Ajoutez la méthode `AddCustomXmlPartToWorkbook` à la classe `ThisWorkbook` dans un projet au niveau du document pour Excel.

3. Appelez cette méthode à partir d'un autre code dans votre projet. Par exemple, pour créer la partie XML personnalisée quand l’utilisateur ouvre le classeur, appelez la méthode à partir du gestionnaire d’événements `ThisWorkbook_Startup` .

### <a name="to-add-a-custom-xml-part-to-a-word-document"></a>Pour ajouter une partie XML personnalisée à un document Word

1. Ajoutez un nouvel objet <xref:Microsoft.Office.Core.CustomXMLPart> à la collection <xref:Microsoft.Office.Core.CustomXMLParts> figurant dans le document. <xref:Microsoft.Office.Core.CustomXMLPart> contient la chaîne XML que vous souhaitez stocker dans le document.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_AddCustomXmlPartWordDocLevel/ThisDocument.vb" id="Snippet1":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartWordDocLevel/ThisDocument.cs" id="Snippet1":::

2. Ajoutez la méthode `AddCustomXmlPartToDocument` à la classe `ThisDocument` dans un projet au niveau du document pour Word.

3. Appelez cette méthode à partir d'un autre code dans votre projet. Par exemple, pour créer la partie XML personnalisée quand l’utilisateur ouvre le document, appelez la méthode à partir du gestionnaire d’événements `ThisDocument_Startup` .

## <a name="robust-programming"></a>Programmation fiable
 Par souci de simplicité, cet exemple utilise une chaîne XML définie comme variable locale dans la méthode. En règle générale, vous devez obtenir le code XML auprès d'une source externe, telle qu'un fichier ou une base de données.

## <a name="see-also"></a>Voir aussi
- [Vue d’ensemble des parties XML personnalisées](../vsto/custom-xml-parts-overview.md)
- [Comment : ajouter des parties XML personnalisées à des documents à l’aide des compléments VSTO](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md)
