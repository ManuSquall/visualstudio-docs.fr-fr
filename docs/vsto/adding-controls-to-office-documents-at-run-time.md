---
title: Ajouter des contrôles aux documents Office au moment de l’exécution
description: Découvrez comment ajouter des contrôles à un document Word Microsoft Office et Microsoft Office classeur Excel au moment de l’exécution.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office documents [Office development in Visual Studio, Windows Forms controls
- host controls [Office development in Visual Studio], adding
- Windows Forms controls [Office development in Visual Studio], adding
- Office documents [Office development in Visual Studio, host controls
- user controls [Office development in Visual Studio], adding at run time
- documents [Office development in Visual Studio], Windows Forms controls
- document-level customizations [Office development in Visual Studio], host controls
- documents [Office development in Visual Studio], host controls
- document-level customizations [Office development in Visual Studio], Windows Forms controls
- controls [Office development in Visual Studio], adding at run time
- helper methods [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e971556605a120b4ef475f434390c6dcf7b17938
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96844840"
---
# <a name="add-controls-to-office-documents-at-run-time"></a>Ajouter des contrôles aux documents Office au moment de l’exécution
  Vous pouvez ajouter des contrôles à un document Microsoft Office Word et à un classeur Microsoft Office Excel au moment de l’exécution. Vous pouvez également les supprimer au moment de l’exécution. Les contrôles que vous ajoutez aux documents ou que vous supprimez au moment de l’exécution sont appelés *contrôles dynamiques*.

 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

 Cette rubrique décrit les tâches suivantes :

- [Gérez les contrôles au moment de l’exécution à l’aide des collections de contrôles](#ControlsCollection).

- [Ajoutez des contrôles hôtes à des documents](#HostControls).

- [Ajoutez Windows Forms contrôles aux documents](#WindowsForms).

## <a name="manage-controls-at-run-time-by-using-control-collections"></a><a name="ControlsCollection"></a> Gérer les contrôles au moment de l’exécution à l’aide des collections de contrôles
 Pour ajouter, obtenir ou supprimer des contrôles au moment de l’exécution, utilisez les méthodes d’assistance des objets <xref:Microsoft.Office.Tools.Excel.ControlCollection> et <xref:Microsoft.Office.Tools.Word.ControlCollection> .

 La façon dont vous accédez à ces objets dépend du type de projet que vous développez :

- Dans un projet au niveau du document pour Excel, utilisez la propriété <xref:Microsoft.Office.Tools.Excel.Worksheet.Controls%2A> des classes `Sheet1`, `Sheet2`et `Sheet3` . Pour plus d’informations sur ces classes, consultez [élément hôte de feuille de calcul](../vsto/worksheet-host-item.md).

- Dans un projet au niveau du document pour Word, utilisez la propriété <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> de la classe `ThisDocument` . Pour plus d’informations sur cette classe, consultez [élément hôte de document](../vsto/document-host-item.md).

- Dans un projet de complément VSTO pour Excel ou Word, utilisez la `Controls` propriété d’un <xref:Microsoft.Office.Tools.Excel.Worksheet> ou <xref:Microsoft.Office.Tools.Word.Document> que vous générez au moment de l’exécution. Pour plus d’informations sur la génération de ces objets au moment de l’exécution, consultez [extension de documents Word et de classeurs Excel dans des compléments VSTO au moment](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)de l’exécution.

### <a name="add-controls"></a>Ajouter des contrôles
 Les types <xref:Microsoft.Office.Tools.Excel.ControlCollection> et <xref:Microsoft.Office.Tools.Word.ControlCollection> incluent des méthodes d’assistance que vous pouvez utiliser pour ajouter des contrôles hôtes et des contrôles Windows Forms communs aux documents et aux feuilles de calcul. Chaque nom de méthode est au format `Add`*control class* où *control class* correspond au nom de la classe du contrôle que vous souhaitez ajouter. Par exemple, pour ajouter un contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange> à votre document, utilisez la méthode <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddNamedRange%2A> .

 L’exemple de code suivant montre comment ajouter <xref:Microsoft.Office.Tools.Excel.NamedRange> à `Sheet1` dans un projet au niveau du document pour Excel.

 [!code-vb[Trin_ExcelWorkbookDynamicControls#3](../vsto/codesnippet/VisualBasic/trin_excelworkbookdynamiccontrols4/ThisWorkbook.vb#3)]
 [!code-csharp[Trin_ExcelWorkbookDynamicControls#3](../vsto/codesnippet/CSharp/trin_excelworkbookdynamiccontrols4/ThisWorkbook.cs#3)]

### <a name="access-and-delete-controls"></a>Contrôles d’accès et de suppression
 Vous pouvez utiliser la propriété `Controls` d’un <xref:Microsoft.Office.Tools.Excel.Worksheet> ou <xref:Microsoft.Office.Tools.Word.Document> pour effectuer une itération dans tous les contrôles dans votre document, y compris les contrôles que vous avez ajoutés au moment de la conception. Les contrôles que vous avez ajoutés au moment de la conception sont également appelés *contrôles statiques*.

 Vous pouvez supprimer des contrôles dynamiques en appelant la `Delete` méthode du contrôle ou en appelant la `Remove` méthode de chaque collection de contrôles. L’exemple de code suivant utilise la méthode <xref:Microsoft.Office.Tools.Excel.ControlCollection.Remove%2A> pour supprimer une <xref:Microsoft.Office.Tools.Excel.NamedRange> de `Sheet1` dans un projet au niveau du document pour Excel.

 [!code-vb[Trin_ExcelWorkbookDynamicControls#4](../vsto/codesnippet/VisualBasic/trin_excelworkbookdynamiccontrols4/ThisWorkbook.vb#4)]
 [!code-csharp[Trin_ExcelWorkbookDynamicControls#4](../vsto/codesnippet/CSharp/trin_excelworkbookdynamiccontrols4/ThisWorkbook.cs#4)]

 Vous ne pouvez pas supprimer les contrôles statiques au moment de l’exécution. Si vous essayez d’utiliser la méthode `Delete` ou `Remove` pour supprimer un contrôle statique, une exception <xref:Microsoft.Office.Tools.CannotRemoveControlException> sera levée.

> [!NOTE]
> Ne supprimez pas les contrôles par programmation dans le gestionnaire d’événements `Shutdown` du document. Les éléments d’interface utilisateur du document ne sont plus disponibles quand l’événement `Shutdown` est déclenché. Si vous souhaitez supprimer les contrôles avant la fermeture du document, ajoutez votre code au gestionnaire d’événements pour un autre événement, tel que <xref:Microsoft.Office.Tools.Word.Document.BeforeClose> ou <xref:Microsoft.Office.Tools.Word.Document.BeforeSave> pour Word, ou <xref:Microsoft.Office.Tools.Excel.Workbook.BeforeClose>ou <xref:Microsoft.Office.Tools.Excel.Workbook.BeforeSave> pour Excel.

## <a name="add-host-controls-to-documents"></a><a name="HostControls"></a> Ajouter des contrôles hôtes à des documents

Lorsque vous ajoutez par programmation des contrôles hôtes aux documents, vous devez fournir un nom qui identifie de façon unique le contrôle. Vous devez également spécifier où le contrôle doit être ajouté dans le document. Pour obtenir des instructions spécifiques, consultez les rubriques suivantes :

- [Comment : ajouter des contrôles ListObject à des feuilles de calcul](../vsto/how-to-add-listobject-controls-to-worksheets.md)

- [Comment : ajouter des contrôles NamedRange aux feuilles de calcul](../vsto/how-to-add-namedrange-controls-to-worksheets.md)

- [Comment : ajouter des contrôles Chart à des feuilles de calcul](../vsto/how-to-add-chart-controls-to-worksheets.md)

- [Comment : ajouter des contrôles de contenu à des documents Word](../vsto/how-to-add-content-controls-to-word-documents.md)

- [Comment : ajouter des contrôles Bookmark à des documents Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)

Pour plus d’informations sur les contrôles hôtes, consultez [vue d’ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md).

Lorsqu’un document est enregistré puis fermé, tous les contrôles hôtes créés dynamiquement sont déconnectés de leurs événements et perdent leur fonctionnalité de liaison de données. Vous pouvez ajouter du code à votre solution pour recréer les contrôles hôtes lorsque le document est de nouveau ouvert. Pour plus d’informations, consultez [persistance des contrôles dynamiques dans les documents Office](../vsto/persisting-dynamic-controls-in-office-documents.md).

> [!NOTE]
> Les méthodes d’assistance ne sont pas fournies pour les contrôles hôtes suivants, car ceux-ci ne peuvent pas être ajoutés par programmation aux documents : <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>, <xref:Microsoft.Office.Tools.Word.XMLNode>et <xref:Microsoft.Office.Tools.Word.XMLNodes>.

## <a name="add-windows-forms-controls-to-documents"></a><a name="WindowsForms"></a> Ajouter des contrôles de Windows Forms aux documents
 Lorsque vous ajoutez par programmation un contrôle Windows Forms à un document, vous devez fournir l’emplacement du contrôle et un nom qui identifie de façon unique le contrôle. Le [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] fournit des méthodes d’assistance pour chaque contrôle. Ces méthodes sont surchargées afin que vous puissiez transmettre une plage ou des coordonnées spécifiques pour l’emplacement du contrôle.

 Lorsqu’un document est enregistré puis fermé, tous les contrôles Windows Forms créés dynamiquement sont supprimés du document. Vous pouvez ajouter du code à votre solution pour recréer les contrôles lorsque le document est de nouveau ouvert. Si vous créez des contrôles de Windows Forms dynamique à l’aide d’un complément VSTO, les wrappers ActiveX des contrôles sont laissés dans le document. Pour plus d’informations, consultez [persistance des contrôles dynamiques dans les documents Office](../vsto/persisting-dynamic-controls-in-office-documents.md).

> [!NOTE]
> Les contrôles Windows Forms ne peuvent pas être ajoutés par programmation aux documents protégés. Si vous déprotégez par programmation un document Word ou une feuille de calcul Excel pour ajouter un contrôle, vous devez écrire le code supplémentaire pour supprimer le wrapper ActiveX du contrôle lorsque le document est fermé. Le wrapper ActiveX du contrôle n’est pas supprimé automatiquement des documents protégés.

### <a name="add-custom-controls"></a>Ajouter des contrôles personnalisés
 Si vous souhaitez ajouter un <xref:System.Windows.Forms.Control> qui n’est pas pris en charge par les méthodes d’assistance disponibles, tel qu’un contrôle utilisateur personnalisé, utilisez les méthodes suivantes :

- Pour Excel, utilisez l’une des méthodes <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddControl%2A> d’un objet <xref:Microsoft.Office.Tools.Excel.ControlCollection> .

- Pour Word, utilisez l’une des méthodes <xref:Microsoft.Office.Tools.Word.ControlCollection.AddControl%2A> d’un objet <xref:Microsoft.Office.Tools.Word.ControlCollection> .

  Pour ajouter le contrôle, transmettez le <xref:System.Windows.Forms.Control>, un emplacement pour le contrôle et un nom qui identifie de façon unique le contrôle à la méthode `AddControl`. La méthode `AddControl` renvoie un objet qui définit la façon dont le contrôle interagit avec la feuille de calcul ou le document. La `AddControl` méthode retourne un <xref:Microsoft.Office.Tools.Excel.ControlSite> (pour Excel) ou un <xref:Microsoft.Office.Tools.Word.ControlSite> objet (pour Word).

  L’exemple de code suivant montre comment utiliser la méthode <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddControl%2A> pour ajouter dynamiquement un contrôle utilisateur personnalisé à une feuille de calcul dans un projet Excel au niveau du document. Dans cet exemple, le contrôle utilisateur est nommé `UserControl1`, et la <xref:Microsoft.Office.Interop.Excel.Range> est nommée `range1`. Pour utiliser cet exemple, exécutez-le à partir d’une classe `Sheet`*n* dans le projet.

  [!code-vb[Trin_VstcoreProgrammingControlsExcel#2](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#2)]
  [!code-csharp[Trin_VstcoreProgrammingControlsExcel#2](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#2)]

### <a name="use-members-of-custom-controls"></a>Utiliser des membres de contrôles personnalisés
 Après avoir utilisé l’une des méthodes `AddControl` pour ajouter un contrôle à une feuille de calcul ou à un document, vous avez désormais deux objets de contrôle différents :

- Le <xref:System.Windows.Forms.Control> qui représente le contrôle personnalisé.

- Le `ControlSite`, `OLEObject` ou l’objet `OLEControl` qui représente le contrôle après qu’il a été ajouté à la feuille de calcul ou au document.

  De nombreuses propriétés et méthodes sont partagées entre ces contrôles. Il est important que vous accédiez à ces membres via le contrôle approprié :

- Pour accéder aux membres qui appartiennent uniquement au contrôle personnalisé, utilisez le <xref:System.Windows.Forms.Control>.

- Pour accéder aux membres partagés par les contrôles, utilisez le `ControlSite`, `OLEObject` ou l’objet `OLEControl`.

  Si vous accédez à un membre partagé à partir du <xref:System.Windows.Forms.Control>, un échec peut survenir sans que vous soyez averti ou notifié, ou des résultats non valides peuvent être générés. Utilisez toujours les méthodes ou propriétés du `ControlSite`, `OLEObject` ou de l’objet `OLEControl`, sauf si la méthode ou la propriété nécessaire n’est pas disponible ; ensuite seulement vous devez référencez le <xref:System.Windows.Forms.Control>.

  Par exemple, la classe <xref:Microsoft.Office.Tools.Excel.ControlSite> et la classe <xref:System.Windows.Forms.Control> ont une propriété `Top`. Pour obtenir ou définir la distance entre le haut du contrôle et le haut du document, utilisez la propriété <xref:Microsoft.Office.Tools.Excel.ControlSite.Top%2A> du <xref:Microsoft.Office.Tools.Excel.ControlSite>, et non la propriété <xref:System.Windows.Forms.Control.Top%2A> du <xref:System.Windows.Forms.Control>.

  [!code-vb[Trin_VstcoreProgrammingControlsExcel#3](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#3)]
  [!code-csharp[Trin_VstcoreProgrammingControlsExcel#3](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#3)]

## <a name="see-also"></a>Voir aussi
- [Contrôles sur les documents Office](../vsto/controls-on-office-documents.md)
- [Rendre des contrôles dynamiques persistants dans des documents Office](../vsto/persisting-dynamic-controls-in-office-documents.md)
- [Comment : ajouter des contrôles ListObject à des feuilles de calcul](../vsto/how-to-add-listobject-controls-to-worksheets.md)
- [Comment : ajouter des contrôles NamedRange aux feuilles de calcul](../vsto/how-to-add-namedrange-controls-to-worksheets.md)
- [Comment : ajouter des contrôles Chart à des feuilles de calcul](../vsto/how-to-add-chart-controls-to-worksheets.md)
- [Comment : ajouter des contrôles de contenu à des documents Word](../vsto/how-to-add-content-controls-to-word-documents.md)
- [Comment : ajouter des contrôles Bookmark à des documents Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)
- [Vue d’ensemble des contrôles de Windows Forms sur les documents Office](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Comment : ajouter des contrôles Windows Forms à des documents Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
