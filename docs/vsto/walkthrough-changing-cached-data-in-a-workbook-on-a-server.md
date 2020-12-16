---
title: 'Procédure pas à pas : modification des données mises en cache dans un classeur sur un serveur'
description: Découvrez comment modifier un jeu de données mis en cache dans un classeur Microsoft Excel sans démarrer Excel à l’aide de la classe ServerDocument.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks [Office development in Visual Studio], changing server data
- datasets [Office development in Visual Studio], accessing on server
- server-side data access [Office development in Visual Studio]
- data [Office development in Visual Studio], accessing on server
- documents [Office development in Visual Studio], server-side data access
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 01ae4894d76e22f619bf498b4ac6a53f1232b5d5
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97527272"
---
# <a name="walkthrough-change-cached-data-in-a-workbook-on-a-server"></a>Procédure pas à pas : modification des données mises en cache dans un classeur sur un serveur
  Cette procédure pas à pas montre comment modifier un DataSet mis en cache dans un Microsoft Office classeur Excel sans démarrer Excel à l’aide de la <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> classe.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

 Cette procédure pas à pas décrit les tâches suivantes :

- Définition d’un DataSet qui contient des données de la base de données AdventureWorksLT.

- Création d’instances du DataSet dans un projet de classeur Excel et un projet d’application console.

- Création d’un <xref:Microsoft.Office.Tools.Excel.ListObject> lié au DataSet dans le classeur et remplissage du avec les <xref:Microsoft.Office.Tools.Excel.ListObject> données lorsque le classeur est ouvert.

- Ajout du DataSet dans le classeur au cache de données.

- Modification d’une colonne de données dans le DataSet mis en cache en exécutant le code dans l’application console, sans démarrer Excel.

  Bien que cette procédure pas à pas suppose que vous exécutiez le code sur votre ordinateur de développement, le code présenté dans cette procédure pas à pas peut être utilisé sur un serveur sur lequel Excel n’est pas installé.

> [!NOTE]
> Il est possible que pour certains des éléments de l'interface utilisateur de Visual Studio, votre ordinateur affiche des noms ou des emplacements différents de ceux indiqués dans les instructions suivantes. L'édition de Visual Studio dont vous disposez et les paramètres que vous utilisez déterminent ces éléments. Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Prérequis
 Vous devez disposer des éléments suivants pour exécuter cette procédure pas à pas :

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

- Accès à une instance en cours d’exécution de Microsoft SQL Server ou Microsoft SQL Server Express à laquelle l’exemple de base de données AdventureWorksLT est attaché. Vous pouvez télécharger la base de données AdventureWorksLT à partir du [SQL Server exemples GitHub référentiel](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks). Pour plus d’informations sur l’attachement d’une base de données, consultez les rubriques suivantes :

  - Pour attacher une base de données à l’aide d’SQL Server Management Studio ou SQL Server Management Studio Express, consultez [Comment : attacher une base de données (SQL Server Management Studio)](/sql/relational-databases/databases/attach-a-database).

  - Pour attacher une base de données à l’aide de la ligne de commande, consultez [Comment : attacher un fichier de base de données à SQL Server Express](/previous-versions/sql/).

## <a name="create-a-class-library-project-that-defines-a-dataset"></a>Créer un projet de bibliothèque de classes qui définit un DataSet
 Pour utiliser le même jeu de données dans un projet de classeur Excel et une application console, vous devez définir le jeu de données dans un assembly distinct qui est référencé par ces deux projets. Pour cette procédure pas à pas, définissez le DataSet dans un projet de bibliothèque de classes.

### <a name="to-create-the-class-library-project"></a>Pour créer le projet de bibliothèque de classes

1. Démarrez [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Dans le menu **Fichier** , pointez sur **Nouveau**, puis cliquez sur **Projet**.

3. Dans le volet modèles, développez **Visual C#** ou **Visual Basic**, puis cliquez sur **Windows**.

4. Dans la liste des modèles de projet, sélectionnez **bibliothèque de classes**.

5. Dans la zone **nom** , tapez **AdventureWorksDataSet**.

6. Cliquez sur **Parcourir**, accédez à votre dossier *%UserProfile%\My Documents* (pour Windows XP et versions antérieures) ou *%UserProfile%\Documents* (pour Windows Vista), puis cliquez sur **Sélectionner un dossier**.

7. Dans la boîte de dialogue **nouveau projet** , assurez-vous que la case à cocher **créer le répertoire pour la solution** n’est pas activée.

8. Cliquez sur **OK**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Ajoute le projet **AdventureWorksDataSet** à **Explorateur de solutions** et ouvre le fichier de code **Class1.cs** ou **Class1. vb** .

9. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur **Class1.cs** ou **Class1. vb**, puis cliquez sur **supprimer**. Vous n’avez pas besoin de ce fichier pour cette procédure pas à pas.

## <a name="define-a-dataset-in-the-class-library-project"></a>Définir un DataSet dans le projet de bibliothèque de classes
 Définissez un DataSet typé qui contient les données de la base de données AdventureWorksLT pour SQL Server 2005. Plus loin dans cette procédure pas à pas, vous allez référencer ce DataSet à partir d’un projet de classeur Excel et d’un projet d’application console.

 Le DataSet est un *DataSet typé* qui représente les données de la table Product de la base de données AdventureWorksLT. Pour plus d’informations sur les datasets typés, consultez [outils de DataSet dans Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).

### <a name="to-define-a-typed-dataset-in-the-class-library-project"></a>Pour définir un DataSet typé dans le projet de bibliothèque de classes

1. Dans **Explorateur de solutions**, cliquez sur le projet **AdventureWorksDataSet** .

2. Si la fenêtre **sources de données** n’est pas visible, affichez-la en cliquant sur **Afficher** d'  >  **autres**  >  **sources de données** Windows dans la barre de menus.

3. Choisissez **Ajouter une nouvelle source de données** pour démarrer l' **Assistant Configuration de source de données**.

4. Cliquez sur **Base de données**, puis sur **Suivant**.

5. Si vous disposez d’une connexion existante à la base de données AdventureWorksLT, choisissez cette connexion et cliquez sur **suivant**.

    Sinon, cliquez sur **Nouvelle connexion** et utilisez la boîte de dialogue **Ajouter une connexion** pour créer la connexion. Pour plus d’informations, consultez [ajouter de nouvelles connexions](../data-tools/add-new-connections.md).

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

### <a name="to-create-the-excel-workbook-project"></a>Pour créer le projet de classeur Excel

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur la solution **AdventureWorksDataSet** , pointez sur **Ajouter**, puis cliquez sur **nouveau projet**.

2. Dans le volet modèles, développez **Visual C#** ou **Visual Basic**, puis développez **Office**.

3. Sous le nœud **Office** développé, sélectionnez le nœud **2010** .

4. Dans la liste des modèles de projet, sélectionnez le projet de classeur Excel.

5. Dans la zone **nom** , tapez **AdventureWorksReport**. Ne modifiez pas l’emplacement.

6. Cliquez sur **OK**.

     L' **Assistant Projet Visual Studio Tools pour Office** s'ouvre.

7. Assurez-vous que l’option **créer un nouveau document** est sélectionnée, puis cliquez sur **OK**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ouvre le classeur **AdventureWorksReport** dans le concepteur et ajoute le projet **AdventureWorksReport** à **Explorateur de solutions**.

## <a name="add-the-dataset-to-data-sources-in-the-excel-workbook-project"></a>Ajouter le DataSet à des sources de données dans le projet de classeur Excel
 Avant de pouvoir afficher le DataSet dans le classeur Excel, vous devez d’abord ajouter le jeu de données aux sources de données dans le projet de classeur Excel.

### <a name="to-add-the-dataset-to-the-data-sources-in-the-excel-workbook-project"></a>Pour ajouter le DataSet aux sources de données dans le projet de classeur Excel

1. Dans **Explorateur de solutions**, double-cliquez sur **Sheet1.cs** ou **Feuille1. vb** sous le projet **AdventureWorksReport** .

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

### <a name="to-create-a-listobject-that-is-bound-to-an-instance-of-the-dataset"></a>Pour créer un ListObject lié à une instance du DataSet

1. Dans la fenêtre **sources de données** , développez le nœud **AdventureWorksLTDataSet** sous **AdventureWorksDataSet**.

2. Sélectionnez le nœud **Product** , cliquez sur la flèche déroulante qui s’affiche, puis sélectionnez **ListObject** dans la liste déroulante.

     Si la flèche déroulante n’apparaît pas, vérifiez que le classeur est ouvert dans le concepteur.

3. Faites glisser la table **Product** vers la cellule a1.

     Un <xref:Microsoft.Office.Tools.Excel.ListObject> contrôle nommé `productListObject` est créé sur la feuille de calcul, en commençant par la cellule a1. Au même moment, un objet dataset nommé `adventureWorksLTDataSet` et un <xref:System.Windows.Forms.BindingSource> nommé `productBindingSource` sont ajoutés au projet. <xref:Microsoft.Office.Tools.Excel.ListObject> est lié à <xref:System.Windows.Forms.BindingSource>, qui est lui-même lié à l’objet dataset.

## <a name="add-the-dataset-to-the-data-cache"></a>Ajouter le DataSet au cache de données
 Pour permettre au code en dehors du projet de classeur Excel d’accéder au DataSet dans le classeur, vous devez ajouter le DataSet au cache de données. Pour plus d’informations sur le cache de données, consultez [données mises en cache dans les personnalisations au niveau du document](../vsto/cached-data-in-document-level-customizations.md) et [données du cache](../vsto/caching-data.md).

### <a name="to-add-the-dataset-to-the-data-cache"></a>Pour ajouter le DataSet au cache de données

1. Dans le concepteur, cliquez sur **AdventureWorksLTDataSet**.

2. Dans la fenêtre **Propriétés** , affectez à la propriété **Modifiers** la valeur **public**.

3. Affectez à la propriété **CacheInDocument** la **valeur true**.

## <a name="initialize-the-dataset-in-the-workbook"></a>Initialiser le jeu de données dans le classeur
 Avant de pouvoir récupérer les données du DataSet mis en cache à l’aide de l’application console, vous devez d’abord remplir le DataSet mis en cache avec des données.

### <a name="to-initialize-the-dataset-in-the-workbook"></a>Pour initialiser le jeu de données dans le classeur

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le fichier **Sheet1.cs** ou **Feuille1. vb** , puis cliquez sur **afficher le code**.

2. Remplacez le gestionnaire d'événements `Sheet1_Startup` par le code suivant. Ce code utilise une instance de la `ProductTableAdapter` classe qui est définie dans le projet **AdventureWorksDataSet** pour remplir le DataSet mis en cache avec des données, s’il est actuellement vide.

     [!code-csharp[Trin_CachedDataWalkthroughs#8](../vsto/codesnippet/CSharp/AdventureWorksDataSet/AdventureWorksReport/Sheet1.cs#8)]
     [!code-vb[Trin_CachedDataWalkthroughs#8](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/AdventureWorksReport/Sheet1.vb#8)]

## <a name="checkpoint"></a>Point de contrôle
 Générez et exécutez le projet de classeur Excel pour vous assurer qu’il se compile et s’exécute sans erreur. Cette opération remplit également le DataSet mis en cache et enregistre les données dans le classeur.

### <a name="to-build-and-run-the-project"></a>Pour générer et exécuter le projet

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet **AdventureWorksReport** , choisissez **Déboguer**, puis cliquez sur **Démarrer une nouvelle instance**.

     Le projet est généré et le classeur s’ouvre dans Excel. Vérifiez les éléments suivants :

    - Le <xref:Microsoft.Office.Tools.Excel.ListObject> remplissage des données.

    - La valeur de la colonne **ListPrice** pour la première ligne de <xref:Microsoft.Office.Tools.Excel.ListObject> est 1431,5. Plus loin dans cette procédure pas à pas, vous allez utiliser une application console pour modifier les valeurs de la colonne **ListPrice** .

2. Enregistrez le classeur. Ne modifiez pas le nom de fichier ou l’emplacement du classeur.

3. Fermez Excel.

## <a name="create-a-console-application-project"></a>Créer un projet d’application console
 Créez un projet d’application console à utiliser pour modifier les données du DataSet mis en cache dans le classeur.

### <a name="to-create-the-console-application-project"></a>Pour créer le projet d’application console

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur la solution **AdventureWorksDataSet** , pointez sur **Ajouter**, puis cliquez sur **nouveau projet**.

2. Dans le volet **types de projets** , développez **Visual C#** ou **Visual Basic**, puis cliquez sur **Windows**.

3. Dans le volet **Modèles**, sélectionnez **Application console**.

4. Dans la zone **nom** , tapez **DataWriter**. Ne modifiez pas l’emplacement.

5. Cliquez sur **OK**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Ajoute le projet **DataWriter** à **Explorateur de solutions** et ouvre le fichier de code **Program.cs** ou **Module1. vb** .

## <a name="change-data-in-the-cached-dataset-by-using-the-console-application"></a>Modifier des données dans le DataSet mis en cache à l’aide de l’application console
 Utilisez la <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> classe dans l’application console pour lire les données dans un `AdventureWorksLTDataSet` objet local, modifiez ces données, puis enregistrez-les à nouveau dans le DataSet mis en cache.

### <a name="to-change-data-in-the-cached-dataset"></a>Pour modifier des données dans le DataSet mis en cache

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet **DataWriter** , puis cliquez sur **Ajouter une référence**.

2. Sous l’onglet **.net** , sélectionnez **Microsoft. VisualStudio. Tools. applications**.

3. Cliquez sur **OK**.

4. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet **DataWriter** , puis cliquez sur **Ajouter une référence**.

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
     > Le code suivant suppose que vous utilisez un classeur qui a l’extension de fichier *. xlsx* . Si le classeur de votre projet a une extension de fichier différente, modifiez le chemin d’accès si nécessaire.

     [!code-csharp[Trin_CachedDataWalkthroughs#6](../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs#6)]
     [!code-vb[Trin_CachedDataWalkthroughs#6](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb#6)]

9. Ajoutez le code suivant à la `Main` méthode, après le code que vous avez ajouté à l’étape précédente. Ce code effectue les tâches suivantes :

   - Elle utilise la <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> propriété de la <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> classe pour accéder au DataSet mis en cache dans le classeur.

   - Il lit les données du DataSet mis en cache dans le jeu de données local.

   - Elle modifie la `ListPrice` valeur de chaque produit dans la table Product du jeu de données.

   - Il enregistre les modifications apportées au jeu de données mis en cache dans le classeur.

     [!code-csharp[Trin_CachedDataWalkthroughs#7](../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs#7)]
     [!code-vb[Trin_CachedDataWalkthroughs#7](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb#7)]

10. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet **DataWriter** , pointez sur **Déboguer**, puis cliquez sur **Démarrer une nouvelle instance**.

     L’application console affiche les messages lors de la lecture du DataSet mis en cache dans le jeu de données local, modifie les prix des produits dans le jeu de données local et enregistre les nouvelles valeurs dans le jeu de données mis en cache. Appuyez sur **Entrée** pour fermer l'application.

## <a name="test-the-workbook"></a>Tester le classeur
 Lorsque vous ouvrez le classeur, <xref:Microsoft.Office.Tools.Excel.ListObject> affiche maintenant les modifications que vous avez apportées à la `ListPrice` colonne de données dans le jeu de données mis en cache.

### <a name="to-test-the-workbook"></a>Pour tester le classeur

1. Fermez le classeur AdventureWorksReport dans le concepteur Visual Studio, s’il est toujours ouvert.

2. Ouvrez le classeur AdventureWorksReport qui se trouve dans le dossier Build du projet **AdventureWorksReport** . Par défaut, le dossier de build se trouve dans l’un des emplacements suivants :

    - *%UserProfile%\My Documents\AdventureWorksReport\bin\Debug* (pour Windows XP et versions antérieures)

    - *%UserProfile%\Documents\AdventureWorksReport\bin\Debug* (pour Windows Vista)

3. Vérifiez que la valeur de la colonne **ListPrice** pour la première ligne de <xref:Microsoft.Office.Tools.Excel.ListObject> est maintenant 1574,65.

4. Fermez le classeur.

## <a name="see-also"></a>Voir aussi

- [Procédure pas à pas : insertion de données dans un classeur sur un serveur](../vsto/walkthrough-inserting-data-into-a-workbook-on-a-server.md)
