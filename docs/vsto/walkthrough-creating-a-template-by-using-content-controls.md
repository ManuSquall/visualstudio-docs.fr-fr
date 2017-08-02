---
title: "Proc&#233;dure pas &#224; pas&#160;: cr&#233;ation d&#39;un mod&#232;le &#224; l&#39;aide de contr&#244;les de contenu"
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
  - "blocs de construction (développement Office dans Visual Studio)"
  - "contrôles de contenu (développement Office dans Visual Studio), ajouter à des documents"
  - "Word (développement Office dans Visual Studio), créer des documents"
ms.assetid: 88fb9a60-dcc3-4a5f-a8c9-7aff01ca4b4b
caps.latest.revision: 46
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 42
---
# Proc&#233;dure pas &#224; pas&#160;: cr&#233;ation d&#39;un mod&#232;le &#224; l&#39;aide de contr&#244;les de contenu
  Cette procédure pas à pas montre comment créer une personnalisation au niveau du document qui utilise des contrôles de contenu pour créer un contenu structuré et réutilisable dans un modèle Microsoft Office Word.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Word vous permet de créer une collection de parties de document réutilisables, nommées *blocs de construction*.  Cette procédure pas à pas montre comment créer deux tableaux en tant que blocs de construction.  Chaque tableau contient plusieurs contrôles de contenu qui peuvent contenir différents types de contenu, tels que du texte brut ou des dates.  L'un des tableaux contient des informations sur un employé, et l'autre contient des commentaires des clients.  
  
 Après avoir créé un document à partir du modèle, vous pouvez ajouter l'un de ces tableaux dans le document en utilisant plusieurs objets <xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl> qui affichent les blocs de construction disponibles dans le modèle.  
  
 Cette procédure pas à pas décrit les tâches suivantes :  
  
-   Création de tableaux contenant des contrôles de contenu dans un modèle Word au moment du design  
  
-   Remplissage par programmation d'un contrôle de contenu de type zone de liste modifiable et d'un contrôle de contenu de type liste déroulante  
  
-   Protection d'un tableau spécifié contre toute modification  
  
-   Ajout de tableaux à la collection de blocs de construction d'un modèle  
  
-   Création d'un contrôle de contenu affichant les blocs de construction disponibles dans le modèle  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Composants requis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Word.  
  
## Création d'un projet de modèle Word  
 Créez un modèle Word pour que les utilisateurs puissent créer aisément leurs propres copies.  
  
#### Pour créer un projet de modèle Word  
  
1.  Créez un projet de modèle Word avec le nom MonModèleDeBlocDeConstruction.  Dans l'Assistant, créez un nouveau document dans la solution.  Pour plus d'informations, consultez [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ouvre le nouveau modèle Word dans le concepteur et ajoute le projet **MonModèleDeBlocDeConstruction** à l'**Explorateur de solutions**.  
  
## Création du tableau Employé  
 Créez un tableau contenant quatre types différents de contrôles de contenu, dans lequel l'utilisateur peut entrer des informations sur un employé.  
  
#### Pour créer le tableau Employé  
  
1.  Dans le modèle Word hébergé dans le concepteur [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], dans le ruban, cliquez sur l'onglet **Insertion**.  
  
2.  Dans le groupe **Tableaux**, cliquez sur **Tableau** et insérez un tableau comportant 2 colonnes et 4 lignes.  
  
3.  Complétez la première colonne pour obtenir une colonne similaire à ceci :  
  
    ||  
    |-|  
    |Nom de l'employé|  
    |Date d'embauche|  
    |Titre|  
    |Image|  
  
4.  Cliquez dans la première cellule de la seconde colonne \(à côté de **Nom de l'employé**\).  
  
5.  Dans le ruban, cliquez sur l'onglet **Développeur**.  
  
    > [!NOTE]  
    >  Si l'onglet **Développeur** n'est pas visible, vous devez commencer par l'afficher.  Pour plus d'informations, consultez [Comment : afficher l'onglet Développeur sur le ruban](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
6.  Dans le groupe **Contrôles**, cliquez sur le bouton **Texte** ![PlainTextContentControl](~/docs/vsto/media/plaintextcontrol.gif "PlainTextContentControl") pour ajouter <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> dans la première cellule.  
  
7.  Cliquez dans la deuxième cellule de la seconde colonne \(à côté de **Date d'embauche**\).  
  
8.  Dans le groupe **Contrôles**, cliquez sur le bouton **Sélecteur de dates** ![DatePickerContentControl](~/docs/vsto/media/datepicker.gif "DatePickerContentControl") pour ajouter <xref:Microsoft.Office.Tools.Word.DatePickerContentControl> dans la deuxième cellule.  
  
9. Cliquez dans la troisième cellule de la seconde colonne \(à côté de **Titre**\).  
  
10. Dans le groupe **Contrôles**, cliquez sur le bouton **Zone de liste modifiable** ![ComboBoxContentControl](~/docs/vsto/media/combobox.gif "ComboBoxContentControl") pour ajouter <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> dans la troisième cellule.  
  
11. Cliquez dans la dernière cellule de la seconde colonne \(à côté de **Image**\).  
  
12. Dans le groupe **Contrôles**, cliquez sur le bouton **Contrôle du contenu d'image** ![PictureContentControl](~/docs/vsto/media/pictcontentcontrol.gif "PictureContentControl") pour ajouter <xref:Microsoft.Office.Tools.Word.PictureContentControl> dans la dernière cellule.  
  
## Création du tableau Commentaires des clients  
 Créez un tableau contenant trois types différents de contrôles de contenu, dans lequel l'utilisateur peut entrer des informations sur les commentaires des clients.  
  
#### Pour créer le tableau Commentaires des clients  
  
1.  Dans le modèle Word, cliquez dans la ligne située après le tableau Employé que vous avez ajouté précédemment, et appuyez sur Entrée pour ajouter un nouveau paragraphe.  
  
2.  Dans le ruban, cliquez sur l'onglet **Insertion**.  
  
3.  Dans le groupe **Tableaux**, cliquez sur **Tableau** et insérez un tableau comportant 2 colonnes et 3 lignes.  
  
4.  Complétez la première colonne pour obtenir une colonne similaire à ceci :  
  
    ||  
    |-|  
    |Nom du client|  
    |Satisfaction|  
    |Commentaires|  
  
5.  Cliquez dans la première cellule de la seconde colonne \(à côté de **Nom du client**\).  
  
6.  Dans le ruban, cliquez sur l'onglet **Développeur**.  
  
7.  Dans le groupe **Contrôles**, cliquez sur le bouton **Texte** ![PlainTextContentControl](~/docs/vsto/media/plaintextcontrol.gif "PlainTextContentControl") pour ajouter <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> dans la première cellule.  
  
8.  Cliquez dans la deuxième cellule de la seconde colonne \(à côté de **Satisfaction**\).  
  
9. Dans le groupe **Contrôles**, cliquez sur le bouton **Liste déroulante** ![DropDownListContentControl](~/docs/vsto/media/dropdownlist.gif "DropDownListContentControl") pour ajouter <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> dans la deuxième cellule.  
  
10. Cliquez dans la dernière cellule de la seconde colonne \(à côté de **Commentaires**\).  
  
11. Dans le groupe **Contrôles**, cliquez sur le bouton **Texte enrichi** ![RichTextContentControl](~/docs/vsto/media/richtextcontrol.gif "RichTextContentControl") pour ajouter <xref:Microsoft.Office.Tools.Word.RichTextContentControl> dans la dernière cellule.  
  
## Remplissage par programmation de la zone de liste modifiable et de la liste déroulante  
 Vous pouvez initialiser les contrôles de contenu au moment du design en utilisant la fenêtre **Propriétés** de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  Vous pouvez également les initialiser au moment de l'exécution, ce qui vous permet de définir leurs états initiaux de manière dynamique.  Pour cette procédure pas à pas, utilisez du code pour renseigner les entrées des objets <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> et <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> au moment de l'exécution, pour être en mesure de voir comment ces objets fonctionnent.  
  
#### Pour modifier par programmation l'interface utilisateur des contrôles de contenu  
  
1.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur **ThisDocument.cs** ou **ThisDocument.vb**, puis cliquez sur **Afficher le code**.  
  
2.  Ajoutez le code suivant à la classe `ThisDocument`.  Ce code déclare plusieurs objets que vous utiliserez ultérieurement dans cette procédure pas à pas.  
  
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ContentControlTemplateWalkthrough/CS/ThisDocument.cs#1)]
     [!code-vb[Trin_ContentControlTemplateWalkthrough#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ContentControlTemplateWalkthrough/VB/ThisDocument.vb#1)]  
  
3.  Ajoutez le code suivant à la méthode `ThisDocument_Startup` de la classe `ThisDocument`.  Ce code ajoute des entrées aux contrôles <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> et <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> dans les tableaux, et définit le texte de l'espace réservé affiché dans chacun de ces contrôles avant que l'utilisateur les modifie.  
  
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ContentControlTemplateWalkthrough/CS/ThisDocument.cs#2)]
     [!code-vb[Trin_ContentControlTemplateWalkthrough#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ContentControlTemplateWalkthrough/VB/ThisDocument.vb#2)]  
  
## Protection du tableau Employé contre toute modification  
 Utilisez l'objet <xref:Microsoft.Office.Tools.Word.GroupContentControl> que vous avez déclaré précédemment pour protéger le tableau Employé.  Une fois le tableau protégé, les utilisateurs peuvent encore modifier les contrôles de contenu du tableau.  Toutefois, ils ne peuvent plus modifier le texte de la première colonne ni modifier le tableau d'une quelconque autre manière, par exemple en ajoutant ou en supprimant des lignes et des colonnes.  Pour plus d'informations sur la façon d'utiliser un objet <xref:Microsoft.Office.Tools.Word.GroupContentControl> pour protéger une partie d'un document, consultez [Contrôles de contenu](../vsto/content-controls.md).  
  
#### Pour empêcher les utilisateurs de modifier le tableau Employé  
  
1.  Ajoutez le code suivant à la méthode `ThisDocument_Startup` de la classe `ThisDocument`, après le code que vous avez ajouté à l'étape précédente.  Ce code empêche les utilisateurs de modifier le tableau Employé en plaçant celui\-ci dans l'objet <xref:Microsoft.Office.Tools.Word.GroupContentControl> que vous avez déclaré précédemment.  
  
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ContentControlTemplateWalkthrough/CS/ThisDocument.cs#3)]
     [!code-vb[Trin_ContentControlTemplateWalkthrough#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ContentControlTemplateWalkthrough/VB/ThisDocument.vb#3)]  
  
## Ajout des tableaux à la collection de blocs de construction  
 Ajoutez les tableaux à une collection de blocs de construction de document dans le modèle afin que les utilisateurs puissent insérer les tableaux que vous avez créés dans le document.  Pour plus d'informations sur les blocs de construction de document, consultez [Contrôles de contenu](../vsto/content-controls.md).  
  
#### Pour ajouter les tableaux aux blocs de construction du modèle  
  
1.  Ajoutez le code suivant à la méthode `ThisDocument_Startup` de la classe `ThisDocument`, après le code que vous avez ajouté à l'étape précédente.  Ce code ajoute de nouveaux blocs de construction contenant les tableaux à la collection Microsoft.Office.Interop.Word.BuildingBlockEntries qui contient tous les blocs de construction réutilisables du modèle.  Les nouveaux blocs de construction sont définis dans une nouvelle catégorie nommée **Informations employé et client**, à laquelle le type de bloc de construction Microsoft.Office.Interop.Word.WdBuildingBlockTypes.wdTypeCustom1 est affecté.  
  
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ContentControlTemplateWalkthrough/CS/ThisDocument.cs#4)]
     [!code-vb[Trin_ContentControlTemplateWalkthrough#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ContentControlTemplateWalkthrough/VB/ThisDocument.vb#4)]  
  
2.  Ajoutez le code suivant à la méthode `ThisDocument_Startup` de la classe `ThisDocument`, après le code que vous avez ajouté à l'étape précédente.  Ce code supprime les tableaux dans le modèle.  Ces tableaux ne sont plus nécessaires car vous les avez ajoutés à la galerie des blocs de construction réutilisables du modèle.  Le code place en premier lieu le document en mode Création pour permettre la suppression du tableau protégé Employé.  
  
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ContentControlTemplateWalkthrough/CS/ThisDocument.cs#5)]
     [!code-vb[Trin_ContentControlTemplateWalkthrough#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ContentControlTemplateWalkthrough/VB/ThisDocument.vb#5)]  
  
## Création d'un contrôle de contenu affichant les blocs de construction  
 Créez un contrôle de contenu permettant d'accéder aux blocs de construction \(autrement dit, aux tableaux\) que vous avez créés précédemment.  Les utilisateurs peuvent cliquer sur ce contrôle pour ajouter les tableaux dans le document.  
  
#### Pour créer un contrôle de contenu affichant les blocs de construction  
  
1.  Ajoutez le code suivant à la méthode `ThisDocument_Startup` de la classe `ThisDocument`, après le code que vous avez ajouté à l'étape précédente.  Ce code initialise l'objet <xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl> déclaré précédemment.  L'objet <xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl> affiche tous les blocs de construction définis dans la catégorie **Informations employé et client**, à laquelle le type de bloc de construction Microsoft.Office.Interop.Word.WdBuildingBlockTypes.wdTypeCustom1 est affecté.  
  
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ContentControlTemplateWalkthrough/CS/ThisDocument.cs#6)]
     [!code-vb[Trin_ContentControlTemplateWalkthrough#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ContentControlTemplateWalkthrough/VB/ThisDocument.vb#6)]  
  
## Test du projet  
 Les utilisateurs peuvent cliquer sur les contrôles de la galerie des blocs de construction du document pour insérer le tableau Employé ou le tableau Commentaires des clients.  Ils peuvent taper ou sélectionner des réponses dans les contrôles de contenu des deux tableaux.  Ils peuvent aussi modifier d'autres parties du tableau Commentaires des clients, mais ils ne doivent pas pouvoir modifier d'autres parties du tableau Employé.  
  
#### Pour tester le tableau Employé  
  
1.  Appuyez sur F5 pour exécuter le projet.  
  
2.  Cliquez sur **Choisir votre premier bloc de construction** pour afficher le premier contrôle de contenu de la galerie des blocs de construction.  
  
3.  Cliquez sur la flèche déroulante à côté du titre **Galerie 1 personnalisée** dans le contrôle et sélectionnez **Tableau Employé**.  
  
4.  Cliquez dans la cellule située à droite de la cellule Nom de l'employé et tapez un nom.  
  
     Vérifiez que vous pouvez ajouter uniquement du texte dans cette cellule.  Le contrôle <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> permet aux utilisateurs d'ajouter du texte uniquement, pas d'autres types de contenu tels que des illustrations ou des tableaux.  
  
5.  Cliquez dans la cellule située à droite de la cellule Date d'embauche et sélectionnez une date dans le sélecteur de dates.  
  
6.  Cliquez dans la cellule située à droite de la cellule Titre et sélectionnez l'une des fonctions proposées dans la zone de liste modifiable.  
  
     Si vous le souhaitez, tapez le nom d'une fonction qui ne figure pas dans la liste.  Cela est possible car le contrôle <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> permet aux utilisateurs d'effectuer un choix dans une liste d'entrées ou de taper leurs propres entrées.  
  
7.  Cliquez sur l'icône dans la cellule située à droite de la cellule Image et recherchez une image pour l'afficher.  
  
8.  Essayez d'ajouter et de supprimer des lignes et des colonnes dans le tableau.  Vérifiez que vous ne pouvez pas modifier le tableau.  L'objet <xref:Microsoft.Office.Tools.Word.GroupContentControl> vous empêche d'apporter la moindre modification.  
  
#### Pour tester le tableau Commentaires des clients  
  
1.  Cliquez sur **Choisir votre deuxième bloc de construction** pour afficher le deuxième contrôle de contenu de la galerie des blocs de construction.  
  
2.  Cliquez sur la flèche déroulante à côté du titre **Galerie 1 personnalisée** dans le contrôle et sélectionnez **Tableau Clients**.  
  
3.  Cliquez dans la cellule située à droite de la cellule Nom du client et tapez un nom.  
  
4.  Cliquez dans la cellule située à droite de la cellule Satisfaction et sélectionnez l'une des options disponibles.  
  
     Vérifiez que vous ne pouvez pas taper votre propre entrée.  L'objet <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> permet uniquement aux utilisateurs d'effectuer un choix dans une liste d'entrées.  
  
5.  Cliquez dans la cellule située à droite de la cellule Commentaires et tapez des commentaires.  
  
     Si vous le souhaitez, ajoutez du contenu autre que du texte, comme une illustration ou un tableau incorporé.  Cela est possible car l'objet <xref:Microsoft.Office.Tools.Word.RichTextContentControl> permet aux utilisateurs d'ajouter du contenu autre que du texte.  
  
6.  Vérifiez que vous pouvez ajouter et supprimer des lignes et des colonnes dans le tableau.  Cela est possible parce que vous n'avez pas protégé le tableau en le plaçant dans un objet <xref:Microsoft.Office.Tools.Word.GroupContentControl>.  
  
7.  Fermez le modèle.  
  
## Étapes suivantes  
 Pour plus d'informations sur l'utilisation des contrôles de contenu, consultez la rubrique suivante :  
  
-   Lier des contrôles de contenu à des fragments XML, ou parties XML personnalisées, qui sont incorporés dans un document.  Pour plus d'informations, consultez [Procédure pas à pas : liaison de contrôles de contenu à des parties XML personnalisées](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md).  
  
## Voir aussi  
 [Automatisation de Word à l'aide d'objets étendus](../vsto/automating-word-by-using-extended-objects.md)   
 [Contrôles de contenu](../vsto/content-controls.md)   
 [Comment : ajouter des contrôles de contenu à des documents Word](../vsto/how-to-add-content-controls-to-word-documents.md)   
 [Comment : protéger des parties de documents à l'aide de contrôles de contenu](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md)   
 [Vue d'ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)   
 [Limitations de programmation des éléments hôtes et des contrôles hôtes](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Ajout de contrôles à des documents Office au moment de l'exécution](../vsto/adding-controls-to-office-documents-at-run-time.md)  
  
  