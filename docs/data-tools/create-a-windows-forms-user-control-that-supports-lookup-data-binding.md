---
title: À l’aide de tables de recherche dans la liaison de données - contrôles Windows Forms | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data binding, user controls
- LookupBindingPropertiesAttribute class, examples
- user controls [Visual Basic], creating
ms.assetid: c48b4d75-ccfc-4950-8b14-ff8adbfe4208
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 07c9cf40952eabcafe9d1587d3e2ae4aa02de3a0
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2018
ms.locfileid: "52305079"
---
# <a name="create-a-windows-forms-user-control-that-supports-lookup-data-binding"></a>Créer un contrôle utilisateur Windows Forms prenant en charge la liaison de données de recherche

Pour afficher des données dans Windows Forms, vous pouvez choisir des contrôles existants dans la **Boîte à outils** ou créer des contrôles personnalisés si votre application requiert des fonctionnalités qui ne sont pas disponibles dans les contrôles standard. Cette procédure pas à pas vous indique comment créer un contrôle qui implémente l'objet <xref:System.ComponentModel.LookupBindingPropertiesAttribute>. Les contrôles qui implémentent <xref:System.ComponentModel.LookupBindingPropertiesAttribute> peuvent contenir trois propriétés pouvant être liées aux données. Ce type de contrôles est similaire à <xref:System.Windows.Forms.ComboBox>.

Pour plus d’informations sur la création de contrôles, consultez [développement de formulaires Windows contrôle au moment du design](/dotnet/framework/winforms/controls/developing-windows-forms-controls-at-design-time).

Quand vous créez des contrôles utilisables dans des scénarios de liaison de données, vous devez implémenter l’un des attributs Databinding suivants :

|Utilisation d’attributs de liaison de données|
| - |
|Implémentez <xref:System.ComponentModel.DefaultBindingPropertyAttribute> sur des contrôles simples, comme <xref:System.Windows.Forms.TextBox>, qui affichent une seule colonne (ou propriété) de données. Pour plus d’informations, consultez [créer un contrôle utilisateur Windows Forms qui prend en charge la liaison de données simple](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).|
|Implémentez <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> sur des contrôles, comme <xref:System.Windows.Forms.DataGridView>, qui affichent des listes (ou tables) de données. Pour plus d’informations, consultez [créer un contrôle utilisateur Windows Forms qui prend en charge la liaison de données complexe](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md).|
|Implémentez <xref:System.ComponentModel.LookupBindingPropertiesAttribute> sur des contrôles, comme <xref:System.Windows.Forms.ComboBox>, qui affichent des listes (ou tables) de données, mais doivent également présenter une seule colonne ou propriété. (Ce processus est décrit dans cette page de procédure pas à pas.)|

Cette procédure pas à pas crée un contrôle de recherche qui effectue une liaison vers les données de deux tables. Cet exemple utilise les tables `Customers` et `Orders` de l'exemple de base de données Northwind. Le contrôle de recherche est lié à la `CustomerID` champ à partir de la `Orders` table. Il utilise cette valeur pour rechercher le `CompanyName` à partir de la `Customers` table.

Au cours de cette procédure pas à pas, vous allez découvrir comment :

-   Créer une **application Windows Forms**.

-   Ajouter un nouveau **Contrôle utilisateur** à votre projet.

-   Concevoir visuellement le contrôle utilisateur.

-   Implémenter l'attribut `LookupBindingProperty`.

-   Créer un jeu de données avec le **Configuration de Source de données** Assistant.

-   Définir la colonne **CustomerID** de la table **Orders** dans la fenêtre **Sources de données** pour qu’elle utilise le nouveau contrôle.

-   Créer un formulaire pour afficher des données dans le nouveau contrôle.

## <a name="prerequisites"></a>Prérequis

Cette procédure pas à pas utilise SQL Server Express LocalDB et la base de données Northwind.

1.  Si vous n’avez pas SQL Server Express LocalDB, installez-le à partir de la [page de téléchargement de SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), ou via le **le programme d’installation de Visual Studio**. Dans le **le programme d’installation de Visual Studio**, vous pouvez installer SQL Server Express LocalDB dans le cadre de la **stockage de données et de traitement** charge de travail, ou comme un composant individuel.

2.  Installer la base de données Northwind en suivant ces étapes :

    1. Dans Visual Studio, ouvrez le **Explorateur d’objets SQL Server** fenêtre. (Explorateur d’objets SQL Server est installé dans le cadre de la **stockage de données et de traitement** charge de travail dans Visual Studio Installer.) Développez le **SQL Server** nœud. Avec le bouton droit sur votre instance de base de données locale et sélectionnez **nouvelle requête**.

       Une fenêtre d’éditeur de requête s’ouvre.

    2. Copie le [script Transact-SQL de Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) dans votre Presse-papiers. Ce script T-SQL crée la base de données Northwind à partir de zéro et la remplit avec des données.

    3. Collez le script T-SQL dans l’éditeur de requête, puis choisissez le **Execute** bouton.

       Après une courte période, la requête est terminée en cours d’exécution et la base de données Northwind est créé.

## <a name="create-a-windows-forms-app-project"></a>Créer un projet d’application Windows Forms

La première étape consiste à créer un **Windows Forms Application** projet.

1. Dans Visual Studio, sur le **fichier** menu, sélectionnez **New** > **projet**.

2. Développez le **Visual C#**  ou **Visual Basic** dans le volet gauche, puis sélectionnez **Windows Desktop**.

3. Dans le volet central, sélectionnez le **Windows Forms application** type de projet.

4. Nommez le projet **LookupControlWalkthrough**, puis choisissez **OK**.

     Le projet **LookupControlWalkthrough** est créé et ajouté à l’**Explorateur de solutions**.

## <a name="add-a-user-control-to-the-project"></a>Ajouter un contrôle utilisateur au projet

Cette procédure pas à pas crée un contrôle de recherche à partir d’un **Contrôle utilisateur** : ajoutez donc un élément **Contrôle utilisateur** au projet **LookupControlWalkthrough**.

1.  Dans le menu **Projet**, sélectionnez **Ajouter un contrôle utilisateur**.

2.  Type `LookupBox` dans le **nom** zone, puis cliquez sur **ajouter**.

     Le contrôle **LookupBox** est ajouté à l’**Explorateur de solutions** et s’ouvre dans le concepteur.

## <a name="design-the-lookupbox-control"></a>Concevoir le contrôle LookupBox

Pour concevoir le contrôle LookupBox, faites glisser un <xref:System.Windows.Forms.ComboBox> à partir de la **boîte à outils** aire de conception du contrôle utilisateur.

## <a name="add-the-required-data-binding-attribute"></a>Ajoutez l’attribut de liaison de données requis

Pour des contrôles de recherche prenant en charge la liaison de données, vous pouvez implémenter l’attribut<xref:System.ComponentModel.LookupBindingPropertiesAttribute>.

1.  Faites passer le contrôle **LookupBox** en mode Code. (Dans le menu **Affichage**, choisissez **Code**.)

2.  Remplacez le code de `LookupBox` par le code suivant :

     [!code-vb[VbRaddataDisplaying#5](../data-tools/codesnippet/VisualBasic/create-a-windows-forms-user-control-that-supports-lookup-data-binding_1.vb)]
     [!code-csharp[VbRaddataDisplaying#5](../data-tools/codesnippet/CSharp/create-a-windows-forms-user-control-that-supports-lookup-data-binding_1.cs)]

3.  Dans le menu **Générer** , cliquez sur **Générer la solution**.

## <a name="create-a-data-source-from-your-database"></a>Créer une source de données à partir de votre base de données

Cette étape crée une source de données à l’aide de l’Assistant **Configuration de source de données** basée sur les tables `Customers` et `Orders` de l’exemple de base de données Northwind.

1.  Pour ouvrir le **des Sources de données** fenêtre, dans le **données** menu, cliquez sur **afficher les Sources de données**.

2.  Dans la fenêtre **Sources de données**, sélectionnez **Ajouter une nouvelle source de données** pour démarrer l’Assistant **Configuration de source de données**.

3.  Sélectionnez **Base de données** dans la page **Choisir un type de source de données** , puis cliquez sur **Suivant**.

4.  Dans la page **Choisir votre connexion de données**, effectuez l’une des opérations suivantes :

    -   Si une connexion de données à l’exemple de base de données Northwind est disponible dans la liste déroulante, sélectionnez-la.

    -   Sélectionnez **Nouvelle connexion** pour afficher la boîte de dialogue **Ajouter/Modifier la connexion**.

5.  Si votre base de données nécessite un mot de passe, sélectionnez l’option pour inclure les données sensibles, puis cliquez sur **Suivant**.

6.  Sur le **enregistrer la chaîne de connexion dans le fichier de Configuration de l’Application** , cliquez sur **suivant**.

7.  Dans la page **Choisir vos objets de base de données**, développez le nœud **Tables**.

8.  Sélectionnez les tables `Customers` et `Orders`, puis cliquez sur **Terminer**.

     **NorthwindDataSet** est ajouté à votre projet, et les tables `Customers` et `Orders` apparaissent dans la fenêtre **Sources de données**.

## <a name="set-the-customerid-column-of-the-orders-table-to-use-the-lookupbox-control"></a>Définir la colonne CustomerID de la table Orders pour utiliser le contrôle LookupBox

Dans la fenêtre **Sources de données**, vous pouvez définir le contrôle à créer avant de faire glisser des éléments vers votre formulaire.

1.  Ouvrez **Form1** dans le concepteur.

2.  Développez le nœud **Customers** dans la fenêtre **Sources de données**.

3.  Développez le nœud **Orders** (inclus dans le nœud **Customers** sous la colonne **Fax**).

4.  Cliquez sur la flèche déroulante du nœud **Orders** et choisissez **Détails** dans la liste de contrôles.

5.  Cliquez sur la flèche déroulante de la colonne **CustomerID** (dans le nœud **Orders**), puis choisissez **Personnaliser**.

6.  Sélectionnez **LookupBox** dans la liste des **Contrôles associés** de la boîte de dialogue **Options de personnalisation de l’interface utilisateur des données**.

7.  Cliquez sur **OK**.

8.  Cliquez sur la flèche de déroulement de la colonne **CustomerID** et choisissez **LookupBox**.

## <a name="add-controls-to-the-form"></a>Ajouter des contrôles au formulaire

Pour créer des contrôles liés aux données, vous pouvez faire glisser des éléments depuis la fenêtre **Sources de données** vers **Form1**.

Pour créer des contrôles liés aux données sur le formulaire Windows, faites glisser le **commandes** nœud à partir de la **des Sources de données** fenêtre vers le formulaire Windows et vérifiez que le **LookupBox** contrôle est utilisé pour afficher les données dans le `CustomerID` colonne.

## <a name="bind-the-control-to-look-up-companyname-from-the-customers-table"></a>Lier le contrôle pour rechercher CompanyName à partir de la table Customers

Pour configurer les liaisons de recherche, sélectionnez le principal **clients** nœud dans le **des Sources de données** et faire glisser vers la liste déroulante zone dans le **CustomerIDLookupBox** sur **Form1**.

Ceci configure la liaison des données pour afficher le `CompanyName` de la table `Customers` tout en conservant la valeur de `CustomerID` de la table `Orders`.

## <a name="run-the-application"></a>Exécuter l'application

-   Appuyez sur **F5** pour exécuter l’application.

-   Parcourez quelques enregistrements et vérifiez que le `CompanyName` apparaît dans le contrôle `LookupBox`.

## <a name="see-also"></a>Voir aussi

- [Lier des contrôles Windows Forms à des données dans Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)