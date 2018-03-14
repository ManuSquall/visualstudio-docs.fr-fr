---
title: "Comment : ajouter des contrôles de contenu à des Documents Word | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
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
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: b1dd59fc777c012f92baaf96302f7cf031ad151c
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-add-content-controls-to-word-documents"></a>Comment : ajouter des contrôles de contenu à des documents Word
  Dans les projets Word au niveau du document, vous pouvez ajouter des contrôles de contenu au document de votre projet au moment du design ou au moment de l'exécution. Dans les projets de complément Word VSTO, vous pouvez ajouter des contrôles de contenu à un document ouvert au moment de l'exécution.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 Cette rubrique décrit les tâches suivantes :  
  
-   [Ajout de contrôles de contenu au moment du design](#designtime)  
  
-   [Ajout de contrôles de contenu au moment de l'exécution dans un projet au niveau du document](#runtimedoclevel)  
  
-   [Ajout de contrôles de contenu au moment de l’exécution dans un projet de complément VSTO](#runtimeaddin)  
  
 Pour plus d’informations sur les contrôles de contenu, consultez [Content Controls](../vsto/content-controls.md).  
  
##  <a name="designtime"></a> Adding Content Controls at Design Time  
 Il existe plusieurs façons d'ajouter des contrôles de contenu au document dans un projet au niveau du document au moment du design :  
  
-   Ajoutez un contrôle de contenu à partir de l'onglet **Contrôles Word** de la **Boîte à outils**.  
  
-   Ajoutez un contrôle de contenu à votre document de la même manière que vous ajoutez un contrôle de contenu natif dans Word.  
  
-   Faites glisser le contrôle de contenu vers votre document à partir de la fenêtre **Sources de données** . Cela est utile quand vous souhaitez lier le contrôle aux données, une fois le contrôle créé. Pour plus d’informations, consultez [Comment : remplir des Documents avec des données à partir des objets](../vsto/how-to-populate-documents-with-data-from-objects.md) et [Comment : remplir des Documents avec les données d’une base de données](../vsto/how-to-populate-documents-with-data-from-a-database.md).  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
#### <a name="to-add-a-content-control-to-a-document-by-using-the-toolbox"></a>Pour ajouter un contrôle de contenu à un document à l'aide de la boîte à outils  
  
1.  Dans le document hébergé dans le concepteur [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , placez le curseur à l'endroit où vous souhaitez ajouter le contrôle de contenu, ou sélectionnez le texte que le contrôle de contenu doit remplacer.  
  
2.  Ouvrez la **Boîte à outils** , puis cliquez sur l'onglet **Contrôles Word** .  
  
3.  Ajoutez le contrôle en procédant de l'une des manières suivantes :  
  
    -   Double-cliquez sur un contrôle de contenu dans la **Boîte à outils**.  
  
         ou  
  
    -   Cliquez sur un contrôle de contenu dans la **Boîte à outils** , puis appuyez sur la touche Entrée.  
  
         ou  
  
    -   Faites glisser un contrôle de contenu de la **Boîte à outils** vers le document. Le contrôle de contenu est ajouté à la sélection actuelle dans le document, et non à l'emplacement correspondant au pointeur de souris.  
  
> [!NOTE]  
>  Vous ne pouvez pas ajouter <xref:Microsoft.Office.Tools.Word.GroupContentControl> à l'aide de la **Boîte à outils**. Vous pouvez uniquement ajouter <xref:Microsoft.Office.Tools.Word.GroupContentControl> dans Word, ou au moment de l'exécution.  
  
> [!NOTE]  
>  Visual Studio ne fournit aucun contrôle de contenu de case à cocher dans la boîte à outils. Pour ajouter un contrôle de contenu de case à cocher au document, vous devez créer un objet <xref:Microsoft.Office.Tools.Word.ContentControl> par programmation. Pour plus d'informations, consultez [Content Controls](../vsto/content-controls.md).  
  
#### <a name="to-add-a-content-control-to-a-document-in-word"></a>Pour ajouter un contrôle de contenu à un document dans Word  
  
1.  Dans le document hébergé dans le concepteur [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , placez le curseur à l'endroit où vous souhaitez ajouter le contrôle de contenu, ou sélectionnez le texte que le contrôle de contenu doit remplacer.  
  
2.  Dans le ruban, cliquez sur l'onglet **Développeur** .  
  
    > [!NOTE]  
    >  Si l'onglet **Développeur** n'est pas visible, vous devez tout d'abord l'afficher. Pour plus d'informations, consultez [Comment : afficher l'onglet Développeur sur le ruban](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
3.  Dans le groupe **Contrôles** , cliquez sur l'icône du contrôle de contenu à ajouter.  
  
##  <a name="runtimedoclevel"></a> Adding Content Controls at Run Time in a Document-Level Project  
 Vous pouvez ajouter des contrôles de contenu par programmation à votre document au moment de l'exécution en utilisant les méthodes de la propriété <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> de la classe `ThisDocument` dans votre projet. Chaque méthode possède trois surcharges qui vous permettent d'ajouter un contrôle de contenu comme suit :  
  
-   ajout d'un contrôle à la sélection actuelle ;  
  
-   ajout d'un contrôle à une plage spécifique ;  
  
-   ajout d'un contrôle basé sur un contrôle de contenu natif dans le document.  
  
 Les contrôles de contenu créés de façon dynamique ne sont pas conservés dans le document quand ce dernier est fermé. Toutefois, un contrôle de contenu natif demeure dans le document. Vous pouvez recréer un contrôle de contenu basé sur un contrôle de contenu natif à la prochaine ouverture du document. Pour plus d'informations, consultez [Ajout de contrôles à des documents Office au moment de l'exécution](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
> [!NOTE]  
>  Pour ajouter un contrôle de contenu de case à cocher à un document dans un projet Word 2010, vous devez créer un objet <xref:Microsoft.Office.Tools.Word.ContentControl> . Pour plus d'informations, consultez [Content Controls](../vsto/content-controls.md).  
  
#### <a name="to-add-a-content-control-at-the-current-selection"></a>Pour ajouter un contrôle de contenu à la sélection actuelle  
  
1.  Utilisez un <xref:Microsoft.Office.Tools.Word.ControlCollection> méthode portant le nom `Add` \< *classe contrôle*> (où *classe contrôle* est le nom de classe du contrôle de contenu que vous souhaitez ajouter, par exemple <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A>), et qui comporte un paramètre unique pour le nom du nouveau contrôle.  
  
     L'exemple de code suivant utilise la méthode <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> pour ajouter un nouveau <xref:Microsoft.Office.Tools.Word.RichTextContentControl> au début du document. Pour exécuter ce code, ajoutez-le à la classe `ThisDocument` dans votre projet, puis appelez la méthode `AddRichTextControlAtSelection` à partir du gestionnaire d'événements `ThisDocument_Startup` .  
  
     [!code-csharp[Trin_ContentControlReference#700](../vsto/codesnippet/CSharp/trin_wordcontentcontrolreference/RichText.cs#700)]
     [!code-vb[Trin_ContentControlReference#700](../vsto/codesnippet/VisualBasic/trin_contentcontrolreference/RichText.vb#700)]  
  
#### <a name="to-add-a-content-control-at-a-specified-range"></a>Pour ajouter un contrôle de contenu à une plage spécifique  
  
1.  Utilisez un <xref:Microsoft.Office.Tools.Word.ControlCollection> méthode portant le nom `Add` \< *classe contrôle*> (où *classe contrôle* est le nom de la classe de contrôle de contenu que vous souhaitez ajouter, par exemple <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A>), et qui comporte un <xref:Microsoft.Office.Interop.Word.Range> paramètre.  
  
     L'exemple de code suivant utilise la méthode <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> pour ajouter un nouveau <xref:Microsoft.Office.Tools.Word.RichTextContentControl> au début du document. Pour exécuter ce code, ajoutez-le à la classe `ThisDocument` dans votre projet, puis appelez la méthode `AddRichTextControlAtRange` à partir du gestionnaire d'événements `ThisDocument_Startup` .  
  
     [!code-csharp[Trin_ContentControlReference#701](../vsto/codesnippet/CSharp/trin_wordcontentcontrolreference/RichText.cs#701)]
     [!code-vb[Trin_ContentControlReference#701](../vsto/codesnippet/VisualBasic/trin_contentcontrolreference/RichText.vb#701)]  
  
#### <a name="to-add-a-content-control-that-is-based-on-a-native-content-control"></a>Pour ajouter un contrôle de contenu basé sur un contrôle de contenu natif  
  
1.  Utilisez un <xref:Microsoft.Office.Tools.Word.ControlCollection> méthode portant le nom `Add` \< *classe contrôle*> (où *classe contrôle* est le nom de la classe de contrôle de contenu que vous souhaitez ajouter, par exemple <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A>), et qui comporte un paramètre Microsoft.Office.Interop.Word.ContentControl.  
  
     L'exemple de code suivant utilise la méthode <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> pour créer un <xref:Microsoft.Office.Tools.Word.RichTextContentControl> pour chaque contrôle de texte enrichi natif présent dans le document. Pour exécuter ce code, ajoutez-le à la classe `ThisDocument` dans votre projet, puis appelez la méthode `CreateRichTextControlsFromNativeControls` à partir du gestionnaire d'événements `ThisDocument_Startup` .  
  
     [!code-csharp[Trin_ContentControlReference#702](../vsto/codesnippet/CSharp/trin_wordcontentcontrolreference/RichText.cs#702)]
     [!code-vb[Trin_ContentControlReference#702](../vsto/codesnippet/VisualBasic/trin_contentcontrolreference/RichText.vb#702)]  
  
##  <a name="runtimeaddin"></a> Ajout de contrôles de contenu au moment de l'exécution dans un projet de complément VSTO  
 Vous pouvez ajouter des contrôles de contenu par programmation à un document ouvert au moment de l'exécution en utilisant un complément VSTO. Pour ce faire, vous devez générer un élément hôte <xref:Microsoft.Office.Tools.Word.Document> basé sur un document ouvert, puis utiliser les méthodes de la propriété <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> de cet élément hôte. Chaque méthode possède trois surcharges qui vous permettent d'ajouter un contrôle de contenu comme suit :  
  
-   ajout d'un contrôle à la sélection actuelle ;  
  
-   ajout d'un contrôle à une plage spécifique ;  
  
-   ajout d'un contrôle basé sur un contrôle de contenu natif dans le document.  
  
 Les contrôles de contenu créés de façon dynamique ne sont pas conservés dans le document quand ce dernier est fermé. Toutefois, un contrôle de contenu natif demeure dans le document. Vous pouvez recréer un contrôle de contenu basé sur un contrôle de contenu natif à la prochaine ouverture du document. Pour plus d'informations, consultez [Persisting Dynamic Controls in Office Documents](../vsto/persisting-dynamic-controls-in-office-documents.md).  
  
 Pour plus d’informations sur la génération d’éléments hôtes dans les projets de complément VSTO, consultez [extension de Documents Word et classeurs Excel dans des Compléments VSTO au moment de l’exécution](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
> [!NOTE]  
>  Pour ajouter un contrôle de contenu de case à cocher à un document, vous devez créer un objet <xref:Microsoft.Office.Tools.Word.ContentControl> . Pour plus d'informations, consultez [Content Controls](../vsto/content-controls.md).  
  
#### <a name="to-add-a-content-control-at-the-current-selection"></a>Pour ajouter un contrôle de contenu à la sélection actuelle  
  
1.  Utilisez un <xref:Microsoft.Office.Tools.Word.ControlCollection> méthode portant le nom `Add` \< *classe contrôle*> (où *classe contrôle* est le nom de classe du contrôle de contenu que vous souhaitez ajouter, par exemple <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A>), et qui comporte un paramètre unique pour le nom du nouveau contrôle.  
  
     L'exemple de code suivant utilise la méthode <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> pour ajouter un nouveau <xref:Microsoft.Office.Tools.Word.RichTextContentControl> au début du document actif. Pour exécuter ce code, ajoutez-le à la classe `ThisAddIn` dans votre projet, puis appelez la méthode `AddRichTextControlAtSelection` à partir du gestionnaire d'événements `ThisAddIn_Startup` .  
  
     [!code-vb[Trin_WordAddInDynamicControls#1](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#1)]
     [!code-csharp[Trin_WordAddInDynamicControls#1](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#1)]  
  
#### <a name="to-add-a-content-control-at-a-specified-range"></a>Pour ajouter un contrôle de contenu à une plage spécifique  
  
1.  Utilisez un <xref:Microsoft.Office.Tools.Word.ControlCollection> méthode portant le nom `Add` \< *classe contrôle*> (où *classe contrôle* est le nom de la classe de contrôle de contenu que vous souhaitez ajouter, par exemple <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A>), et qui comporte un <xref:Microsoft.Office.Interop.Word.Range> paramètre.  
  
     L'exemple de code suivant utilise la méthode <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> pour ajouter un nouveau <xref:Microsoft.Office.Tools.Word.RichTextContentControl> au début du document actif. Pour exécuter ce code, ajoutez-le à la classe `ThisAddIn` dans votre projet, puis appelez la méthode `AddRichTextControlAtRange` à partir du gestionnaire d'événements `ThisAddIn_Startup` .  
  
     [!code-vb[Trin_WordAddInDynamicControls#2](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#2)]
     [!code-csharp[Trin_WordAddInDynamicControls#2](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#2)]  
  
#### <a name="to-add-a-content-control-that-is-based-on-a-native-content-control"></a>Pour ajouter un contrôle de contenu basé sur un contrôle de contenu natif  
  
1.  Utilisez un <xref:Microsoft.Office.Tools.Word.ControlCollection> méthode portant le nom `Add` \< *classe contrôle*> (où *classe contrôle* est le nom de la classe de contrôle de contenu que vous souhaitez ajouter, par exemple <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A>), et qui comporte un paramètre Microsoft.Office.Interop.Word.ContentControl.  
  
     L'exemple de code suivant utilise la méthode <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> pour créer un <xref:Microsoft.Office.Tools.Word.RichTextContentControl> pour chaque contrôle de texte enrichi natif présent dans un document, une fois ce dernier ouvert. Pour exécuter ce code, ajoutez-le à la classe `ThisAddIn` dans votre projet.  
  
     [!code-vb[Trin_WordAddInDynamicControls#3](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#3)]
     [!code-csharp[Trin_WordAddInDynamicControls#3](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#3)]  
  
     En C#, vous devez également attacher le gestionnaire d'événements `Application_DocumentOpen` à l'événement <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen> .  
  
     [!code-csharp[Trin_WordAddInDynamicControls#6](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#6)]  
  
## <a name="see-also"></a>Voir aussi  
 [Automatisation de Word à l’aide d’objets étendus](../vsto/automating-word-by-using-extended-objects.md)   
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)   
 [Ajout de contrôles aux Documents Office au moment de l’exécution](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Programmatic Limitations of Host Items and Host Controls](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)   
 [Programming Document-Level Customizations](../vsto/programming-document-level-customizations.md)  
  