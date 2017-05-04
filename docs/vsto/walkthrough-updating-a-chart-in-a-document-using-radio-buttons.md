---
title: "Proc&#233;dure pas&#160;&#224;&#160;pas&#160;: mise &#224; jour d&#39;un graphique dans un document &#224; l&#39;aide de cases d&#39;option | Microsoft Docs"
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
  - "contrôles (développement Office dans Visual Studio), mettre à jour des documents"
  - "documents (développement Office dans Visual Studio), mettre à jour à l'aide de contrôles"
ms.assetid: 56e6d1f2-65a4-41f0-aff5-f0cfd96d7185
caps.latest.revision: 60
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 59
---
# Proc&#233;dure pas&#160;&#224;&#160;pas&#160;: mise &#224; jour d&#39;un graphique dans un document &#224; l&#39;aide de cases d&#39;option
  Cette procédure pas à pas montre comment utiliser des cases d'option dans une personnalisation de document pour Microsoft Office Word dans le but de donner aux utilisateurs la possibilité de sélectionner des styles de graphique dans le document.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Cette procédure pas à pas décrit les tâches suivantes :  
  
-   Ajout d'un graphique au document d'un projet de niveau document au moment du design.  
  
-   Regroupement de cases d'option en les ajoutant à un contrôle utilisateur.  
  
-   Changement de style de graphique quand une option est sélectionnée.  
  
 Pour voir le résultat dans un exemple complet, consultez l'exemple Commandes Word dans [Exemples et procédures pas à pas relatifs au développement Office](../vsto/office-development-samples-and-walkthroughs.md).  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Composants requis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] ou [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].  
  
## Création du projet  
 La première étape consiste à créer un projet de document Word.  
  
#### Pour créer un projet  
  
1.  Créez un projet de document Word et appelez\-le **Mes options de graphique**.  Dans l'Assistant, sélectionnez **Créer un nouveau document**.  Pour plus d'informations, consultez [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio ouvre le nouveau document Word dans le concepteur et ajoute le projet **Mes options de graphique** à l'**Explorateur de solutions**.  
  
## Ajout d'un graphique dans le document  
  
#### Pour ajouter un graphique  
  
1.  Dans le document Word qui est hébergé dans le concepteur Visual Studio, sur le ruban, cliquez sur l'onglet **Insertion**.  
  
2.  Dans le groupe **Texte**, cliquez sur le bouton déroulant **Insérer un objet** et cliquez sur **Objet**.  
  
     La boîte de dialogue **Objet** s'ouvre.  
  
3.  Dans la liste **Type d'objet**, sous l'onglet **Nouvel objet**, sélectionnez **Graphique Microsoft Graph** et cliquez sur **OK**.  
  
     Un graphique est ajouté dans le document au point d'insertion et la fenêtre **Feuille de données** apparaît avec quelques données par défaut.  
  
4.  Fermez la fenêtre **Feuille de données** pour accepter les valeurs par défaut dans le graphique et cliquez dans le document pour déplacer le point d'insertion en dehors du graphique.  
  
5.  Cliquez avec le bouton droit sur le graphique, puis cliquez sur **Format d'objet**.  
  
6.  Sous l'onglet **Disposition** de la boîte de dialogue **Format d'objet**, sélectionnez **Carré** et cliquez sur **OK**.  
  
## Ajout d'un contrôle utilisateur au projet  
 Les cases d'option d'un document ne s'excluent pas mutuellement par défaut.  Vous pouvez les faire fonctionner correctement en les ajoutant à un contrôle utilisateur, puis en écrivant du code pour commander la sélection.  
  
#### Pour ajouter un contrôle utilisateur  
  
1.  Sélectionnez le projet **Mes options de graphique** dans l'**Explorateur de solutions**.  
  
2.  Dans le menu **Projet**, cliquez sur **Ajouter un nouvel élément**.  
  
3.  Dans la boîte de dialogue **Ajouter un nouvel élément**, cliquez sur **Contrôle utilisateur**, appelez le contrôle **ChartOptions** et cliquez sur **Ajouter**.  
  
#### Pour ajouter des contrôles Windows Form au contrôle utilisateur  
  
1.  Si le contrôle utilisateur n'apparaît pas dans le concepteur, double\-cliquez sur **ChartOptions** dans l'**Explorateur de solutions**.  
  
2.  Sous l'onglet **Contrôles communs** de la **Boîte à outils**, faites glisser le premier contrôle **Case d'option** vers le contrôle utilisateur et modifiez les propriétés suivantes.  
  
    |Propriété|Valeur|  
    |---------------|------------|  
    |**Nom**|**columnChart**|  
    |**Texte**|Histogramme|  
  
3.  Ajoutez une deuxième **Case d'option** au contrôle utilisateur et modifiez les propriétés suivantes.  
  
    |Propriété|Valeur|  
    |---------------|------------|  
    |**Nom**|**barChart**|  
    |**Texte**|Graphique à barres|  
  
4.  Ajoutez une troisième **Case d'option** au contrôle utilisateur et modifiez les propriétés suivantes.  
  
    |Propriété|Valeur|  
    |---------------|------------|  
    |**Nom**|**lineChart**|  
    |**Texte**|Courbes|  
  
5.  Ajoutez une quatrième **Case d'option** au contrôle utilisateur et modifiez les propriétés suivantes.  
  
    |Propriété|Valeur|  
    |---------------|------------|  
    |**Nom**|**areaBlockChart**|  
    |**Texte**|Graphique en secteurs|  
  
## Ajout de références  
 Pour accéder au graphique depuis le contrôle utilisateur dans un document, vous devez avoir une référence à l'assembly Microsoft.Office.Interop.Graph dans votre projet.  
  
#### Pour ajouter une référence à l'assembly Microsoft.Office.Interop.Graph  
  
1.  Dans le menu **Projet**, cliquez sur **Ajouter une référence**.  
  
     La boîte de dialogue **Ajouter une référence** s'affiche.  
  
2.  Sous l'onglet **.NET**, sélectionnez **Microsoft.Office.Interop.Graph** et cliquez sur **OK**.  Sélectionnez la version 14.0.0.0 de l'assembly.  
  
## Changement de style de graphique quand une case d'option est sélectionnée  
 Pour que les boutons fonctionnent correctement, créez un événement public sur le contrôle utilisateur, ajoutez une propriété pour définir le type de sélection et créez une procédure pour l'événement `CheckedChanged` de chacune des cases d'option.  
  
#### Pour créer un événement et une propriété sur un contrôle utilisateur  
  
1.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur le contrôle utilisateur, puis cliquez sur **Afficher le code**.  
  
2.  Ajoutez du code pour créer un événement `SelectionChanged` et la propriété `Selection` à la classe `ChartOptions`.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#9](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ChartOptions.cs#9)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#9](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/VB/ChartOptions.vb#9)]  
  
#### Pour gérer l'événement CheckedChange des cases d'option  
  
1.  Définissez le type de graphique dans le gestionnaire d’événements `CheckedChanged` de la case d'option `areaBlockChart`, puis déclenchez l'événement.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ChartOptions.cs#10)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#10](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/VB/ChartOptions.vb#10)]  
  
2.  Définissez le type de graphique dans le gestionnaire d’événements `CheckedChanged` de la case d'option `barChart`.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#11](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ChartOptions.cs#11)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#11](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/VB/ChartOptions.vb#11)]  
  
3.  Définissez le type de graphique dans le gestionnaire d’événements `CheckedChanged` de la case d'option `columnChart`.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#12](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ChartOptions.cs#12)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#12](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/VB/ChartOptions.vb#12)]  
  
4.  Définissez le type de graphique dans le gestionnaire d’événements `CheckedChanged` de la case d'option `lineChart`.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#13](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ChartOptions.cs#13)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#13](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/VB/ChartOptions.vb#13)]  
  
5.  En C\#, vous devez ajouter des gestionnaires d'événements pour les cases d'option.  Vous pouvez ajouter du code au constructeur `ChartOptions`, sous l'appel à `InitializeComponent`.  Pour plus d'informations sur la création de gestionnaires d'événements, consultez [Comment : créer des gestionnaires d'événements dans les projets Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#14](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ChartOptions.cs#14)]  
  
## Ajout du contrôle utilisateur au document  
 Quand vous créez la solution, le nouveau contrôle utilisateur est automatiquement ajouté à la **Boîte à outils**.  Vous pouvez alors faire glisser le contrôle depuis la **Boîte à outils** directement dans votre document.  
  
#### Pour ajouter le contrôle utilisateur à votre document  
  
1.  Dans le menu **Générer**, cliquez sur **Générer la solution**.  
  
     Le contrôle utilisateur **ChartOptions** est ajouté à la **Boîte à outils**.  
  
2.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur **ThisDocument.vb** ou **ThisDocument.cs**, puis cliquez sur **Concepteur de vues**.  
  
3.  Faites glisser le contrôle `ChartOptions` depuis la **Boîte à outils** vers le document.  
  
     Dans la fenêtre **Propriétés**, nommez le contrôle que vous venez d'ajouter au document `ChartOptions1`.  
  
## Changement de type de graphique  
 Créez un gestionnaire d'événements pour changer de type de graphique en fonction de l'option sélectionnée dans le contrôle utilisateur.  
  
#### Pour changer le type de graphique affiché dans le document  
  
1.  Ajoutez le gestionnaire d'événements suivant à la classe `ThisDocument`.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#15](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ThisDocument.cs#15)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#15](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/VB/ThisDocument.vb#15)]  
  
2.  En C\#, vous devez ajouter un gestionnaire d'événements pour le contrôle utilisateur à l'événement <xref:Microsoft.Office.Tools.Word.Document.Startup>.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#16](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ThisDocument.cs#16)]  
  
## Test de l'application  
 À présent, vous pouvez tester votre document et vérifier que le style de graphique est mis à jour correctement quand vous sélectionnez une case d'option.  
  
#### Pour tester votre document  
  
1.  Appuyez sur F5 pour exécuter votre projet.  
  
2.  Sélectionnez plusieurs cases d'option.  
  
3.  Confirmez que le style de graphique change pour refléter la sélection.  
  
## Étapes suivantes  
 Voici quelques tâches susceptibles de venir après :  
  
-   Utilisation d'un bouton pour renseigner une zone de texte.  Pour plus d'informations, consultez [Procédure pas à pas : affichage de texte dans une zone de texte d'un document à l'aide d'un bouton](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-document-using-a-button.md).  
  
-   Modifier la mise en forme en sélectionnant un style dans une zone déroulante.  Pour plus d'informations, consultez [Procédure pas à pas : modification de la mise en forme d'un document à l'aide de contrôles CheckBox](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md).  
  
## Voir aussi  
 [Procédures pas à pas utilisant Word](../vsto/walkthroughs-using-word.md)   
 [Exemples et procédures pas à pas relatifs au développement Office](../vsto/office-development-samples-and-walkthroughs.md)   
 [Limitations des contrôles Windows Forms dans les documents Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
  
  