---
title: 'Procédure pas à pas : création d’un onglet personnalisé à l’aide du concepteur de ruban'
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
ms.openlocfilehash: 5a32cfc84aa9bc93761dc8b57c13651eb04031a2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "71255523"
---
# <a name="walkthrough-create-a-custom-tab-by-using-the-ribbon-designer"></a>Procédure pas à pas : création d’un onglet personnalisé à l’aide du concepteur de ruban
  Le Concepteur de ruban vous permet de créer un onglet personnalisé puis d'ajouter et de positionner des contrôles dessus.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 Cette procédure pas à pas décrit les tâches suivantes :

- [Créer des volets actions](#BKMK_CreateActionsPanes).

- [Créez un onglet personnalisé](#BKMK_CreateCustomTab).

- [Masquer et afficher les volets actions à l’aide des boutons de l’onglet personnalisé](#BKMK_HideShowActionsPane).

> [!NOTE]
> Il est possible que pour certains des éléments de l'interface utilisateur de Visual Studio, votre ordinateur affiche des noms ou des emplacements différents de ceux indiqués dans les instructions suivantes. L'édition de Visual Studio dont vous disposez et les paramètres que vous utilisez déterminent ces éléments. Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Prérequis
 Vous devez disposer des éléments suivants pour exécuter cette procédure pas à pas :

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Excel

## <a name="create-an-excel-workbook-project"></a>Créer un projet de classeur Excel
 Les étapes pour utiliser le Concepteur de ruban sont presque identiques pour toutes les applications Office. Cet exemple utilise un classeur Excel.

### <a name="to-create-an-excel-workbook-project"></a>Pour créer un projet de classeur Excel

- Créez un projet de classeur Excel portant le nom **MyExcelRibbon**. Pour plus d'informations, consultez [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio ouvre le nouveau classeur dans le concepteur et ajoute le projet **MyExcelRibbon** à **Explorateur de solutions**.

## <a name="create-actions-panes"></a><a name="BKMK_CreateActionsPanes"></a> Créer des volets actions
 Ajoutez deux volets Actions personnalisés au projet. Vous ajouterez ultérieurement à l'onglet personnalisé des boutons qui affichent et masquent ces volets Actions.

### <a name="to-create-actions-panes"></a>Pour créer des volets Actions

1. Dans le menu **Projet** , choisissez **Ajouter un nouvel élément**.

2. Dans la boîte de dialogue **Ajouter un nouvel élément** , sélectionnez **ActionsPaneControl**, puis cliquez sur **Ajouter**.

     Le fichier **ActionsPaneControl1.cs** ou **ActionsPaneControl1. vb** s’ouvre dans le concepteur.

3. À partir de l’onglet **contrôles communs** de la **boîte à outils**, ajoutez une étiquette à l’aire du concepteur.

4. Dans la fenêtre **Propriétés** , affectez à la propriété **Text** de Label1 la valeur **volet Actions 1**.

5. Répétez les étapes 1 à 5 pour créer un deuxième volet Actions et une deuxième étiquette. Affectez à la propriété **Text** de la deuxième étiquette la valeur **volet Actions 2**.

## <a name="create-a-custom-tab"></a><a name="BKMK_CreateCustomTab"></a> Créer un onglet personnalisé
 L'une des règles de conception d'une application Office stipule que les utilisateurs doivent toujours avoir le contrôle de l'interface utilisateur de l'application Office. Pour ajouter cette fonction pour les volets Actions, vous pouvez ajouter des boutons qui affichent et masquent chaque volet Actions à partir d'un onglet personnalisé sur le ruban. Pour créer un onglet personnalisé, ajoutez un élément **Ruban (concepteur visuel)** au projet. Le concepteur vous permet d'ajouter et de position des contrôles, de définir les propriétés des contrôles et de gérer les événements de contrôle.

### <a name="to-create-a-custom-tab"></a>Pour créer un onglet personnalisé

1. Dans le menu **Projet** , choisissez **Ajouter un nouvel élément**.

2. Dans la boîte de dialogue **Ajouter un nouvel élément** , sélectionnez **Ruban (Concepteur visuel)**.

3. Remplacez le nom du nouveau ruban par **MyRibbon**, puis cliquez sur **Ajouter**.

     Le fichier **MyRibbon.cs** ou **MyRibbon.vb** s'ouvre dans le Concepteur de ruban et affiche un onglet et un groupe par défaut.

4. Dans le Concepteur de ruban, choisissez l'onglet par défaut.

5. Dans la fenêtre **Propriétés** , développez la propriété **ControlID** , puis affectez à la propriété **ControlIdType** la valeur **Custom**.

6. Définissez la propriété **étiquette** sur **mon onglet personnalisé**.

7. Dans le concepteur de ruban, choisissez **Group1**.

8. Dans la fenêtre **Propriétés** , affectez à **label** la valeur **Gestionnaire de volets actions**.

9. À partir de l’onglet **contrôles de ruban Office** de la **boîte à outils**, faites glisser un bouton sur **Group1**.

10. Sélectionnez **Button1**.

11. Dans la fenêtre **Propriétés** , affectez à **label** la valeur **Afficher volet Actions 1**.

12. Ajoutez un deuxième bouton à **Group1**et affectez à la propriété **label** la valeur **Afficher volet Actions 2**.

13. À partir de l’onglet **contrôles de ruban Office** de la **boîte à outils**, faites glisser un contrôle **ToggleButton** sur **Group1**.

14. Définissez la propriété **étiquette** sur **masquer le volet Actions**.

## <a name="hide-and-show-actions-panes-by-using-buttons-on-the-custom-tab"></a><a name="BKMK_HideShowActionsPane"></a> Masquer et afficher les volets actions à l’aide des boutons de l’onglet personnalisé
 La dernière étape consiste à ajouter le code qui répond à l'utilisateur. Ajoutez les gestionnaires d'événements pour les événements <xref:Microsoft.Office.Tools.Ribbon.RibbonButton.Click> des deux boutons et l'événement <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> du bouton bascule. Ajoutez le code aux gestionnaires d'événements pour permettre de masquer et d'afficher les volets Actions.

### <a name="to-hide-and-show-actions-panes-by-using-buttons-in-the-custom-tab"></a>Pour masquer et afficher des volets Actions à l'aide de boutons dans l'onglet personnalisé

1. Dans **Explorateur de solutions**, ouvrez le menu contextuel pour *MyRibbon.cs* ou *MyRibbon. vb*, puis choisissez **afficher le code**.

2. Ajoutez le code suivant en haut de la classe `MyRibbon`. Ce code crée deux objets du volet Actions.

     [!code-csharp[Trin_Ribbon_Custom_Tab#1](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab/MyRibbon.cs#1)]
     [!code-vb[Trin_Ribbon_Custom_Tab#1](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab/MyRibbon.vb#1)]

3. Remplacez la méthode `MyRibbon_Load` par le code suivant. Ce code ajoute les objets du volet Actions à la collection <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> et masque les objets. Le code Visual C# attache également les délégués à plusieurs événements de contrôle du ruban.

     [!code-csharp[Trin_Ribbon_Custom_Tab#2](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab/MyRibbon.cs#2)]
     [!code-vb[Trin_Ribbon_Custom_Tab#2](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab/MyRibbon.vb#2)]

4. Ajoutez les trois méthodes de gestionnaire d'événements suivantes à la classe `MyRibbon`. Ces méthodes gèrent les événements <xref:Microsoft.Office.Tools.Ribbon.RibbonButton.Click> des deux boutons et l'événement <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> du bouton bascule. Les gestionnaires d'événements pour button1 et button2 affichent d'autres volets Actions. Le gestionnaire d'événements pour toggleButton1 affiche et masque le volet Actions actif.

     [!code-csharp[Trin_Ribbon_Custom_Tab#3](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab/MyRibbon.cs#3)]
     [!code-vb[Trin_Ribbon_Custom_Tab#3](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab/MyRibbon.vb#3)]

## <a name="test-the-custom-tab"></a>Tester l’onglet personnalisé
 Quand vous exécutez le projet, Excel démarre et l’onglet **mon onglet personnalisé** s’affiche sur le ruban. Choisissez les boutons de **mon onglet personnalisé** pour afficher et masquer les volets actions.

### <a name="to-test-the-custom-tab"></a>Pour tester l'onglet personnalisé

1. Appuyez sur **F5** pour exécuter votre projet.

2. Choisissez l’onglet **mon onglet personnalisé** .

3. Dans le groupe **Gestionnaire de volets actions personnalisées** , choisissez **afficher le volet Actions 1**.

     Le volet Actions apparaît et affiche l’étiquette **volet Actions 1**.

4. Choisissez **afficher le volet Actions 2**.

     Le volet Actions apparaît et affiche l’étiquette **volet Actions 2**.

5. Choisissez **masquer le volet Actions**.

     Les volets Actions ne sont plus visibles.

## <a name="next-steps"></a>Étapes suivantes
 Pour plus d'informations sur la personnalisation de l'interface utilisateur d'Office, consultez les rubriques suivantes :

- Ajouter une interface utilisateur contextuelle à une personnalisation au niveau du document. Pour plus d’informations, consultez [vue d’ensemble du volet Actions](../vsto/actions-pane-overview.md).

- Étendre un formulaire Microsoft Office standard ou personnalisé. Pour plus d’informations, consultez [procédure pas à pas : concevoir une zone de formulaire Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md).

## <a name="see-also"></a>Voir aussi
- [Accéder au ruban au moment de l’exécution](../vsto/accessing-the-ribbon-at-run-time.md)
- [Vue d’ensemble du ruban](../vsto/ribbon-overview.md)
- [Concepteur de ruban](../vsto/ribbon-designer.md)
- [Personnaliser un ruban pour Outlook](../vsto/customizing-a-ribbon-for-outlook.md)
- [Comment : prendre en main la personnalisation du ruban](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [Comment : modifier la position d’un onglet sur le ruban](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)
- [Comment : personnaliser un onglet intégré](../vsto/how-to-customize-a-built-in-tab.md)
- [Comment : ajouter des contrôles au mode Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)
- [Vue d’ensemble du modèle objet de ruban](../vsto/ribbon-object-model-overview.md)
