---
title: "Proc&#233;dure pas &#224; pas&#160;: Liaison &#224; des donn&#233;es de service dans un projet de compl&#233;ment VSTO | Microsoft Docs"
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
  - "bases de données (développement Office dans Visual Studio), défilement des enregistrements"
  - "enregistrements (développement Office dans Visual Studio), défilement"
  - "données (développement Office dans Visual Studio), défilement des enregistrements de base de données"
ms.assetid: 9b008be4-06a3-4ffc-9f02-79dd6cfe00ab
caps.latest.revision: 38
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 37
---
# Proc&#233;dure pas &#224; pas&#160;: Liaison &#224; des donn&#233;es de service dans un projet de compl&#233;ment VSTO
  Vous pouvez lier des données à des contrôles hôtes dans les projets de complément VSTO. Cette procédure pas à pas montre comment ajouter des contrôles à un document Microsoft Office Word, comment lier les contrôles aux données extraites du service de contenu MSDN et comment répondre aux événements au moment de l’exécution.  
  
 **S’applique à :** les informations contenues dans cette rubrique s’appliquent aux projets au niveau de l’application pour Word 2010. Pour plus d'informations, consultez [Fonctionnalités disponibles par type d'application et de projet Office](../vsto/features-available-by-office-application-and-project-type.md).  
  
 Cette procédure pas à pas décrit les tâches suivantes :  
  
-   Ajout d’un contrôle <xref:Microsoft.Office.Tools.Word.RichTextContentControl> à un document au moment du design.  
  
-   Liaison du contrôle <xref:Microsoft.Office.Tools.Word.RichTextContentControl> aux données à partir d’un service web.  
  
-   Réponse à l’événement <xref:Microsoft.Office.Tools.Word.ContentControlBase.Entering> d’un contrôle <xref:Microsoft.Office.Tools.Word.RichTextContentControl>.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Composants requis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] ou [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].  
  
## Création d'un projet  
 La première étape consiste à créer un projet de complément VSTO Word.  
  
#### Pour créer un projet  
  
1.  Créez un projet de complément VSTO Word portant le nom **MTPS Content Service**, en Visual Basic ou C\#.  
  
     Pour plus d'informations, consultez [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio ouvre le fichier `ThisAddIn.vb` ou `ThisAddIn.cs` et ajoute le projet à l’**Explorateur de solutions**.  
  
## Ajout d’un service web  
 Pour cette procédure pas à pas, utilisez un service web appelé MTPS Content Service. Ce service web retourne les informations d’un article MSDN spécifié sous la forme d’une chaîne XML ou de texte brut. Une étape ultérieure indique comment afficher les informations retournées dans un contrôle de contenu.  
  
#### Pour ajouter MTPS Content Service au projet  
  
1.  Dans le menu **Données**, cliquez sur **Ajouter une nouvelle source de données**.  
  
2.  Dans l’**Assistant Configuration de source de données**, cliquez sur **Service**, puis sur **Suivant**.  
  
3.  Dans le champ **Adresse**, tapez l’URL suivante :  
  
     **http:\/\/services.msdn.microsoft.com\/ContentServices\/ContentService.asmx**  
  
4.  Cliquez sur **OK**.  
  
5.  Dans le champ **Espace de noms**, tapez **ContentService**, puis cliquez sur **OK**.  
  
6.  Dans la boîte de dialogue **Assistant Ajout de référence** , cliquez sur **Terminer**.  
  
## Ajout d’un contrôle de contenu et liaison de données au moment de l’exécution  
 Dans les projets de complément VSTO, vous ajoutez et liez des contrôles au moment de l’exécution. Pour cette procédure pas à pas, configurez le contrôle de contenu pour extraire des données du service web quand un utilisateur clique sur le contrôle.  
  
#### Pour ajouter un contrôle de contenu et le lier à des données  
  
1.  Dans la classe `ThisAddIn`, déclarez les variables de MTPS Content Service, du contrôle de contenu et de la liaison de données.  
  
     [!code-csharp[Trin_WordAddIn_BindingDataToContentControl#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddIn_BindingDataToContentControl/CS/ThisAddIn.cs#2)]
     [!code-vb[Trin_WordAddIn_BindingDataToContentControl#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddIn_BindingDataToContentControl/VB/ThisAddIn.vb#2)]  
  
2.  Ajoutez la méthode suivante à la classe `ThisAddIn`. Cette méthode crée un contrôle de contenu au début du document actif.  
  
     [!code-csharp[Trin_WordAddIn_BindingDataToContentControl#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddIn_BindingDataToContentControl/CS/ThisAddIn.cs#4)]
     [!code-vb[Trin_WordAddIn_BindingDataToContentControl#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddIn_BindingDataToContentControl/VB/ThisAddIn.vb#4)]  
  
3.  Ajoutez la méthode suivante à la classe `ThisAddIn`. Cette méthode initialise les objets requis pour créer et envoyer une requête au service web.  
  
     [!code-csharp[Trin_WordAddIn_BindingDataToContentControl#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddIn_BindingDataToContentControl/CS/ThisAddIn.cs#6)]
     [!code-vb[Trin_WordAddIn_BindingDataToContentControl#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddIn_BindingDataToContentControl/VB/ThisAddIn.vb#6)]  
  
4.  Créez un gestionnaire d’événements pour extraire le document de la Bibliothèque MSDN sur les contrôles de contenu quand un utilisateur clique sur le contrôle de contenu et liez les données au contrôle de contenu.  
  
     [!code-csharp[Trin_WordAddIn_BindingDataToContentControl#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddIn_BindingDataToContentControl/CS/ThisAddIn.cs#5)]
     [!code-vb[Trin_WordAddIn_BindingDataToContentControl#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddIn_BindingDataToContentControl/VB/ThisAddIn.vb#5)]  
  
5.  Appelez les méthodes `AddRichTextControlAtRange` et `InitializeServiceObjects` à partir de la méthode `ThisAddIn_Startup`. Programmeurs C\#, ajoutez un gestionnaire d’événements.  
  
     [!code-csharp[Trin_WordAddIn_BindingDataToContentControl#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddIn_BindingDataToContentControl/CS/ThisAddIn.cs#3)]
     [!code-vb[Trin_WordAddIn_BindingDataToContentControl#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddIn_BindingDataToContentControl/VB/ThisAddIn.vb#3)]  
  
## Test du complément  
 Quand vous ouvrez Word, le contrôle <xref:Microsoft.Office.Tools.Word.RichTextContentControl> apparaît. Le texte du contrôle change quand vous cliquez dessus.  
  
#### Pour tester le complément VSTO  
  
1.  Appuyez sur **F5**.  
  
2.  Cliquez à l’intérieur du contrôle de contenu.  
  
     Les informations sont téléchargées depuis MTPS Content Service et elles s’affichent dans le contrôle de contenu.  
  
## Voir aussi  
 [Liaison de données aux contrôles dans les solutions Office](../vsto/binding-data-to-controls-in-office-solutions.md)  
  
  