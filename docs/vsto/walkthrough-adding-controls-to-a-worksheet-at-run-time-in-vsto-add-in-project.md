---
title: "Proc&#233;dure pas &#224; pas&#160;: ajout de contr&#244;les &#224; une feuille de calcul au moment de l&#39;ex&#233;cution dans un projet de compl&#233;ment VSTO"
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
  - "compléments (développement Office dans Visual Studio), ajouter des contrôles"
  - "compléments d'application (développement Office dans Visual Studio), ajouter des contrôles"
  - "contrôles (développement Office dans Visual Studio), ajouter aux feuilles de calcul au moment de l'exécution"
  - "feuilles de calcul, ajouter des contrôles au moment de l'exécution"
ms.assetid: 4f68677a-4789-4564-b229-02e2d4031a5f
caps.latest.revision: 38
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 37
---
# Proc&#233;dure pas &#224; pas&#160;: ajout de contr&#244;les &#224; une feuille de calcul au moment de l&#39;ex&#233;cution dans un projet de compl&#233;ment VSTO
  Vous pouvez ajouter des contrôles à une feuille de calcul ouverte en utilisant un complément Excel VSTO.  Cette procédure pas à pas montre comment utiliser le ruban pour permettre aux utilisateurs d'ajouter <xref:Microsoft.Office.Tools.Excel.Controls.Button>, <xref:Microsoft.Office.Tools.Excel.NamedRange> et <xref:Microsoft.Office.Tools.Excel.ListObject> à une feuille de calcul.  Pour plus d'informations, consultez [Ajout de contrôles à des documents Office au moment de l'exécution](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
 **S'applique à :** les informations contenues dans cette rubrique s'appliquent aux projets de compléments VSTO pour Excel.  Pour plus d'informations, consultez [Fonctionnalités disponibles par type d'application et de projet Office](../vsto/features-available-by-office-application-and-project-type.md).  
  
 Cette procédure pas à pas décrit les tâches suivantes :  
  
-   Fournit une interface utilisateur permettant d'ajouter des contrôles à la feuille de calcul.  
  
-   Ajout de contrôles à la feuille de calcul.  
  
-   Suppression de contrôles dans la feuille de calcul.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Composants requis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Excel  
  
## Création d'un projet de complément Excel VSTO  
 Commencez par créer un projet de complément Excel VSTO.  
  
#### Pour créer un projet de complément Excel VSTO  
  
1.  Dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], créez un projet de complément Excel VSTO nommé ExcelDynamicControls.  Pour plus d'informations, consultez [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  Ajoutez une référence à l'assembly **Microsoft.Office.Tools.Excel.v4.0.Utilities.dll**.  Cette référence est obligatoire pour ajouter par programmation un contrôle Windows Forms à une feuille de calcul, plus loin dans cette procédure pas à pas.  
  
## Mise à disposition d'une interface utilisateur permettant d'ajouter des contrôles à une feuille de calcul  
 Ajoutez un onglet personnalisé au ruban Excel.  Les utilisateurs peuvent cocher des cases sous l'onglet pour ajouter des contrôles à une feuille de calcul.  
  
#### Pour fournir une interface utilisateur permettant d'ajouter des contrôles à une feuille de calcul  
  
1.  Dans le menu **Projet**, cliquez sur **Ajouter un nouvel élément**.  
  
2.  Dans la boîte de dialogue **Ajouter un nouvel élément**, sélectionnez **Ruban \(Concepteur visuel\)**, puis cliquez sur **Ajouter**.  
  
     Un fichier nommé **Ribbon1.cs** ou **Ribbon1.vb** s'ouvre dans le Concepteur de ruban, puis affiche un onglet et un groupe par défaut.  
  
3.  Sous l'onglet **Contrôles de ruban Office** de la **Boîte à outils**, faites glisser un contrôle CheckBox sur **group1**.  
  
4.  Cliquez sur **CheckBox1** pour le sélectionner.  
  
5.  Dans la fenêtre **Propriétés**, changez les propriétés suivantes.  
  
    |Propriété|Valeur|  
    |---------------|------------|  
    |**Nom**|Bouton|  
    |**Étiquette**|Bouton|  
  
6.  Ajoutez une deuxième case à cocher pour **group1**, puis modifiez les propriétés suivantes.  
  
    |Propriété|Valeur|  
    |---------------|------------|  
    |**Nom**|NamedRange|  
    |**Étiquette**|NamedRange|  
  
7.  Ajoutez une troisième case à cocher pour **group1**, puis modifiez les propriétés suivantes.  
  
    |Propriété|Valeur|  
    |---------------|------------|  
    |**Nom**|ListObject|  
    |**Étiquette**|ListObject|  
  
## Ajout de contrôles à la feuille de calcul  
 Les contrôles managés ne peuvent être ajoutés qu'aux éléments hôtes, lesquels servent de conteneurs.  Dans la mesure où les projets de complément VSTO fonctionnent avec n'importe quel classeur ouvert, le complément VSTO convertit la feuille de calcul en élément hôte, ou récupère un élément hôte existant, avant d'ajouter le contrôle.  Ajoutez du code aux gestionnaires d'événements click de chaque contrôle pour générer un élément hôte <xref:Microsoft.Office.Tools.Excel.Worksheet> basé sur la feuille de calcul ouverte.  Ajoutez ensuite <xref:Microsoft.Office.Tools.Excel.Controls.Button>, <xref:Microsoft.Office.Tools.Excel.NamedRange> et <xref:Microsoft.Office.Tools.Excel.ListObject> à la sélection actuelle dans la feuille de calcul.  
  
#### Pour ajouter des contrôles à une feuille de calcul  
  
1.  Dans le Concepteur de ruban, double\-cliquez sur **Button**.  
  
     Le Gestionnaire d'événements <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click> de la case à cocher **Button** s'ouvre dans l'éditeur de code.  
  
2.  Remplacez le gestionnaire d'événements `Button_Click` par le code suivant.  
  
     Ce code utilise la méthode `GetVstoObject` pour obtenir un élément hôte qui représente la première feuille de calcul du classeur, puis ajoute un contrôle <xref:Microsoft.Office.Tools.Excel.Controls.Button> à la cellule sélectionnée.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/CS/Ribbon1.cs#2)]
     [!code-vb[Trin_Excel_Dynamic_Controls#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/VB/Ribbon1.vb#2)]  
  
3.  Dans l'**Explorateur de solutions**, sélectionnez Ribbon1.cs ou Ribbon1.vb.  
  
4.  Dans le menu **Affichage**, cliquez sur **Concepteur**.  
  
5.  Dans le Concepteur de ruban, double\-cliquez sur **NamedRange**.  
  
6.  Remplacez le gestionnaire d'événements `NamedRange_Click` par le code suivant.  
  
     Ce code utilise la méthode `GetVstoObject` pour obtenir un élément hôte qui représente la première feuille de calcul du classeur, puis définit un contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange> pour la ou les cellules sélectionnées.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/CS/Ribbon1.cs#3)]
     [!code-vb[Trin_Excel_Dynamic_Controls#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/VB/Ribbon1.vb#3)]  
  
7.  Dans le Concepteur de ruban, double\-cliquez sur **ListObject**.  
  
8.  Remplacez le gestionnaire d'événements `ListObject_Click` par le code suivant.  
  
     Ce code utilise la méthode `GetVstoObject` pour obtenir un élément hôte qui représente la première feuille de calcul du classeur, puis définit un <xref:Microsoft.Office.Tools.Excel.ListObject> pour la ou les cellules sélectionnées.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/CS/Ribbon1.cs#4)]
     [!code-vb[Trin_Excel_Dynamic_Controls#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/VB/Ribbon1.vb#4)]  
  
9. Ajoutez les instructions suivantes au début du fichier de code du ruban.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/CS/Ribbon1.cs#1)]
     [!code-vb[Trin_Excel_Dynamic_Controls#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/VB/Ribbon1.vb#1)]  
  
## Suppression de contrôles dans la feuille de calcul  
 Les contrôles ne sont pas conservés quand la feuille de calcul est enregistrée et fermée.  Supprimez par programmation tous les contrôles Windows Forms générés avant que la feuille de calcul ne soit enregistrée. Sinon, seul le contour du contrôle apparaît quand vous rouvrez le classeur.  Ajoutez du code à l'événement <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave> qui supprime les contrôles Windows Forms dans la collection de contrôles de l'élément hôte généré.  Pour plus d'informations, consultez [Rendre des contrôles dynamiques persistants dans des documents Office](../vsto/persisting-dynamic-controls-in-office-documents.md).  
  
#### Pour supprimer des contrôles dans la feuille de calcul  
  
1.  Dans l'**Explorateur de solutions**, sélectionnez ThisAddIn.cs ou ThisAddIn.vb.  
  
2.  Dans le menu **Affichage**, cliquez sur **Code**.  
  
3.  Ajoutez la méthode suivante à la classe ThisAddIn.  Ce code récupère la première feuille de calcul du classeur, puis utilise la méthode `HasVstoObject` pour vérifier si la feuille de calcul possède un objet de feuille de calcul généré.  Si l'objet de feuille de calcul généré possède des contrôles, le code récupère cet objet de feuille de calcul, puis effectue une itération dans la collection de contrôles, en supprimant ces derniers.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/CS/ThisAddIn.cs#6)]
     [!code-vb[Trin_Excel_Dynamic_Controls#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/VB/ThisAddIn.vb#6)]  
  
4.  En C\#, vous devez créer un gestionnaire d'événements pour l'événement <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave>.  Vous pouvez placer ce code dans la méthode `ThisAddIn_Startup`.  Pour plus d'informations sur la création de gestionnaires d'événements, consultez [Comment : créer des gestionnaires d'événements dans les projets Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  Remplacez la méthode `ThisAddIn_Startup` par le code suivant.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/CS/ThisAddIn.cs#5)]  
  
## Test de la solution  
 Ajoutez des contrôles à une feuille de calcul en les sélectionnant à partir d'un onglet personnalisé sur le ruban.  Quand vous enregistrez la feuille de calcul, ces contrôles sont supprimés.  
  
#### Pour tester la solution.  
  
1.  Appuyez sur F5 pour exécuter votre projet.  
  
2.  Sélectionnez n'importe quelle cellule dans Feuil1.  
  
3.  Cliquez sur l'onglet **Compléments**.  
  
4.  Dans **group1**, cliquez sur **Button**.  
  
     Un bouton s'affiche dans la cellule sélectionnée.  
  
5.  Sélectionnez une autre cellule dans Feuil1.  
  
6.  Dans **group1**, cliquez sur **NamedRange**.  
  
     Une plage nommée est définie pour la cellule sélectionnée.  
  
7.  Sélectionnez une série de cellules dans Feuil1.  
  
8.  Dans **group1**, cliquez sur **ListObject**.  
  
     Un objet de liste est ajouté pour les cellules sélectionnées.  
  
9. Enregistrez la feuille de calcul.  
  
     Les contrôles que vous avez ajoutés à Feuil1 ne s'affichent plus.  
  
## Étapes suivantes  
 Pour plus d'informations sur les contrôles dans les projets de complément Excel VSTO, consultez cette rubrique :  
  
-   Pour savoir comment enregistrer des contrôles dans une feuille de calcul, consultez l'exemple de contrôles dynamiques de complément Excel VSTO dans [Exemples et procédures pas à pas relatifs au développement Office](../vsto/office-development-samples-and-walkthroughs.md).  
  
## Voir aussi  
 [Solutions Excel](../vsto/excel-solutions.md)   
 [Vue d'ensemble des contrôles Windows Forms dans les documents Office](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Contrôles sur des documents Office](../vsto/controls-on-office-documents.md)   
 [NamedRange, contrôle](../vsto/namedrange-control.md)   
 [ListObject, contrôle](../vsto/listobject-control.md)  
  
  