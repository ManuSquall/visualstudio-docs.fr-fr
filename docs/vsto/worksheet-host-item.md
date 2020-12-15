---
title: Élément hôte de feuille de calcul
description: Découvrez que l’élément hôte de feuille de calcul est un type qui étend le type de feuille de calcul à partir de l’assembly PIA (Primary Interop Assembly) pour Excel.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- host items [Office development in Visual Studio], Worksheet
- Excel [Office development in Visual Studio], worksheets
- Worksheet host items
- worksheets, events
- Worksheet host items, events
- Excel worksheets
- worksheets, Excel
- worksheets
- events [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b25b921d29bee832ef37b943fd57edc38b7518db
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97523223"
---
# <a name="worksheet-host-item"></a>Élément hôte de feuille de calcul
  L’élément hôte <xref:Microsoft.Office.Tools.Excel.Worksheet> est un type qui étend le type <xref:Microsoft.Office.Interop.Excel.Worksheet> à partir de l’assembly PIA (Primary Interop Assembly) pour Excel. L’élément hôte <xref:Microsoft.Office.Tools.Excel.Worksheet> fournit les mêmes propriétés, méthodes et événements qu’un objet <xref:Microsoft.Office.Interop.Excel.Worksheet> , mais il expose également des événements supplémentaires et agit comme conteneur pour les contrôles hôtes et les contrôles Windows Forms.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Dans les projets au niveau du document, vous pouvez ajouter des éléments hôtes <xref:Microsoft.Office.Tools.Excel.Worksheet> à votre projet au moment du design. Dans les projets de compléments VSTO, vous pouvez générer des éléments hôtes <xref:Microsoft.Office.Tools.Excel.Worksheet> au moment de l'exécution.

## <a name="understand-worksheet-host-items-in-document-level-projects"></a>Comprendre les éléments hôtes de feuille de calcul dans les projets au niveau du document
 Quand vous créez un projet au niveau du document pour Excel, Visual Studio crée automatiquement trois éléments hôtes <xref:Microsoft.Office.Tools.Excel.Worksheet> dans le projet. Les noms par défaut des feuilles de calcul sont `Sheet1`, `Sheet2`et `Sheet3`. Si vous créez un projet basé sur un classeur existant, le nombre d’éléments hôtes dépend du nombre de feuilles de calcul dans le classeur.

 Ces classes de feuille de calcul vous donnent accès aux membres de l’élément hôte <xref:Microsoft.Office.Tools.Excel.Worksheet> pour effectuer des tâches de base dans votre personnalisation, telles que la modification du contenu d’une feuille de calcul. Vous pouvez aussi utiliser ces classes pour ajouter des contrôles à des feuilles de calcul. En combinant plusieurs jeux de contrôles et en écrivant du code, vous pouvez lier les contrôles à des données, recueillir des informations auprès de l’utilisateur et répondre aux actions de l’utilisateur. Pour plus d’informations, consultez [programmes personnalisations au niveau du document](../vsto/programming-document-level-customizations.md).

 Les classes de feuille de calcul fournissent un emplacement dans lequel vous pouvez commencer à écrire du code dans votre projet. Étant donné que la classe fournit les mêmes propriétés, méthodes et événements que l’objet <xref:Microsoft.Office.Interop.Excel.Worksheet> dans l’assembly PIA pour Excel, vous pouvez aussi utiliser ces classes pour accéder au modèle objet d’Excel. Pour plus d’informations, consultez [vue d’ensemble du modèle objet Excel](../vsto/excel-object-model-overview.md).

 Dans les projets au niveau du document, vous pouvez ajouter des éléments hôtes <xref:Microsoft.Office.Tools.Excel.Worksheet> supplémentaires au projet au moment du design en ajoutant une nouvelle feuille de calcul au classeur dans le concepteur.

### <a name="rename-worksheets"></a>Renommer des feuilles de calcul
 Dans un projet au niveau du document, vous pouvez renommer les feuilles de calcul dans le concepteur Visual Studio, mais cela modifie uniquement le nom d’affichage de la feuille de calcul. Le nom de programmation est encore le nom par défaut de la feuille de calcul. Si vous renommez la feuille de calcul dans la fenêtre **Propriétés** , seul le nom de programmation est modifié.

### <a name="limitations-of-the-worksheet-host-item-in-document-level-projects"></a>Limitations de l’élément hôte Worksheet dans les projets au niveau du document
 Vous ne pouvez pas créer d’éléments hôtes <xref:Microsoft.Office.Tools.Excel.Worksheet> au moment de l’exécution dans un projet au niveau du document. Si vous créez une feuille de calcul Excel au moment de l’exécution, elle sera de type <xref:Microsoft.Office.Interop.Excel.Worksheet>. Comme il ne s’agit pas d’un élément hôte, il ne peut pas contenir de contrôles hôtes ni de contrôles Windows Forms. Pour plus d’informations sur la création de documents au moment de l’exécution, consultez [Comment : ajouter des feuilles de calcul à des classeurs par programmation](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md).

## <a name="understand-worksheet-host-items-in-vsto-add-in-projects"></a>Comprendre les éléments hôtes de feuille de calcul dans les projets de complément VSTO
 Dans les projets de niveau application, vous pouvez générer un élément hôte <xref:Microsoft.Office.Tools.Excel.Worksheet> au moment de l’exécution pour toute feuille de calcul ouverte dans Excel. Vous pouvez utiliser l’élément hôte <xref:Microsoft.Office.Tools.Excel.Worksheet> pour ajouter des contrôles à la feuille de calcul associée ou pour gérer des événements qui ne sont pas disponibles sur des objets <xref:Microsoft.Office.Interop.Excel.Worksheet> .

 Pour générer un élément hôte <xref:Microsoft.Office.Tools.Excel.Worksheet>, utilisez la méthode `GetVstoObject`. Pour plus d’informations, consultez [extension de documents Word et de classeurs Excel dans des compléments VSTO au moment](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)de l’exécution.

## <a name="see-also"></a>Voir aussi
- [Exemples et procédures pas à pas relatifs au développement Office](../vsto/office-development-samples-and-walkthroughs.md)
- [Étendre des documents Word et des classeurs Excel dans des compléments VSTO au moment de l’exécution](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Contrôles sur les documents Office](../vsto/controls-on-office-documents.md)
- [Ajouter des contrôles aux documents Office au moment de l’exécution](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Vue d’ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)
- [Élément hôte de classeur](../vsto/workbook-host-item.md)
- [Automatiser Excel à l’aide d’objets étendus](../vsto/automating-excel-by-using-extended-objects.md)
- [Limitations de programmation des éléments hôtes et des contrôles hôtes](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
