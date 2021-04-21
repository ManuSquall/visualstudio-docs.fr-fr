---
title: 'Comment : ajouter des contrôles Bookmark à des documents Word'
description: En savoir plus sur les projets au niveau du document, vous pouvez ajouter des contrôles Bookmark au document de votre projet au moment du design ou au moment de l’exécution.
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VST.Bookmark.Dialog
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Bookmark control, adding to documents
- Create Bookmark Control dialog box
- controls [Office development in Visual Studio], adding to documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 0a5520582db9919417b1c70d773355901ac0b0a5
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826601"
---
# <a name="how-to-add-bookmark-controls-to-word-documents"></a>Comment : ajouter des contrôles Bookmark à des documents Word
  Dans les projets au niveau du document, vous pouvez ajouter des contrôles <xref:Microsoft.Office.Tools.Word.Bookmark> au document de votre projet au moment du design ou au moment de l'exécution. Dans les projets de complément VSTO, vous pouvez ajouter des contrôles <xref:Microsoft.Office.Tools.Word.Bookmark> à tout document ouvert au moment de l’exécution.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 Cette rubrique décrit les tâches suivantes :

- [Ajouter des contrôles Bookmark au moment du design](#designtime)

- [Ajouter des contrôles Bookmark au moment de l’exécution dans un projet au niveau du document](#runtimedoclevel)

- [Ajouter des contrôles Bookmark au moment de l’exécution dans un projet de complément VSTO](#runtimeaddin)

  Pour plus d’informations sur les <xref:Microsoft.Office.Tools.Word.Bookmark> contrôles, consultez [contrôle Bookmark](../vsto/bookmark-control.md).

## <a name="add-bookmark-controls-at-design-time"></a><a name="designtime"></a> Ajouter des contrôles Bookmark au moment du design
 Il existe plusieurs façons d'ajouter des contrôles <xref:Microsoft.Office.Tools.Word.Bookmark> au document Word d'un projet au niveau du document au moment du design :

- À partir de la **boîte à outils** Visual Studio.

   Vous pouvez alors faire glisser le contrôle <xref:Microsoft.Office.Tools.Word.Bookmark> depuis la **boîte à outils** vers votre document. Vous souhaiterez peut-être choisir cette méthode si vous utilisez déjà la **boîte à outils** pour ajouter des contrôles Windows Forms à votre document.

- À partir de Word.

   Vous pouvez ajouter le contrôle <xref:Microsoft.Office.Tools.Word.Bookmark> à votre document de la même manière que vous ajouteriez le signet natif. L'avantage de cette méthode est que vous pouvez nommer votre contrôle au moment de sa création.

- À partir de la fenêtre **Sources de données** .

   Vous pouvez faire glisser le contrôle <xref:Microsoft.Office.Tools.Word.Bookmark> vers votre document à partir de la fenêtre **Sources de données** . Cela est utile lorsque vous souhaitez lier simultanément le contrôle aux données. Vous pouvez ajouter le contrôle hôte de la même manière que vous ajouteriez un contrôle Windows Form à partir de la fenêtre **Sources de données** . Pour plus d’informations, consultez [liaison de données et Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms).

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

#### <a name="to-add-a-bookmark-control-to-a-document-from-the-toolbox"></a>Pour ajouter un contrôle Bookmark à un document à partir de la boîte à outils

1. Ouvrez la **boîte à outils** et cliquez sur l'onglet **Contrôles Word** .

2. Faites glisser un contrôle <xref:Microsoft.Office.Tools.Word.Bookmark> vers le document.

     La boîte de dialogue **Ajouter un signet** s'affiche.

3. Sélectionnez le texte ou autres éléments que vous souhaitez inclure dans le signet.

4. Cliquez sur **OK**.

     Si vous ne souhaitez pas conserver le nom du signet par défaut, vous pouvez modifier le nom dans la fenêtre **Propriétés** .

#### <a name="to-add-a-bookmark-control-to-a-document-in-word"></a>Pour ajouter un contrôle Bookmark à un document dans Word

1. Dans le document hébergé dans le Concepteur [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , placez le curseur où vous souhaitez ajouter le signet ou sélectionnez le texte que le signet doit encadrer.

2. Sous l'onglet **Insertion** du ruban, dans le groupe **Liens** , cliquez sur le bouton **Signet** .

3. Dans la boîte de dialogue **Signet** , entrez le nom du nouveau signet, puis cliquez sur **Ajouter**.

## <a name="add-bookmark-controls-at-run-time-in-a-document-level-project"></a><a name="runtimedoclevel"></a> Ajouter des contrôles Bookmark au moment de l’exécution dans un projet au niveau du document
 Vous pouvez ajouter des contrôles <xref:Microsoft.Office.Tools.Word.Bookmark> par programmation à votre document au moment de l'exécution à l'aide des méthodes de la propriété <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> de la classe `ThisDocument` de votre projet. Il existe deux surcharges de méthode qui permettent d'ajouter un contrôle <xref:Microsoft.Office.Tools.Word.Bookmark> de la façon suivante :

- Ajouter un <xref:Microsoft.Office.Tools.Word.Bookmark> à une plage spécifiée.

- Ajouter un <xref:Microsoft.Office.Tools.Word.Bookmark> basé sur un signet natif dans le document (autrement dit, un <xref:Microsoft.Office.Interop.Word.Bookmark>).

  Les contrôles <xref:Microsoft.Office.Tools.Word.Bookmark> créés de façon dynamique ne sont pas conservés dans le document lorsque le document est fermé. Toutefois, un <xref:Microsoft.Office.Interop.Word.Bookmark> natif demeure dans le document. Vous pouvez recréer un <xref:Microsoft.Office.Tools.Word.Bookmark> basé sur un signet lors de la prochaine ouverture du document. Pour plus d’informations, consultez [Ajouter des contrôles aux documents Office au moment de l’exécution](../vsto/adding-controls-to-office-documents-at-run-time.md).

#### <a name="to-add-a-bookmark-control-to-a-document-programmatically"></a>Pour ajouter un contrôle Bookmark à un document par programmation

1. Dans le gestionnaire d'événements `ThisDocument_Startup` de votre projet, insérez le code suivant pour ajouter le contrôle <xref:Microsoft.Office.Tools.Word.Bookmark> au premier paragraphe du document.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorehostcontrolsword/ThisDocument.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsWordVB/ThisDocument.vb" id="Snippet1":::

    > [!NOTE]
    > Si vous souhaitez créer un contrôle <xref:Microsoft.Office.Tools.Word.Bookmark> à partir d'un <xref:Microsoft.Office.Interop.Word.Bookmark>existant, utilisez la méthode <xref:Microsoft.Office.Tools.Word.ControlCollection.AddBookmark%2A> et transmettez le <xref:Microsoft.Office.Interop.Word.Bookmark>existant.

## <a name="add-bookmark-controls-at-run-time-in-a-vsto-add-in-project"></a><a name="runtimeaddin"></a> Ajouter des contrôles Bookmark au moment de l’exécution dans un projet de complément VSTO
 Vous pouvez ajouter des contrôles <xref:Microsoft.Office.Tools.Word.Bookmark> par programmation à tout document ouvert au moment de l'exécution en utilisant un complément VSTO. Pour ce faire, vous devez générer un élément hôte <xref:Microsoft.Office.Tools.Word.Document> basé sur un document ouvert, puis utiliser les méthodes de la propriété <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> de cet élément hôte. Il existe deux surcharges de méthode qui permettent d'ajouter un contrôle <xref:Microsoft.Office.Tools.Word.Bookmark> de la façon suivante :

- Ajouter un <xref:Microsoft.Office.Tools.Word.Bookmark> à une plage spécifiée.

- Ajouter un <xref:Microsoft.Office.Tools.Word.Bookmark> basé sur un signet natif dans le document (autrement dit, un <xref:Microsoft.Office.Interop.Word.Bookmark>).

  Les contrôles <xref:Microsoft.Office.Tools.Word.Bookmark> créés de façon dynamique ne sont pas conservés dans le document lorsque le document est fermé. Toutefois, un <xref:Microsoft.Office.Interop.Word.Bookmark> natif demeure dans le document. Vous pouvez recréer un <xref:Microsoft.Office.Tools.Word.Bookmark> basé sur un signet lors de la prochaine ouverture du document. Pour plus d’informations, consultez [persistance des contrôles dynamiques dans les documents Office](../vsto/persisting-dynamic-controls-in-office-documents.md).

  Pour plus d’informations sur la génération d’éléments hôtes dans des projets de complément VSTO, consultez [extension de documents Word et de classeurs Excel dans des compléments VSTO au moment](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)de l’exécution.

#### <a name="to-add-a-bookmark-control-at-a-specified-range"></a>Pour ajouter un contrôle Bookmark à une plage spécifiée

1. Utilisez la méthode <xref:Microsoft.Office.Tools.Word.ControlCollection.AddBookmark%2A> et passez le <xref:Microsoft.Office.Interop.Word.Range> à l'emplacement où vous souhaitez ajouter le <xref:Microsoft.Office.Tools.Word.Bookmark>.

     L'exemple de code suivant ajoute un nouveau <xref:Microsoft.Office.Tools.Word.Bookmark> au début du document actif. Pour utiliser cet exemple, exécutez le code à partir du gestionnaire d'événements `ThisAddIn_Startup` dans un projet de complément VSTO Word.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb" id="Snippet4":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs" id="Snippet4":::

#### <a name="to-add-a-bookmark-control-that-is-based-on-a-native-bookmark-control"></a>Pour ajouter un contrôle Bookmark basé sur un contrôle Bookmark natif

1. Utilisez la méthode <xref:Microsoft.Office.Tools.Word.ControlCollection.AddBookmark%2A> et passez le <xref:Microsoft.Office.Interop.Word.Bookmark> existant que vous souhaitez utiliser comme base pour le nouveau <xref:Microsoft.Office.Tools.Word.Bookmark>.

     L'exemple de code suivant crée un <xref:Microsoft.Office.Tools.Word.Bookmark> basé sur le premier <xref:Microsoft.Office.Interop.Word.Bookmark> du document actif. Pour utiliser cet exemple, exécutez le code à partir du gestionnaire d'événements `ThisAddIn_Startup` dans un projet de complément VSTO Word.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb" id="Snippet5":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs" id="Snippet5":::

## <a name="see-also"></a>Voir aussi
- [Automatiser Word à l’aide d’objets étendus](../vsto/automating-word-by-using-extended-objects.md)
- [Vue d’ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)
- [Ajouter des contrôles aux documents Office au moment de l’exécution](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Limitations de programmation des éléments hôtes et des contrôles hôtes](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Programmer les compléments VSTO](../vsto/programming-vsto-add-ins.md)
- [Personnaliser les personnalisations au niveau du document](../vsto/programming-document-level-customizations.md)
- [Comment : redimensionner les contrôles Bookmark](../vsto/how-to-resize-bookmark-controls.md)
