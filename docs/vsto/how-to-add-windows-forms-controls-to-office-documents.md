---
title: 'Comment : ajouter des contrôles Windows Forms à des documents Office'
description: Découvrez comment vous pouvez ajouter des contrôles Windows Forms pour Microsoft Office des documents Word Excel et Microsoft Office au moment du design dans des projets au niveau du document.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office documents [Office development in Visual Studio, Windows Forms controls
- Windows Forms controls [Office development in Visual Studio], adding
- controls [Office development in Visual Studio], Windows Forms controls
- documents [Office development in Visual Studio], Windows Forms controls
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a8f073a72db1a18574dff6ab060b1ea069475fbb
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96846777"
---
# <a name="how-to-add-windows-forms-controls-to-office-documents"></a>Comment : ajouter des contrôles Windows Forms à des documents Office
  Vous pouvez ajouter des contrôles Windows Forms à des documents Microsoft Office Excel et Microsoft Office Word au moment du design dans les projets au niveau du document. Au moment de l’exécution, vous pouvez ajouter des contrôles dans les personnalisations au niveau du document et dans les compléments VSTO. Par exemple, vous pouvez ajouter un <xref:Microsoft.Office.Tools.Excel.Controls.ComboBox> contrôle à votre feuille de calcul afin que les utilisateurs puissent les sélectionner dans une liste d’options.

 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

 Cette rubrique décrit les tâches suivantes :

- [Ajouter des contrôles au moment du design](#designtime)

- [Ajouter des contrôles au moment de l’exécution dans des projets au niveau du document](#runtimedoclevel)

- [Ajouter des contrôles au moment de l’exécution dans des compléments VSTO](#runtimeaddin)

## <a name="add-controls-at-design-time"></a><a name="designtime"></a> Ajouter des contrôles au moment du design
 Il existe plusieurs façons d'ajouter des contrôles Windows Forms au document dans un projet au niveau du document au moment du design.

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-drag-a-windows-forms-control-to-the-document"></a>Pour faire glisser un contrôle Windows Forms vers le document

1. Créez ou ouvrez un projet de classeur Excel ou un projet de document Word dans Visual Studio pour que le document soit visible dans le concepteur. Pour plus d’informations sur la création de projets, consultez [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

2. Sous l’onglet **contrôles communs** de la **boîte à outils**, cliquez sur le contrôle que vous souhaitez ajouter, puis faites-le glisser vers le document.

    > [!NOTE]
    > Quand vous sélectionnez un contrôle dans Excel, vous voyez **=EMBED("WinForms.Control.Host","")** dans la **Barre de formule**. Ce texte est nécessaire et ne doit pas être supprimé.

### <a name="to-draw-a-windows-forms-control-on-the-document"></a>Pour dessiner un contrôle Windows Forms sur le document

1. Créez ou ouvrez un projet de classeur Excel ou un projet de document Word dans Visual Studio pour que le document soit visible dans le concepteur. Pour plus d’informations sur la création de projets, consultez [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

2. Sous l’onglet **contrôles communs** de la **boîte à outils**, cliquez sur le contrôle que vous souhaitez ajouter.

3. Dans le document, cliquez à l'endroit où l'angle supérieur gauche du contrôle doit se trouver, puis faites glisser le curseur vers l'endroit où l'angle inférieur droit du contrôle doit se trouver.

     Le contrôle est ajouté au document avec l'emplacement et la taille spécifiés.

    > [!NOTE]
    > Quand vous sélectionnez un contrôle dans Excel, vous voyez **= embed ("WinForms. Control. Host", "")**  dans la **barre de formule**. Ce texte est nécessaire et ne doit pas être supprimé.

### <a name="to-add-a-windows-forms-control-to-the-document-by-single-clicking-the-control"></a>Pour ajouter un contrôle Windows Forms au document en cliquant une fois sur le contrôle

1. Créez ou ouvrez un projet de classeur Excel ou un projet de document Word dans Visual Studio pour que le document soit visible dans le concepteur. Pour plus d’informations sur la création de projets, consultez [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

2. Sous l’onglet **contrôles communs** de la **boîte à outils**, cliquez sur le contrôle que vous souhaitez ajouter.

3. Dans le document, cliquez à l'emplacement où vous souhaitez ajouter le contrôle.

     Le contrôle est ajouté au document avec la taille par défaut.

    > [!NOTE]
    > Quand vous sélectionnez un contrôle dans Excel, vous voyez **=EMBED("WinForms.Control.Host","")** dans la **Barre de formule**. Ce texte est nécessaire et ne doit pas être supprimé.

### <a name="to-add-a-windows-forms-control-to-the-document-by-double-clicking-the-control"></a>Pour ajouter un contrôle Windows Forms au document en double-cliquant sur le contrôle

1. Créez ou ouvrez un projet de classeur Excel ou un projet de document Word dans Visual Studio pour que le document soit visible dans le concepteur. Pour plus d’informations sur la création de projets, consultez [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

2. Sous l’onglet **contrôles communs** de la **boîte à outils**, double-cliquez sur le contrôle que vous souhaitez ajouter.

     Le contrôle est ajouté au document, au centre de ce dernier ou du volet actif.

    > [!NOTE]
    > Quand vous sélectionnez un contrôle dans Excel, vous voyez **=EMBED("WinForms.Control.Host","")** dans la **Barre de formule**. Ce texte est nécessaire et ne doit pas être supprimé.

### <a name="to-add-a-windows-forms-control-to-the-document-by-pressing-the-enter-key"></a>Pour ajouter un contrôle Windows Forms au document en appuyant sur la touche entrée

1. Créez ou ouvrez un projet de classeur Excel ou un projet de document Word dans Visual Studio pour que le document soit visible dans le concepteur. Pour plus d’informations sur la création de projets, consultez [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

2. Sous l’onglet **contrôles communs** de la **boîte à outils**, cliquez sur le contrôle que vous souhaitez ajouter, puis appuyez sur la touche **entrée** .

     Le contrôle est ajouté au document, au centre de ce dernier ou du volet actif.

    > [!NOTE]
    > Quand vous sélectionnez un contrôle dans Excel, vous voyez **=EMBED("WinForms.Control.Host","")** dans la **Barre de formule**. Ce texte est nécessaire et ne doit pas être supprimé.

## <a name="add-controls-at-run-time-in-document-level-projects"></a><a name="runtimedoclevel"></a> Ajouter des contrôles au moment de l’exécution dans des projets au niveau du document
 Vous pouvez ajouter par programmation des contrôles Windows Forms à un document au moment de l'exécution. Dans Word, utilisez les méthodes de la propriété <xref:Microsoft.Office.Tools.Word.DocumentBase.Controls%2A> de la classe `ThisDocument`. Dans Excel, utilisez les méthodes de la <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Controls%2A> propriété d’une `Sheet` classe *n* . Chaque méthode a plusieurs surcharges qui vous permettent de spécifier l'emplacement du contrôle de différentes façons.

 Quand vous ajoutez un contrôle Windows Forms à un document au moment de l'exécution, le contrôle n'est pas conservé dans le document après la fermeture de ce dernier. Vous pouvez recréer le contrôle à la prochaine ouverture du document. Pour plus d’informations, consultez [Ajouter des contrôles aux documents Office au moment de l’exécution](../vsto/adding-controls-to-office-documents-at-run-time.md).

### <a name="to-add-a-windows-forms-control-at-run-time"></a>Pour ajouter un contrôle Windows Forms au moment de l'exécution

1. Utilisez une méthode portant le nom Add \<*control class*> (où *Control Class* est le nom de classe du contrôle Windows Forms que vous souhaitez ajouter, tel que <xref:Microsoft.Office.Tools.Word.ControlExtensions.AddButton%2A> ).

     L’exemple de code suivant montre comment ajouter un <xref:Microsoft.Office.Tools.Excel.Controls.Button> à la cellule **C5** de `Sheet1` dans un projet au niveau du document pour Excel.

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#4](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#4)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#4](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#4)]

## <a name="add-controls-at-run-time-in-vsto-add-ins"></a><a name="runtimeaddin"></a> Ajouter des contrôles au moment de l’exécution dans des compléments VSTO
 Vous pouvez ajouter des contrôles Windows Forms par programmation à un document ouvert au moment de l'exécution. Tout d'abord, générez un élément hôte basé sur un document ouvert ou une feuille de calcul ouverte. Dans Word, utilisez les méthodes de la propriété <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> du nouvel élément hôte. Dans Excel, utilisez les méthodes de la propriété <xref:Microsoft.Office.Tools.Excel.Worksheet.Controls%2A> du nouvel élément hôte. Chaque méthode a plusieurs surcharges qui vous permettent de spécifier l'emplacement du contrôle de différentes façons.

 Quand vous ajoutez un contrôle Windows Forms à un document au moment de l'exécution, le contrôle n'est pas conservé dans le document après la fermeture de ce dernier. Vous pouvez recréer le contrôle à la prochaine ouverture du document. Pour plus d’informations, consultez [Ajouter des contrôles aux documents Office au moment de l’exécution](../vsto/adding-controls-to-office-documents-at-run-time.md).

 Pour plus d’informations sur la génération d’éléments hôtes dans des projets de complément VSTO, consultez [extension de documents Word et de classeurs Excel dans des compléments VSTO au moment](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)de l’exécution.

### <a name="to-add-a-windows-forms-control-at-run-time"></a>Pour ajouter un contrôle Windows Forms au moment de l'exécution

1. Utilisez une méthode portant le nom Add \<*control class*> (où *Control Class* est le nom de classe du contrôle Windows Forms que vous souhaitez ajouter, tel que <xref:Microsoft.Office.Tools.Word.ControlExtensions.AddButton%2A> ).

    > [!NOTE]
    > Dans les projets de complément VSTO qui ciblent le [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou version ultérieure, vous devez ajouter une référence au *Microsoft.Office.Tools.Excel.v4.0.Utilities.dll* ou *Microsoft.Office.Tools.Word.v4.0.Utilities.dll* assembly avant de pouvoir accéder aux \<*control class*> méthodes Add.

     L’exemple de code suivant montre comment ajouter <xref:Microsoft.Office.Tools.Word.Controls.Button> au premier paragraphe du document actif en utilisant un complément Word VSTO.

     [!code-vb[Trin_WordAddInDynamicControls#7](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#7)]
     [!code-csharp[Trin_WordAddInDynamicControls#7](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#7)]

## <a name="see-also"></a>Voir aussi
- [Vue d’ensemble des contrôles de Windows Forms sur les documents Office](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Ajouter des contrôles aux documents Office au moment de l’exécution](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Comment : redimensionner des contrôles dans des cellules de feuille de calcul](../vsto/how-to-resize-controls-within-worksheet-cells.md)
- [Vue d’ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)
- [Paramètres facultatifs dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)
