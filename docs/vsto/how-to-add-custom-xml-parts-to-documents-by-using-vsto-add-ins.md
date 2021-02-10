---
title: Ajouter des parties XML personnalisées à des documents à l’aide des compléments VSTO
description: Découvrez comment vous pouvez stocker des données XML dans les types suivants de documents en créant une partie XML personnalisée dans un complément VSTO.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- add-ins [Office development in Visual Studio], custom XML parts
- Office documents [Office development in Visual Studio, custom XML parts
- Word [Office development in Visual Studio], custom XML parts
- PowerPoint [Office development in Visual Studio], custom XML parts
- Excel [Office development in Visual Studio], custom XML parts
- custom XML parts [Office development in Visual Studio], adding
- documents [Office development in Visual Studio], custom XML parts
- application-level add-ins [Office development in Visual Studio], custom XML parts
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: fbba5c629807815a306221368d00b7d759dcc294
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99954226"
---
# <a name="how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins"></a>Comment : ajouter des parties XML personnalisées à des documents à l’aide des compléments VSTO
  Vous pouvez stocker des données XML dans les types suivants de documents en créant une partie XML personnalisée dans un complément VSTO :

- un classeur Microsoft Office Excel,

- un document Microsoft Office Word,

- une présentation Microsoft Office PowerPoint.

  Pour plus d’informations, consultez [vue d’ensemble des parties XML personnalisées](../vsto/custom-xml-parts-overview.md).

  **S'applique à :** les informations de cette rubrique s'appliquent aux projets de niveau application pour Excel, PowerPoint et Word. Pour plus d’informations, consultez [fonctionnalités disponibles par type d’application et de projet Office](../vsto/features-available-by-office-application-and-project-type.md).

## <a name="to-add-a-custom-xml-part-to-an-excel-workbook"></a>Pour ajouter une partie XML personnalisée à un classeur Excel

1. Ajoutez un nouvel objet <xref:Microsoft.Office.Core.CustomXMLPart> à la collection <xref:Microsoft.Office.Interop.Excel._Workbook.CustomXMLParts%2A> figurant dans le classeur. <xref:Microsoft.Office.Core.CustomXMLPart> contient la chaîne XML que vous souhaitez stocker dans le classeur.

     L'exemple de code suivant ajoute une partie XML personnalisée à un classeur spécifié.

     [!code-vb[Trin_AddCustomXmlPartExcelAppLevel#1](../vsto/codesnippet/VisualBasic/trin_addcustomxmlpartexcelapplevel/ThisAddIn.vb#1)]
     [!code-csharp[Trin_AddCustomXmlPartExcelAppLevel#1](../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartExcelAppLevel/ThisAddIn.cs#1)]

2. Ajoutez la `AddCustomXmlPartToWorkbook` méthode à la `ThisAddIn` classe dans un projet de complément VSTO pour Excel.

3. Appelez cette méthode à partir d'un autre code dans votre projet. Par exemple, pour créer la partie XML personnalisée quand l'utilisateur ouvre un classeur, appelez la méthode à partir d'un gestionnaire d'événements pour l'événement <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookOpen> .

## <a name="to-add-a-custom-xml-part-to-a-word-document"></a>Pour ajouter une partie XML personnalisée à un document Word

1. Ajoutez un nouvel objet <xref:Microsoft.Office.Core.CustomXMLPart> à la collection <xref:Microsoft.Office.Interop.Word._Document.CustomXMLParts%2A> figurant dans le document. <xref:Microsoft.Office.Core.CustomXMLPart> contient la chaîne XML que vous souhaitez stocker dans le document.

     L'exemple de code suivant ajoute une partie XML personnalisée à un document spécifié.

     [!code-vb[Trin_AddCustomXmlPartWordAppLevel#1](../vsto/codesnippet/VisualBasic/Trin_AddCustomXmlPartWordAppLevel/ThisAddIn.vb#1)]
     [!code-csharp[Trin_AddCustomXmlPartWordAppLevel#1](../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartWordAppLevel/ThisAddIn.cs#1)]

2. Ajoutez la `AddCustomXmlPartToDocument` méthode à la `ThisAddIn` classe dans un projet de complément VSTO pour Word.

3. Appelez cette méthode à partir d'un autre code dans votre projet. Par exemple, pour créer la partie XML personnalisée quand l'utilisateur ouvre un document, appelez la méthode à partir d'un gestionnaire d'événements pour l'événement <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen> .

## <a name="to-add-a-custom-xml-part-to-a-powerpoint-presentation"></a>Pour ajouter une partie XML personnalisée à une présentation PowerPoint

1. Ajoutez un nouvel <xref:Microsoft.Office.Core.CustomXMLPart> objet à la collection [Microsoft.Office.Interop.PowerPoint._Presentation. CustomXMLParts](/previous-versions/office/developer/office-2010/ff760806%28v%3doffice.14%29) dans la présentation. <xref:Microsoft.Office.Core.CustomXMLPart> contient la chaîne XML que vous souhaitez stocker dans la présentation.

     L'exemple de code suivant ajoute une partie XML personnalisée à une présentation spécifiée.

     [!code-csharp[Trin_AddCustomXmlPartPowerPointAppLevel#1](../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartPowerPointAppLevel/ThisAddIn.cs#1)]
     [!code-vb[Trin_AddCustomXmlPartPowerPointAppLevel#1](../vsto/codesnippet/VisualBasic/Trin_AddCustomXmlPartPowerPointAppLevel/ThisAddIn.vb#1)]

2. Ajoutez la `AddCustomXmlPartToPresentation` méthode à la `ThisAddIn` classe dans un projet de complément VSTO pour PowerPoint.

3. Appelez cette méthode à partir d'un autre code dans votre projet. Par exemple, pour créer la partie XML personnalisée quand l’utilisateur ouvre une présentation, appelez la méthode à partir d’un gestionnaire d’événements pour l’événement [Microsoft.Office.Interop.PowerPoint.EApplication_Event. AfterPresentationOpen](/previous-versions/office/developer/office-2010/ff762843(v=office.14)) .

## <a name="robust-programming"></a>Programmation fiable
 Par souci de simplicité, cet exemple utilise une chaîne XML définie comme variable locale dans la méthode. En règle générale, vous devez obtenir le code XML auprès d'une source externe, telle qu'un fichier ou une base de données.

## <a name="see-also"></a>Voir aussi
- [Vue d’ensemble des parties XML personnalisées](../vsto/custom-xml-parts-overview.md)
- [Comment : ajouter des parties XML personnalisées aux personnalisations au niveau du document](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md)
