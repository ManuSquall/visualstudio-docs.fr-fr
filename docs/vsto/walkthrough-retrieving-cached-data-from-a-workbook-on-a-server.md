---
title: 'Procédure pas à pas : récupération des données mises en cache d’un classeur sur un serveur'
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks [Office development in Visual Studio], retrieving data
- datasets [Office development in Visual Studio], accessing on server
- server-side data access [Office development in Visual Studio]
- data [Office development in Visual Studio], accessing on server
- documents [Office development in Visual Studio], server-side data access
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 69d5a9932a781260609a0b00c8576c9ecc85ad1d
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91584948"
---
# <a name="walkthrough-retrieve-cached-data-from-a-workbook-on-a-server"></a>Procédure pas à pas : récupération des données mises en cache d’un classeur sur un serveur
  Cette procédure pas à pas montre comment récupérer des données d’un DataSet mis en cache dans un Microsoft Office classeur Excel sans démarrer Excel à l’aide de la <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> classe.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 Cette procédure pas à pas décrit les tâches suivantes :

- Définition d’un DataSet qui contient des données de la base de données *AdventureWorksLT* .

- Création d’instances du DataSet dans un projet de classeur Excel et un projet d’application console.

- Création d’un <xref:Microsoft.Office.Tools.Excel.ListObject> lié au DataSet dans le classeur et remplissage du avec les <xref:Microsoft.Office.Tools.Excel.ListObject> données lorsque le classeur est ouvert.

- Ajout du DataSet dans le classeur au cache de données.

- Lecture des données du DataSet mis en cache dans le jeu de données dans l’application console, sans démarrer Excel.

  Bien que cette procédure pas à pas suppose que vous exécutiez le code sur votre ordinateur de développement, le code présenté dans cette procédure pas à pas peut être utilisé sur un serveur sur lequel Excel n’est pas installé.

> [!NOTE]
> Il est possible que pour certains des éléments de l'interface utilisateur de Visual Studio, votre ordinateur affiche des noms ou des emplacements différents de ceux indiqués dans les instructions suivantes. L'édition de Visual Studio dont vous disposez et les paramètres que vous utilisez déterminent ces éléments. Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Prérequis
 Vous devez disposer des éléments suivants pour exécuter cette procédure pas à pas :

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] ou [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

- Accès à une instance en cours d’exécution de Microsoft SQL Server ou Microsoft SQL Server Express à laquelle l’exemple de base de données AdventureWorksLT est attaché. Vous pouvez télécharger la base de données AdventureWorksLT à partir du [site Web CodePlex](https://archive.codeplex.com/?p=SqlServerSamples). Pour plus d’informations sur l’attachement d’une base de données, consultez les rubriques suivantes :

  - Pour attacher une base de données à l’aide d’SQL Server Management Studio ou SQL Server Management Studio Express, consultez [Comment : attacher une base de données (SQL Server Management Studio)](/sql/relational-databases/databases/attach-a-database).

  - Pour attacher une base de données à l’aide de la ligne de commande, consultez [Comment : attacher un fichier de base de données à SQL Server Express](/previous-versions/sql/).

## <a name="create-a-class-library-project-that-defines-a-dataset"></a>Créer un projet de bibliothèque de classes qui définit un DataSet
 Pour utiliser le même jeu de données dans un projet de classeur Excel et une application console, vous devez définir le jeu de données dans un assembly distinct qui est référencé par ces deux projets. Pour cette procédure pas à pas, définissez le DataSet dans un projet de bibliothèque de classes.

### <a name="create-the-class-library-project"></a>Créer le projet de bibliothèque de classes

1. Démarrez [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Dans le menu **Fichier** , pointez sur **Nouveau**, puis cliquez sur **Projet**.

3. Dans le volet modèles, développez **Visual C#** ou **Visual Basic**, puis cliquez sur **Windows**.

4. Dans la liste des modèles de projet, sélectionnez **bibliothèque de classes**.

5. Dans la zone **nom** , tapez **AdventureWorksDataSet**.

6. Cliquez sur **Parcourir**, accédez à votre dossier *%UserProfile%\My Documents* (pour Windows XP et versions antérieures) ou *%UserProfile%\Documents* (pour Windows Vista), puis cliquez sur **Sélectionner un dossier**.

7. Dans la boîte de dialogue **nouveau projet** , assurez-vous que la case à cocher **créer le répertoire pour la solution** n’est pas activée.

8. Cliquez sur **OK**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Ajoute le projet **AdventureWorksDataSet** à **Explorateur de solutions** et ouvre le fichier de code *Class1.cs* ou *Class1. vb* .

9. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur *Class1.cs* ou *Class1. vb*, puis cliquez sur **supprimer**. Vous n’avez pas besoin de ce fichier pour cette procédure pas à pas.

## <a name="define-a-dataset-in-the-class-library-project"></a>Définir un DataSet dans le projet de bibliothèque de classes
 Définissez un DataSet typé qui contient les données de la base de données AdventureWorksLT pour SQL Server 2005. Plus loin dans cette procédure pas à pas, vous allez référencer ce DataSet à partir d’un projet de classeur Excel et d’un projet d’application console.

 Le DataSet est un *DataSet typé* qui représente les données de la table Product de la base de données AdventureWorksLT. Pour plus d’informations sur les datasets typés, consultez [outils de DataSet dans Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).

### <a name="define-a-typed-dataset-in-the-class-library-project"></a>Définir un DataSet typé dans le projet de bibliothèque de classes

1. Dans **Explorateur de solutions**, cliquez sur le projet **AdventureWorksDataSet** .

2. Si la fenêtre **sources de données** n’est pas visible, affichez-la en cliquant sur **Afficher**d'  >  **autres**  >  **sources de données**Windows dans la barre de menus.

3. Choisissez **Ajouter une nouvelle source de données** pour démarrer l' **Assistant Configuration de source de données**.

4. Cliquez sur **Base de données**, puis sur **Suivant**.

5. Si vous disposez d’une connexion existante à la base de données AdventureWorksLT, choisissez cette connexion et cliquez sur **suivant**.

    Sinon, cliquez sur **Nouvelle connexion**et utilisez la boîte de dialogue **Ajouter une connexion** pour créer la connexion. Pour plus d’informations, consultez [ajouter de nouvelles connexions](../data-tools/add-new-connections.md).

6. Dans la page **Enregistrer la chaîne de connexion dans le fichier de configuration de l’application** , cliquez sur **Suivant**.

7. Dans la page **choisir vos objets de base de données** , développez **tables** et sélectionnez **Product (SalesLT)**.

8. Cliquez sur **Terminer**.

    Le fichier *AdventureWorksLTDataSet. xsd* est ajouté au projet **AdventureWorksDataSet** . Ce fichier définit les éléments suivants :

   - Un dataset typé nommé `AdventureWorksLTDataSet`. Ce jeu de données représente le contenu de la table Product dans la base de données AdventureWorksLT.

   - Un TableAdapter nommé `ProductTableAdapter` . Ce TableAdapter peut être utilisé pour lire et écrire des données dans le `AdventureWorksLTDataSet` . Pour plus d’informations, consultez [vue d’ensemble de TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview).

     Vous utiliserez ces deux objets ultérieurement dans cette procédure pas à pas.

9. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur **AdventureWorksDataSet** , puis cliquez sur **générer**.

     Vérifiez que le projet se génère sans erreur.

## <a name="create-an-excel-workbook-project"></a>Créer un projet de classeur Excel
 Créez un projet de classeur Excel pour l’interface pour les données. Plus loin dans cette procédure pas à pas, vous allez créer un <xref:Microsoft.Office.Tools.Excel.ListObject> qui affiche les données, et vous allez ajouter une instance du DataSet au cache de données dans le classeur.

### <a name="create-the-excel-workbook-project"></a>Créer le projet de classeur Excel

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur la solution **AdventureWorksDataSet** , pointez sur **Ajouter**, puis cliquez sur **nouveau projet**.

2. Dans le volet Modèles, développez **Visual C#** ou **Visual Basic**, puis développez **Office/SharePoint**.

3. Sous le nœud développé **Office/SharePoint** , sélectionnez le nœud **Compléments Office** .

4. Dans la liste des modèles de projet, sélectionnez le projet **Classeur Excel 2010** ou **Classeur Excel 2013** .

5. Dans la zone **nom** , tapez **AdventureWorksReport**. Ne modifiez pas l’emplacement.

6. Cliquez sur **OK**.

     L' **Assistant Projet Visual Studio Tools pour Office** s'ouvre.

7. Assurez-vous que l’option **créer un nouveau document** est sélectionnée, puis cliquez sur **OK**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ouvre le classeur **AdventureWorksReport** dans le concepteur et ajoute le projet **AdventureWorksReport** à **Explorateur de solutions**.

## <a name="add-the-dataset-to-data-sources-in-the-excel-workbook-project"></a>Ajouter le DataSet à des sources de données dans le projet de classeur Excel
 Avant de pouvoir afficher le DataSet dans le classeur Excel, vous devez d’abord ajouter le jeu de données aux sources de données dans le projet de classeur Excel.

1. Dans **Explorateur de solutions**, double-cliquez sur *Sheet1.cs* ou *Feuille1. vb* sous le projet **AdventureWorksReport** .

     Le classeur s’ouvre dans le concepteur.

2. Dans le menu **Données** , cliquez sur **Ajouter une nouvelle source de données**.

     L' **Assistant Configuration de source de données** s’ouvre.

3. Cliquez sur **objet**, puis sur **suivant**.

4. Dans la page **Sélectionner l’objet que vous voulez lier** , cliquez sur **Ajouter une référence**.

5. Sous l’onglet **projets** , cliquez sur **AdventureWorksDataSet** , puis sur **OK**.

6. Sous l’espace de noms **AdventureWorksDataSet** de l’assembly **AdventureWorksDataSet** , cliquez sur **AdventureWorksLTDataSet** , puis sur **Terminer**.

     La fenêtre **sources de données** s’ouvre et **AdventureWorksLTDataSet** est ajouté à la liste des sources de données.

## <a name="create-a-listobject-that-is-bound-to-an-instance-of-the-dataset"></a>Créer un ListObject lié à une instance du DataSet
 Pour afficher le DataSet dans le classeur, créez un <xref:Microsoft.Office.Tools.Excel.ListObject> lié à une instance du DataSet. Pour plus d’informations sur la liaison des contrôles aux données, consultez [lier des données aux contrôles dans les solutions Office](../vsto/binding-data-to-controls-in-office-solutions.md).

1. Dans la fenêtre **sources de données** , développez le nœud **AdventureWorksLTDataSet** sous **AdventureWorksDataSet**.

2. Sélectionnez le nœud **Product** , cliquez sur la flèche déroulante qui s’affiche, puis sélectionnez **ListObject** dans la liste déroulante.

     Si la flèche déroulante n’apparaît pas, vérifiez que le classeur est ouvert dans le concepteur.

3. Faites glisser la table **Product** vers la cellule a1.

     Un <xref:Microsoft.Office.Tools.Excel.ListObject> contrôle nommé `productListObject` est créé sur la feuille de calcul, en commençant par la cellule a1. Au même moment, un objet dataset nommé `adventureWorksLTDataSet` et un <xref:System.Windows.Forms.BindingSource> nommé `productBindingSource` sont ajoutés au projet. <xref:Microsoft.Office.Tools.Excel.ListObject> est lié à <xref:System.Windows.Forms.BindingSource>, qui est lui-même lié à l’objet dataset.

## <a name="add-the-dataset-to-the-data-cache"></a>Ajouter le DataSet au cache de données
 Pour permettre au code en dehors du projet de classeur Excel d’accéder au DataSet dans le classeur, vous devez ajouter le DataSet au cache de données. Pour plus d’informations sur le cache de données, consultez [données mises en cache dans les personnalisations au niveau du document](../vsto/cached-data-in-document-level-customizations.md) et [données du cache](../vsto/caching-data.md).

1. Dans le concepteur, cliquez sur **AdventureWorksLTDataSet**.

2. Dans la fenêtre **Propriétés** , affectez à la propriété **Modifiers** la valeur **public**.

3. Affectez à la propriété **CacheInDocument** la **valeur true**.

## <a name="initialize-the-dataset-in-the-workbook"></a>Initialiser le jeu de données dans le classeur
 Avant de pouvoir récupérer les données du DataSet mis en cache à l’aide de l’application console, vous devez d’abord remplir le DataSet mis en cache avec des données.

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le fichier *Sheet1.cs* ou *Feuille1. vb* , puis cliquez sur **afficher le code**.

2. Remplacez le gestionnaire d'événements `Sheet1_Startup` par le code suivant. Ce code utilise une instance de la `ProductTableAdapter` classe qui est définie dans le projet **AdventureWorksDataSet** pour remplir le DataSet mis en cache avec des données, s’il est actuellement vide.

     [!code-csharp[Trin_CachedDataWalkthroughs#8](../vsto/codesnippet/CSharp/AdventureWorksDataSet/AdventureWorksReport/Sheet1.cs#8)]
     [!code-vb[Trin_CachedDataWalkthroughs#8](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/AdventureWorksReport/Sheet1.vb#8)]

## <a name="checkpoint"></a>Point de contrôle
 Générez et exécutez le projet de classeur Excel pour vous assurer qu’il se compile et s’exécute sans erreur. Cette opération remplit également le DataSet mis en cache et enregistre les données dans le classeur.

### <a name="build-and-run-the-project"></a>Créer et exécuter le projet

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet **AdventureWorksReport** , choisissez **Déboguer**, puis cliquez sur **Démarrer une nouvelle instance**.

     Le projet est généré et le classeur s’ouvre dans Excel. Vérifiez les éléments suivants :

    - Le <xref:Microsoft.Office.Tools.Excel.ListObject> remplissage des données.

    - La valeur de la colonne **ListPrice** pour la première ligne de <xref:Microsoft.Office.Tools.Excel.ListObject> est 1431,5. Plus loin dans cette procédure pas à pas, vous allez utiliser une application console pour modifier les valeurs de la colonne **ListPrice** .

2. Enregistrez le classeur. Ne modifiez pas le nom de fichier ou l’emplacement du classeur.

3. Fermez Excel.

## <a name="create-a-console-application-project"></a>Créer un projet d’application console
 Créez un projet d’application console à utiliser pour modifier les données du DataSet mis en cache dans le classeur.

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur la solution **AdventureWorksDataSet** , pointez sur **Ajouter**, puis cliquez sur **nouveau projet**.

2. Dans le volet **types de projets** , développez **Visual C#** ou **Visual Basic**, puis cliquez sur **Windows**.

3. Dans le volet **Modèles**, sélectionnez **Application console**.

4. Dans la zone **nom** , tapez **DataReader**. Ne modifiez pas l’emplacement.

5. Cliquez sur **OK**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Ajoute le projet **DataReader** à **Explorateur de solutions** et ouvre le fichier de code *Program.cs* ou *Module1. vb* .

## <a name="retrieve-data-from-the-cached-dataset-by-using-the-console-application"></a>Récupérer des données du DataSet mis en cache à l’aide de l’application console
 Utilisez la <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> classe dans l’application console pour lire les données dans un `AdventureWorksLTDataSet` objet local. Pour confirmer que le DataSet local a été initialisé avec les données du DataSet mis en cache, l’application affiche le nombre de lignes dans le jeu de données local.

### <a name="retrieve-data-from-the-cached-dataset"></a>Récupérer les données du DataSet mis en cache

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet **DataReader** , puis cliquez sur **Ajouter une référence**.

2. Sous l’onglet **.net** , sélectionnez **Microsoft. VisualStudio. Tools. applications. ServerDocument**.

3. Cliquez sur **OK**.

4. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet **DataReader** , puis cliquez sur **Ajouter une référence**.

5. Sous l’onglet **projets** , sélectionnez **AdventureWorksDataSet**, puis cliquez sur **OK**.

6. Ouvrez le fichier *Program.cs* ou *Module1. vb* dans l’éditeur de code.

7. Ajoutez le code suivant **à l’aide** de (pour C#) ou de l’instruction **Imports** (pour Visual Basic) en haut du fichier de code.

    [!code-csharp[Trin_CachedDataWalkthroughs#1](../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs#1)]
    [!code-vb[Trin_CachedDataWalkthroughs#1](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb#1)]

8. Ajoutez le code suivant à la méthode `Main` . Ce code déclare les objets suivants :

   - Instance du `AdventureWorksLTDataSet` type qui est définie dans le projet **AdventureWorksDataSet** .

   - Chemin d’accès au classeur AdventureWorksReport dans le dossier Build du projet **AdventureWorksReport** .

   - <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>Objet à utiliser pour accéder au cache de données dans le classeur.

     > [!NOTE]
     > Le code suivant suppose que le classeur est enregistré à l’aide de l’extension *. xlsx* . Si le classeur de votre projet a une extension différente, modifiez le chemin d’accès si nécessaire.

     [!code-csharp[Trin_CachedDataWalkthroughs#10](../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs#10)]
     [!code-vb[Trin_CachedDataWalkthroughs#10](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb#10)]

9. Ajoutez le code suivant à la `Main` méthode, après le code que vous avez ajouté à l’étape précédente. Ce code effectue les tâches suivantes :

   - Elle utilise la <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> propriété de la <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> classe pour accéder au DataSet mis en cache dans le classeur.

   - Il lit les données du DataSet mis en cache dans le jeu de données local.

   - Il affiche le nombre de lignes dans le jeu de données local pour confirmer qu’il contient des données.

     [!code-csharp[Trin_CachedDataWalkthroughs#11](../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs#11)]
     [!code-vb[Trin_CachedDataWalkthroughs#11](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb#11)]

10. Dans le menu **générer** , cliquez sur **générer DataReader**.

## <a name="test-the-project"></a>Tester le projet
 Lorsque vous exécutez l’application console, elle affiche le nombre de lignes dans le jeu de données local.

### <a name="test-the-workbook"></a>Tester le classeur

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet **DataReader** , pointez sur **Déboguer**, puis cliquez sur **Démarrer une nouvelle instance**.

     Vérifiez que l’application signale que le jeu de données local a 295 lignes.

2. Appuyez sur **Entrée** pour fermer l'application.

## <a name="next-steps"></a>Étapes suivantes
 Pour plus d’informations sur l’utilisation des données mises en cache, consultez les rubriques suivantes :

- Modification des données dans un DataSet mis en cache sans démarrer Excel. Pour plus d’informations, consultez [procédure pas à pas : modification des données mises en cache dans un classeur sur un serveur](../vsto/walkthrough-changing-cached-data-in-a-workbook-on-a-server.md).

## <a name="see-also"></a>Voir aussi

- [Procédure pas à pas : insertion de données dans un classeur sur un serveur](../vsto/walkthrough-inserting-data-into-a-workbook-on-a-server.md)
- [Procédure pas à pas : modification des données mises en cache dans un classeur sur un serveur](../vsto/walkthrough-changing-cached-data-in-a-workbook-on-a-server.md)
