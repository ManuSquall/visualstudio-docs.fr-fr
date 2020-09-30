---
title: 'Procédure pas à pas : liaison de données simple dans un projet de complément VSTO'
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Office development in Visual Studio], binding data
- data binding [Office development in Visual Studio], Word
- data [Office development in Visual Studio], simple binding data
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 67264800fd2baa1ca685bcc578fb4d400e6538dd
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91584909"
---
# <a name="walkthrough-simple-data-binding-in-vsto-add-in-project"></a>Procédure pas à pas : liaison de données simple dans un projet de complément VSTO

Vous pouvez lier des données à des contrôles hôtes et des contrôles Windows Forms dans des projets de complément VSTO. Cette procédure pas à pas montre comment ajouter des contrôles à un document Microsoft Office Word et les lier à des données au moment de l’exécution.

[!INCLUDE[appliesto_wdallapp](../vsto/includes/appliesto-wdallapp-md.md)]

Cette procédure pas à pas décrit les tâches suivantes :

- Ajouter un <xref:Microsoft.Office.Tools.Word.ContentControl> à un document au moment de l’exécution.

- Création d’un <xref:System.Windows.Forms.BindingSource> qui connecte le contrôle à une instance d’un dataset.

- Permettre à l’utilisateur de parcourir les enregistrements et de les afficher dans le contrôle.

[!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prérequis

Vous devez disposer des éléments suivants pour exécuter cette procédure pas à pas :

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] ou [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].

- Accès à une instance en cours d’exécution de SQL Server 2005 ou SQL Server 2005 Express à laquelle l’exemple de base de données `AdventureWorksLT` est attaché. Vous pouvez télécharger la `AdventureWorksLT` base de données à partir du [SQL Server exemples GitHub référentiel](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks). Pour plus d’informations sur l’attachement d’une base de données, consultez les rubriques suivantes :

  - Pour attacher une base de données à l’aide d’SQL Server Management Studio ou SQL Server Management Studio Express, consultez [Comment : attacher une base de données (SQL Server Management Studio)](/sql/relational-databases/databases/attach-a-database).

  - Pour attacher une base de données à l’aide de la ligne de commande, consultez [Comment : attacher un fichier de base de données à SQL Server Express](/previous-versions/sql/).

## <a name="create-a-new-project"></a>Créer un projet

La première étape consiste à créer un projet de complément VSTO Word.

### <a name="to-create-a-new-project"></a>Pour créer un projet

1. Créez un projet de complément VSTO Word nommé **Remplissage de documents à partir d’une base de données**, à l’aide de Visual Basic ou C#.

     Pour plus d’informations, consultez [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio ouvre le fichier *ThisAddIn. vb* ou *ThisAddIn.cs* et ajoute le **remplissage de documents à partir d’un projet de base de données** à **Explorateur de solutions**.

2. Si votre projet cible le [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou le [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] , ajoutez une référence à l’assembly *Microsoft.Office.Tools.Word.v4.0.Utilities.dll* . Cette référence est obligatoire pour ajouter par programmation un contrôle Windows Forms au document, plus loin dans cette procédure pas à pas.

## <a name="create-a-data-source"></a>Création d'une source de données

Utilisez la fenêtre **Sources de données** pour ajouter un dataset typé à votre projet.

### <a name="to-add-a-typed-dataset-to-the-project"></a>Pour ajouter un dataset typé au projet

1. Si la fenêtre **sources de données** n’est pas visible, affichez-la en cliquant sur **Afficher**d'  >  **autres**  >  **sources de données**Windows dans la barre de menus.

2. Choisissez **Ajouter une nouvelle source de données** pour démarrer l' **Assistant Configuration de source de données**.

3. Cliquez sur **Base de données**, puis sur **Suivant**.

4. Si vous disposez d’une connexion à la base de données `AdventureWorksLT` , choisissez cette connexion et cliquez sur **Suivant**.

    Sinon, cliquez sur **Nouvelle connexion**et utilisez la boîte de dialogue **Ajouter une connexion** pour créer la connexion. Pour plus d’informations, consultez [ajouter de nouvelles connexions](../data-tools/add-new-connections.md).

5. Dans la page **Enregistrer la chaîne de connexion dans le fichier de configuration de l’application** , cliquez sur **Suivant**.

6. Dans la page **Choisir vos objets de base de données** , développez **Tables** et sélectionnez **Customer (SalesLT)**.

7. Cliquez sur **Terminer**.

    Le fichier *AdventureWorksLTDataSet. xsd* est ajouté à **Explorateur de solutions**. Ce fichier définit les éléments suivants :

   - Un dataset typé nommé `AdventureWorksLTDataSet`. Ce dataset représente le contenu de la table **Customer (SalesLT)** dans la base de données AdventureWorksLT.

   - Un TableAdapter nommé `CustomerTableAdapter` . Ce TableAdapter peut être utilisé pour lire et écrire des données dans le `AdventureWorksLTDataSet` . Pour plus d’informations, consultez [vue d’ensemble de TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview).

     Vous utiliserez ces deux objets ultérieurement dans cette procédure pas à pas.

## <a name="create-controls-and-binding-controls-to-data"></a>Créer des contrôles et lier des contrôles à des données

L’interface d’affichage des enregistrements de base de données dans cette procédure pas à pas est de base et est créée directement à l’intérieur du document. Un <xref:Microsoft.Office.Tools.Word.ContentControl> affiche un enregistrement de base de données à la fois et deux contrôles <xref:Microsoft.Office.Tools.Word.Controls.Button> vous permettent de parcourir les enregistrements. Le contrôle de contenu utilise un <xref:System.Windows.Forms.BindingSource> pour se connecter à la base de données.

Pour plus d’informations sur la liaison des contrôles aux données, consultez [lier des données aux contrôles dans les solutions Office](../vsto/binding-data-to-controls-in-office-solutions.md).

### <a name="to-create-the-interface-in-the-document"></a>Pour créer l’interface dans le document

1. Dans la classe `ThisAddIn` , déclarez les contrôles suivants pour afficher et parcourir la table `Customer` de la base de données `AdventureWorksLTDataSet` .

     [!code-vb[Trin_WordAddInDatabase#1](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#1)]
     [!code-csharp[Trin_WordAddInDatabase#1](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#1)]

2. Dans la méthode `ThisAddIn_Startup` , ajoutez le code suivant pour initialiser le dataset et le remplir avec des informations de la base de données `AdventureWorksLTDataSet` .

     [!code-vb[Trin_WordAddInDatabase#2](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#2)]
     [!code-csharp[Trin_WordAddInDatabase#2](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#2)]

3. Ajoutez le code suivant à la méthode `ThisAddIn_Startup` . Cela génère un élément hôte qui étend le document. Pour plus d’informations, consultez [extension de documents Word et de classeurs Excel dans des compléments VSTO au moment](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)de l’exécution.

     [!code-vb[Trin_WordAddInDatabase#3](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#3)]
     [!code-csharp[Trin_WordAddInDatabase#3](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#3)]

4. Définissez plusieurs plages au début du document. Ces plages identifient où insérer du texte et placer des contrôles.

     [!code-vb[Trin_WordAddInDatabase#4](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#4)]
     [!code-csharp[Trin_WordAddInDatabase#4](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#4)]

5. Ajoutez les contrôles d’interface aux plages précédemment définies.

     [!code-vb[Trin_WordAddInDatabase#5](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#5)]
     [!code-csharp[Trin_WordAddInDatabase#5](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#5)]

6. Liez le contrôle de contenu à `AdventureWorksLTDataSet` à l’aide de <xref:System.Windows.Forms.BindingSource>. Pour les développeurs C# : ajoutez deux gestionnaires d’événements pour les contrôles <xref:Microsoft.Office.Tools.Word.Controls.Button> .

     [!code-vb[Trin_WordAddInDatabase#6](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#6)]
     [!code-csharp[Trin_WordAddInDatabase#6](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#6)]

7. Ajoutez le code suivant pour parcourir les enregistrements de base de données.

     [!code-vb[Trin_WordAddInDatabase#7](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#7)]
     [!code-csharp[Trin_WordAddInDatabase#7](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#7)]

## <a name="test-the-add-in"></a>Tester le complément

Lorsque vous ouvrez Word, le contrôle de contenu affiche des données du dataset `AdventureWorksLTDataSet` . Parcourez les enregistrements de base de données en cliquant sur les boutons **Suivant** et **Précédent** .

### <a name="to-test-the-vsto-add-in"></a>Pour tester le complément VSTO

1. Appuyez sur **F5**.

     Un contrôle de contenu nommé `customerContentControl` est créé et rempli avec des données. Au même moment, un objet dataset nommé `adventureWorksLTDataSet` et un <xref:System.Windows.Forms.BindingSource> nommé `customerBindingSource` sont ajoutés au projet. <xref:Microsoft.Office.Tools.Word.ContentControl> est lié à <xref:System.Windows.Forms.BindingSource>, qui est lui-même lié à l’objet dataset.

2. Cliquez sur les boutons **Suivant** et **Précédent** pour parcourir les enregistrements de base de données.

## <a name="see-also"></a>Voir aussi

- [Données dans les solutions Office](../vsto/data-in-office-solutions.md)
- [Lier des données à des contrôles dans les solutions Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Comment : remplir des feuilles de calcul avec des données d’une base de données](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)
- [Comment : remplir des documents avec des données d’une base de données](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [Comment : remplir des documents avec des données de services](../vsto/how-to-populate-documents-with-data-from-services.md)
- [Comment : remplir des documents avec des données d’objets](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [Comment : faire défiler des enregistrements de base de données dans une feuille de calcul](../vsto/how-to-scroll-through-database-records-in-a-worksheet.md)
- [Comment : mettre à jour une source de données avec les données d’un contrôle hôte](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
- [Procédure pas à pas : liaison de données simple dans un projet au niveau du document](../vsto/walkthrough-simple-data-binding-in-a-document-level-project.md)
- [Procédure pas à pas : liaison de données complexe dans un projet au niveau du document](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md)
- [Vue d’ensemble de l’utilisation des fichiers de base de données locaux dans les solutions Office](../vsto/using-local-database-files-in-office-solutions-overview.md)
- [Ajouter de nouvelles sources de données](../data-tools/add-new-data-sources.md)
- [Lier des contrôles Windows Forms à des données dans Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Comment : remplir des documents avec des données d’objets](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [Comment : mettre à jour une source de données avec les données d’un contrôle hôte](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
- [Vue d’ensemble de l’utilisation des fichiers de base de données locaux dans les solutions Office](../vsto/using-local-database-files-in-office-solutions-overview.md)
- [Vue d’ensemble du composant BindingSource](/dotnet/framework/winforms/controls/bindingsource-component-overview)
