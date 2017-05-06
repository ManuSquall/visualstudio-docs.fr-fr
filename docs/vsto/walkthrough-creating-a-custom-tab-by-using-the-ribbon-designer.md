---
title: "Proc&#233;dure pas &#224; pas&#160;: cr&#233;ation d&#39;un onglet personnalis&#233; &#224; l&#39;aide du Concepteur de ruban"
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
  - "volets Actions (développement Office dans Visual Studio), contrôler à partir du ruban"
  - "ruban personnalisé, onglets"
  - "Personnalisé (onglet) (développement Office dans Visual Studio)"
  - "personnaliser le ruban, onglets"
  - "ruban (développement Office dans Visual Studio), personnaliser"
  - "Concepteur de ruban (développement Office dans Visual Studio)"
ms.assetid: 312865e6-950f-46ab-88de-fe7eb8036bfe
caps.latest.revision: 68
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 67
---
# Proc&#233;dure pas &#224; pas&#160;: cr&#233;ation d&#39;un onglet personnalis&#233; &#224; l&#39;aide du Concepteur de ruban
  Le Concepteur de ruban vous permet de créer un onglet personnalisé puis d'ajouter et de positionner des contrôles dessus.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 Cette procédure pas à pas décrit les tâches suivantes :  
  
-   [Création de volets Actions](#BKMK_CreateActionsPanes).  
  
-   [Création d'un onglet personnalisé](#BKMK_CreateCustomTab).  
  
-   [Masquage et affichage de volets Actions à l'aide de boutons sur l'onglet personnalisé](#BKMK_HideShowActionsPane).  
  
> [!NOTE]  
>  Il est possible que pour certains des éléments de l'interface utilisateur de Visual Studio, votre ordinateur affiche des noms ou des emplacements différents de ceux indiqués dans les instructions suivantes.  L'édition de Visual Studio dont vous disposez et les paramètres que vous utilisez déterminent ces éléments.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Composants requis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Excel  
  
## Création d'un projet de classeur Excel  
 Les étapes pour utiliser le Concepteur de ruban sont presque identiques pour toutes les applications Office.  Cet exemple utilise un classeur Excel.  
  
#### Pour créer un projet de classeur Excel  
  
-   Créez un projet de classeur Excel et attribuez\-lui le nom MyExcelRibbon.  Pour plus d'informations, consultez [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio ouvre le nouveau classeur Excel dans le concepteur et ajoute le projet **MyExcelRibbon** à l'**Explorateur de solutions**.  
  
##  <a name="BKMK_CreateActionsPanes"></a> Création de volets Actions  
 Ajoutez deux volets Actions personnalisés au projet.  Vous ajouterez ultérieurement à l'onglet personnalisé des boutons qui affichent et masquent ces volets Actions.  
  
#### Pour créer des volets Actions  
  
1.  Dans le menu **Projet**, choisissez **Ajouter un nouvel élément**.  
  
2.  Dans la boîte de dialogue **Ajouter un nouvel élément**, sélectionnez **ActionsPaneControl**, puis choisissez **Ajouter**.  
  
     Le fichier **ActionsPaneControl1.cs** ou **ActionsPaneControl1.vb** s'ouvre dans le concepteur.  
  
3.  Dans l'onglet **Contrôles communs** de la **Boîte à outils**, ajoutez une étiquette à l'aire du Concepteur.  
  
4.  Dans la fenêtre **Propriétés**, affectez à la propriété **Text** de label1 la valeur Volet Actions 1.  
  
5.  Répétez les étapes 1 à 5 pour créer un deuxième volet Actions et une deuxième étiquette.  Affectez à la propriété **Text** de la deuxième étiquette la valeur Volet Actions 2.  
  
##  <a name="BKMK_CreateCustomTab"></a> Création d'un onglet personnalisé  
 L'une des règles de conception d'une application Office stipule que les utilisateurs doivent toujours avoir le contrôle de l'interface utilisateur de l'application Office.  Pour ajouter cette fonction pour les volets Actions, vous pouvez ajouter des boutons qui affichent et masquent chaque volet Actions à partir d'un onglet personnalisé sur le ruban.  Pour créer un onglet personnalisé, ajoutez un élément **Ruban \(Concepteur visuel\)** au projet.  Le concepteur vous permet d'ajouter et de position des contrôles, de définir les propriétés des contrôles et de gérer les événements de contrôle.  
  
#### Pour créer un onglet personnalisé  
  
1.  Dans le menu **Projet**, choisissez **Ajouter un nouvel élément**.  
  
2.  Dans la boîte de dialogue **Ajouter un nouvel élément**, sélectionnez **Ruban \(Concepteur visuel\)**.  
  
3.  Remplacez le nom du nouveau ruban par **MyRibbon**, puis sélectionnez **Ajouter**.  
  
     Le fichier **MyRibbon.cs** ou **MyRibbon.vb** s'ouvre dans le Concepteur de ruban et affiche un onglet et un groupe par défaut.  
  
4.  Dans le Concepteur de ruban, choisissez l'onglet par défaut.  
  
5.  Dans la fenêtre **Propriétés**, développez la propriété **ControlId**, puis affectez à la propriété **ControlIdType** la valeur **Personnalisé**.  
  
6.  Attribuez à la propriété **Label** la valeur Mon onglet personnalisé.  
  
7.  Dans le Concepteur de ruban, choisissez **group1**.  
  
8.  Dans la fenêtre **Propriétés**, définissez **Label** avec la valeur Gestionnaire de volets Actions.  
  
9. Dans l'onglet **Contrôles de ruban Office** de la **Boîte à outils**, faites glisser un bouton sur **group1**.  
  
10. Sélectionnez **button1**.  
  
11. Dans la fenêtre **Propriétés**, définissez **Label** avec la valeur Afficher volet Actions 1.  
  
12. Ajoutez un deuxième bouton à **group1** et affectez à la propriété **Label** la valeur Afficher volet Actions 2.  
  
13. Dans l'onglet **Contrôles de ruban Office** de la **Boîte à outils**, faites glisser un contrôle **ToggleButton** sur **group1**.  
  
14. Affectez à la propriété **Label** la valeur Masquer volet Actions.  
  
##  <a name="BKMK_HideShowActionsPane"></a> Masquage et affichage de volets Actions à l'aide de boutons sur l'onglet personnalisé  
 La dernière étape consiste à ajouter le code qui répond à l'utilisateur.  Ajoutez les gestionnaires d'événements pour les événements <xref:Microsoft.Office.Tools.Ribbon.RibbonButton.Click> des deux boutons et l'événement <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> du bouton bascule.  Ajoutez le code aux gestionnaires d'événements pour permettre de masquer et d'afficher les volets Actions.  
  
#### Pour masquer et afficher des volets Actions à l'aide de boutons dans l'onglet personnalisé  
  
1.  Dans l'**Explorateur de solutions**, ouvrez le menu contextuel de MyRibbon.cs ou MyRibbon.vb, puis choisissez **Afficher le Code**.  
  
2.  Ajoutez le code suivant en haut de la classe `MyRibbon`.  Ce code crée deux objets du volet Actions.  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Custom_Tab/CS/MyRibbon.cs#1)]
     [!code-vb[Trin_Ribbon_Custom_Tab#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Custom_Tab/VB/MyRibbon.vb#1)]  
  
3.  Remplacez la méthode `MyRibbon_Load` par le code suivant.  Ce code ajoute les objets du volet Actions à la collection <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> et masque les objets.  Le code Visual C\# attache également les délégués à plusieurs événements de contrôle du ruban.  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Custom_Tab/CS/MyRibbon.cs#2)]
     [!code-vb[Trin_Ribbon_Custom_Tab#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Custom_Tab/VB/MyRibbon.vb#2)]  
  
4.  Ajoutez les trois méthodes de gestionnaire d'événements suivantes à la classe `MyRibbon`.  Ces méthodes gèrent les événements <xref:Microsoft.Office.Tools.Ribbon.RibbonButton.Click> des deux boutons et l'événement <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> du bouton bascule.  Les gestionnaires d'événements pour button1 et button2 affichent d'autres volets Actions.  Le gestionnaire d'événements pour toggleButton1 affiche et masque le volet Actions actif.  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Custom_Tab/CS/MyRibbon.cs#3)]
     [!code-vb[Trin_Ribbon_Custom_Tab#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Custom_Tab/VB/MyRibbon.vb#3)]  
  
## Test de l'onglet personnalisé  
 Lorsque vous exécutez le projet, Excel démarre et l'onglet **Mon onglet personnalisé** apparaît sur le ruban.  Sélectionnez les boutons de **Mon onglet personnalisé** pour afficher et masquer les volets Actions.  
  
#### Pour tester l'onglet personnalisé  
  
1.  Appuyez sur F5 pour exécuter votre projet.  
  
2.  Choisissez l'onglet **Mon onglet personnalisé**.  
  
3.  Dans le groupe **Gestionnaire de volets Actions personnalisées**, choisissez **Afficher volet Actions 1**.  
  
     Le volet Actions apparaît et affiche l'étiquette Volet Actions 1.  
  
4.  Sélectionnez **Afficher le volet Actions 2**.  
  
     Le volet Actions apparaît et affiche l'étiquette Volet Actions 2.  
  
5.  Sélectionnez **Masquer le volet Actions**.  
  
     Les volets Actions ne sont plus visibles.  
  
## Étapes suivantes  
 Pour plus d'informations sur la personnalisation de l'interface utilisateur d'Office, consultez les rubriques suivantes :  
  
-   Ajouter une interface utilisateur contextuelle à une personnalisation au niveau du document.  Pour plus d'informations, consultez [Vue d'ensemble du volet Actions](../vsto/actions-pane-overview.md).  
  
-   Étendre un formulaire Microsoft Office standard ou personnalisé.  Pour plus d'informations, consultez [Procédure pas à pas : conception d'une zone de formulaire Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md).  
  
## Voir aussi  
 [Accès au ruban au moment de l'exécution](../vsto/accessing-the-ribbon-at-run-time.md)   
 [Vue d'ensemble du ruban](../vsto/ribbon-overview.md)   
 [Concepteur de ruban](../vsto/ribbon-designer.md)   
 [Personnalisation d'un ruban pour Outlook](../vsto/customizing-a-ribbon-for-outlook.md)   
 [Comment : démarrer avec la personnalisation du ruban](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [Comment : modifier la position d'un onglet dans le ruban](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)   
 [Comment : personnaliser un onglet intégré](../vsto/how-to-customize-a-built-in-tab.md)   
 [Comment : ajouter des contrôles au mode Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)   
 [Vue d'ensemble du modèle objet de ruban](../vsto/ribbon-object-model-overview.md)  
  
  