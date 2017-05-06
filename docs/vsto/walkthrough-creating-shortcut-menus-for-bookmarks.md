---
title: "Proc&#233;dure pas &#224; pas&#160;: cr&#233;ation de menus contextuels pour les signets"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Bookmark (contrôle), événements"
  - "menus contextuels, Word"
  - "menus, créer dans les applications Office"
  - "menus contextuels, Word"
ms.assetid: 86dbf3ff-ba75-42f9-8df6-abfc19b3cf6b
caps.latest.revision: 57
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 53
---
# Proc&#233;dure pas &#224; pas&#160;: cr&#233;ation de menus contextuels pour les signets
  Cette procédure pas à pas montre comment créer des menus contextuels pour les contrôles <xref:Microsoft.Office.Tools.Word.Bookmark> dans une personnalisation au niveau du document pour Word.  Lorsqu'un utilisateur clique avec le bouton droit sur le texte d'un signet, un menu contextuel proposant des options de mise en forme apparaît.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Cette procédure pas à pas décrit les tâches suivantes :  
  
-   [Création du projet](#BKMK_CreateProject).  
  
-   [Ajout de texte et de signets au document](#BKMK_addtextandbookmarks).  
  
-   [Commandes à un menu contextuel](#BKMK_AddCmndsShortMenu).  
  
-   [Mettez en forme le texte dans un signet](#BKMK_formattextbkmk).  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Composants requis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] ou [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]  
  
##  <a name="BKMK_CreateProject"></a> Création du projet  
 La première étape consiste à créer un projet de document Word dans Visual Studio.  
  
#### Pour créer un projet  
  
-   Créez un projet de document Word portant le nom My Bookmark Shortcut Menu.  Dans l'Assistant, sélectionnez **Créer un nouveau document**.  Pour plus d'informations, consultez [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio ouvre le nouveau document Word dans le concepteur et ajoute le projet **My Bookmark Shortcut Menu** à l'**Explorateur de solutions**.  
  
##  <a name="BKMK_addtextandbookmarks"></a> Ajout de texte et de signets au document  
 Ajoutez du texte à votre document puis ajoutez deux signets superposés.  
  
#### Pour ajouter du texte à votre document  
  
-   Dans le document qui apparaît dans le concepteur de votre projet, tapez le texte suivant.  
  
     Il s'agit d'un exemple de création d'un menu contextuel lorsque vous cliquez avec le bouton droit sur le texte dans un signet.  
  
#### Pour ajouter un contrôle Bookmark à votre document  
  
1.  Dans **Boîte à outils**, sous l'onglet **Contrôles Word**, faites glisser un contrôle <xref:Microsoft.Office.Tools.Word.Bookmark> à votre document.  
  
     La boîte de dialogue **Ajouter un contrôle Bookmark** s'affiche.  
  
2.  Sélectionnez les mots « Création d'un menu contextuel lorsque vous cliquez avec le bouton droit sur le texte », puis cliquez sur **OK**.  
  
     `bookmark1` est ajouté au document.  
  
3.  Ajoutez un autre contrôle <xref:Microsoft.Office.Tools.Word.Bookmark> aux mots « bouton droit sur le texte d'un signet ».  
  
     `bookmark2` est ajouté au document.  
  
    > [!NOTE]  
    >  Les mots « bouton droit sur le texte » apparaissent dans `bookmark1` et `bookmark2`.  
  
 Lorsque vous ajoutez un signet à un document au moment du design, un contrôle <xref:Microsoft.Office.Tools.Word.Bookmark> est créé.  Vous pouvez programmer plusieurs événements du signet.  Ainsi, il est possible d'écrire du code dans l'événement <xref:Microsoft.Office.Tools.Word.Bookmark.BeforeRightClick> du signet de manière à faire apparaître un menu contextuel lorsque l'utilisateur clique avec le bouton droit sur le texte du signet.  
  
##  <a name="BKMK_AddCmndsShortMenu"></a> Commandes à un menu contextuel  
 Ajoutez des boutons au menu contextuel qui apparaît lorsque vous cliquez avec le bouton droit sur le document.  
  
#### Pour ajouter des commandes à un menu contextuel  
  
1.  Ajoutez un élément **Ruban XML** au projet.  Pour plus d'informations, consultez [Comment : démarrer avec la personnalisation du ruban](../vsto/how-to-get-started-customizing-the-ribbon.md).  
  
2.  Dans l'**Explorateur de solutions**, sélectionnez **ThisDocument.cs** ou **ThisDocument.vb**.  
  
3.  Dans la barre de menus, sélectionnez **Afficher**, **Code**.  
  
     Le fichier de classe **ThisDocument** s'ouvre dans l'éditeur de code.  
  
4.  Ajoutez le code suivant à la classe **ThisDocument**.  Ce code substitue la méthode CreateRibbonExtensibilityObject et retourne la classe Ribbon XML à l'application Office.  
  
     [!code-csharp[Trin_Word_Document_Menus#1](../snippets/csharp/VS_Snippets_OfficeSP/trin_word_document_menus/cs/thisdocument.cs#1)]
     [!code-vb[Trin_Word_Document_Menus#1](../snippets/visualbasic/VS_Snippets_OfficeSP/trin_word_document_menus/vb/thisdocument.vb#1)]  
  
5.  Dans l'**Explorateur de solutions**, sélectionnez le fichier XML du ruban.  Par défaut, le fichier XML du ruban est nommé Ribbon1.xml.  
  
6.  Dans la barre de menus, sélectionnez **Afficher**, **Code**.  
  
     Le fichier xml ruban s'ouvre dans l'éditeur de code.  
  
7.  Dans l'éditeur de code, remplacez le contenu du fichier XML du ruban par le code suivant.  
  
    ```  
  
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
  
     Ce code ajoute deux boutons au menu contextuel qui apparaît lorsque vous cliquez avec le bouton droit sur le document.  
  
8.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur `ThisDocument`, puis cliquez sur **Afficher le code**.  
  
9. Déclarez les variables suivantes et une variable de signet au niveau de la classe.  
  
     [!code-csharp[Trin_Word_Document_Menus#2](../snippets/csharp/VS_Snippets_OfficeSP/trin_word_document_menus/cs/thisdocument.cs#2)]
     [!code-vb[Trin_Word_Document_Menus#2](../snippets/visualbasic/VS_Snippets_OfficeSP/trin_word_document_menus/vb/thisdocument.vb#2)]  
  
10. Dans l'**Explorateur de solutions**, sélectionnez le fichier de code du ruban.  Par défaut, le fichier de code du ruban est nommé **Ribbon1.cs** ou **Ribbon1.vb**.  
  
11. Dans la barre de menus, sélectionnez **Afficher**, **Code**.  
  
     Le fichier de code du ruban s'ouvre dans l'éditeur de code.  
  
12. Dans le fichier de code du ruban, ajoutez la méthode suivante.  C'est une méthode de rappel pour les deux boutons que vous avez ajoutés au menu contextuel du document.  Cette méthode détermine si ces boutons apparaissent dans le menu contextuel.  Les boutons gras et italique apparaissent uniquement si vous cliquez avec le bouton droit sur le texte dans le signet.  
  
     [!code-csharp[Trin_Word_Document_Menus#5](../snippets/csharp/VS_Snippets_OfficeSP/trin_word_document_menus/cs/ribbon1.cs#5)]
     [!code-vb[Trin_Word_Document_Menus#5](../snippets/visualbasic/VS_Snippets_OfficeSP/trin_word_document_menus/vb/ribbon1.vb#5)]  
  
##  <a name="BKMK_formattextbkmk"></a> Mettez en forme le texte dans un signet  
  
#### Pour mettre en forme le texte dans le signet  
  
1.  Dans le fichier de code du ruban, ajoutez un gestionnaire d'événements `ButtonClick` pour appliquer la mise en forme au signet.  
  
     [!code-csharp[Trin_Word_Document_Menus#6](../snippets/csharp/VS_Snippets_OfficeSP/trin_word_document_menus/cs/ribbon1.cs#6)]
     [!code-vb[Trin_Word_Document_Menus#6](../snippets/visualbasic/VS_Snippets_OfficeSP/trin_word_document_menus/vb/ribbon1.vb#6)]  
  
2.  **Explorateur de solutions**, sélectionnez **ThisDocument.cs** ou **ThisDocument.vb**.  
  
3.  Dans la barre de menus, sélectionnez **Afficher**, **Code**.  
  
     Le fichier de classe **ThisDocument** s'ouvre dans l'éditeur de code.  
  
4.  Ajoutez le code suivant à la classe **ThisDocument**.  
  
     [!code-csharp[Trin_Word_Document_Menus#3](../snippets/csharp/VS_Snippets_OfficeSP/trin_word_document_menus/cs/thisdocument.cs#3)]
     [!code-vb[Trin_Word_Document_Menus#3](../snippets/visualbasic/VS_Snippets_OfficeSP/trin_word_document_menus/vb/thisdocument.vb#3)]  
  
    > [!NOTE]  
    >  Vous devez écrire du code pour gérer la superposition éventuelle des signets.  Si vous ne le faites pas, par défaut, le code sera appelé pour tous les signets de la sélection.  
  
5.  En C\#, vous devez ajouter des gestionnaires d'événements pour les contrôles Bookmark à l'événement <xref:Microsoft.Office.Tools.Word.Document.Startup>.  Pour plus d'informations sur la création de gestionnaires d'événements, consultez [Comment : créer des gestionnaires d'événements dans les projets Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_Word_Document_Menus#4](../snippets/csharp/VS_Snippets_OfficeSP/trin_word_document_menus/cs/thisdocument.cs#4)]  
  
## Test de l'application  
 Testez votre document pour vérifier que les éléments de menu Gras et Italique apparaissent dans le menu contextuel lorsque vous cliquez avec le bouton droit sur le texte du signet et que le texte est correctement mis en forme.  
  
#### Pour tester votre document  
  
1.  Appuyez sur F5 pour exécuter votre projet.  
  
2.  Cliquez avec le bouton droit dans le premier signet, puis cliquez sur **Gras**.  
  
3.  Vérifiez que la mise en forme de l'ensemble du texte dans `bookmark1` est en gras.  
  
4.  Cliquez avec le bouton droit sur le texte, à l'endroit où les signets se chevauchent, puis cliquez sur **Italique**.  
  
5.  Vérifiez que sont en italique tout le texte de `bookmark2` et seulement la partie du texte de `bookmark1` qui recoupe `bookmark2`.  
  
## Étapes suivantes  
 Vous devrez peut\-être ensuite exécuter les opérations suivantes :  
  
-   Écrire du code pour répondre aux événements de contrôles hôtes dans Excel.  Pour plus d'informations, consultez [Procédure pas à pas : programmation d'événements d'un contrôle NamedRange](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md).  
  
-   Utiliser une case à cocher pour modifier la mise en forme d'un signet.  Pour plus d'informations, consultez [Procédure pas à pas : modification de la mise en forme d'un document à l'aide de contrôles CheckBox](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md).  
  
## Voir aussi  
 [Procédures pas à pas utilisant Word](../vsto/walkthroughs-using-word.md)   
 [Personnalisation de l'interface utilisateur Office](../vsto/office-ui-customization.md)   
 [Automatisation de Word à l'aide d'objets étendus](../vsto/automating-word-by-using-extended-objects.md)   
 [Bookmark, contrôle](../vsto/bookmark-control.md)   
 [Paramètres optionnels dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  