---
title: 'Comment : ajouter des contrôles NamedRange aux feuilles de calcul'
description: Découvrez comment ajouter des contrôles NamedRange à une feuille de calcul Microsoft Office Excel au moment du design et au moment de l’exécution dans des projets au niveau du document.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, adding to worksheets
- NamedRange control, adding to worksheets
- controls [Office development in Visual Studio], adding to worksheets
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: b7bf2f3ef91a6f572c64f94cb4b1a9a2f493e864
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827706"
---
# <a name="how-to-add-namedrange-controls-to-worksheets"></a>Comment : ajouter des contrôles NamedRange aux feuilles de calcul
  Vous pouvez ajouter des contrôles <xref:Microsoft.Office.Tools.Excel.NamedRange> à une feuille de calcul Microsoft Office Excel au moment du design et au moment de l’exécution dans des projets au niveau du document.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Vous pouvez aussi ajouter des contrôles <xref:Microsoft.Office.Tools.Excel.NamedRange> au moment de l’exécution dans des projets de complément VSTO.

 Cette rubrique décrit les tâches suivantes :

- [Ajouter des contrôles NamedRange au moment du design](#designtime)

- [Ajouter des contrôles NamedRange au moment de l’exécution dans un projet au niveau du document](#runtimedoclevel)

- [Ajouter des contrôles NamedRange au moment de l’exécution dans un projet de complément VSTO](#runtimeaddin)

  Pour plus d’informations sur les <xref:Microsoft.Office.Tools.Excel.NamedRange> contrôles, consultez [NamedRange, contrôle](../vsto/namedrange-control.md).

## <a name="add-namedrange-controls-at-design-time"></a><a name="designtime"></a> Ajouter des contrôles NamedRange au moment du design
 Il existe plusieurs façons d’ajouter des contrôles <xref:Microsoft.Office.Tools.Excel.NamedRange> à une feuille de calcul dans un projet au niveau du document au moment de la conception : dans Excel, à partir de la **Boîte à outils** Visual Studio, et à partir de la fenêtre **Sources de données** .

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-add-a-namedrange-control-to-a-worksheet-using-the-name-box-in-excel"></a>Pour ajouter un contrôle NamedRange à une feuille de calcul via la Zone Nom d’Excel

1. Sélectionnez la ou les cellules que vous souhaitez inclure dans l'étendue nommée.

2. Dans la **zone Nom**, tapez un nom pour la plage et appuyez sur **entrée**.

     La **Zone Nom** se trouve à côté de la barre de formule, juste au-dessus de la colonne **A** de la feuille de calcul.

### <a name="to-add-a-namedrange-control-to-a-worksheet-using-the-toolbox"></a>Pour ajouter un contrôle NamedRange à une feuille de calcul via la Boîte à outils

1. Ouvrez la **Boîte à outils** , puis cliquez sur l’onglet **Contrôles Excel** .

2. Cliquez sur <xref:Microsoft.Office.Tools.Excel.NamedRange> et faites-le glisser vers une feuille de calcul.

     La boîte de dialogue **Ajouter une plage nommée** s’affiche.

3. Sélectionnez la ou les cellules que vous souhaitez inclure dans l'étendue nommée.

4. Cliquez sur **OK**.

     Si vous ne voulez pas du nom attribué par défaut au contrôle, vous pouvez le modifier dans la fenêtre **Propriétés** .

### <a name="to-add-a-namedrange-control-to-a-worksheet-using-the-data-sources-window"></a>Pour ajouter un contrôle NamedRange à une feuille de calcul via la fenêtre Sources de données

1. Ouvrez la fenêtre **Sources de données** et créez une source de données pour votre projet. Pour plus d’informations, consultez [ajouter de nouvelles connexions](../data-tools/add-new-connections.md).

2. Faites glisser un seul champ de la fenêtre **Sources de données** vers votre feuille de calcul.

     Un contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange> lié aux données est ajouté à la feuille de calcul. Pour plus d’informations, consultez [liaison de données et Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms).

## <a name="add-namedrange-controls-at-run-time-in-a-document-level-project"></a><a name="runtimedoclevel"></a> Ajouter des contrôles NamedRange au moment de l’exécution dans un projet au niveau du document
 Vous pouvez ajouter un <xref:Microsoft.Office.Tools.Excel.NamedRange> contrôle par programmation à votre feuille de calcul au moment de l’exécution. Cela vous permet de créer les contrôles hôtes en réponse à des événements. Les plages nommées créées dynamiquement ne sont pas conservées dans la feuille de calcul en tant que contrôles hôtes au moment où la feuille de calcul est fermée. Pour plus d’informations, consultez [Ajouter des contrôles aux documents Office au moment de l’exécution](../vsto/adding-controls-to-office-documents-at-run-time.md).

### <a name="to-add-a-namedrange-control-to-a-worksheet-programmatically"></a>Pour ajouter un contrôle NamedRange à une feuille de calcul par programmation

1. Dans le gestionnaire d’événements <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> de `Sheet1`, insérez le code suivant pour ajouter le contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange> à la cellule **A1** et attribuez à sa propriété <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> la valeur `Hello world!`

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs" id="Snippet3":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb" id="Snippet3":::

## <a name="add-namedrange-controls-at-run-time-in-a-vsto-add-in-project"></a><a name="runtimeaddin"></a> Ajouter des contrôles NamedRange au moment de l’exécution dans un projet de complément VSTO
 Vous pouvez ajouter par programmation un contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange> à une feuille de calcul ouverte dans un projet de complément VSTO. Les plages nommées créées dynamiquement ne sont pas conservées dans la feuille de calcul en tant que contrôles hôtes au moment où la feuille de calcul est fermée. Pour plus d’informations, consultez [extension de documents Word et de classeurs Excel dans des compléments VSTO au moment](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)de l’exécution.

### <a name="to-add-a-namedrange-control-to-a-worksheet-programmatically"></a>Pour ajouter un contrôle NamedRange à une feuille de calcul par programmation

1. Le code suivant génère un élément hôte de feuille de calcul basé sur la feuille de calcul ouverte, puis ajoute un contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange> à la cellule **A1** et attribue à sa propriété <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> la valeur `Hello world`.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs" id="Snippet7":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb" id="Snippet7":::

## <a name="see-also"></a>Voir aussi
- [Étendre des documents Word et des classeurs Excel dans des compléments VSTO au moment de l’exécution](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Contrôles sur les documents Office](../vsto/controls-on-office-documents.md)
- [NamedRange, contrôle](../vsto/namedrange-control.md)
- [Automatiser Excel à l’aide d’objets étendus](../vsto/automating-excel-by-using-extended-objects.md)
- [Vue d’ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)
- [Comment : redimensionner des contrôles NamedRange](../vsto/how-to-resize-namedrange-controls.md)
- [Limitations de programmation des éléments hôtes et des contrôles hôtes](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
