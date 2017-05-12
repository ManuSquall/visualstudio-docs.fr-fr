---
title: "Proc&#233;dure pas &#224; pas&#160;: mise &#224; jour d&#39;un graphique dans une feuille de calcul &#224; l&#39;aide de cases d&#39;option"
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
  - "contrôles (développement Office dans Visual Studio), mettre à jour des feuilles de calcul"
  - "feuilles de calcul, mettre à jour à l'aide de contrôles managés"
  - "feuilles de calcul, utiliser les cases d'option"
ms.assetid: cacc43a3-6d95-4a47-b943-3457d97a16f8
caps.latest.revision: 58
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 57
---
# Proc&#233;dure pas &#224; pas&#160;: mise &#224; jour d&#39;un graphique dans une feuille de calcul &#224; l&#39;aide de cases d&#39;option
  Cette procédure pas à pas présente les principes de base de l'utilisation de cases d'option sur une feuille de calcul Microsoft Office Excel pour permettre à l'utilisateur de basculer rapidement entre les options.  Dans ce cas, les options modifient le style d'un graphique.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 Pour consulter le résultat sous forme d'exemple terminé, consultez les exemples de contrôles Excel dans [Exemples et procédures pas à pas relatifs au développement Office](../vsto/office-development-samples-and-walkthroughs.md).  
  
 Cette procédure pas à pas décrit les tâches suivantes :  
  
-   Ajout d'un groupe de cases d'option à une feuille de calcul.  
  
-   Modification du style de graphique lorsqu'une option est sélectionnée  
  
> [!NOTE]  
>  Il est possible que pour certains des éléments de l'interface utilisateur de Visual Studio, votre ordinateur affiche des noms ou des emplacements différents de ceux indiqués dans les instructions suivantes.  Ces éléments dépendent de l'édition de Visual Studio dont vous disposez et des paramètres que vous utilisez.  Pour plus d’informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Composants requis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] ou [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
## Ajout d'un graphique à une feuille de calcul  
 Vous pouvez créer un projet de classeur Excel qui personnalise un classeur existant.  Dans cette procédure pas à pas, vous ajouterez un graphique à un classeur, puis utiliserez ce classeur dans une nouvelle solution Excel.  La source de données dans cette procédure pas à pas est une feuille de calcul nommée **Données pour Graphique**.  
  
#### Pour ajouter les données  
  
1.  Ouvrez Microsoft Excel.  
  
2.  Cliquez avec le bouton droit sur l'onglet **Feuil3** et sélectionnez **Renommer** dans le menu contextuel.  
  
3.  Renommez la feuille en Données pour Graphique.  
  
4.  Ajoutez les données suivantes à **Données pour Graphique**, la cellule A4 correspondant à l'angle supérieur gauche et la cellule E8 à l'angle inférieur droit.  
  
    ||Q1|Q2|Q3|Q4|  
    |-|--------|--------|--------|--------|  
    |West|500|550|550|600|  
    |East|600|625|675|700|  
    |North|450|470|490|510|  
    |South|800|750|775|790|  
  
 Ajoutez ensuite un graphique à la première feuille de calcul pour afficher les données.  
  
#### Pour ajouter un graphique dans Excel  
  
1.  Dans le groupe **Graphiques** de l'onglet **Insertion**, cliquez sur **Colonne**, puis sur **Tous types de graphiques**.  
  
2.  Dans la boîte de dialogue **Insérer un graphique**, cliquez sur **OK**.  
  
3.  Dans l'onglet **Création**, dans le groupe **Données**, cliquez sur **Sélectionner des données**.  
  
4.  Dans la boîte de dialogue **Sélectionner une source de données**, cliquez dans la zone **Plage de données du graphique** et effacez toute sélection par défaut.  
  
5.  Dans la feuille **Données pour Graphique**, sélectionnez le bloc de cellules contenant les nombres \(bloc dont la cellule A4 constitue l'angle supérieur gauche et dont la cellule E8 constitue l'angle inférieur droit\).  
  
6.  Dans la boîte de dialogue **Sélectionner une source de données**, cliquez sur **OK**.  
  
7.  Repositionnez le graphique afin que l'angle supérieur droit s'aligne avec la cellule **E2**.  
  
8.  Enregistrez votre fichier sur le lecteur C et nommez \-le **ExcelChart.xlsx**.  
  
9. Quittez Excel.  
  
## Création d'un projet  
 Au cours de cette étape, vous allez créer un projet de classeur Excel basé sur le classeur **ExcelChart**.  
  
#### Pour créer un projet  
  
1.  Créez un projet de classeur Excel et attribuez\-lui le nom **My Excel Chart**.  Dans l'Assistant, sélectionnez **Copier un document existant**.  
  
     Pour plus d’informations, consultez [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  Cliquez sur le buttonandde **Parcourir** recherchez le classeur que vous avez créé précédemment dans cette procédure pas \- à \- pas.  
  
3.  Cliquez sur **OK**.  
  
     Visual Studio ouvre le nouveau classeur Excel dans le concepteur et ajoute le projet **My Excel Chart** à l'**Explorateur de solutions**.  
  
## Définition des propriétés du graphique  
 Lorsque vous créez un projet de classeur Excel à partir d'un classeur existant, des contrôles hôtes sont automatiquement créés pour l'ensemble des plages nommées, des objets de liste et des graphiques du classeur.  Vous pouvez renommer le contrôle <xref:Microsoft.Office.Tools.Excel.Chart> à l'aide de la fenêtre **Propriétés**.  
  
#### Pour modifier le nom du contrôle Chart  
  
1.  Sélectionnez le contrôle <xref:Microsoft.Office.Tools.Excel.Chart> dans le concepteur et modifiez les propriétés suivantes dans la fenêtre **Propriétés**.  
  
    |Propriété|Valeur|  
    |---------------|------------|  
    |**Nom**|**dataChart**|  
    |**HasLegend**|**false**|  
  
## Ajout de contrôles  
 Cette feuille de calcul utilise des cases d'option pour permettre aux utilisateurs de modifier rapidement le style de graphique.  Ces cases d'option doivent toutefois être exclusives, ce qui signifie qu'une seule case peut être sélectionnée au sein d'un groupe.  Ce comportement ne s'applique pas par défaut lorsque vous ajoutez plusieurs cases d'option à une feuille de calcul.  
  
 Pour ajouter ce comportement, vous pouvez regrouper les cases d'option sur un contrôle utilisateur, écrire votre code associé au contrôle utilisateur, puis ajouter le contrôle utilisateur à la feuille de calcul.  
  
#### Pour ajouter un contrôle utilisateur  
  
1.  Sélectionnez le projet **My Excel Chart** dans l'**Explorateur de solutions**.  
  
2.  Dans le menu **Projet**, cliquez sur **Ajouter un nouvel élément**.  
  
3.  Dans la boîte de dialogue **Ajouter un nouvel élément**, cliquez sur **Contrôle utilisateur**, nommez le contrôle **ChartOptions** et cliquez sur **Ajouter**.  
  
#### Pour ajouter des cases d'option au contrôle utilisateur  
  
1.  Si le contrôle utilisateur n'est pas visible dans le concepteur, double\-cliquez sur **ChartOptions** dans l'**Explorateur de solutions**.  
  
2.  À partir de l'onglet **Contrôles communs** de la **Boîte à outils**, faites glisser un contrôle **Radio Button** vers le contrôle utilisateur et modifiez les propriétés suivantes :  
  
    |Propriété|Valeur|  
    |---------------|------------|  
    |**Nom**|**columnChart**|  
    |**du texte ;**|Histogramme|  
  
3.  Ajoutez une deuxième case d'option au contrôle utilisateur et modifiez les propriétés suivantes.  
  
    |Propriété|Valeur|  
    |---------------|------------|  
    |**Nom**|**barChart**|  
    |**du texte ;**|Graphique à barres|  
  
4.  Ajoutez une troisième case d'option au contrôle utilisateur et modifiez les propriétés suivantes.  
  
    |Propriété|Valeur|  
    |---------------|------------|  
    |**Nom**|**lineChart**|  
    |**du texte ;**|Graphique en courbes|  
  
5.  Ajoutez une quatrième case d'option au contrôle utilisateur et modifiez les propriétés suivantes.  
  
    |Propriété|Valeur|  
    |---------------|------------|  
    |**Nom**|**areaBlockChart**|  
    |**du texte ;**|Graphique blocs en aires|  
  
 L'étape suivante consiste à écrire du code pour mettre à jour le graphique lorsque l'utilisateur clique sur une case d'option.  
  
## Modification du style de graphique lorsqu'une case d'option est sélectionnée  
 Vous pouvez maintenant ajouter le code pour modifier le style de graphique.  Pour cela, créez un événement public sur le contrôle utilisateur, ajoutez une propriété pour définir le type de sélection et créez un gestionnaire d'événements pour l'événement `CheckedChanged` de chacune des cases d'option.  
  
#### Pour créer un événement et une propriété sur un contrôle utilisateur  
  
1.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur le contrôle utilisateur et sélectionnez **Afficher le code**.  
  
2.  Ajoutez du code à la classe `ChartOptions` pour créer un événement `SelectionChanged` et la propriété `Selection`.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#13](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/ChartOptions.cs#13)]
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#13](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/VB/ChartOptions.vb#13)]  
  
#### Pour gérer l'événement CheckedChanged des cases d'option  
  
1.  Définissez le type de graphique dans le gestionnaire d'événements `CheckedChanged` de la case d'option `areaBlockChart`, puis déclenchez l'événement.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#14](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/ChartOptions.cs#14)]
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#14](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/VB/ChartOptions.vb#14)]  
  
2.  Définissez le type de graphique dans le gestionnaire d'événements `CheckedChanged` de la case d'option `barChart`.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#15](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/ChartOptions.cs#15)]
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#15](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/VB/ChartOptions.vb#15)]  
  
3.  Définissez le type de graphique dans le gestionnaire d'événements `CheckedChanged` de la case d'option `columnChart`.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#16](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/ChartOptions.cs#16)]
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#16](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/VB/ChartOptions.vb#16)]  
  
4.  Définissez le type de graphique dans le gestionnaire d'événements `CheckedChanged` de la case d'option `lineChart`.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#17](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/ChartOptions.cs#17)]
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#17](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/VB/ChartOptions.vb#17)]  
  
5.  En C\#, vous devez ajouter des gestionnaires d'événements pour les cases d'option.  Vous pouvez ajouter le code au constructeur `ChartOptions`, sous l'appel à `InitializeComponent`.  Pour plus d'informations sur la création de gestionnaires d'événements, consultez [Comment : créer des gestionnaires d'événements dans les projets Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#18](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/ChartOptions.cs#18)]  
  
## Ajout du contrôle utilisateur à la feuille de calcul  
 Lorsque vous générez la solution, le nouveau contrôle utilisateur est automatiquement ajouté à la **boîte à outils**.  Vous pouvez faire glisser le contrôle de la **Boîte à outils** vers votre feuille de calcul.  
  
#### Pour ajouter le contrôle utilisateur à votre feuille de calcul  
  
1.  Dans le menu **Générer**, cliquez sur **Générer la solution**.  
  
     Le contrôle utilisateur **ChartOptions** est ajouté à la **boîte à outils**.  
  
2.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur **Sheet1.vb** ou **Sheet1.cs** et sélectionnez **Concepteur de vues**.  
  
3.  Faites glisser un contrôle **ChartOptions** de la **boîte à outils** jusqu'à la feuille de calcul.  
  
     Un nouveau contrôle nommé `my_Excel_Chart_ChartOptions1` est ajouté au projet.  
  
4.  Remplacez le nom du contrôle par ChartOptions1.  
  
## Modification du type de graphique  
 Pour modifier le type de graphique, créez un gestionnaire d'événements qui définit le style en fonction de l'option sélectionnée dans le contrôle utilisateur.  
  
#### Pour modifier le type de graphique qui est affiché dans la feuille de calcul  
  
1.  Ajoutez le gestionnaire d'événements suivant à la classe `Sheet1`.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#19](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/Sheet1.cs#19)]
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#19](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/VB/Sheet1.vb#19)]  
  
2.  En C\#, vous devez ajouter un gestionnaire d'événements pour le contrôle utilisateur à l'événement <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> comme indiqué ci\-dessous.  Pour plus d'informations sur la création de gestionnaires d'événements, consultez [Comment : créer des gestionnaires d'événements dans les projets Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#20](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/Sheet1.cs#20)]  
  
## Test de l'application  
 Vous pouvez maintenant tester votre classeur pour vérifier que le style du graphique est correct lorsque vous sélectionnez une case d'option.  
  
#### Pour tester votre classeur  
  
1.  Appuyez sur F5 pour exécuter votre projet.  
  
2.  Sélectionnez plusieurs cases d'option.  
  
3.  Vérifiez que le style du graphique change conformément à la sélection.  
  
## Étapes suivantes  
 Cette procédure pas à pas présente les principes de base de l'utilisation de cases d'option et de styles de graphique sur les feuilles de calcul Excel.  Vous devrez peut\-être ensuite exécuter les opérations suivantes :  
  
-   Déploiement du projet.  Pour plus d’informations, consultez [Déploiement d'une solution Office](../vsto/deploying-an-office-solution.md).  
  
-   Utilisation d'un bouton pour remplir une zone de texte.  Pour plus d’informations, consultez [Procédure pas à pas : affichage de texte dans une zone de texte d'une feuille de calcul à l'aide d'un bouton](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md).  
  
-   Modification de la mise en forme sur une feuille de calcul à l'aide de cases à cocher.  Pour plus d’informations, consultez [Procédure pas à pas : modification de la mise en forme d'une feuille de calcul à l'aide de contrôles CheckBox](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md).  
  
## Voir aussi  
 [Procédures pas à pas utilisant Excel](../vsto/walkthroughs-using-excel.md)  
  
  