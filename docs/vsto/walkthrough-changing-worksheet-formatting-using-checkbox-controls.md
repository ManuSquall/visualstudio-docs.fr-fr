---
title: "Proc&#233;dure pas &#224; pas&#160;: modification de la mise en forme d&#39;une feuille de calcul &#224; l&#39;aide de contr&#244;les CheckBox | Microsoft Docs"
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
  - "contrôles (développement Office dans Visual Studio), ajouter à des feuilles de calcul"
  - "feuilles de calcul, modifier la mise en forme à l'aide de contrôles managés"
  - "feuilles de calcul, contrôles check box"
ms.assetid: 4be79613-50a0-428e-9816-aadbc098272a
caps.latest.revision: 70
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 69
---
# Proc&#233;dure pas &#224; pas&#160;: modification de la mise en forme d&#39;une feuille de calcul &#224; l&#39;aide de contr&#244;les CheckBox
  Cette procédure pas à pas présente les notions de base de l'utilisation de cases à cocher dans une feuille de calcul Microsoft Office Excel pour modifier la mise en forme.  Vous utiliserez des outils de développement Office dans Visual Studio pour créer et ajouter du code à votre projet.  Pour consulter le résultat sous forme d'exemple terminé, consultez les exemples de contrôles Excel dans [Exemples et procédures pas à pas relatifs au développement Office](../vsto/office-development-samples-and-walkthroughs.md).  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 Au cours de cette procédure pas à pas, vous apprendrez à :  
  
-   ajouter du texte et des contrôles à une feuille de calcul ;  
  
-   mettre en forme du texte lorsqu'une option est sélectionnée ;  
  
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
  
1.  Créez un projet de classeur Excel et attribuez\-lui le nom My Excel Formatting.  Assurez\-vous d'avoir sélectionné **Créer un nouveau document**.  Pour plus d’informations, consultez [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio ouvre le nouveau classeur Excel dans le concepteur et ajoute le projet **My Excel Formatting** à l'**Explorateur de solutions**.  
  
## Ajout de texte et de contrôles à la feuille de calcul  
 Pour cette procédure pas à pas, vous aurez besoin de trois contrôles <xref:Microsoft.Office.Tools.Excel.Controls.CheckBox> et de texte dans un contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange>.  
  
#### Pour ajouter trois cases à cocher  
  
1.  Vérifiez que le classeur est ouvert dans le concepteur Visual Studio et que `Sheet1` est ouvert.  
  
2.  À partir de l'onglet **Contrôles communs** de la **Boîte à outils**, faites glisser un contrôle <xref:Microsoft.Office.Tools.Excel.Controls.CheckBox> sur ou à côté de la cellule **B2** dans **Sheet1**.  
  
3.  Dans le menu **Affichage**, sélectionnez la fenêtre **Propriétés**.  
  
4.  Assurez\-vous que **Checkbox1** est visible dans la zone de liste de nom d'objet de la fenêtre **Propriétés** et modifiez les propriétés suivantes :  
  
    |Propriété|Valeur|  
    |---------------|------------|  
    |**Nom**|**applyBoldFont**|  
    |**du texte ;**|Bold|  
  
5.  Faites glisser une deuxième case à cocher sur ou à côté de la cellule **B4** et modifiez les propriétés suivantes :  
  
    |Propriété|Valeur|  
    |---------------|------------|  
    |**Nom**|**applyItalicFont**|  
    |**du texte ;**|Italique|  
  
6.  Faites glisser une troisième case à cocher sur ou à côté de la cellule **B6** et modifiez les propriétés suivantes :  
  
    |Propriété|Valeur|  
    |---------------|------------|  
    |**Nom**|**applyUnderlineFont**|  
    |**du texte ;**|Souligné|  
  
7.  Sélectionnez les trois contrôles Check Box en maintenant enfoncée la touche CTRL.  
  
8.  Dans le groupe de réorganisation de l'onglet de format dans Excel, cliquez **Aligner**, puis cliquez **Aligner à gauche**.  
  
     Les trois contrôles Check Box sont alignés à gauche, à la position du premier contrôle sélectionné.  
  
     Ensuite, faites glisser un contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange> jusqu'à la feuille de calcul.  
  
    > [!NOTE]  
    >  Vous pouvez également ajouter le contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange> en tapant **textFont** dans la zone **Nom**.  
  
#### Pour ajouter du texte à un contrôle NamedRange  
  
1.  À partir de l'onglet **Contrôles Excel** de la boîte à outils, faites glisser un contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange> vers la cellule **B9**.  
  
2.  Vérifiez que **$B$9** apparaît dans la zone de texte modifiable, et que la cellule **B9** est sélectionnée.  Si ce n'est pas le cas, cliquez sur la cellule **B9** pour la sélectionner.  
  
3.  Cliquez sur **OK**.  
  
4.  La cellule **B9** devient une plage nommée `NamedRange1`.  
  
     Il n'existe aucune indication visible sur la feuille de calcul, mais `NamedRange1` apparaît dans la zone **Nom** \(juste au\-dessus de la feuille de calcul sur le côté gauche\) lorsque la cellule **B9** est sélectionnée.  
  
5.  Assurez\-vous que **NamedRange1** est visible dans la zone de liste de nom d'objet de la fenêtre **Propriétés** et modifiez les propriétés suivantes :  
  
    |Propriété|Valeur|  
    |---------------|------------|  
    |**Nom**|**textFont**|  
    |**Value2**|Activez une case à cocher pour modifier la mise en forme de ce texte.|  
  
 L'étape suivante consiste à mettre en forme le texte lorsqu'une option est sélectionnée.  
  
## Mise en forme du texte lorsqu'une option est sélectionnée  
 Dans cette section, vous écrirez du code de sorte que lorsque l'utilisateur sélectionne une option de mise en forme, le format du texte dans la feuille de calcul soit modifié.  
  
#### Pour modifier la mise en forme lorsqu'une case à cocher est activée  
  
1.  Cliquez avec le bouton droit sur **Sheet1**, puis cliquez sur **Afficher le code** dans le menu contextuel.  
  
2.  Ajoutez le code suivant au gestionnaire d'événements <xref:System.Windows.Forms.Control.Click> de la case à cocher `applyBoldFont` :  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#7](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/Sheet1.cs#7)]
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#7](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/VB/Sheet1.vb#7)]  
  
3.  Ajoutez le code suivant au gestionnaire d'événements <xref:System.Windows.Forms.Control.Click> de la case à cocher `applyItalicFont` :  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#8](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/Sheet1.cs#8)]
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#8](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/VB/Sheet1.vb#8)]  
  
4.  Ajoutez le code suivant au gestionnaire d'événements <xref:System.Windows.Forms.Control.Click> de la case à cocher `applyUnderlineFont` :  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#9](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/Sheet1.cs#9)]
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#9](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/VB/Sheet1.vb#9)]  
  
5.  En C\#, vous devez ajouter des gestionnaires d'événements pour les cases à cocher à l'événement <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> comme indiqué ci\-dessous.  Pour plus d'informations sur la création de gestionnaires d'événements, consultez [Comment : créer des gestionnaires d'événements dans les projets Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/Sheet1.cs#10)]  
  
## Test de l'application  
 Vous pouvez maintenant tester votre classeur et vous assurer que le texte est correctement mis en forme lorsque vous activez ou désactivez une case à cocher.  
  
#### Pour tester votre classeur  
  
1.  Appuyez sur F5 pour exécuter votre projet.  
  
2.  Activez ou désactivez une case à cocher.  
  
3.  Vérifiez que le texte est correctement mis en forme.  
  
## Étapes suivantes  
 Cette procédure pas à pas présente les notions de base de l'utilisation des cases à cocher et de la mise en forme de texte dans les feuilles de calcul Excel.  Vous devrez peut\-être ensuite exécuter les opérations suivantes :  
  
-   Déploiement du projet.  Pour plus d’informations, consultez [Déploiement d'une solution Office à l'aide de ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).  
  
-   Utilisation d'un bouton pour remplir une zone de texte.  Pour plus d’informations, consultez [Procédure pas à pas : affichage de texte dans une zone de texte d'une feuille de calcul à l'aide d'un bouton](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md).  
  
## Voir aussi  
 [Procédures pas à pas utilisant Excel](../vsto/walkthroughs-using-excel.md)   
 [NamedRange, contrôle](../vsto/namedrange-control.md)   
 [Limitations des contrôles Windows Forms dans les documents Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
  
  