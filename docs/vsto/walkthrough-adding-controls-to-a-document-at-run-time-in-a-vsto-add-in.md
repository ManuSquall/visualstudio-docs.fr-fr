---
title: "Proc&#233;dure pas &#224; pas&#160;: ajout de contr&#244;les &#224; un document au moment de l’ex&#233;cution dans un compl&#233;ment VSTO"
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
  - "compléments (développement Office dans Visual Studio), ajout de contrôles"
  - "compléments de niveau application (développement Office dans Visual Studio), ajout de contrôles"
  - "contrôles (développement Office dans Visual Studio), ajout de documents au moment de l’exécution"
  - "documents (développement Office dans Visual Studio), ajout de contrôles au moment de l’exécution"
ms.assetid: ab6dff40-9964-468a-938c-a71a3ac23718
caps.latest.revision: 29
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 28
---
# Proc&#233;dure pas &#224; pas&#160;: ajout de contr&#244;les &#224; un document au moment de l’ex&#233;cution dans un compl&#233;ment VSTO
  Vous pouvez ajouter des contrôles à un document Microsoft Office Word ouvert en utilisant un complément VSTO. Cette procédure pas à pas montre comment utiliser le ruban pour permettre aux utilisateurs d’ajouter un <xref:Microsoft.Office.Tools.Word.Controls.Button> ou un <xref:Microsoft.Office.Tools.Word.RichTextContentControl> à un document.  
  
 **S’applique à :** les informations contenues dans cette rubrique s’appliquent aux projets de compléments VSTO pour Word 2010. Pour plus d'informations, consultez [Fonctionnalités disponibles par type d'application et de projet Office](../vsto/features-available-by-office-application-and-project-type.md).  
  
 Cette procédure pas à pas décrit les tâches suivantes :  
  
-   Création d’un projet de complément VSTO Word.  
  
-   Mise à disposition d’une interface utilisateur permettant d’ajouter des contrôles au document.  
  
-   Ajout de contrôles au document au moment de l’exécution.  
  
-   Suppression de contrôles dans le document.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Composants requis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] ou [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].  
  
## Création d’un projet de complément Word  
 Commencez par créer un projet de complément VSTO Word.  
  
#### Pour créer un projet de complément VSTO Word  
  
1.  Créez un projet de complément VSTO pour Word nommé **WordDynamicControls**. Pour plus d'informations, consultez [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  Ajoutez une référence à l’assembly **Microsoft.Office.Tools.Word.v4.0.Utilities.dll**. Cette référence est obligatoire pour ajouter par programmation un contrôle Windows Forms au document, plus loin dans cette procédure pas à pas.  
  
## Mise à disposition d’une interface utilisateur permettant d’ajouter des contrôles à un document  
 Ajoutez un onglet personnalisé au ruban dans Word. Les utilisateurs peuvent cocher des cases sous l’onglet pour ajouter des contrôles à un document.  
  
#### Pour fournir une interface utilisateur permettant d’ajouter des contrôles à un document  
  
1.  Dans le menu **Projet**, cliquez sur **Ajouter un nouvel élément**.  
  
2.  Dans la boîte de dialogue **Ajouter un nouvel élément**, sélectionnez **Ruban \(Concepteur visuel\)**.  
  
3.  Remplacez le nom du nouveau ruban par **MyRibbon**, puis cliquez sur **Ajouter**.  
  
     Le fichier **MyRibbon.cs** ou **MyRibbon.vb** s'ouvre dans le Concepteur de ruban et affiche un onglet et un groupe par défaut.  
  
4.  Dans le Concepteur de ruban, cliquez sur le groupe **group1**.  
  
5.  Dans la fenêtre **Propriétés**, affectez **Ajouter des contrôles** comme propriété **Étiquette** de **group1**.  
  
6.  Sous l’onglet **Contrôles de ruban Office** de la **Boîte à outils**, faites glisser un contrôle **CheckBox** sur **group1**.  
  
7.  Cliquez sur **CheckBox1** pour le sélectionner.  
  
8.  Dans la fenêtre **Propriétés**, changez les propriétés suivantes.  
  
    |Propriété|Valeur|  
    |---------------|------------|  
    |**Nom**|**addButtonCheckBox**|  
    |**Étiquette**|**Bouton Ajouter**|  
  
9. Ajoutez une deuxième case à cocher pour **group1**, puis modifiez les propriétés suivantes.  
  
    |Propriété|Valeur|  
    |---------------|------------|  
    |**Nom**|**addRichTextCheckBox**|  
    |**Étiquette**|**Ajouter un contrôle de texte enrichi**|  
  
10. Dans le Concepteur de ruban, double\-cliquez sur **Bouton Ajouter**.  
  
     Le gestionnaire d’événements <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click> de la case à cocher **Bouton Ajouter** s’ouvre dans l’éditeur de code.  
  
11. Revenez au Concepteur de ruban et double\-cliquez sur **Ajouter un contrôle de texte enrichi**.  
  
     Le gestionnaire d’événements <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click> de la case à cocher **Ajouter un contrôle de texte enrichi** s’ouvre dans l’éditeur de code.  
  
 Plus loin dans cette procédure pas à pas, vous ajouterez du code à ces gestionnaires d’événements pour ajouter et supprimer des contrôles dans le document actif.  
  
## Ajout et suppression de contrôles dans le document actif  
 Dans le code de complément VSTO, vous devez convertir le document actif en *élément hôte*<xref:Microsoft.Office.Tools.Word.Document> avant de pouvoir ajouter un contrôle.  Dans les solutions Office, vous ne pouvez ajouter des contrôles managés qu’à des éléments hôtes, qui agissent comme des conteneurs pour les contrôles. Dans les projets de complément VSTO, vous pouvez créer des éléments hôtes au moment de l’exécution à l’aide de la méthode GetVstoObject.  
  
 Ajoutez des méthodes à la classe `ThisAddIn` qui peut être appelée pour ajouter ou supprimer un <xref:Microsoft.Office.Tools.Word.Controls.Button> ou <xref:Microsoft.Office.Tools.Word.RichTextContentControl> dans le document actif. Plus loin dans cette procédure, vous appellerez ces méthodes à partir des gestionnaires d’événements <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click> des cases à cocher dans le ruban.  
  
#### Pour ajouter et supprimer des contrôles dans le document actif  
  
1.  Dans l’**Explorateur de solutions**, double\-cliquez sur ThisAddIn.cs ou ThisAddIn.vb pour ouvrir le fichier dans l’éditeur de code.  
  
2.  Ajoutez le code suivant à la classe `ThisAddIn`. Ce code déclare des objets <xref:Microsoft.Office.Tools.Word.Controls.Button> et <xref:Microsoft.Office.Tools.Word.RichTextContentControl> qui représentent les contrôles qui seront ajoutés au document.  
  
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControlsWalkthrough/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_WordAddInDynamicControlsWalkthrough#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControlsWalkthrough/VB/ThisAddIn.vb#1)]  
  
3.  Ajoutez la méthode suivante à la classe `ThisAddIn`. Quand l’utilisateur clique sur la case à cocher **Bouton Ajouter** dans le ruban, cette méthode ajoute un <xref:Microsoft.Office.Tools.Word.Controls.Button> à la sélection actuelle dans le document si la case est cochée, ou supprime le <xref:Microsoft.Office.Tools.Word.Controls.Button> si la case est décochée.  
  
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControlsWalkthrough/CS/ThisAddIn.cs#2)]
     [!code-vb[Trin_WordAddInDynamicControlsWalkthrough#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControlsWalkthrough/VB/ThisAddIn.vb#2)]  
  
4.  Ajoutez la méthode suivante à la classe `ThisAddIn`. Quand l’utilisateur clique sur la case à cocher **Ajouter un contrôle de texte enrichi** dans le ruban, cette méthode ajoute un <xref:Microsoft.Office.Tools.Word.RichTextContentControl> à la sélection actuelle dans le document si la case est cochée, ou supprime le <xref:Microsoft.Office.Tools.Word.RichTextContentControl> si la case est décochée.  
  
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControlsWalkthrough/CS/ThisAddIn.cs#3)]
     [!code-vb[Trin_WordAddInDynamicControlsWalkthrough#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControlsWalkthrough/VB/ThisAddIn.vb#3)]  
  
## Suppression du contrôle Button quand le document est enregistré  
 Les contrôles Windows Forms ne sont pas conservés lorsque le document est enregistré puis fermé. Toutefois, un wrapper ActiveX pour chaque contrôle reste dans le document, et la bordure de ce wrapper est visible par les utilisateurs finaux quand le document est rouvert. Il existe plusieurs façons de nettoyer des contrôles Windows Forms créés de manière dynamique dans des compléments VSTO. Lors de cette procédure pas à pas, vous allez supprimer par programmation le contrôle <xref:Microsoft.Office.Tools.Word.Controls.Button> quand le document est enregistré.  
  
#### Pour supprimer le contrôle Button quand le document est enregistré  
  
1.  Dans le fichier de code ThisAddIn.cs ou ThisAddIn.vb, ajoutez la méthode suivante à la classe `ThisAddIn`. Cette méthode est un gestionnaire d’événements pour l’événement <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave>. Si le document enregistré a un élément hôte <xref:Microsoft.Office.Tools.Word.Document> qui lui est associé, le gestionnaire d’événements obtient l’élément hôte et supprime le contrôle <xref:Microsoft.Office.Tools.Word.Controls.Button>, s’il existe.  
  
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControlsWalkthrough/CS/ThisAddIn.cs#4)]
     [!code-vb[Trin_WordAddInDynamicControlsWalkthrough#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControlsWalkthrough/VB/ThisAddIn.vb#4)]  
  
2.  En C\#, ajoutez le code suivant au gestionnaire d’événements `ThisAddIn_Startup`. Ce code est nécessaire en C\# pour connecter le gestionnaire d’événements `Application_DocumentBeforeSave` à l’événement <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave>.  
  
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControlsWalkthrough/CS/ThisAddIn.cs#5)]  
  
## Ajout et suppression de contrôles quand l’utilisateur clique sur les cases à cocher dans le ruban  
 Pour finir, modifiez les gestionnaires d’événements <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click> des cases à cocher que vous avez ajoutées au ruban pour ajouter ou supprimer des contrôles dans le document.  
  
#### Pour ajouter ou supprimer des contrôles quand l’utilisateur clique sur les cases à cocher dans le ruban  
  
1.  Dans le fichier de code MyRibbon.cs ou MyRibbon.vb, remplacez les gestionnaires d’événements `addButtonCheckBox_Click` et `addRichTextCheckBox_Click` générés par le code suivant. Ce code redéfinit ces gestionnaires d’événements pour appeler les méthodes `ToggleButtonOnDocument` et `ToggleRichTextControlOnDocument` que vous avez ajoutées à la classe `ThisAddIn` plus tôt lors de cette procédure pas à pas.  
  
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControlsWalkthrough/CS/MyRibbon.cs#6)]
     [!code-vb[Trin_WordAddInDynamicControlsWalkthrough#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControlsWalkthrough/VB/MyRibbon.vb#6)]  
  
## Test de la solution  
 Ajoutez des contrôles à un document en les sélectionnant à partir de l’onglet personnalisé dans le ruban. Quand vous enregistrez le document, le contrôle <xref:Microsoft.Office.Tools.Word.Controls.Button> est supprimé.  
  
#### Pour tester la solution.  
  
1.  Appuyez sur F5 pour exécuter votre projet.  
  
2.  Dans le document actif, appuyez plusieurs fois sur Entrée pour ajouter de nouveaux paragraphes vides au document.  
  
3.  Sélectionnez le premier paragraphe.  
  
4.  Cliquez sur l'onglet **Compléments**.  
  
5.  Dans le groupe **Ajouter des contrôles**, cliquez sur **Bouton Ajouter**.  
  
     Un bouton apparaît dans le premier paragraphe.  
  
6.  Sélectionnez le dernier paragraphe.  
  
7.  Dans le groupe **Ajouter des contrôles**, cliquez sur **Ajouter un contrôle de texte enrichi**.  
  
     Un contrôle de contenu de texte enrichi est ajouté au dernier paragraphe.  
  
8.  Enregistrez le document.  
  
     Le bouton est supprimé du document.  
  
## Étapes suivantes  
 Pour en savoir plus sur les contrôles dans les compléments VSTO, consultez les rubriques suivantes :  
  
-   Pour obtenir un exemple qui montre comment ajouter de nombreux autres types de contrôles à un document au moment de l’exécution et comment recréer les contrôles quand le document est rouvert, consultez l’exemple de contrôles dynamiques de complément Word disponible à l’adresse [Exemples et procédures pas à pas relatifs au développement Office](../vsto/office-development-samples-and-walkthroughs.md).  
  
-   Pour obtenir une procédure pas à pas qui montre comment ajouter des contrôles à une feuille de calcul à l’aide d’un complément VSTO pour Excel, consultez [Procédure pas à pas : ajout de contrôles à une feuille de calcul au moment de l'exécution dans un projet de complément VSTO](../vsto/walkthrough-adding-controls-to-a-worksheet-at-run-time-in-vsto-add-in-project.md).  
  
## Voir aussi  
 [Solutions Word](../vsto/word-solutions.md)   
 [Ajout de contrôles à des documents Office au moment de l'exécution](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Rendre des contrôles dynamiques persistants dans des documents Office](../vsto/persisting-dynamic-controls-in-office-documents.md)   
 [Comment : ajouter des contrôles Windows Forms à des documents Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [Comment : ajouter des contrôles de contenu à des documents Word](../vsto/how-to-add-content-controls-to-word-documents.md)   
 [Extension de documents Word et de classeurs Excel dans des compléments VSTO au moment de l'exécution](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)  
  
  