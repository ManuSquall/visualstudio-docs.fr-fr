---
title: 'Procédure pas à pas : Créer un onglet personnalisé à l’aide du Concepteur de ruban'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- actions panes [Office development in Visual Studio], controlling from Ribbon
- Ribbon [Office development in Visual Studio], customizing
- Ribbon Designer [Office development in Visual Studio]
- customizing the Ribbon, tabs
- custom Ribbon, tabs
- Custom tab [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 30d05c39c9216385d4255055c5d660f79b529ab6
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2019
ms.locfileid: "54876094"
---
# <a name="walkthrough-create-a-custom-tab-by-using-the-ribbon-designer"></a>Procédure pas à pas : Créer un onglet personnalisé à l’aide du Concepteur de ruban
  Le Concepteur de ruban vous permet de créer un onglet personnalisé puis d'ajouter et de positionner des contrôles dessus.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 Cette procédure pas à pas décrit les tâches suivantes :  
  
-   [Créer des volets actions](#BKMK_CreateActionsPanes).  
  
-   [Créer un onglet personnalisé](#BKMK_CreateCustomTab).  
  
-   [Afficher et masquer les volets actions à l’aide des boutons sur l’onglet personnalisé](#BKMK_HideShowActionsPane).  
  
> [!NOTE]  
>  Il est possible que pour certains des éléments de l’interface utilisateur de Visual Studio, votre ordinateur affiche des noms ou des emplacements différents de ceux indiqués dans les instructions suivantes. L’édition de Visual Studio dont vous disposez et les paramètres que vous utilisez déterminent ces éléments. Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Prérequis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Excel  
  
## <a name="create-an-excel-workbook-project"></a>Créez un projet de classeur Excel  
 Les étapes pour utiliser le Concepteur de ruban sont presque identiques pour toutes les applications Office. Cet exemple utilise un classeur Excel.  
  
### <a name="to-create-an-excel-workbook-project"></a>Pour créer un projet de classeur Excel  
  
-   Créer un projet de classeur Excel portant le nom **MyExcelRibbon**. Pour plus d'informations, voir [Procédure : Créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio ouvre le nouveau classeur dans le concepteur et ajoute le **MyExcelRibbon** projet **l’Explorateur de solutions**.  
  
##  <a name="BKMK_CreateActionsPanes"></a> Créer des volets actions  
 Ajoutez deux volets Actions personnalisés au projet. Vous ajouterez ultérieurement à l'onglet personnalisé des boutons qui affichent et masquent ces volets Actions.  
  
### <a name="to-create-actions-panes"></a>Pour créer des volets Actions  
  
1.  Dans le menu **Projet** , choisissez **Ajouter un nouvel élément**.  
  
2.  Dans le **ajouter un nouvel élément** boîte de dialogue, sélectionnez **ActionsPaneControl**, puis choisissez **ajouter**.  
  
     Le **ActionsPaneControl1.cs** ou **ActionsPaneControl1.vb** fichier s’ouvre dans le concepteur.  
  
3.  À partir de la **contrôles communs** onglet de la **boîte à outils**, ajoutez une étiquette à l’aire du concepteur.  
  
4.  Dans le **propriétés** fenêtre, définissez la **texte** propriété de label1 la valeur **volet Actions 1**.  
  
5.  Répétez les étapes 1 à 5 pour créer un deuxième volet Actions et une deuxième étiquette. Définir le **texte** propriété de la deuxième contrôle label **volet Actions 2**.  
  
##  <a name="BKMK_CreateCustomTab"></a> Créer un onglet personnalisé  
 L'une des règles de conception d'une application Office stipule que les utilisateurs doivent toujours avoir le contrôle de l'interface utilisateur de l'application Office. Pour ajouter cette fonction pour les volets Actions, vous pouvez ajouter des boutons qui affichent et masquent chaque volet Actions à partir d'un onglet personnalisé sur le ruban. Pour créer un onglet personnalisé, ajoutez un **ruban (Concepteur visuel)** élément au projet. Le concepteur vous permet d'ajouter et de position des contrôles, de définir les propriétés des contrôles et de gérer les événements de contrôle.  
  
### <a name="to-create-a-custom-tab"></a>Pour créer un onglet personnalisé  
  
1.  Dans le menu **Projet** , choisissez **Ajouter un nouvel élément**.  
  
2.  Dans la boîte de dialogue **Ajouter un nouvel élément** , sélectionnez **Ruban (Concepteur visuel)**.  
  
3.  Modifier le nom du nouveau ruban par **MyRibbon**, puis choisissez **ajouter**.  
  
     Le fichier **MyRibbon.cs** ou **MyRibbon.vb** s'ouvre dans le Concepteur de ruban et affiche un onglet et un groupe par défaut.  
  
4.  Dans le Concepteur de ruban, choisissez l'onglet par défaut.  
  
5.  Dans le **propriétés** fenêtre, développez le **ControlId** propriété, puis définissez le **ControlIdType** propriété **personnalisé**.  
  
6.  Définir le **étiquette** propriété **Mon onglet personnalisé**.  
  
7.  Dans le Concepteur de ruban, choisissez **group1**.  
  
8.  Dans le **propriétés** fenêtre, définissez **étiquette** à **Gestionnaire de volets Actions**.  
  
9. À partir de la **contrôles de ruban Office** onglet de la **boîte à outils**, faites glisser un bouton sur **group1**.  
  
10. Sélectionnez **button1**.  
  
11. Dans le **propriétés** fenêtre, définissez **étiquette** à **Afficher volet Actions 1**.  
  
12. Ajouter un deuxième bouton à **group1**et définissez le **étiquette** propriété **Afficher volet Actions 2**.  
  
13. À partir de la **contrôles de ruban Office** onglet de la **boîte à outils**, faites glisser un **ToggleButton** contrôler sur **group1**.  
  
14. Définir le **étiquette** propriété **masquer le volet Actions**.  
  
##  <a name="BKMK_HideShowActionsPane"></a> Afficher et masquer les volets actions à l’aide des boutons sur l’onglet personnalisé  
 La dernière étape consiste à ajouter le code qui répond à l'utilisateur. Ajoutez les gestionnaires d'événements pour les événements <xref:Microsoft.Office.Tools.Ribbon.RibbonButton.Click> des deux boutons et l'événement <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> du bouton bascule. Ajoutez le code aux gestionnaires d'événements pour permettre de masquer et d'afficher les volets Actions.  
  
### <a name="to-hide-and-show-actions-panes-by-using-buttons-in-the-custom-tab"></a>Pour masquer et afficher des volets Actions à l'aide de boutons dans l'onglet personnalisé  
  
1.  Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour *MyRibbon.cs* ou *MyRibbon.vb*, puis choisissez **afficher le Code**.  
  
2.  Ajoutez le code suivant en haut de la classe `MyRibbon`. Ce code crée deux objets du volet Actions.  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab#1](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab/MyRibbon.cs#1)]
     [!code-vb[Trin_Ribbon_Custom_Tab#1](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab/MyRibbon.vb#1)]  
  
3.  Remplacez la méthode `MyRibbon_Load` par le code suivant. Ce code ajoute les objets du volet Actions à la collection <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> et masque les objets. Le code Visual C# attache également les délégués à plusieurs événements de contrôle du ruban.  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab#2](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab/MyRibbon.cs#2)]
     [!code-vb[Trin_Ribbon_Custom_Tab#2](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab/MyRibbon.vb#2)]  
  
4.  Ajoutez les trois méthodes de gestionnaire d'événements suivantes à la classe `MyRibbon`. Ces méthodes gèrent les événements <xref:Microsoft.Office.Tools.Ribbon.RibbonButton.Click> des deux boutons et l'événement <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> du bouton bascule. Les gestionnaires d'événements pour button1 et button2 affichent d'autres volets Actions. Le gestionnaire d'événements pour toggleButton1 affiche et masque le volet Actions actif.  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab#3](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab/MyRibbon.cs#3)]
     [!code-vb[Trin_Ribbon_Custom_Tab#3](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab/MyRibbon.vb#3)]  
  
## <a name="test-the-custom-tab"></a>Tester l’onglet personnalisé  
 Lorsque vous exécutez le projet, Excel démarre et le **Mon onglet personnalisé** onglet apparaît sur le ruban. Sélectionnez les boutons de **Mon onglet personnalisé** pour afficher et masquer les volets actions.  
  
### <a name="to-test-the-custom-tab"></a>Pour tester l'onglet personnalisé  
  
1.  Appuyez sur **F5** pour exécuter votre projet.  
  
2.  Choisissez le **Mon onglet personnalisé** onglet.  
  
3.  Dans le **Gestionnaire de volets Actions personnalisés** de groupe, choisissez **Afficher volet Actions 1**.  
  
     Le volet actions apparaît et affiche l’étiquette **volet Actions 1**.  
  
4.  Choisissez **Afficher volet Actions 2**.  
  
     Le volet actions apparaît et affiche l’étiquette **volet Actions 2**.  
  
5.  Choisissez **Masquer volet Actions**.  
  
     Les volets Actions ne sont plus visibles.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Pour plus d'informations sur la personnalisation de l'interface utilisateur d'Office, consultez les rubriques suivantes :  
  
-   Ajouter une interface utilisateur contextuelle à une personnalisation au niveau du document. Pour plus d’informations, consultez [vue d’ensemble du volet Actions](../vsto/actions-pane-overview.md).  
  
-   Étendre un formulaire Microsoft Office standard ou personnalisé. Pour plus d’informations, consultez [Procédure pas à pas : Concevoir une zone de formulaire Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Accéder au ruban lors de l’exécution](../vsto/accessing-the-ribbon-at-run-time.md)   
 [Vue d’ensemble du ruban](../vsto/ribbon-overview.md)   
 [Concepteur de ruban](../vsto/ribbon-designer.md)   
 [Personnaliser un ruban pour Outlook](../vsto/customizing-a-ribbon-for-outlook.md)   
 [Guide pratique pour Commencer la personnalisation du ruban](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [Guide pratique pour Modifier la position d’un onglet dans le ruban](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)   
 [Guide pratique pour Personnaliser un onglet intégré](../vsto/how-to-customize-a-built-in-tab.md)   
 [Guide pratique pour Ajouter des contrôles au mode Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)   
 [Présentation du modèle objet de ruban](../vsto/ribbon-object-model-overview.md)  
