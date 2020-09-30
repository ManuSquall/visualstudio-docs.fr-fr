---
title: 'Procédure pas à pas : mise à jour d’un graphique dans un document à l’aide de cases d’option'
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], updating using controls
- controls [Office development in Visual Studio], updating documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f4b39949deb3bcbf3d9330ca8d820a5841b0f4c4
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91584293"
---
# <a name="walkthrough-update-a-chart-in-a-document-using-radio-buttons"></a>Procédure pas à pas : mise à jour d’un graphique dans un document à l’aide de cases d’option
  Cette procédure pas à pas montre comment utiliser des cases d'option dans une personnalisation de document pour Microsoft Office Word dans le but de donner aux utilisateurs la possibilité de sélectionner des styles de graphique dans le document.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 Cette procédure pas à pas décrit les tâches suivantes :

- Ajout d'un graphique au document d'un projet de niveau document au moment du design.

- Regroupement de cases d'option en les ajoutant à un contrôle utilisateur.

- Changement de style de graphique quand une option est sélectionnée.

  Pour voir le résultat sous forme d’exemple terminé, consultez l’exemple de contrôles Word dans les [exemples et procédures pas à pas relatifs au développement Office](../vsto/office-development-samples-and-walkthroughs.md).

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prérequis
 Vous devez disposer des éléments suivants pour exécuter cette procédure pas à pas :

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] ou [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].

## <a name="create-the-project"></a>Créer le projet
 La première étape consiste à créer un projet de document Word.

### <a name="to-create-a-new-project"></a>Pour créer un projet

1. Créez un projet de document Word avec les **options nom My Chart**. Dans l’Assistant, sélectionnez **créer un nouveau document**. Pour plus d’informations, consultez [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio ouvre le nouveau document Word dans le concepteur et ajoute le projet **mes options de graphique** à **Explorateur de solutions**.

## <a name="add-a-chart-to-the-document"></a>Ajouter un graphique au document

### <a name="to-add-a-chart"></a>Pour ajouter un graphique

1. Dans le document Word qui est hébergé dans le concepteur Visual Studio, sur le ruban, cliquez sur l’onglet **Insérer** .

2. Dans le groupe **texte** , cliquez sur le bouton déroulant **Insérer un objet** , puis cliquez sur **objet**.

     La boîte de dialogue **objet** s’ouvre.

3. Dans la liste **type d’objet** de l’onglet **créer nouveau** , sélectionnez **Microsoft Graph graphique** , puis cliquez sur **OK**.

     Un graphique est ajouté au document au point d’insertion et la fenêtre **feuille** de données s’affiche avec des données par défaut.

4. Fermez la fenêtre **feuille** de données pour accepter les valeurs par défaut dans le graphique et cliquez à l’intérieur du document pour déplacer le focus en dehors du graphique.

5. Cliquez avec le bouton droit sur le graphique, puis cliquez sur format de l' **objet**.

6. Sous l’onglet **disposition** de la boîte de dialogue Format de l' **objet** , sélectionnez **Square** , puis cliquez sur **OK**.

## <a name="add-a-user-control-to-the-project"></a>Ajouter un contrôle utilisateur au projet
 Les cases d'option d'un document ne s'excluent pas mutuellement par défaut. Vous pouvez les faire fonctionner correctement en les ajoutant à un contrôle utilisateur, puis en écrivant du code pour commander la sélection.

### <a name="to-add-a-user-control"></a>Pour ajouter un contrôle utilisateur

1. Sélectionnez le projet **mes options de graphique** dans **Explorateur de solutions**.

2. Dans le menu **Projet** , cliquez sur **Ajouter un nouvel élément**.

3. Dans la boîte de dialogue **Ajouter un nouvel élément** , cliquez sur **contrôle utilisateur**, nommez le contrôle **ChartOptions,** puis cliquez sur **Ajouter**.

### <a name="to-add-windows-form-controls-to-the-user-control"></a>Pour ajouter des contrôles Windows Form au contrôle utilisateur

1. Si le contrôle utilisateur n’est pas visible dans le concepteur, double-cliquez sur **ChartOptions** dans **Explorateur de solutions**.

2. Dans l’onglet **contrôles communs** de la **boîte à outils**, faites glisser le premier contrôle de case d' **option** vers le contrôle utilisateur et modifiez les propriétés suivantes.

    |Propriété|Valeur|
    |--------------|-----------|
    |**Nom**|**columnChart**|
    |**Text**|**Histogramme**|

3. Ajoutez une deuxième case d' **option** au contrôle utilisateur et modifiez les propriétés suivantes.

    |Propriété|Valeur|
    |--------------|-----------|
    |**Nom**|**barChart**|
    |**Text**|**Graphique à barres**|

4. Ajoutez une troisième **case d’option** au contrôle utilisateur et modifiez les propriétés suivantes.

    |Propriété|Valeur|
    |--------------|-----------|
    |**Nom**|**lineChart**|
    |**Text**|**Graphique en courbes**|

5. Ajoutez une quatrième case d' **option** au contrôle utilisateur et modifiez les propriétés suivantes.

    |Propriété|Valeur|
    |--------------|-----------|
    |**Nom**|**areaBlockChart**|
    |**Text**|**Graphique en secteurs**|

## <a name="add-references"></a>Ajouter des références
 Pour accéder au graphique à partir du contrôle utilisateur sur un document, vous devez avoir une référence à l' `Microsoft.Office.Interop.Graph` assembly dans votre projet.

### <a name="to-add-a-reference-to-the-microsoftofficeinteropgraph-assembly"></a>Pour ajouter une référence à l'assembly Microsoft.Office.Interop.Graph

1. Dans le menu **Projet**, cliquez sur **Ajouter une référence**.

     La boîte de dialogue **Ajouter une référence** s’affiche.

2. Sous l’onglet **.net** , sélectionnez **Microsoft. Office. Interop. Graph** , puis cliquez sur **OK**. Sélectionnez la version 14.0.0.0 de l'assembly.

## <a name="change-the-chart-style-when-a-radio-button-is-selected"></a>Modifier le style du graphique lorsqu’une case d’option est sélectionnée
 Pour que les boutons fonctionnent correctement, créez un événement public sur le contrôle utilisateur, ajoutez une propriété pour définir le type de sélection et créez une procédure pour l'événement `CheckedChanged` de chacune des cases d'option.

### <a name="to-create-an-event-and-property-on-a-user-control"></a>Pour créer un événement et une propriété sur un contrôle utilisateur

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le contrôle utilisateur, puis cliquez sur **afficher le code**.

2. Ajoutez du code pour créer un événement `SelectionChanged` et la propriété `Selection` à la classe `ChartOptions`.

     [!code-csharp[Trin_VstcoreProgrammingControlsWord#9](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs#9)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#9](../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb#9)]

### <a name="to-handle-the-checkedchange-event-of-the-radio-buttons"></a>Pour gérer l'événement CheckedChange des cases d'option

1. Définissez le type de graphique dans le gestionnaire d’événements `CheckedChanged` de la case d'option `areaBlockChart`, puis déclenchez l'événement.

     [!code-csharp[Trin_VstcoreProgrammingControlsWord#10](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs#10)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#10](../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb#10)]

2. Définissez le type de graphique dans le gestionnaire d’événements `CheckedChanged` de la case d'option `barChart`.

     [!code-csharp[Trin_VstcoreProgrammingControlsWord#11](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs#11)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#11](../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb#11)]

3. Définissez le type de graphique dans le gestionnaire d’événements `CheckedChanged` de la case d'option `columnChart`.

     [!code-csharp[Trin_VstcoreProgrammingControlsWord#12](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs#12)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#12](../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb#12)]

4. Définissez le type de graphique dans le gestionnaire d’événements `CheckedChanged` de la case d'option `lineChart`.

     [!code-csharp[Trin_VstcoreProgrammingControlsWord#13](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs#13)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#13](../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb#13)]

5. En C#, vous devez ajouter des gestionnaires d'événements pour les cases d'option. Vous pouvez ajouter du code au constructeur `ChartOptions`, sous l'appel à `InitializeComponent`. Pour plus d’informations sur la création de gestionnaires d’événements, consultez [Comment : créer des gestionnaires d’événements dans les projets Office](../vsto/how-to-create-event-handlers-in-office-projects.md).

     [!code-csharp[Trin_VstcoreProgrammingControlsWord#14](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs#14)]

## <a name="add-the-user-control-to-the-document"></a>Ajouter le contrôle utilisateur au document
 Lorsque vous générez la solution, le nouveau contrôle utilisateur est automatiquement ajouté à la **boîte à outils**. Vous pouvez ensuite faire glisser le contrôle de la **boîte à outils** vers votre document.

### <a name="to-add-the-user-control-your-document"></a>Pour ajouter le contrôle utilisateur à votre document

1. Dans le menu **Générer**, cliquez sur **Générer la solution**.

     Le contrôle utilisateur **ChartOptions** est ajouté à la **boîte à outils**.

2. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur **ThisDocument. vb** ou **ThisDocument.cs**, puis cliquez sur **Concepteur de vues**.

3. Faites glisser le `ChartOptions` contrôle de la **boîte à outils** vers le document.

     Dans la fenêtre **Propriétés** , nommez le contrôle que vous venez d’ajouter au document  `ChartOptions1` .

## <a name="change-the-chart-type"></a>Modifier le type de graphique
 Créez un gestionnaire d'événements pour changer de type de graphique en fonction de l'option sélectionnée dans le contrôle utilisateur.

### <a name="to-change-the-type-of-chart-that-is-displayed-in-the-document"></a>Pour changer le type de graphique affiché dans le document

1. Ajoutez le gestionnaire d'événements suivant à la classe `ThisDocument`.

     [!code-vb[Trin_VstcoreProgrammingControlsWord#15](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#15)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#15](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#15)]

2. En C#, vous devez ajouter un gestionnaire d'événements pour le contrôle utilisateur à l'événement <xref:Microsoft.Office.Tools.Word.Document.Startup>.

     [!code-csharp[Trin_VstcoreProgrammingControlsWord#16](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#16)]

## <a name="test-the-application"></a>Test de l’application
 À présent, vous pouvez tester votre document et vérifier que le style de graphique est mis à jour correctement quand vous sélectionnez une case d'option.

### <a name="to-test-your-document"></a>Pour tester votre document

1. Appuyez sur **F5** pour exécuter votre projet.

2. Sélectionnez plusieurs cases d'option.

3. Confirmez que le style de graphique change pour refléter la sélection.

## <a name="next-steps"></a>Étapes suivantes
 Voici quelques tâches susceptibles de venir après :

- Utilisation d'un bouton pour renseigner une zone de texte. Pour plus d’informations, consultez [procédure pas à pas : affichage de texte dans une zone de texte dans un document à l’aide d’un bouton](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-document-using-a-button.md).

- Modifier la mise en forme en sélectionnant un style dans une zone déroulante. Pour plus d’informations, consultez [procédure pas à pas : modifier la mise en forme d’un document à l’aide de contrôles CheckBox](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md).

## <a name="see-also"></a>Voir aussi
- [Procédures pas à pas utilisant Word](../vsto/walkthroughs-using-word.md)
- [Exemples et procédures pas à pas relatifs au développement Office](../vsto/office-development-samples-and-walkthroughs.md)
- [Limitations des contrôles de Windows Forms sur les documents Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)
