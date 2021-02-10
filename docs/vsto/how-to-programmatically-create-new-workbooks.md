---
title: 'Comment : créer des classeurs par programmation'
description: Découvrez comment vous pouvez créer un classeur Microsoft Excel par programmation à l’aide de Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel [Office development in Visual Studio], creating workbooks
- workbooks, creating
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 13acd34d9883cfdc7df201dff193d261252f8a9d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99963989"
---
# <a name="how-to-programmatically-create-new-workbooks"></a>Comment : créer des classeurs par programmation
  Quand vous créez un classeur par programmation, il correspond à un objet <xref:Microsoft.Office.Interop.Excel.Workbook> natif et non pas à un élément hôte <xref:Microsoft.Office.Tools.Excel.Workbook>.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Vous pouvez générer un élément hôte <xref:Microsoft.Office.Tools.Excel.Workbook> pour un objet <xref:Microsoft.Office.Interop.Excel.Workbook> dans le projet de complément VSTO. Pour plus d’informations, consultez [extension de documents Word et de classeurs Excel dans des compléments VSTO au moment](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)de l’exécution.

## <a name="to-create-a-new-workbook"></a>Pour créer un classeur

1. Utilisez la méthode <xref:Microsoft.Office.Interop.Excel.Workbooks.Add%2A> de la collection <xref:Microsoft.Office.Interop.Excel.Workbooks> .

     [!code-csharp[Trin_VstcoreExcelAutomation#1](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#1)]
     [!code-vb[Trin_VstcoreExcelAutomation#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#1)]

    > [!NOTE]
    > Vous pouvez créer un classeur basé sur un modèle autre que le modèle par défaut : passez le modèle à utiliser en tant que paramètre à la méthode <xref:Microsoft.Office.Interop.Excel.Workbooks.Add%2A>.

## <a name="see-also"></a>Voir aussi
- [Étendre des documents Word et des classeurs Excel dans des compléments VSTO au moment de l’exécution](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Ajouter des contrôles aux documents Office au moment de l’exécution](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Utiliser des classeurs](../vsto/working-with-workbooks.md)
- [Comment : ouvrir des classeurs par programmation](../vsto/how-to-programmatically-open-workbooks.md)
- [Comment : enregistrer des classeurs par programmation](../vsto/how-to-programmatically-save-workbooks.md)
- [Comment : fermer des classeurs par programmation](../vsto/how-to-programmatically-close-workbooks.md)
- [Limitations de programmation des éléments hôtes et des contrôles hôtes](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Paramètres facultatifs dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)
- [Vue d’ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)
