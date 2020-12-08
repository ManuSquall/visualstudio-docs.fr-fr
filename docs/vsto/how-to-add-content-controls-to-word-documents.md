---
title: 'Comment : ajouter des contrôles de contenu à des documents Word'
description: Pour plus d’informations sur les projets Word au niveau du document, vous pouvez ajouter des contrôles de contenu au document de votre projet au moment du design ou au moment de l’exécution.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- restricted permissions [Office development in Visual Studio]
- DropDownListContentControl, adding to documents
- BuildingBlockGalleryContentControl, adding to documents
- partial document protection [Office development in Visual Studio]
- RichTextContentControl, adding to documents
- Word [Office development in Visual Studio], partial document protection
- content controls [Office development in Visual Studio], protecting
- PictureContentControl, adding to documents
- GroupContentControl, adding to documents
- document protection [Office development in Visual Studio]
- PlainTextContentControl, adding to documents
- content controls [Office development in Visual Studio], adding
- ComboBoxContentControl, adding to documents
- DatePickerContentControl, adding to documents
- Word [Office development in Visual Studio], restricted permissions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: aa1528371a1466ec2886bf652ed33561b66b7028
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96845554"
---
# <a name="how-to-add-content-controls-to-word-documents"></a>Comment : ajouter des contrôles de contenu à des documents Word
  Dans les projets Word au niveau du document, vous pouvez ajouter des contrôles de contenu au document de votre projet au moment du design ou au moment de l'exécution. Dans les projets de complément Word VSTO, vous pouvez ajouter des contrôles de contenu à un document ouvert au moment de l'exécution.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 Cette rubrique décrit les tâches suivantes :

- [Ajouter des contrôles de contenu au moment du design](#designtime)

- [Ajouter des contrôles de contenu au moment de l’exécution dans un projet au niveau du document](#runtimedoclevel)

- [Ajouter des contrôles de contenu au moment de l’exécution dans un projet de complément VSTO](#runtimeaddin)

  Pour plus d’informations sur les contrôles de contenu, consultez [contrôles de contenu](../vsto/content-controls.md).

## <a name="add-content-controls-at-design-time"></a><a name="designtime"></a> Ajouter des contrôles de contenu au moment du design
 Il existe plusieurs façons d'ajouter des contrôles de contenu au document dans un projet au niveau du document au moment du design :

- Ajoutez un contrôle de contenu à partir de l'onglet **Contrôles Word** de la **Boîte à outils**.

- Ajoutez un contrôle de contenu à votre document de la même manière que vous ajoutez un contrôle de contenu natif dans Word.

- Faites glisser le contrôle de contenu vers votre document à partir de la fenêtre **Sources de données** . Cela est utile quand vous souhaitez lier le contrôle aux données, une fois le contrôle créé. Pour plus d’informations, consultez [Comment : remplir des documents avec des données d’objets](../vsto/how-to-populate-documents-with-data-from-objects.md) et [Comment : remplir des documents avec des données d’une base de données](../vsto/how-to-populate-documents-with-data-from-a-database.md).

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-add-a-content-control-to-a-document-by-using-the-toolbox"></a>Pour ajouter un contrôle de contenu à un document à l'aide de la boîte à outils

1. Dans le document hébergé dans le concepteur [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , placez le curseur à l'endroit où vous souhaitez ajouter le contrôle de contenu, ou sélectionnez le texte que le contrôle de contenu doit remplacer.

2. Ouvrez la **boîte à outils** et cliquez sur l'onglet **Contrôles Word** .

3. Ajoutez le contrôle en procédant de l'une des manières suivantes :

    - Double-cliquez sur un contrôle de contenu dans la **Boîte à outils**.

         or

    - Cliquez sur un contrôle de contenu dans la **boîte à outils** , puis appuyez sur la touche **entrée** .

         or

    - Faites glisser un contrôle de contenu de la **Boîte à outils** vers le document. Le contrôle de contenu est ajouté à la sélection actuelle dans le document, et non à l'emplacement correspondant au pointeur de souris.

> [!NOTE]
> Vous ne pouvez pas ajouter <xref:Microsoft.Office.Tools.Word.GroupContentControl> à l'aide de la **Boîte à outils**. Vous pouvez uniquement ajouter <xref:Microsoft.Office.Tools.Word.GroupContentControl> dans Word, ou au moment de l'exécution.

> [!NOTE]
> Visual Studio ne fournit aucun contrôle de contenu de case à cocher dans la boîte à outils. Pour ajouter un contrôle de contenu de case à cocher au document, vous devez créer un objet <xref:Microsoft.Office.Tools.Word.ContentControl> par programmation. Pour plus d’informations, consultez [contrôles de contenu](../vsto/content-controls.md).

#### <a name="to-add-a-content-control-to-a-document-in-word"></a>Pour ajouter un contrôle de contenu à un document dans Word

1. Dans le document hébergé dans le concepteur [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , placez le curseur à l'endroit où vous souhaitez ajouter le contrôle de contenu, ou sélectionnez le texte que le contrôle de contenu doit remplacer.

2. Dans le ruban, cliquez sur l'onglet **Développeur** .

    > [!NOTE]
    > Si l'onglet **Développeur** n'est pas visible, vous devez tout d'abord l'afficher. Pour plus d’informations, consultez [Comment : afficher l’onglet Développeur sur le ruban](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

3. Dans le groupe **Contrôles** , cliquez sur l'icône du contrôle de contenu à ajouter.

## <a name="add-content-controls-at-run-time-in-a-document-level-project"></a><a name="runtimedoclevel"></a> Ajouter des contrôles de contenu au moment de l’exécution dans un projet au niveau du document
 Vous pouvez ajouter des contrôles de contenu par programmation à votre document au moment de l'exécution en utilisant les méthodes de la propriété <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> de la classe `ThisDocument` dans votre projet. Chaque méthode possède trois surcharges qui vous permettent d'ajouter un contrôle de contenu comme suit :

- ajout d'un contrôle à la sélection actuelle ;

- ajout d'un contrôle à une plage spécifique ;

- ajout d'un contrôle basé sur un contrôle de contenu natif dans le document.

  Les contrôles de contenu créés de façon dynamique ne sont pas conservés dans le document quand ce dernier est fermé. Toutefois, un contrôle de contenu natif demeure dans le document. Vous pouvez recréer un contrôle de contenu basé sur un contrôle de contenu natif à la prochaine ouverture du document. Pour plus d’informations, consultez [Ajouter des contrôles aux documents Office au moment de l’exécution](../vsto/adding-controls-to-office-documents-at-run-time.md).

> [!NOTE]
> Pour ajouter un contrôle de contenu de case à cocher à un document dans un projet Word 2010, vous devez créer un objet <xref:Microsoft.Office.Tools.Word.ContentControl> . Pour plus d’informations, consultez [contrôles de contenu](../vsto/content-controls.md).

### <a name="to-add-a-content-control-at-the-current-selection"></a>Pour ajouter un contrôle de contenu à la sélection actuelle

1. Utilisez une <xref:Microsoft.Office.Tools.Word.ControlCollection> méthode qui a le nom `Add` \<*control class*> (où *classe du contrôle* est le nom de la classe du contrôle de contenu que vous souhaitez ajouter, tel que <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> ) et qui a un paramètre unique pour le nom du nouveau contrôle.

     L'exemple de code suivant utilise la méthode <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> pour ajouter un nouveau <xref:Microsoft.Office.Tools.Word.RichTextContentControl> au début du document. Pour exécuter ce code, ajoutez-le à la classe `ThisDocument` dans votre projet, puis appelez la méthode `AddRichTextControlAtSelection` à partir du gestionnaire d'événements `ThisDocument_Startup` .

     [!code-csharp[Trin_ContentControlReference#700](../vsto/codesnippet/CSharp/trin_wordcontentcontrolreference/RichText.cs#700)]
     [!code-vb[Trin_ContentControlReference#700](../vsto/codesnippet/VisualBasic/trin_contentcontrolreference/RichText.vb#700)]

### <a name="to-add-a-content-control-at-a-specified-range"></a>Pour ajouter un contrôle de contenu à une plage spécifique

1. Utilisez une <xref:Microsoft.Office.Tools.Word.ControlCollection> méthode qui a le nom `Add` \<*control class*> (où *classe du contrôle* est le nom de la classe de contrôle de contenu que vous souhaitez ajouter, par exemple <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> ), et qui a un <xref:Microsoft.Office.Interop.Word.Range> paramètre.

     L'exemple de code suivant utilise la méthode <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> pour ajouter un nouveau <xref:Microsoft.Office.Tools.Word.RichTextContentControl> au début du document. Pour exécuter ce code, ajoutez-le à la classe `ThisDocument` dans votre projet, puis appelez la méthode `AddRichTextControlAtRange` à partir du gestionnaire d'événements `ThisDocument_Startup` .

     [!code-csharp[Trin_ContentControlReference#701](../vsto/codesnippet/CSharp/trin_wordcontentcontrolreference/RichText.cs#701)]
     [!code-vb[Trin_ContentControlReference#701](../vsto/codesnippet/VisualBasic/trin_contentcontrolreference/RichText.vb#701)]

### <a name="to-add-a-content-control-that-is-based-on-a-native-content-control"></a>Pour ajouter un contrôle de contenu basé sur un contrôle de contenu natif

1. Utilisez une <xref:Microsoft.Office.Tools.Word.ControlCollection> méthode qui a le nom `Add` \<*control class*> (où *classe du contrôle* est le nom de la classe de contrôle de contenu que vous souhaitez ajouter, par exemple <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> ), et qui a un `Microsoft.Office.Interop.Word.ContentControl` paramètre.

     L'exemple de code suivant utilise la méthode <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> pour créer un <xref:Microsoft.Office.Tools.Word.RichTextContentControl> pour chaque contrôle de texte enrichi natif présent dans le document. Pour exécuter ce code, ajoutez-le à la classe `ThisDocument` dans votre projet, puis appelez la méthode `CreateRichTextControlsFromNativeControls` à partir du gestionnaire d'événements `ThisDocument_Startup` .

     [!code-csharp[Trin_ContentControlReference#702](../vsto/codesnippet/CSharp/trin_wordcontentcontrolreference/RichText.cs#702)]
     [!code-vb[Trin_ContentControlReference#702](../vsto/codesnippet/VisualBasic/trin_contentcontrolreference/RichText.vb#702)]

## <a name="add-content-controls-at-run-time-in-a-vsto-add-in-project"></a><a name="runtimeaddin"></a> Ajouter des contrôles de contenu au moment de l’exécution dans un projet de complément VSTO
 Vous pouvez ajouter des contrôles de contenu par programmation à un document ouvert au moment de l'exécution en utilisant un complément VSTO. Pour ce faire, vous devez générer un élément hôte <xref:Microsoft.Office.Tools.Word.Document> basé sur un document ouvert, puis utiliser les méthodes de la propriété <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> de cet élément hôte. Chaque méthode possède trois surcharges qui vous permettent d'ajouter un contrôle de contenu comme suit :

- ajout d'un contrôle à la sélection actuelle ;

- ajout d'un contrôle à une plage spécifique ;

- ajout d'un contrôle basé sur un contrôle de contenu natif dans le document.

  Les contrôles de contenu créés de façon dynamique ne sont pas conservés dans le document quand ce dernier est fermé. Toutefois, un contrôle de contenu natif demeure dans le document. Vous pouvez recréer un contrôle de contenu basé sur un contrôle de contenu natif à la prochaine ouverture du document. Pour plus d’informations, consultez [persistance des contrôles dynamiques dans les documents Office](../vsto/persisting-dynamic-controls-in-office-documents.md).

  Pour plus d’informations sur la génération d’éléments hôtes dans des projets de complément VSTO, consultez [extension de documents Word et de classeurs Excel dans des compléments VSTO au moment](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)de l’exécution.

> [!NOTE]
> Pour ajouter un contrôle de contenu de case à cocher à un document, vous devez créer un objet <xref:Microsoft.Office.Tools.Word.ContentControl> . Pour plus d’informations, consultez [contrôles de contenu](../vsto/content-controls.md).

### <a name="to-add-a-content-control-at-the-current-selection"></a>Pour ajouter un contrôle de contenu à la sélection actuelle

1. Utilisez une <xref:Microsoft.Office.Tools.Word.ControlCollection> méthode qui a le nom `Add` \<*control class*> (où *classe du contrôle* est le nom de la classe du contrôle de contenu que vous souhaitez ajouter, tel que <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> ) et qui a un paramètre unique pour le nom du nouveau contrôle.

     L'exemple de code suivant utilise la méthode <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> pour ajouter un nouveau <xref:Microsoft.Office.Tools.Word.RichTextContentControl> au début du document actif. Pour exécuter ce code, ajoutez-le à la classe `ThisAddIn` dans votre projet, puis appelez la méthode `AddRichTextControlAtSelection` à partir du gestionnaire d'événements `ThisAddIn_Startup` .

     [!code-vb[Trin_WordAddInDynamicControls#1](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#1)]
     [!code-csharp[Trin_WordAddInDynamicControls#1](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#1)]

### <a name="to-add-a-content-control-at-a-specified-range"></a>Pour ajouter un contrôle de contenu à une plage spécifique

1. Utilisez une <xref:Microsoft.Office.Tools.Word.ControlCollection> méthode qui a le nom `Add` \<*control class*> (où *classe du contrôle* est le nom de la classe de contrôle de contenu que vous souhaitez ajouter, par exemple <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> ), et qui a un <xref:Microsoft.Office.Interop.Word.Range> paramètre.

     L'exemple de code suivant utilise la méthode <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> pour ajouter un nouveau <xref:Microsoft.Office.Tools.Word.RichTextContentControl> au début du document actif. Pour exécuter ce code, ajoutez-le à la classe `ThisAddIn` dans votre projet, puis appelez la méthode `AddRichTextControlAtRange` à partir du gestionnaire d'événements `ThisAddIn_Startup` .

     [!code-vb[Trin_WordAddInDynamicControls#2](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#2)]
     [!code-csharp[Trin_WordAddInDynamicControls#2](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#2)]

#### <a name="to-add-a-content-control-that-is-based-on-a-native-content-control"></a>Pour ajouter un contrôle de contenu basé sur un contrôle de contenu natif

1. Utilisez une <xref:Microsoft.Office.Tools.Word.ControlCollection> méthode qui a le nom `Add` \<*control class*> (où *classe du contrôle* est le nom de la classe de contrôle de contenu que vous souhaitez ajouter, par exemple <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> ), et qui a un `Microsoft.Office.Interop.Word.ContentControl` paramètre.

     L'exemple de code suivant utilise la méthode <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> pour créer un <xref:Microsoft.Office.Tools.Word.RichTextContentControl> pour chaque contrôle de texte enrichi natif présent dans un document, une fois ce dernier ouvert. Pour exécuter ce code, ajoutez-le à la classe `ThisAddIn` dans votre projet.

     [!code-vb[Trin_WordAddInDynamicControls#3](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#3)]
     [!code-csharp[Trin_WordAddInDynamicControls#3](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#3)]

     En C#, vous devez également attacher le gestionnaire d'événements `Application_DocumentOpen` à l'événement <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen> .

     [!code-csharp[Trin_WordAddInDynamicControls#6](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#6)]

## <a name="see-also"></a>Voir aussi
- [Automatiser Word à l’aide d’objets étendus](../vsto/automating-word-by-using-extended-objects.md)
- [Vue d’ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)
- [Ajouter des contrôles aux documents Office au moment de l’exécution](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Limitations de programmation des éléments hôtes et des contrôles hôtes](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Programmer les compléments VSTO](../vsto/programming-vsto-add-ins.md)
- [Personnaliser les personnalisations au niveau du document](../vsto/programming-document-level-customizations.md)
