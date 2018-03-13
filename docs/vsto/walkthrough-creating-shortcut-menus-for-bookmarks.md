---
title: "Procédure pas à pas : Création de Menus contextuels pour les signets | Documents Microsoft"
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
- context menus, Word
- Bookmark control, events
- shortcut menus, Word
- menus, creating in Office applications
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 9af7c7dd4a4c56cbd872b757704d64afd22c6101
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-creating-shortcut-menus-for-bookmarks"></a>Procédure pas à pas : création de menus contextuels pour les signets
  Cette procédure pas à pas montre comment créer des menus contextuels pour <xref:Microsoft.Office.Tools.Word.Bookmark> contrôles dans une personnalisation au niveau du document pour Word. Lorsqu’un utilisateur clique sur le texte d’un signet, un menu contextuel s’affiche et proposant des options de mise en forme le texte.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Cette procédure pas à pas décrit les tâches suivantes :  
  
-   [Création du projet](#BKMK_CreateProject).  
  
-   [Ajout de texte et signets au Document](#BKMK_addtextandbookmarks).  
  
-   [Ajout de commandes à un Menu contextuel](#BKMK_AddCmndsShortMenu).  
  
-   [Mettre en forme le texte dans le signet](#BKMK_formattextbkmk).  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Prérequis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] ou [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]  
  
##  <a name="BKMK_CreateProject"></a>Création du projet  
 La première étape consiste à créer un projet de document Word dans Visual Studio.  
  
#### <a name="to-create-a-new-project"></a>Pour créer un projet  
  
-   Créez un projet de document Word qui porte le nom **My Bookmark Shortcut Menu**. Dans l’Assistant, sélectionnez **créer un nouveau document**. Pour plus d'informations, consultez [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio ouvre le nouveau document Word dans le concepteur et ajoute le **My Bookmark Shortcut Menu** projet **l’Explorateur de solutions**.  
  
##  <a name="BKMK_addtextandbookmarks"></a>Ajout de texte et signets au Document  
 Ajouter du texte à votre document, puis ajoutez deux signets qui se chevauchent.  
  
#### <a name="to-add-text-to-your-document"></a>Pour ajouter du texte à votre document  
  
-   Dans le document qui s’affiche dans le Concepteur de votre projet, tapez le texte suivant.  
  
     **Il s’agit d’un exemple de création d’un menu contextuel lorsque vous cliquez sur le texte d’un signet.**  
  
#### <a name="to-add-a-bookmark-control-to-your-document"></a>Pour ajouter un contrôle Bookmark à votre document  
  
1.  Dans le **boîte à outils**, à partir de la **des contrôles Word** onglet, faites glisser un <xref:Microsoft.Office.Tools.Word.Bookmark> contrôle à votre document.  
  
     Le **ajouter un contrôle Bookmark** boîte de dialogue s’affiche.  
  
2.  Sélectionnez les mots « création d’un menu contextuel lorsque vous cliquez sur le texte », puis cliquez sur **OK**.  
  
     `bookmark1`est ajouté au document.  
  
3.  Ajoutez un autre <xref:Microsoft.Office.Tools.Word.Bookmark> avec les mots de contrôle « cliquez sur le texte d’un signet ».  
  
     `bookmark2`est ajouté au document.  
  
    > [!NOTE]  
    >  Les mots « cliquez sur le texte » est à la fois dans `bookmark1` et `bookmark2`.  
  
 Lorsque vous ajoutez un signet à un document au moment du design, un <xref:Microsoft.Office.Tools.Word.Bookmark> contrôle est créé. Vous pouvez programmer plusieurs événements du signet. Vous pouvez écrire du code le <xref:Microsoft.Office.Tools.Word.Bookmark.BeforeRightClick> événement du signet afin que lorsque l’utilisateur clique sur le texte du signet, un menu contextuel s’affiche.  
  
##  <a name="BKMK_AddCmndsShortMenu"></a>Ajout de commandes à un Menu contextuel  
 Ajouter des boutons pour le menu contextuel qui s’affiche lorsque vous cliquez sur le document.  
  
#### <a name="to-add-commands-to-a-shortcut-menu"></a>Pour ajouter des commandes à un menu contextuel  
  
1.  Ajouter un **XML du ruban** élément au projet. Pour plus d'informations, consultez [How to: Get Started Customizing the Ribbon](../vsto/how-to-get-started-customizing-the-ribbon.md).  
  
2.  Dans **l’Explorateur de solutions**, sélectionnez **ThisDocument.cs** ou **ThisDocument.vb**.  
  
3.  Dans la barre de menus, sélectionnez **Afficher**, **Code**.  
  
     Le **ThisDocument** fichier de classe s’ouvre dans l’éditeur de Code.  
  
4.  Ajoutez le code suivant à la **ThisDocument** classe. Ce code substitue la méthode CreateRibbonExtensibilityObject et retourne la classe Ribbon XML à l’application Office.  
  
     [!code-csharp[Trin_Word_Document_Menus#1](../vsto/codesnippet/CSharp/trin_word_document_menus.cs/thisdocument.cs#1)]
     [!code-vb[Trin_Word_Document_Menus#1](../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/thisdocument.vb#1)]  
  
5.  Dans l’ **Explorateur de solutions**, sélectionnez le fichier XML de ruban. Par défaut, le fichier XML de ruban se nomme Ribbon1.xml.  
  
6.  Dans la barre de menus, sélectionnez **Afficher**, **Code**.  
  
     Le fichier XML de ruban s’ouvre dans l’éditeur de code.  
  
7.  Dans l’éditeur de Code, remplacez le contenu du fichier XML du ruban avec le code suivant.  
  
    ```  
    <?xml version="1.0" encoding="UTF-8"?>  
    <customUI xmlns="http://schemas.microsoft.com/office/2009/07/customui" onLoad="Ribbon_Load">  
      <contextMenus>  
        <contextMenu idMso="ContextMenuText">  
          <button id="BoldButton" label="Bold" onAction="ButtonClick"          
               getVisible="GetVisible" />  
          <button id="ItalicButton" label="Italic" onAction="ButtonClick"   
              getVisible="GetVisible"/>  
        </contextMenu>  
      </contextMenus>  
    </customUI>  
    ```  
  
     Ce code ajoute deux boutons au menu contextuel qui s’affiche lorsque vous cliquez sur le document.  
  
8.  Dans **l’Explorateur de solutions**, avec le bouton droit `ThisDocument`, puis cliquez sur **afficher le Code**.  
  
9. Déclarez les variables suivantes et une variable de signet au niveau de la classe.  
  
     [!code-csharp[Trin_Word_Document_Menus#2](../vsto/codesnippet/CSharp/trin_word_document_menus.cs/thisdocument.cs#2)]
     [!code-vb[Trin_Word_Document_Menus#2](../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/thisdocument.vb#2)]  
  
10. Dans **l’Explorateur de solutions**, sélectionnez le fichier de code du ruban. Par défaut, le fichier de code du ruban se nomme **Ribbon1.cs** ou **Ribbon1.vb**.  
  
11. Dans la barre de menus, sélectionnez **Afficher**, **Code**.  
  
     Le fichier de code du ruban s'ouvre dans l'éditeur de code.  
  
12. Dans le fichier de code du ruban, ajoutez la méthode suivante. Il s’agit d’une méthode de rappel pour les deux boutons que vous avez ajoutés au menu contextuel du document. Cette méthode détermine si ces boutons s’affichent dans le menu contextuel. Les boutons gras et italiques apparaissent uniquement si vous cliquez sur le texte dans le signet.  
  
     [!code-csharp[Trin_Word_Document_Menus#5](../vsto/codesnippet/CSharp/trin_word_document_menus.cs/ribbon1.cs#5)]
     [!code-vb[Trin_Word_Document_Menus#5](../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/ribbon1.vb#5)]  
  
##  <a name="BKMK_formattextbkmk"></a>Mettre en forme le texte dans le signet  
  
#### <a name="to-format-the-text-in-the-bookmark"></a>Pour mettre en forme le texte dans le signet  
  
1.  Dans le fichier de code du ruban, ajoutez un `ButtonClick` Gestionnaire d’événements pour appliquer la mise en forme au signet.  
  
     [!code-csharp[Trin_Word_Document_Menus#6](../vsto/codesnippet/CSharp/trin_word_document_menus.cs/ribbon1.cs#6)]
     [!code-vb[Trin_Word_Document_Menus#6](../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/ribbon1.vb#6)]  
  
2.  **L’Explorateur de solutions**, sélectionnez **ThisDocument.cs** ou **ThisDocument.vb**.  
  
3.  Dans la barre de menus, sélectionnez **Afficher**, **Code**.  
  
     Le **ThisDocument** fichier de classe s’ouvre dans l’éditeur de Code.  
  
4.  Ajoutez le code suivant à la **ThisDocument** classe.  
  
     [!code-csharp[Trin_Word_Document_Menus#3](../vsto/codesnippet/CSharp/trin_word_document_menus.cs/thisdocument.cs#3)]
     [!code-vb[Trin_Word_Document_Menus#3](../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/thisdocument.vb#3)]  
  
    > [!NOTE]  
    >  Vous devez écrire du code pour gérer le cas où les signets se chevauchent. Si vous le faites pas, par défaut, le code sera appelé pour tous les signets dans la sélection.  
  
5.  En c#, vous devez ajouter des gestionnaires d’événements pour les contrôles bookmark à la <xref:Microsoft.Office.Tools.Word.Document.Startup> événement. Pour plus d’informations sur la création de gestionnaires d’événements, consultez [Comment : créer des gestionnaires d’événements dans les projets Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_Word_Document_Menus#4](../vsto/codesnippet/CSharp/trin_word_document_menus.cs/thisdocument.cs#4)]  
  
## <a name="testing-the-application"></a>Test de l'application  
 Tester votre document pour vérifier que les éléments de menu gras et italique apparaissent dans le menu contextuel lorsque vous cliquez sur le texte d’un signet et que le texte est correctement formaté.  
  
#### <a name="to-test-your-document"></a>Pour tester votre document  
  
1.  Appuyez sur F5 pour exécuter votre projet.  
  
2.  Avec le bouton droit dans le premier signet, puis cliquez sur **gras**.  
  
3.  Vérifiez que tout le texte dans `bookmark1` est mis en gras.  
  
4.  Cliquez sur le texte dans lequel les signets se chevauchent, puis cliquez sur **italique**.  
  
5.  Vérifiez que tout le texte dans `bookmark2` est italique et seule la partie du texte dans `bookmark1` qui chevauche `bookmark2` est en italique.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Voici quelques tâches susceptibles de venir après :  
  
-   Écrire du code pour répondre aux événements de contrôles hôtes dans Excel. Pour plus d'informations, consultez [Procédure pas à pas : programmation d'événements d'un contrôle NamedRange](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md).  
  
-   Utilisez une case à cocher pour modifier la mise en forme dans un signet. Pour plus d’informations, consultez [procédure pas à pas : modification de Document mise en forme à l’aide de contrôles CheckBox](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures pas à pas utilisant Word](../vsto/walkthroughs-using-word.md)   
 [Personnalisation de l’interface utilisateur Office](../vsto/office-ui-customization.md)   
 [Automatisation de Word à l’aide d’objets étendus](../vsto/automating-word-by-using-extended-objects.md)   
 [Bookmark (contrôle)](../vsto/bookmark-control.md)   
 [Paramètres optionnels dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  