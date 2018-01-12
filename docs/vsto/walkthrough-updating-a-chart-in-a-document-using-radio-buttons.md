---
title: "Procédure pas à pas : Mise à jour d’un graphique dans un Document à l’aide de cases d’option | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], updating using controls
- controls [Office development in Visual Studio], updating documents
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 1f1340c3e67ca0647448228fb2414fa4ba7d4003
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-updating-a-chart-in-a-document-using-radio-buttons"></a>Procédure pas à pas : mise à jour d'un graphique dans un document à l'aide de cases d'option
  Cette procédure pas à pas montre comment utiliser des cases d'option dans une personnalisation de document pour Microsoft Office Word dans le but de donner aux utilisateurs la possibilité de sélectionner des styles de graphique dans le document.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Cette procédure pas à pas décrit les tâches suivantes :  
  
-   Ajout d'un graphique au document d'un projet de niveau document au moment du design.  
  
-   Regroupement de cases d'option en les ajoutant à un contrôle utilisateur.  
  
-   Changement de style de graphique quand une option est sélectionnée.  
  
 Pour afficher le résultat sous la forme d’un exemple complet, consultez l’exemple des contrôles Word [exemples de développement Office et des procédures pas à pas](../vsto/office-development-samples-and-walkthroughs.md).  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Prérequis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] ou [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].  
  
## <a name="creating-the-project"></a>Création du projet  
 La première étape consiste à créer un projet de document Word.  
  
#### <a name="to-create-a-new-project"></a>Pour créer un projet  
  
1.  Créer un projet de Document Word portant le nom **mes Options de graphique**. Dans l’Assistant, sélectionnez **créer un nouveau document**. Pour plus d'informations, consultez [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio ouvre le nouveau document Word dans le concepteur et ajoute le **mes Options de graphique** projet **l’Explorateur de solutions**.  
  
## <a name="adding-a-chart-to-the-document"></a>Ajout d'un graphique dans le document  
  
#### <a name="to-add-a-chart"></a>Pour ajouter un graphique  
  
1.  Dans le document Word qui est hébergé dans le concepteur Visual Studio, dans le ruban, cliquez sur le **insérer** onglet.  
  
2.  Dans le **texte** , cliquez sur le **insérer un objet** bouton de liste déroulante, puis cliquez sur **objet**.  
  
     Le **objet** boîte de dialogue s’ouvre.  
  
3.  Dans le **type d’objet** liste sur le **créer un nouveau** onglet, sélectionnez **graphique Microsoft Graph** puis cliquez sur **OK**.  
  
     Un graphique est ajouté au document au point d’insertion et le **feuille de données** fenêtre s’affiche avec des données par défaut.  
  
4.  Fermer le **feuille de données** fenêtre pour accepter les valeurs par défaut dans le graphique et cliquez dans le document pour déplacer le focus hors du graphique.  
  
5.  Cliquez sur le graphique, puis cliquez sur **Format de l’objet**.  
  
6.  Sur le **disposition** onglet de la **objet Format** boîte de dialogue, sélectionnez **carré** et cliquez sur **OK**.  
  
## <a name="adding-a-user-control-to-the-project"></a>Ajout d'un contrôle utilisateur au projet  
 Les cases d'option d'un document ne s'excluent pas mutuellement par défaut. Vous pouvez les faire fonctionner correctement en les ajoutant à un contrôle utilisateur, puis en écrivant du code pour commander la sélection.  
  
#### <a name="to-add-a-user-control"></a>Pour ajouter un contrôle utilisateur  
  
1.  Sélectionnez le **mes Options de graphique** projet **l’Explorateur de solutions**.  
  
2.  Dans le menu **Projet** , cliquez sur **Ajouter un nouvel élément**.  
  
3.  Dans le **ajouter un nouvel élément** boîte de dialogue, cliquez sur **contrôle utilisateur**, nommez le contrôle **ChartOptions** et cliquez sur **ajouter**.  
  
#### <a name="to-add-windows-form-controls-to-the-user-control"></a>Pour ajouter des contrôles Windows Form au contrôle utilisateur  
  
1.  Si le contrôle utilisateur n’est pas visible dans le concepteur, double-cliquez sur **ChartOptions** dans **l’Explorateur de solutions**.  
  
2.  À partir de la **contrôles communs** onglet de la **boîte à outils**, faites glisser le premier **case** contrôler au contrôle utilisateur et modifiez les propriétés suivantes.  
  
    |Propriété|Value|  
    |--------------|-----------|  
    |**Name**|**columnChart**|  
    |**Text**|**Histogramme**|  
  
3.  Ajoutez un deuxième **case** à l’utilisateur de contrôle et modifier les propriétés suivantes.  
  
    |Propriété|Value|  
    |--------------|-----------|  
    |**Name**|**barChart**|  
    |**Text**|**Graphique à barres**|  
  
4.  Ajoutez une troisième **case** à l’utilisateur de contrôle et modifier les propriétés suivantes.  
  
    |Propriété|Value|  
    |--------------|-----------|  
    |**Name**|**lineChart**|  
    |**Text**|**Graphique en courbes**|  
  
5.  Ajoutez une quatrième **case** à l’utilisateur de contrôle et modifier les propriétés suivantes.  
  
    |Propriété|Value|  
    |--------------|-----------|  
    |**Name**|**areaBlockChart**|  
    |**Text**|**Graphique en secteurs**|  
  
## <a name="adding-references"></a>Ajout de références  
 Pour accéder au graphique depuis le contrôle utilisateur dans un document, vous devez avoir une référence à l'assembly Microsoft.Office.Interop.Graph dans votre projet.  
  
#### <a name="to-add-a-reference-to-the-microsoftofficeinteropgraph-assembly"></a>Pour ajouter une référence à l'assembly Microsoft.Office.Interop.Graph  
  
1.  Dans le menu **Projet**, cliquez sur **Ajouter une référence**.  
  
     La boîte de dialogue **Ajouter une référence** s’affiche.  
  
2.  Sur le **.NET** onglet, sélectionnez **Microsoft.Office.Interop.Graph** et cliquez sur **OK**. Sélectionnez la version 14.0.0.0 de l'assembly.  
  
## <a name="changing-the-chart-style-when-a-radio-button-is-selected"></a>Changement de style de graphique quand une case d'option est sélectionnée  
 Pour que les boutons fonctionnent correctement, créez un événement public sur le contrôle utilisateur, ajoutez une propriété pour définir le type de sélection et créez une procédure pour l'événement `CheckedChanged` de chacune des cases d'option.  
  
#### <a name="to-create-an-event-and-property-on-a-user-control"></a>Pour créer un événement et une propriété sur un contrôle utilisateur  
  
1.  Dans **l’Explorateur de solutions**, cliquez sur le contrôle utilisateur, puis cliquez sur **afficher le Code**.  
  
2.  Ajoutez du code pour créer un événement `SelectionChanged` et la propriété `Selection` à la classe `ChartOptions`.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#9](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs#9)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#9](../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb#9)]  
  
#### <a name="to-handle-the-checkedchange-event-of-the-radio-buttons"></a>Pour gérer l'événement CheckedChange des cases d'option  
  
1.  Définissez le type de graphique dans le gestionnaire d’événements `CheckedChanged` de la case d'option `areaBlockChart`, puis déclenchez l'événement.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#10](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs#10)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#10](../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb#10)]  
  
2.  Définissez le type de graphique dans le gestionnaire d’événements `CheckedChanged` de la case d'option `barChart`.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#11](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs#11)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#11](../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb#11)]  
  
3.  Définissez le type de graphique dans le gestionnaire d’événements `CheckedChanged` de la case d'option `columnChart`.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#12](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs#12)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#12](../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb#12)]  
  
4.  Définissez le type de graphique dans le gestionnaire d’événements `CheckedChanged` de la case d'option `lineChart`.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#13](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs#13)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#13](../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb#13)]  
  
5.  En C#, vous devez ajouter des gestionnaires d'événements pour les cases d'option. Vous pouvez ajouter du code au constructeur `ChartOptions`, sous l'appel à `InitializeComponent`. Pour plus d’informations sur la création de gestionnaires d’événements, consultez [Comment : créer des gestionnaires d’événements dans les projets Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#14](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs#14)]  
  
## <a name="adding-the-user-control-to-the-document"></a>Ajout du contrôle utilisateur au document  
 Lorsque vous générez la solution, le nouveau contrôle utilisateur est automatiquement ajouté à la **boîte à outils**. Vous pouvez ensuite faire glisser le contrôle à partir de la **boîte à outils** à votre document.  
  
#### <a name="to-add-the-user-control-your-document"></a>Pour ajouter le contrôle utilisateur à votre document  
  
1.  Dans le menu **Générer** , cliquez sur **Générer la solution**.  
  
     Le **ChartOptions** contrôle utilisateur est ajouté à la **boîte à outils**.  
  
2.  Dans **l’Explorateur de solutions**, avec le bouton droit **ThisDocument.vb** ou **ThisDocument.cs**, puis cliquez sur **Concepteur de vue**.  
  
3.  Faites glisser le `ChartOptions` contrôle depuis la **boîte à outils** au document.  
  
     Dans le **propriétés** fenêtre, le nom du contrôle que vous venez d’ajouter au document `ChartOptions1`.  
  
## <a name="changing-the-chart-type"></a>Changement de type de graphique  
 Créez un gestionnaire d'événements pour changer de type de graphique en fonction de l'option sélectionnée dans le contrôle utilisateur.  
  
#### <a name="to-change-the-type-of-chart-that-is-displayed-in-the-document"></a>Pour changer le type de graphique affiché dans le document  
  
1.  Ajoutez le gestionnaire d'événements suivant à la classe `ThisDocument`.  
  
     [!code-vb[Trin_VstcoreProgrammingControlsWord#15](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#15)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#15](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#15)]  
  
2.  En C#, vous devez ajouter un gestionnaire d'événements pour le contrôle utilisateur à l'événement <xref:Microsoft.Office.Tools.Word.Document.Startup>.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#16](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#16)]  
  
## <a name="testing-the-application"></a>Test de l'application  
 À présent, vous pouvez tester votre document et vérifier que le style de graphique est mis à jour correctement quand vous sélectionnez une case d'option.  
  
#### <a name="to-test-your-document"></a>Pour tester votre document  
  
1.  Appuyez sur F5 pour exécuter votre projet.  
  
2.  Sélectionnez plusieurs cases d'option.  
  
3.  Confirmez que le style de graphique change pour refléter la sélection.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Voici quelques tâches susceptibles de venir après :  
  
-   Utilisation d'un bouton pour renseigner une zone de texte. Pour plus d’informations, consultez [procédure pas à pas : affichage de texte dans une zone de texte dans un Document à l’aide d’un bouton](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-document-using-a-button.md).  
  
-   Modifier la mise en forme en sélectionnant un style dans une zone déroulante. Pour plus d’informations, consultez [procédure pas à pas : modification de Document mise en forme à l’aide de contrôles CheckBox](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures pas à pas utilisant Word](../vsto/walkthroughs-using-word.md)   
 [Procédures pas à pas et des exemples de développement office](../vsto/office-development-samples-and-walkthroughs.md)   
 [Limitations des contrôles Windows Forms dans les documents Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
  
  