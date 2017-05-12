---
title: "Proc&#233;dure pas &#224; pas&#160;: programmation d&#39;&#233;v&#233;nements d&#39;un contr&#244;le NamedRange"
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
  - "NamedRange (contrôle), événements"
  - "plages, programmer des événements"
  - "feuilles de calcul, automatiser"
  - "feuilles de calcul, modifier les valeurs de cellules"
  - "feuilles de calcul, événements"
ms.assetid: b69676f9-23b2-4ed6-83ab-8868c3f10948
caps.latest.revision: 57
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 56
---
# Proc&#233;dure pas &#224; pas&#160;: programmation d&#39;&#233;v&#233;nements d&#39;un contr&#244;le NamedRange
  Cette procédure pas à pas montre comment ajouter un contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange> à une feuille de calcul Microsoft Office Excel et programmer par rapport à ses événements à l'aide des outils de développement Office dans Visual Studio.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 Au cours de cette procédure pas à pas, vous apprendrez à :  
  
-   ajouter un contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange> à une feuille de calcul ;  
  
-   programmer des événements de contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange> ;  
  
-   tester votre projet.  
  
> [!NOTE]  
>  Il est possible que pour certains des éléments de l'interface utilisateur de Visual Studio, votre ordinateur affiche des noms ou des emplacements différents de ceux indiqués dans les instructions suivantes.  Ces éléments dépendent de l'édition de Visual Studio dont vous disposez et des paramètres que vous utilisez.  Pour plus d’informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Composants requis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] ou [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
## Création du projet  
 Dans cette étape, vous allez créer un projet de classeur Excel à l'aide de Visual Studio.  
  
#### Pour créer un projet  
  
1.  Créez un projet de classeur Excel et attribuez\-lui le nom My Named Range Events.  Assurez\-vous d'avoir sélectionné **Créer un nouveau document**.  Pour plus d’informations, consultez [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio ouvre le nouveau classeur Excel dans le concepteur et ajoute le projet My Named Range Events à l'**Explorateur de solutions**.  
  
## Ajout de texte et de plages nommées à la feuille de calcul  
 Étant donné que les contrôles hôtes sont des objets Office étendus, vous pouvez les ajouter à votre document de la même manière que si vous ajoutiez l'objet natif.  Par exemple, vous pouvez ajouter un contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange> Excel à une feuille de calcul en ouvrant le menu **Insertion**, en pointant sur **Nom** et en choisissant **Définir**.  Vous pouvez également ajouter un contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange> en le faisant glisser de la **Boîte à outils** sur la feuille de calcul.  
  
 Dans cette étape, vous ajouterez deux contrôles de plage nommée à la feuille de calcul à l'aide de la **Boîte à outils**, puis vous ajouterez du texte à la feuille de calcul.  
  
#### Pour ajouter une plage à votre feuille de calcul  
  
1.  Vérifiez que le classeur **My named Range Events.xlsx nommé** est ouvert dans le concepteur Visual Studio, avec `Sheet1` a affiché.  
  
2.  À partir de l'onglet **Contrôles Excel** de la boîte à outils, faites glisser un contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange> vers la cellule **A1** dans `Sheet1`.  
  
     La boîte de dialogue **Ajouter le contrôle NamedRange** s'affiche.  
  
3.  Vérifiez que **$A$1** apparaît dans la zone de texte modifiable, et que la cellule **A1** est sélectionnée.  Si ce n'est pas le cas, cliquez sur la cellule **A1** pour la sélectionner.  
  
4.  Cliquez sur **OK**.  
  
     La cellule **A1** devient une plage nommée `namedRange1`.  Il n'existe aucune indication visible sur la feuille de calcul, mais `namedRange1` apparaît dans la zone **Nom** \(située juste au\-dessus de la feuille de calcul sur le côté gauche\) lorsque la cellule **A1** est sélectionnée.  
  
5.  Ajoutez un autre contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange> à la cellule **B3**.  
  
6.  Vérifiez que **$B$3** apparaît dans la zone de texte modifiable, et que la cellule **B3** est sélectionnée.  Si ce n'est pas le cas, cliquez sur la cellule **B3** pour la sélectionner.  
  
7.  Cliquez sur **OK**.  
  
     La cellule **B3** devient une plage nommée `namedRange2`.  
  
#### Pour ajouter du texte à votre feuille de calcul  
  
1.  Dans la cellule **A1**, tapez le texte suivant :  
  
     Voici un exemple de contrôle NamedRange.  
  
2.  Dans la cellule **A3** \(à gauche de `namedRange2`\), tapez le texte suivant :  
  
     Événements :  
  
 Dans les sections suivantes, vous écrirez du code qui insère du texte dans `namedRange2` et modifie les propriétés du contrôle `namedRange2` en réponse aux événements <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick>, <xref:Microsoft.Office.Tools.Excel.NamedRange.Change> et <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange> de `namedRange1`.  
  
## Ajout de code pour répondre à l'événement BeforeDoubleClick  
  
#### Pour insérer du texte dans NamedRange2 à partir de l'événement BeforeDoubleClick  
  
1.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur **Sheet1.vb** ou **Sheet1.cs**, puis sélectionnez **Afficher le code**.  
  
2.  Ajoutez du code pour que le gestionnaire d'événements `namedRange1_BeforeDoubleClick` ressemble à ceci :  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#24](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#24)]
     [!code-vb[Trin_VstcoreHostControlsExcel#24](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet1.vb#24)]  
  
3.  En C\#, vous devez ajouter des gestionnaires d'événements pour la plage nommée comme indiqué dans l'événement <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> ci\-dessous.  Pour plus d'informations sur la création de gestionnaires d'événements, consultez [Comment : créer des gestionnaires d'événements dans les projets Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#25](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#25)]  
  
## Ajout de code pour répondre à l'événement Change  
  
#### Pour insérer du texte dans namedRange2 à partir de l'événement Change  
  
1.  Ajoutez du code pour que le gestionnaire d'événements `NamedRange1_Change` ressemble à ceci :  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#26](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#26)]
     [!code-vb[Trin_VstcoreHostControlsExcel#26](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet1.vb#26)]  
  
    > [!NOTE]  
    >  Dans la mesure où le fait de double\-cliquer sur une cellule dans une plage Excel fait passer en mode édition, un événement <xref:Microsoft.Office.Tools.Excel.NamedRange.Change> se produit lorsque la sélection est déplacée en dehors de la plage, même si aucune modification n'a été apportée au texte.  
  
## Ajout de code pour répondre à l'événement SelectionChange  
  
#### Pour insérer du texte dans namedRange2 à partir de l'événement SelectionChange  
  
1.  Ajoutez du code pour que le gestionnaire d'événements **NamedRange1\_SelectionChange** ressemble à ceci :  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#27](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#27)]
     [!code-vb[Trin_VstcoreHostControlsExcel#27](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet1.vb#27)]  
  
    > [!NOTE]  
    >  Dans la mesure où le fait de double\-cliquer sur une cellule dans une plage Excel entraîne le déplacement de la sélection dans la plage, un événement <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange> se produit avant que l'événement <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick> ne se produise.  
  
## Test de l'application  
 Maintenant, vous pouvez tester votre classeur pour vérifier que le texte qui décrit les événements d'un contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange> est inséré dans une autre plage nommée lorsque les événements sont déclenchés.  
  
#### Pour tester votre document  
  
1.  Appuyez sur F5 pour exécuter votre projet.  
  
2.  Placez votre curseur dans `namedRange1` et vérifiez que le texte concernant l'événement <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange> est inséré et qu'un commentaire est inséré dans la feuille de calcul.  
  
3.  Double\-cliquez dans `namedRange1` et vérifiez que le texte concernant les événements <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick> est inséré avec du texte en italique rouge dans `namedRange2`.  
  
4.  Cliquez en dehors de `namedRange1` et notez que l'événement de modification se produit au moment de quitter le mode édition, bien qu'aucune modification n'ait été apportée au texte.  
  
5.  Modifiez le texte dans `namedRange1`.  
  
6.  Cliquez en dehors de `namedRange1` et vérifiez que le texte concernant l'événement <xref:Microsoft.Office.Tools.Excel.NamedRange.Change> est inséré avec du texte bleu dans `namedRange2`.  
  
## Étapes suivantes  
 Cette procédure pas à pas présente les notions de base de la programmation des événements d'un contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange>.  Vous devrez peut\-être ensuite exécuter la tâche suivante :  
  
-   Déploiement du projet.  Pour plus d’informations, consultez [Déploiement d'une solution Office](../vsto/deploying-an-office-solution.md).  
  
## Voir aussi  
 [Vue d'ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)   
 [Automatisation d'Excel à l'aide d'objets étendus](../vsto/automating-excel-by-using-extended-objects.md)   
 [NamedRange, contrôle](../vsto/namedrange-control.md)   
 [Comment : redimensionner les contrôles NamedRange](../vsto/how-to-resize-namedrange-controls.md)   
 [Comment : ajouter des contrôles NamedRange aux feuilles de calcul](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [Limitations de programmation des éléments hôtes et des contrôles hôtes](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Comment : créer des gestionnaires d'événements dans les projets Office](../vsto/how-to-create-event-handlers-in-office-projects.md)  
  
  