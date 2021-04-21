---
title: 'Comment : ajouter des contrôles ListObject à des feuilles de calcul'
description: Découvrez comment vous pouvez ajouter des contrôles ListObject à une feuille de calcul Microsoft Office Excel au moment du design et au moment de l’exécution dans des projets au niveau du document.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ListObject control, adding to worksheets
- controls [Office development in Visual Studio], adding to worksheets
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 077ff2e92455df283dfcaeddd7171e1f86698e6b
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827888"
---
# <a name="how-to-add-listobject-controls-to-worksheets"></a>Comment : ajouter des contrôles ListObject à des feuilles de calcul
  Vous pouvez ajouter des contrôles <xref:Microsoft.Office.Tools.Excel.ListObject> à une feuille de calcul Microsoft Office Excel au moment du design et au moment de l’exécution dans des projets au niveau du document.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Vous pouvez aussi ajouter des contrôles <xref:Microsoft.Office.Tools.Excel.ListObject> au moment de l’exécution dans des projets de complément VSTO.

 Cette rubrique décrit les tâches suivantes :

- [Ajouter des contrôles ListObject au moment du design](#designtime)

- [Ajouter des contrôles ListObject au moment de l’exécution dans un projet au niveau du document](#runtimedoclevel)

- [Ajouter des contrôles ListObject au moment de l’exécution dans un projet de complément VSTO](#runtimeaddin)

  Pour plus d’informations sur les <xref:Microsoft.Office.Tools.Excel.ListObject> contrôles, consultez [ListObject, contrôle](../vsto/listobject-control.md).

## <a name="add-listobject-controls-at-design-time"></a><a name="designtime"></a> Ajouter des contrôles ListObject au moment du design
 Il existe plusieurs façons d’ajouter des <xref:Microsoft.Office.Tools.Excel.ListObject> contrôles à une feuille de calcul dans un projet au niveau du document au moment du design : à partir d’Excel, à partir de la **boîte à outils** de Visual Studio et à partir de la fenêtre **sources de données** .

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-use-the-ribbon-in-excel"></a>Pour utiliser le ruban dans Excel

1. Sous l’onglet **Insérer** du groupe **Tableaux** , cliquez sur **Tableau**.

2. Sélectionnez la ou les cellules que vous souhaitez inclure dans la liste, puis cliquez sur **OK**.

#### <a name="to-use-the-toolbox"></a>Pour utiliser la Boîte à outils

1. À partir de l’onglet **Contrôles Excel** de la **boîte à outils**, faites glisser un <xref:Microsoft.Office.Tools.Excel.ListObject> sur la feuille de calcul.

     La boîte de dialogue **Ajouter un contrôle ListObject** s’affiche.

2. Sélectionnez la ou les cellules que vous souhaitez inclure dans la liste, puis cliquez sur **OK**.

     Si vous ne souhaitez pas conserver le nom par défaut, vous pouvez le modifier dans la fenêtre **Propriétés** .

#### <a name="to-use-the-data-sources-window"></a>Pour utiliser la fenêtre Sources de données

1. Ouvrez la fenêtre **Sources de données** et créez une source de données pour votre projet. Pour plus d’informations, consultez [ajouter de nouvelles connexions](../data-tools/add-new-connections.md).

2. Faites glisser un tableau de la fenêtre **Sources de données** vers votre feuille de calcul.

     Un contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> lié aux données est ajouté à la feuille de calcul. Pour plus d’informations, consultez [liaison de données et Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms).

## <a name="add-listobject-controls-at-run-time-in-a-document-level-project"></a><a name="runtimedoclevel"></a> Ajouter des contrôles ListObject au moment de l’exécution dans un projet au niveau du document
 Vous pouvez ajouter dynamiquement le contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> au moment de l'exécution. Cela vous permet de créer les contrôles hôtes en réponse à des événements. Les objets de liste créés de manière dynamique ne sont pas persistants dans la feuille de calcul en tant que contrôles hôtes, une fois la feuille de calcul fermée. Pour plus d’informations, consultez [Ajouter des contrôles aux documents Office au moment de l’exécution](../vsto/adding-controls-to-office-documents-at-run-time.md).

#### <a name="to-add-a-listobject-control-to-a-worksheet-programmatically"></a>Pour ajouter par programmation un contrôle ListObject à une feuille de calcul

1. Dans le gestionnaire d’événements <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> de `Sheet1`, insérez le code suivant pour ajouter un contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> aux cellules **A1** à **A4**.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb" id="Snippet2":::

## <a name="add-listobject-controls-at-run-time-in-a-vsto-add-in-project"></a><a name="runtimeaddin"></a> Ajouter des contrôles ListObject au moment de l’exécution dans un projet de complément VSTO
 Vous pouvez ajouter par programmation un contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> à une feuille de calcul ouverte dans un projet de complément VSTO. Les objets de liste créés de manière dynamique ne sont pas persistants dans la feuille de calcul en tant que contrôles hôtes, une fois la feuille de calcul enregistrée puis fermée. Pour plus d’informations, consultez [extension de documents Word et de classeurs Excel dans des compléments VSTO au moment](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)de l’exécution.

#### <a name="to-add-a-listobject-control-to-a-worksheet-programmatically"></a>Pour ajouter par programmation un contrôle ListObject à une feuille de calcul

1. Le code suivant génère un élément hôte de feuille de calcul basé sur la feuille de calcul ouverte, puis ajoute un contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> aux cellules **A1** à **A4**.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs" id="Snippet8":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb" id="Snippet8":::

## <a name="see-also"></a>Voir aussi
- [Étendre des documents Word et des classeurs Excel dans des compléments VSTO au moment de l’exécution](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Contrôles sur les documents Office](../vsto/controls-on-office-documents.md)
- [ListObject (contrôle)](../vsto/listobject-control.md)
- [Automatiser Excel à l’aide d’objets étendus](../vsto/automating-excel-by-using-extended-objects.md)
- [Vue d’ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)
- [Comment : redimensionner des contrôles ListObject](../vsto/how-to-resize-listobject-controls.md)
- [Lier des données à des contrôles dans les solutions Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Limitations de programmation des éléments hôtes et des contrôles hôtes](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
