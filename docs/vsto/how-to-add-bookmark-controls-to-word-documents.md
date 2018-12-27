---
title: 'Procédure : Ajouter des contrôles Bookmark à des documents Word'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
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
manager: douge
ms.workload:
- office
ms.openlocfilehash: 0e58525d20efe17d24cd916b5e9eff79c7da59d7
ms.sourcegitcommit: a205ff1b389fba1803acd32c54df7feb0ef7a203
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/20/2018
ms.locfileid: "53647788"
---
# <a name="how-to-add-bookmark-controls-to-word-documents"></a>Procédure : Ajouter des contrôles Bookmark à des documents Word
  Dans les projets au niveau du document, vous pouvez ajouter <xref:Microsoft.Office.Tools.Word.Bookmark> contrôles au document dans votre projet au moment du design ou lors de l’exécution. Dans les projets de complément VSTO, vous pouvez ajouter <xref:Microsoft.Office.Tools.Word.Bookmark> contrôles à tout document ouvert au moment de l’exécution.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 Cette rubrique décrit les tâches suivantes :  
  
- [Ajouter des contrôles Bookmark au moment du design](#designtime)  
  
- [Ajouter des contrôles Bookmark au moment de l’exécution dans un projet au niveau du document](#runtimedoclevel)  
  
- [Ajouter des contrôles Bookmark au moment de l’exécution dans un projet de complément VSTO](#runtimeaddin)  
  
  Pour plus d’informations sur <xref:Microsoft.Office.Tools.Word.Bookmark> contrôles, consultez [Bookmark (contrôle)](../vsto/bookmark-control.md).  
  
##  <a name="designtime"></a> Ajouter des contrôles Bookmark au moment du Design  
 Il existe plusieurs façons d'ajouter des contrôles <xref:Microsoft.Office.Tools.Word.Bookmark> au document Word d'un projet au niveau du document au moment du design :  
  
- À partir de la **boîte à outils**Visual Studio.  
  
   Vous pouvez alors faire glisser le contrôle <xref:Microsoft.Office.Tools.Word.Bookmark> depuis la **boîte à outils** vers votre document. Vous souhaiterez peut-être choisir cette méthode si vous utilisez déjà la **boîte à outils** pour ajouter des contrôles Windows Forms à votre document.  
  
- À partir de Word.  
  
   Vous pouvez ajouter le contrôle <xref:Microsoft.Office.Tools.Word.Bookmark> à votre document de la même manière que vous ajouteriez le signet natif. L'avantage de cette méthode est que vous pouvez nommer votre contrôle au moment de sa création.  
  
- À partir de la fenêtre **Sources de données** .  
  
   Vous pouvez faire glisser le contrôle <xref:Microsoft.Office.Tools.Word.Bookmark> vers votre document à partir de la fenêtre **Sources de données** . Cela est utile lorsque vous souhaitez lier simultanément le contrôle aux données. Vous pouvez ajouter le contrôle hôte de la même manière que vous ajouteriez un contrôle Windows Form à partir de la fenêtre **Sources de données** . Pour plus d’informations, consultez [liaison de données et Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms).  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
#### <a name="to-add-a-bookmark-control-to-a-document-from-the-toolbox"></a>Pour ajouter un contrôle Bookmark à un document à partir de la boîte à outils  
  
1.  Ouvrez la **Boîte à outils** , puis cliquez sur l'onglet **Contrôles Word** .  
  
2.  Faites glisser un contrôle <xref:Microsoft.Office.Tools.Word.Bookmark> vers le document.  
  
     La boîte de dialogue **Ajouter un signet** s'affiche.  
  
3.  Sélectionnez le texte ou autres éléments que vous souhaitez inclure dans le signet.  
  
4.  Cliquez sur **OK**.  
  
     Si vous ne souhaitez pas conserver le nom du signet par défaut, vous pouvez modifier le nom dans la fenêtre **Propriétés** .  
  
#### <a name="to-add-a-bookmark-control-to-a-document-in-word"></a>Pour ajouter un contrôle Bookmark à un document dans Word  
  
1.  Dans le document hébergé dans le Concepteur [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , placez le curseur où vous souhaitez ajouter le signet ou sélectionnez le texte que le signet doit encadrer.  
  
2.  Sous l'onglet **Insertion** du ruban, dans le groupe **Liens** , cliquez sur le bouton **Signet** .  
  
3.  Dans la boîte de dialogue **Signet** , entrez le nom du nouveau signet, puis cliquez sur **Ajouter**.  
  
##  <a name="runtimedoclevel"></a> Ajouter des contrôles Bookmark au moment de l’exécution dans un projet au niveau du document  
 Vous pouvez ajouter <xref:Microsoft.Office.Tools.Word.Bookmark> par programmation des contrôles à votre document au moment de l’exécution à l’aide des méthodes de la <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> propriété de la `ThisDocument` classe dans votre projet. Il existe deux surcharges de méthode qui permettent d'ajouter un contrôle <xref:Microsoft.Office.Tools.Word.Bookmark> de la façon suivante :  
  
- Ajouter un <xref:Microsoft.Office.Tools.Word.Bookmark> à une plage spécifiée.  
  
- Ajouter un <xref:Microsoft.Office.Tools.Word.Bookmark> basé sur un signet natif dans le document (autrement dit, un <xref:Microsoft.Office.Interop.Word.Bookmark>).  
  
  Les contrôles <xref:Microsoft.Office.Tools.Word.Bookmark> créés de façon dynamique ne sont pas conservés dans le document lorsque le document est fermé. Toutefois, un <xref:Microsoft.Office.Interop.Word.Bookmark> natif demeure dans le document. Vous pouvez recréer un <xref:Microsoft.Office.Tools.Word.Bookmark> basé sur un signet lors de la prochaine ouverture du document. Pour plus d’informations, consultez [ajouter des contrôles aux documents Office au moment de l’exécution](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
#### <a name="to-add-a-bookmark-control-to-a-document-programmatically"></a>Pour ajouter un contrôle Bookmark à un document par programmation  
  
1.  Dans le gestionnaire d'événements `ThisDocument_Startup` de votre projet, insérez le code suivant pour ajouter le contrôle <xref:Microsoft.Office.Tools.Word.Bookmark> au premier paragraphe du document.  
  
     [!code-csharp[Trin_VstcoreHostControlsWord#1](../vsto/codesnippet/CSharp/trin_vstcorehostcontrolsword/ThisDocument.cs#1)]
     [!code-vb[Trin_VstcoreHostControlsWord#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsWordVB/ThisDocument.vb#1)]  
  
    > [!NOTE]  
    >  Si vous souhaitez créer un contrôle <xref:Microsoft.Office.Tools.Word.Bookmark> à partir d'un <xref:Microsoft.Office.Interop.Word.Bookmark>existant, utilisez la méthode <xref:Microsoft.Office.Tools.Word.ControlCollection.AddBookmark%2A> et transmettez le <xref:Microsoft.Office.Interop.Word.Bookmark>existant.  
  
##  <a name="runtimeaddin"></a> Ajouter des contrôles Bookmark au moment de l’exécution dans un projet de complément VSTO  
 Vous pouvez ajouter <xref:Microsoft.Office.Tools.Word.Bookmark> contrôles par programmation à tout document ouvert lors de l’exécution en utilisant un complément, VSTO. Pour ce faire, vous devez générer un élément hôte <xref:Microsoft.Office.Tools.Word.Document> basé sur un document ouvert, puis utiliser les méthodes de la propriété <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> de cet élément hôte. Il existe deux surcharges de méthode qui permettent d'ajouter un contrôle <xref:Microsoft.Office.Tools.Word.Bookmark> de la façon suivante :  
  
- Ajouter un <xref:Microsoft.Office.Tools.Word.Bookmark> à une plage spécifiée.  
  
- Ajouter un <xref:Microsoft.Office.Tools.Word.Bookmark> basé sur un signet natif dans le document (autrement dit, un <xref:Microsoft.Office.Interop.Word.Bookmark>).  
  
  Les contrôles <xref:Microsoft.Office.Tools.Word.Bookmark> créés de façon dynamique ne sont pas conservés dans le document lorsque le document est fermé. Toutefois, un <xref:Microsoft.Office.Interop.Word.Bookmark> natif demeure dans le document. Vous pouvez recréer un <xref:Microsoft.Office.Tools.Word.Bookmark> basé sur un signet lors de la prochaine ouverture du document. Pour plus d’informations, consultez [conserver des contrôles dynamiques dans les documents Office](../vsto/persisting-dynamic-controls-in-office-documents.md).  
  
  Pour plus d’informations sur la génération d’éléments hôtes dans les projets de complément VSTO, consultez [documents Word d’étendre et classeurs Excel dans des Compléments VSTO lors de l’exécution](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
#### <a name="to-add-a-bookmark-control-at-a-specified-range"></a>Pour ajouter un contrôle Bookmark à une plage spécifiée  
  
1.  Utilisez la méthode <xref:Microsoft.Office.Tools.Word.ControlCollection.AddBookmark%2A> et passez le <xref:Microsoft.Office.Interop.Word.Range> à l'emplacement où vous souhaitez ajouter le <xref:Microsoft.Office.Tools.Word.Bookmark>.  
  
     L'exemple de code suivant ajoute un nouveau <xref:Microsoft.Office.Tools.Word.Bookmark> au début du document actif. Pour utiliser cet exemple, exécutez le code à partir du gestionnaire d'événements `ThisAddIn_Startup` dans un projet de complément VSTO Word.  
  
     [!code-vb[Trin_WordAddInDynamicControls#4](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#4)]
     [!code-csharp[Trin_WordAddInDynamicControls#4](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#4)]  
  
#### <a name="to-add-a-bookmark-control-that-is-based-on-a-native-bookmark-control"></a>Pour ajouter un contrôle Bookmark basé sur un contrôle Bookmark natif  
  
1.  Utilisez la méthode <xref:Microsoft.Office.Tools.Word.ControlCollection.AddBookmark%2A> et passez le <xref:Microsoft.Office.Interop.Word.Bookmark> existant que vous souhaitez utiliser comme base pour le nouveau <xref:Microsoft.Office.Tools.Word.Bookmark>.  
  
     L'exemple de code suivant crée un <xref:Microsoft.Office.Tools.Word.Bookmark> basé sur le premier <xref:Microsoft.Office.Interop.Word.Bookmark> du document actif. Pour utiliser cet exemple, exécutez le code à partir du gestionnaire d'événements `ThisAddIn_Startup` dans un projet de complément VSTO Word.  
  
     [!code-vb[Trin_WordAddInDynamicControls#5](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#5)]
     [!code-csharp[Trin_WordAddInDynamicControls#5](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#5)]  
  
## <a name="see-also"></a>Voir aussi  
 [Automatiser Word à l’aide d’objets étendus](../vsto/automating-word-by-using-extended-objects.md)   
 [Éléments hôtes et la vue d’ensemble des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)   
 [Ajouter des contrôles aux documents Office au moment de l’exécution](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Limitations de programmation des éléments hôtes et contrôles hôtes](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Programmer des Compléments VSTO](../vsto/programming-vsto-add-ins.md)   
 [Programmer des personnalisations au niveau du document](../vsto/programming-document-level-customizations.md)   
 [Guide pratique pour Redimensionner les contrôles Bookmark](../vsto/how-to-resize-bookmark-controls.md)  
  
  