---
title: Lier à des données à partir d’un service dans un projet de complément VSTO
description: Apprenez à ajouter des contrôles à un document Microsoft Word, à lier les contrôles aux données récupérées à partir du service de contenu MSDN et à répondre aux événements au moment de l’exécution.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- databases [Office development in Visual Studio], scrolling records
- records [Office development in Visual Studio], scrolling
- data [Office development in Visual Studio], scrolling database records
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6b65308cfc0ba4dee33dd6b20d3fd4028e9ea22e
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97527485"
---
# <a name="walkthrough-bind-to-data-from-a-service-in-a-vsto-add-in-project"></a>Procédure pas à pas : liaison à des données à partir d’un service dans un projet de complément VSTO
  Vous pouvez lier des données à des contrôles hôtes dans les projets de complément VSTO. Cette procédure pas à pas montre comment ajouter des contrôles à un document Microsoft Office Word, comment lier les contrôles aux données extraites du service de contenu MSDN et comment répondre aux événements au moment de l’exécution.

 **S’applique à :** les informations contenues dans cette rubrique s’appliquent aux projets au niveau de l’application pour Word 2010. Pour plus d'informations, consultez [Features Available by Office Application and Project Type](../vsto/features-available-by-office-application-and-project-type.md).

 Cette procédure pas à pas décrit les tâches suivantes :

- Ajout d’un contrôle <xref:Microsoft.Office.Tools.Word.RichTextContentControl> à un document au moment du design.

- Liaison du <xref:Microsoft.Office.Tools.Word.RichTextContentControl> contrôle aux données d’un service Web.

- Réponse à l’événement <xref:Microsoft.Office.Tools.Word.ContentControlBase.Entering> d’un contrôle <xref:Microsoft.Office.Tools.Word.RichTextContentControl> .

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prérequis
 Vous devez disposer des éléments suivants pour exécuter cette procédure pas à pas :

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] ou [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].

## <a name="create-a-new-project"></a>Créer un projet
 La première étape consiste à créer un projet de complément VSTO Word.

### <a name="to-create-a-new-project"></a>Pour créer un projet

1. Créez un projet de complément VSTO Word portant le nom **MTPS Content Service**, en Visual Basic ou C#.

     Pour plus d’informations, consultez [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio ouvre le fichier `ThisAddIn.vb` ou `ThisAddIn.cs` et ajoute le projet à l’ **Explorateur de solutions**.

## <a name="add-a-web-service"></a>Ajouter un service Web
 Pour cette procédure pas à pas, utilisez un service Web appelé MTPS Content Service. Ce service Web retourne les informations d’un article MSDN spécifié sous la forme d’une chaîne XML ou d’un texte brut. Une étape ultérieure indique comment afficher les informations retournées dans un contrôle de contenu.

### <a name="to-add-the-mtps-content-service-to-the-project"></a>Pour ajouter MTPS Content Service au projet

1. Dans le menu **Données** , cliquez sur **Ajouter une nouvelle source de données**.

2. Dans l’ **Assistant Configuration de source de données**, cliquez sur **Service**, puis sur **Suivant**.

3. Dans le champ **Adresse** , tapez l’URL suivante :

   `http://services.msdn.microsoft.com/ContentServices/ContentService.asmx`

4. Cliquez sur **Atteindre**.

5. Dans le champ **Espace de noms** , tapez **ContentService**, puis cliquez sur **OK**.

6. Dans la boîte de dialogue **Assistant Ajout de référence** , cliquez sur **Terminer**.

## <a name="add-a-content-control-and-bind-to-data-at-run-time"></a>Ajouter un contrôle de contenu et effectuer une liaison à des données au moment de l’exécution
 Dans les projets de complément VSTO, vous ajoutez et liez des contrôles au moment de l’exécution. Pour cette procédure pas à pas, configurez le contrôle de contenu pour récupérer des données du service Web lorsqu’un utilisateur clique à l’intérieur du contrôle.

### <a name="to-add-a-content-control-and-bind-to-data"></a>Pour ajouter un contrôle de contenu et le lier à des données

1. Dans la classe `ThisAddIn` , déclarez les variables de MTPS Content Service, du contrôle de contenu et de la liaison de données.

     [!code-csharp[Trin_WordAddIn_BindingDataToContentControl#2](../vsto/codesnippet/CSharp/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.cs#2)]
     [!code-vb[Trin_WordAddIn_BindingDataToContentControl#2](../vsto/codesnippet/VisualBasic/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.vb#2)]

2. Ajoutez la méthode suivante à la classe `ThisAddIn`. Cette méthode crée un contrôle de contenu au début du document actif.

     [!code-csharp[Trin_WordAddIn_BindingDataToContentControl#4](../vsto/codesnippet/CSharp/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.cs#4)]
     [!code-vb[Trin_WordAddIn_BindingDataToContentControl#4](../vsto/codesnippet/VisualBasic/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.vb#4)]

3. Ajoutez la méthode suivante à la classe `ThisAddIn`. Cette méthode initialise les objets nécessaires à la création et à l’envoi d’une demande au service Web.

     [!code-csharp[Trin_WordAddIn_BindingDataToContentControl#6](../vsto/codesnippet/CSharp/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.cs#6)]
     [!code-vb[Trin_WordAddIn_BindingDataToContentControl#6](../vsto/codesnippet/VisualBasic/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.vb#6)]

4. Créez un gestionnaire d’événements pour extraire le document de la Bibliothèque MSDN sur les contrôles de contenu quand un utilisateur clique sur le contrôle de contenu et liez les données au contrôle de contenu.

     [!code-csharp[Trin_WordAddIn_BindingDataToContentControl#5](../vsto/codesnippet/CSharp/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.cs#5)]
     [!code-vb[Trin_WordAddIn_BindingDataToContentControl#5](../vsto/codesnippet/VisualBasic/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.vb#5)]

5. Appelez les méthodes `AddRichTextControlAtRange` et `InitializeServiceObjects` à partir de la méthode `ThisAddIn_Startup` . Programmeurs C#, ajoutez un gestionnaire d’événements.

     [!code-csharp[Trin_WordAddIn_BindingDataToContentControl#3](../vsto/codesnippet/CSharp/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.cs#3)]
     [!code-vb[Trin_WordAddIn_BindingDataToContentControl#3](../vsto/codesnippet/VisualBasic/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.vb#3)]

## <a name="test-the-add-in"></a>Tester le complément
 Quand vous ouvrez Word, le contrôle <xref:Microsoft.Office.Tools.Word.RichTextContentControl> apparaît. Le texte du contrôle change quand vous cliquez dessus.

### <a name="to-test-the-vsto-add-in"></a>Pour tester le complément VSTO

1. Appuyez sur **F5**.

2. Cliquez à l’intérieur du contrôle de contenu.

     Les informations sont téléchargées depuis MTPS Content Service et elles s’affichent dans le contrôle de contenu.

## <a name="see-also"></a>Voir aussi
- [Lier des données à des contrôles dans les solutions Office](../vsto/binding-data-to-controls-in-office-solutions.md)
