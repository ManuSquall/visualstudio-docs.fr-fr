---
title: "Proc&#233;dure pas&#160;&#224;&#160;pas&#160;: affichage de texte dans une zone de texte d&#39;une feuille de calcul &#224; l&#39;aide d&#39;un bouton | Microsoft Docs"
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
  - "texte (développement Office dans Visual Studio), afficher dans des feuilles de calcul"
  - "texte (développement Office dans Visual Studio), zones de texte"
  - "zones de texte, afficher du texte dans des feuilles de calcul"
  - "feuilles de calcul, afficher du texte"
ms.assetid: 59b73159-aab7-4f61-9ace-1723c18d78d6
caps.latest.revision: 56
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 55
---
# Proc&#233;dure pas&#160;&#224;&#160;pas&#160;: affichage de texte dans une zone de texte d&#39;une feuille de calcul &#224; l&#39;aide d&#39;un bouton
  Cette procédure pas à pas explique l'utilisation de base des boutons et des zones de texte des feuilles de calcul Microsoft Office Excel et comment créer des projets Excel à l'aide d'outils de développement Office dans Visual Studio.  Pour consulter le résultat sous forme d'exemple terminé, consultez les exemples de contrôles Excel dans [Exemples et procédures pas à pas relatifs au développement Office](../vsto/office-development-samples-and-walkthroughs.md).  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 Au cours de cette procédure pas à pas, vous apprendrez à :  
  
-   ajouter des contrôles à une feuille de calcul ;  
  
-   remplir une zone de texte lorsque l'utilisateur clique sur un bouton ;  
  
-   tester votre projet.  
  
> [!NOTE]  
>  Il est possible que pour certains des éléments de l'interface utilisateur de Visual Studio, votre ordinateur affiche des noms ou des emplacements différents de ceux indiqués dans les instructions suivantes.  Ces éléments dépendent de l'édition de Visual Studio dont vous disposez et des paramètres que vous utilisez.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Composants requis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] ou [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
## Création du projet  
 Dans cette étape, vous allez créer un projet de classeur Excel à l'aide de Visual Studio.  
  
#### Pour créer un projet  
  
1.  Créez un projet de classeur Excel et attribuez\-lui le nom My Excel Button.  Assurez\-vous d'avoir sélectionné **Créer un nouveau document**.  Pour plus d'informations, consultez [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio ouvre le nouveau classeur Excel dans le concepteur et ajoute le projet **My Excel Button** à l'**Explorateur de solutions**.  
  
## Ajout de contrôles à la feuille de calcul  
 Pour cette procédure pas à pas, la première feuille de calcul doit comporter un bouton et une zone de texte.  
  
#### Pour ajouter un bouton et une zone de texte  
  
1.  Vérifiez que le classeur **My Excel Button.xlsx** est ouvert dans le concepteur Visual Studio, avec `Sheet1` a affiché.  
  
2.  À partir de l'onglet **Contrôles communs** de la boîte à outils, faites glisser un <xref:Microsoft.Office.Tools.Excel.Controls.TextBox> vers `Sheet1`.  
  
3.  Dans le menu **Affichage**, sélectionnez **Fenêtre Propriétés**.  
  
4.  Assurez\-vous que **TextBox1** est visible dans la liste déroulante de la fenêtre **Propriétés** et remplacez la valeur de la propriété **Name** de la zone de texte par **displayText**.  
  
5.  Faites glisser un contrôle **Button** vers `Sheet1` et modifiez les propriétés suivantes :  
  
    |Propriété|Valeur|  
    |---------------|------------|  
    |**Nom**|**insertText**|  
    |**du texte ;**|Insérer du texte|  
  
 L'étape suivante consiste à écrire le code à exécuter lorsque l'utilisateur clique sur le bouton.  
  
## Remplissage de la zone de texte lorsque l'utilisateur clique sur le bouton  
 Lorsque l'utilisateur clique sur le bouton, **Hello World\!** est ajouté à la zone de texte.  
  
#### Pour écrire dans la zone de texte lorsque l'utilisateur clique sur le bouton  
  
1.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur **Sheet1**, puis cliquez sur **Afficher le code** dans le menu contextuel.  
  
2.  Ajoutez le code suivant au gestionnaire d'événements <xref:System.Windows.Forms.Control.Click> du bouton :  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#11](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/Sheet1.cs#11)]
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#11](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/VB/Sheet1.vb#11)]  
  
3.  En C\#, vous devez ajouter un gestionnaire d'événements à l'événement <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> comme indiqué ci\-dessous.  Pour plus d'informations sur la création de gestionnaires d'événements, consultez [Comment : créer des gestionnaires d'événements dans les projets Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#12](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/Sheet1.cs#12)]  
  
## Test de l'application  
 Vous pouvez maintenant tester votre classeur pour vérifier que le message **Hello World\!** apparaît dans la zone de texte lorsque vous cliquez sur le bouton.  
  
#### Pour tester votre classeur  
  
1.  Appuyez sur F5 pour exécuter votre projet.  
  
2.  Cliquez sur le bouton.  
  
3.  Vérifiez que **Hello World\!** apparaît dans la zone de texte.  
  
## Étapes suivantes  
 Cette procédure pas à pas présente les notions de base de l'utilisation des boutons et des zones de texte dans les feuilles de calcul Excel.  Vous devrez peut\-être ensuite exécuter les opérations suivantes :  
  
-   Déploiement du projet.  Pour plus d'informations, consultez [Déploiement d'une solution Office](../vsto/deploying-an-office-solution.md).  
  
-   Utilisation des cases à cocher pour modifier la mise en forme.  Pour plus d'informations, consultez [Procédure pas à pas : modification de la mise en forme d'une feuille de calcul à l'aide de contrôles CheckBox](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md).  
  
## Voir aussi  
 [Comment : ajouter des contrôles Windows Forms à des documents Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [Procédures pas à pas utilisant Excel](../vsto/walkthroughs-using-excel.md)   
 [Limitations des contrôles Windows Forms dans les documents Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
  
  