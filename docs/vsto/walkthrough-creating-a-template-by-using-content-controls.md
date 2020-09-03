---
title: 'Procédure pas à pas : création d’un modèle à l’aide de contrôles de contenu'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- building blocks [Office development in Visual Studio]
- Word [Office development in Visual Studio], creating documents
- content controls [Office development in Visual Studio], adding to documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ffb7d7f9ad5453d38709802bf5e004c07bb09622
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "71255587"
---
# <a name="walkthrough-create-a-template-by-using-content-controls"></a>Procédure pas à pas : création d’un modèle à l’aide de contrôles de contenu
  Cette procédure pas à pas montre comment créer une personnalisation au niveau du document qui utilise des contrôles de contenu pour créer un contenu structuré et réutilisable dans un modèle Microsoft Office Word.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 Word vous permet de créer une collection de parties de document réutilisables, nommées *blocs de construction*. Cette procédure pas à pas montre comment créer deux tableaux en tant que blocs de construction. Chaque tableau contient plusieurs contrôles de contenu qui peuvent contenir différents types de contenu, tels que du texte brut ou des dates. L'un des tableaux contient des informations sur un employé, et l'autre contient des commentaires des clients.

 Après avoir créé un document à partir du modèle, vous pouvez ajouter l'un de ces tableaux dans le document en utilisant plusieurs objets <xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl> qui affichent les blocs de construction disponibles dans le modèle.

 Cette procédure pas à pas décrit les tâches suivantes :

- Création de tableaux contenant des contrôles de contenu dans un modèle Word au moment du design

- Remplissage par programmation d’un contrôle de contenu de type zone de liste modifiable et d’un contrôle de contenu de type liste déroulante

- Protection d'un tableau spécifié contre toute modification

- Ajout de tableaux à la collection de blocs de construction d'un modèle

- Création d'un contrôle de contenu affichant les blocs de construction disponibles dans le modèle

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prérequis
 Vous devez disposer des éléments suivants pour exécuter cette procédure pas à pas :

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Word.

## <a name="create-a-new-word-template-project"></a>Créer un projet de modèle Word
 Créez un modèle Word pour que les utilisateurs puissent créer aisément leurs propres copies.

### <a name="to-create-a-new-word-template-project"></a>Pour créer un projet de modèle Word

1. Créez un projet de modèle Word portant le nom **MonModèleDeBlocDeConstruction**. Dans l'Assistant, créez un nouveau document dans la solution. Pour plus d’informations, consultez [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ouvre le nouveau modèle Word dans le concepteur et ajoute le projet **MonModèleDeBlocDeConstruction** à **Explorateur de solutions**.

## <a name="create-the-employee-table"></a>Créer la table Employee
 Créez un tableau contenant quatre types différents de contrôles de contenu, dans lequel l'utilisateur peut entrer des informations sur un employé.

### <a name="to-create-the-employee-table"></a>Pour créer le tableau Employé

1. Dans le modèle Word qui est hébergé dans le [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Concepteur, dans le ruban, cliquez sur l’onglet **Insérer** .

2. Dans le groupe **tableaux** , cliquez sur **tableau**et insérez un tableau avec deux colonnes et quatre lignes.

3. Tapez un texte dans la première colonne afin qu'elle se présente de la façon suivante :

   ||
   |-|
   |**Nom de l'employé**|
   |**Date d'embauche**|
   |**Titre**|
   |**Photo**|

4. Cliquez dans la première cellule de la deuxième colonne (en regard de nom de l' **employé**).

5. Dans le ruban, cliquez sur l'onglet **Développeur** .

   > [!NOTE]
   > Si l'onglet **Développeur** n'est pas visible, vous devez tout d'abord l'afficher. Pour plus d’informations, consultez [Comment : afficher l’onglet Développeur sur le ruban](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

6. Dans le groupe **contrôles** , cliquez sur le bouton de **texte** ![PlainTextContentControl](../vsto/media/plaintextcontrol.gif "PlainTextContentControl") pour ajouter un <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> à la première cellule.

7. Cliquez sur la deuxième cellule de la deuxième colonne (à côté de **Date d’embauche**).

8. Dans le groupe **contrôles** , cliquez sur le bouton **Sélecteur de dates** ![DatePickerContentControl](../vsto/media/datepicker.gif "DatePickerContentControl") pour ajouter un <xref:Microsoft.Office.Tools.Word.DatePickerContentControl> à la deuxième cellule.

9. Cliquez sur la troisième cellule de la deuxième colonne (en regard de **titre**).

10. Dans le groupe **contrôles** , cliquez sur le bouton de **zone de liste déroulante** ![ComboBoxContentControl](../vsto/media/combobox.gif "ComboBoxContentControl") pour ajouter un <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> à la troisième cellule.

11. Cliquez sur la dernière cellule de la deuxième colonne (en regard de **image**).

12. Dans le groupe **contrôles** , cliquez sur le bouton **contrôle de contenu d’image** ![PictureContentControl](../vsto/media/pictcontentcontrol.gif "PictureContentControl") pour ajouter un <xref:Microsoft.Office.Tools.Word.PictureContentControl> à la dernière cellule.

## <a name="create-the-customer-feedback-table"></a>Créer le tableau commentaires des clients
 Créez un tableau contenant trois types différents de contrôles de contenu, dans lequel l'utilisateur peut entrer des informations sur les commentaires des clients.

### <a name="to-create-the-customer-feedback-table"></a>Pour créer le tableau Commentaires des clients

1. Dans le modèle Word, cliquez sur la ligne qui suit la table Employee que vous avez ajoutée précédemment, puis appuyez sur **entrée** pour ajouter un nouveau paragraphe.

2. Dans le ruban, cliquez sur l’onglet **Insérer** .

3. Dans le groupe **tableaux** , cliquez sur **tableau**et insérez un tableau avec deux colonnes et trois lignes.

4. Tapez un texte dans la première colonne afin qu'elle se présente de la façon suivante :

   ||
   |-|
   |**Nom du client**|
   |**Satisfaction**|
   |**Commentaires**|

5. Cliquez dans la première cellule de la deuxième colonne (en regard de **nom du client**).

6. Dans le ruban, cliquez sur l'onglet **Développeur** .

7. Dans le groupe **contrôles** , cliquez sur le bouton de **texte** ![PlainTextContentControl](../vsto/media/plaintextcontrol.gif "PlainTextContentControl") pour ajouter un <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> à la première cellule.

8. Cliquez dans la deuxième cellule de la deuxième colonne (en regard de l’évaluation de la **satisfaction**).

9. Dans le groupe **contrôles** , cliquez sur le bouton de **liste déroulante** ![DropDownListContentControl](../vsto/media/dropdownlist.gif "DropDownListContentControl") pour ajouter un <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> à la deuxième cellule.

10. Cliquez dans la dernière cellule de la deuxième colonne (à côté de **Commentaires**).

11. Dans le groupe **contrôles** , cliquez sur le bouton de **texte enrichi** ![RichTextContentControl](../vsto/media/richtextcontrol.gif "RichTextContentControl") pour ajouter un <xref:Microsoft.Office.Tools.Word.RichTextContentControl> à la dernière cellule.

## <a name="populate-the-combo-box-and-drop-down-list-programmatically"></a>Remplir par programmation la zone de liste déroulante et la liste déroulante
 Vous pouvez initialiser des contrôles de contenu au moment du design à l’aide de la fenêtre **Propriétés** dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Vous pouvez également les initialiser au moment de l'exécution, ce qui vous permet de définir leurs états initiaux de manière dynamique. Pour cette procédure pas à pas, utilisez du code pour remplir les entrées dans <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> et <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> au moment de l’exécution afin que vous puissiez voir comment ces objets fonctionnent.

### <a name="to-modify-the-ui-of-the-content-controls-programmatically"></a>Pour modifier par programmation l'interface utilisateur des contrôles de contenu

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur **ThisDocument.cs** ou sur **ThisDocument. vb**, puis cliquez sur **afficher le code**.

2. Ajoutez le code suivant à la classe `ThisDocument` . Ce code déclare plusieurs objets que vous utiliserez ultérieurement dans cette procédure pas à pas.

     [!code-vb[Trin_ContentControlTemplateWalkthrough#1](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#1)]
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#1](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#1)]

3. Ajoutez le code suivant à la méthode `ThisDocument_Startup` de la classe `ThisDocument`. Ce code ajoute des entrées aux contrôles <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> et <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> dans les tableaux, et définit le texte de l'espace réservé affiché dans chacun de ces contrôles avant que l'utilisateur les modifie.

     [!code-vb[Trin_ContentControlTemplateWalkthrough#2](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#2)]
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#2](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#2)]

## <a name="prevent-users-from-editing-the-employee-table"></a>Empêcher les utilisateurs de modifier la table Employee
 Utilisez l'objet <xref:Microsoft.Office.Tools.Word.GroupContentControl> que vous avez déclaré précédemment pour protéger le tableau Employé. Une fois le tableau protégé, les utilisateurs peuvent encore modifier les contrôles de contenu du tableau. Toutefois, ils ne peuvent plus modifier le texte de la première colonne ni modifier le tableau d'une quelconque autre manière, par exemple en ajoutant ou en supprimant des lignes et des colonnes. Pour plus d’informations sur l’utilisation d’un <xref:Microsoft.Office.Tools.Word.GroupContentControl> pour protéger une partie d’un document, consultez [contrôles de contenu](../vsto/content-controls.md).

### <a name="to-prevent-users-from-editing-the-employee-table"></a>Pour empêcher les utilisateurs de modifier le tableau Employé

1. Ajoutez le code suivant à la méthode `ThisDocument_Startup` de la classe `ThisDocument`, après le code que vous avez ajouté à l'étape précédente. Ce code empêche les utilisateurs de modifier le tableau Employé en plaçant celui-ci dans l'objet <xref:Microsoft.Office.Tools.Word.GroupContentControl> que vous avez déclaré précédemment.

     [!code-vb[Trin_ContentControlTemplateWalkthrough#3](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#3)]
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#3](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#3)]

## <a name="add-the-tables-to-the-building-block-collection"></a>Ajouter les tables à la collection de blocs de construction
 Ajoutez les tableaux à une collection de blocs de construction de document dans le modèle afin que les utilisateurs puissent insérer les tableaux que vous avez créés dans le document. Pour plus d’informations sur les blocs de construction de document, consultez [contrôles de contenu](../vsto/content-controls.md).

### <a name="to-add-the-tables-to-the-building-blocks-in-the-template"></a>Pour ajouter les tableaux aux blocs de construction du modèle

1. Ajoutez le code suivant à la méthode `ThisDocument_Startup` de la classe `ThisDocument`, après le code que vous avez ajouté à l'étape précédente. Ce code ajoute de nouveaux blocs de construction qui contiennent les tables à la collection Microsoft. Office. Interop. Word. BuildingBlockEntries, qui contient tous les blocs de construction réutilisables dans le modèle. Les nouveaux blocs de construction sont définis dans une nouvelle catégorie nommée **employé et informations client** et sont affectés au type de bloc de construction `Microsoft.Office.Interop.Word.WdBuildingBlockTypes.wdTypeCustom1` .

     [!code-vb[Trin_ContentControlTemplateWalkthrough#4](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#4)]
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#4](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#4)]

2. Ajoutez le code suivant à la méthode `ThisDocument_Startup` de la classe `ThisDocument`, après le code que vous avez ajouté à l'étape précédente. Ce code supprime les tableaux dans le modèle. Ces tableaux ne sont plus nécessaires car vous les avez ajoutés à la galerie des blocs de construction réutilisables du modèle. Le code place en premier lieu le document en mode Création pour permettre la suppression du tableau protégé Employé.

     [!code-vb[Trin_ContentControlTemplateWalkthrough#5](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#5)]
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#5](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#5)]

## <a name="create-a-content-control-that-displays-the-building-blocks"></a>Créer un contrôle de contenu qui affiche les blocs de construction
 Créez un contrôle de contenu permettant d'accéder aux blocs de construction (autrement dit, aux tableaux) que vous avez créés précédemment. Les utilisateurs peuvent cliquer sur ce contrôle pour ajouter les tableaux dans le document.

### <a name="to-create-a-content-control-that-displays-the-building-blocks"></a>Pour créer un contrôle de contenu affichant les blocs de construction

1. Ajoutez le code suivant à la méthode `ThisDocument_Startup` de la classe `ThisDocument`, après le code que vous avez ajouté à l'étape précédente. Ce code initialise l'objet <xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl> déclaré précédemment. Le <xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl> affiche tous les blocs de construction définis dans la catégorie **informations sur les employés et les clients** , et qui ont le type de bloc de construction `Microsoft.Office.Interop.Word.WdBuildingBlockTypes.wdTypeCustom1` .

     [!code-vb[Trin_ContentControlTemplateWalkthrough#6](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#6)]
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#6](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#6)]

## <a name="test-the-project"></a>Tester le projet
 Les utilisateurs peuvent cliquer sur les contrôles de la galerie des blocs de construction du document pour insérer le tableau Employé ou le tableau Commentaires des clients. Ils peuvent taper ou sélectionner des réponses dans les contrôles de contenu des deux tableaux. Ils peuvent aussi modifier d'autres parties du tableau Commentaires des clients, mais ils ne doivent pas pouvoir modifier d'autres parties du tableau Employé.

### <a name="to-test-the-employee-table"></a>Pour tester le tableau Employé

1. Appuyez sur **F5** pour exécuter le projet.

2. Cliquez sur **choisir votre premier bloc de construction** pour afficher le premier contrôle de contenu de la Galerie des blocs de construction.

3. Cliquez sur la flèche déroulante en regard de l’en-tête **Galerie 1 personnalisée** dans le contrôle, puis sélectionnez **table Employee**.

4. Cliquez dans la cellule située à droite de la cellule **Employee Name** et tapez un nom.

     Vérifiez que vous pouvez ajouter uniquement du texte dans cette cellule. Le contrôle <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> permet aux utilisateurs d'ajouter du texte uniquement, pas d'autres types de contenu tels que des illustrations ou des tableaux.

5. Cliquez dans la cellule située à droite de la cellule **Date d’embauche** et sélectionnez une date dans le sélecteur de dates.

6. Cliquez dans la cellule située à droite de la cellule **titre** et sélectionnez l’une des fonctions dans la zone de liste déroulante.

     Si vous le souhaitez, tapez le nom d'une fonction qui ne figure pas dans la liste. Cela est possible car le contrôle <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> permet aux utilisateurs d'effectuer un choix dans une liste d'entrées ou de taper leurs propres entrées.

7. Cliquez sur l’icône dans la cellule située à droite de la cellule **image** et accédez à une image pour l’afficher.

8. Essayez d'ajouter et de supprimer des lignes et des colonnes dans le tableau. Vérifiez que vous ne pouvez pas modifier le tableau. L'objet <xref:Microsoft.Office.Tools.Word.GroupContentControl> vous empêche d'apporter la moindre modification.

### <a name="to-test-the-customer-feedback-table"></a>Pour tester le tableau Commentaires des clients

1. Cliquez sur **choisir votre deuxième bloc de construction** pour afficher le deuxième contrôle de contenu de la Galerie des blocs de construction.

2. Cliquez sur la flèche déroulante en regard de l’en-tête **Galerie 1 personnalisée** dans le contrôle, puis sélectionnez **table Customer**.

3. Cliquez dans la cellule située à droite de la cellule **nom du client** et tapez un nom.

4. Cliquez dans la cellule située à droite de la cellule évaluation de la **satisfaction** et sélectionnez l’une des options disponibles.

     Vérifiez que vous ne pouvez pas taper votre propre entrée. L'objet <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> permet uniquement aux utilisateurs d'effectuer un choix dans une liste d'entrées.

5. Cliquez dans la cellule située à droite de la cellule **Commentaires** et tapez des commentaires.

     Si vous le souhaitez, ajoutez du contenu autre que du texte, comme une illustration ou un tableau incorporé. Cela est possible car l'objet <xref:Microsoft.Office.Tools.Word.RichTextContentControl> permet aux utilisateurs d'ajouter du contenu autre que du texte.

6. Vérifiez que vous pouvez ajouter et supprimer des lignes et des colonnes dans le tableau. Cela est possible parce que vous n'avez pas protégé le tableau en le plaçant dans un objet <xref:Microsoft.Office.Tools.Word.GroupContentControl>.

7. Fermez le modèle.

## <a name="next-steps"></a>Étapes suivantes
 Pour plus d'informations sur l'utilisation des contrôles de contenu, consultez la rubrique suivante :

- Lier des contrôles de contenu à des fragments XML, ou parties XML personnalisées, qui sont incorporés dans un document. Pour plus d’informations, consultez [procédure pas à pas : liaison de contrôles de contenu à des parties XML personnalisées](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md).

## <a name="see-also"></a>Voir aussi
- [Automatiser Word à l’aide d’objets étendus](../vsto/automating-word-by-using-extended-objects.md)
- [Contrôles de contenu](../vsto/content-controls.md)
- [Comment : ajouter des contrôles de contenu à des documents Word](../vsto/how-to-add-content-controls-to-word-documents.md)
- [Comment : protéger des parties de documents à l’aide de contrôles de contenu](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md)
- [Vue d’ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)
- [Limitations de programmation des éléments hôtes et des contrôles hôtes](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Ajouter des contrôles aux documents Office au moment de l’exécution](../vsto/adding-controls-to-office-documents-at-run-time.md)
