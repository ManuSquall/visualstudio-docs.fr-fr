---
title: Utilisation de tables de recherche dans la liaison de données-Windows Forms
description: Apprenez à créer un contrôle utilisateur Windows Forms qui prend en charge la liaison de données de recherche, à l’aide de la classe LookupBindingPropertiesAttribute (dans Visual Studio.
ms.custom: SEO-VS-2020
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
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 0eeb3e768370066bf93afc766d4d7f67d8d39a1d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99859071"
---
# <a name="create-a-windows-forms-user-control-that-supports-lookup-data-binding"></a>Créer un contrôle utilisateur Windows Forms prenant en charge la liaison de données de recherche

Pour afficher des données dans Windows Forms, vous pouvez choisir des contrôles existants dans la **Boîte à outils** ou créer des contrôles personnalisés si votre application requiert des fonctionnalités qui ne sont pas disponibles dans les contrôles standard. Cette procédure pas à pas vous indique comment créer un contrôle qui implémente l'objet <xref:System.ComponentModel.LookupBindingPropertiesAttribute>. Les contrôles qui implémentent <xref:System.ComponentModel.LookupBindingPropertiesAttribute> peuvent contenir trois propriétés pouvant être liées aux données. Ce type de contrôles est similaire à <xref:System.Windows.Forms.ComboBox>.

Pour plus d’informations sur la création de contrôles, consultez [développement de contrôles Windows Forms au moment du design](/dotnet/framework/winforms/controls/developing-windows-forms-controls-at-design-time).

Quand vous créez des contrôles utilisables dans des scénarios de liaison de données, vous devez implémenter l’un des attributs Databinding suivants :

|Utilisation des attributs de liaison de données|
| - |
|Implémentez <xref:System.ComponentModel.DefaultBindingPropertyAttribute> sur des contrôles simples, comme <xref:System.Windows.Forms.TextBox>, qui affichent une seule colonne (ou propriété) de données. Pour plus d’informations, consultez [créer un Windows Forms contrôle utilisateur qui prend en charge la liaison de données simple](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).|
|Implémentez <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> sur des contrôles, comme <xref:System.Windows.Forms.DataGridView>, qui affichent des listes (ou tables) de données. Pour plus d’informations, consultez [créer un Windows Forms contrôle utilisateur qui prend en charge la liaison de données complexe](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md).|
|Implémentez <xref:System.ComponentModel.LookupBindingPropertiesAttribute> sur des contrôles, comme <xref:System.Windows.Forms.ComboBox>, qui affichent des listes (ou tables) de données, mais doivent également présenter une seule colonne ou propriété. (Ce processus est décrit dans cette page de procédure pas à pas.)|

Cette procédure pas à pas crée un contrôle de recherche qui effectue une liaison vers les données de deux tables. Cet exemple utilise les tables `Customers` et `Orders` de l'exemple de base de données Northwind. Le contrôle de recherche est lié au `CustomerID` champ de la `Orders` table. Elle utilise cette valeur pour rechercher `CompanyName` dans la `Customers` table.

Au cours de cette procédure pas à pas, vous apprendrez à :

- Créez une **application de Windows Forms**.

- Ajouter un nouveau **Contrôle utilisateur** à votre projet.

- Concevoir visuellement le contrôle utilisateur.

- Implémenter l'attribut `LookupBindingProperty`.

- Créez un DataSet à l’aide de l’Assistant **configuration de source de données** .

- Définir la colonne **CustomerID** de la table **Orders** dans la fenêtre **Sources de données** pour qu’elle utilise le nouveau contrôle.

- Créer un formulaire pour afficher des données dans le nouveau contrôle.

## <a name="prerequisites"></a>Prérequis

Cette procédure pas à pas utilise SQL Server Express base de données locale et l’exemple de base de données Northwind.

1. Si vous n’avez pas SQL Server Express base de données locale, installez-la à partir de la [page de téléchargement SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express)ou via le **Visual Studio installer**. Dans le **Visual Studio installer**, vous pouvez installer SQL Server Express base de données locale dans le cadre de la charge de travail de **stockage et de traitement des données** , ou en tant que composant individuel.

2. Installez l’exemple de base de données Northwind en procédant comme suit :

    1. Dans Visual Studio, ouvrez la fenêtre de **Explorateur d’objets SQL Server** . (Explorateur d’objets SQL Server est installé dans le cadre de la charge de travail **stockage et traitement des données** dans le Visual Studio installer.) Développez le nœud **SQL Server** . Cliquez avec le bouton droit sur votre instance de base de données locale, puis sélectionnez **nouvelle requête**.

       Une fenêtre de l’éditeur de requête s’ouvre.

    2. Copiez le [script Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) dans le presse-papiers. Ce script T-SQL crée la base de données Northwind à partir de zéro et la remplit avec des données.

    3. Collez le script T-SQL dans l’éditeur de requête, puis choisissez le bouton **exécuter** .

       Après un bref laps de temps, l’exécution de la requête se termine et la base de données Northwind est créée.

## <a name="create-a-windows-forms-app-project"></a>Créer un projet d’application Windows Forms

La première étape consiste à créer un projet d' **Application Windows Forms** .

1. Dans Visual Studio, dans le menu **Fichier**, sélectionnez **Nouveau** > **Projet**.

2. Développez **Visual C#** ou **Visual Basic** dans le volet gauche, puis sélectionnez **Bureau Windows**.

3. Dans le volet central, sélectionnez le type de projet d' **application Windows Forms** .

4. Nommez le projet **LookupControlWalkthrough**, puis choisissez **OK**.

     Le projet **LookupControlWalkthrough** est créé et ajouté à l’**Explorateur de solutions**.

## <a name="add-a-user-control-to-the-project"></a>Ajouter un contrôle utilisateur au projet

Cette procédure pas à pas crée un contrôle de recherche à partir d’un **Contrôle utilisateur** : ajoutez donc un élément **Contrôle utilisateur** au projet **LookupControlWalkthrough**.

1. Dans le menu **Projet**, sélectionnez **Ajouter un contrôle utilisateur**.

2. Tapez `LookupBox` dans la zone **nom** , puis cliquez sur **Ajouter**.

     Le contrôle **LookupBox** est ajouté à l’**Explorateur de solutions** et s’ouvre dans le concepteur.

## <a name="design-the-lookupbox-control"></a>Concevoir le contrôle LookupBox

Pour concevoir le contrôle LookupBox, faites glisser un <xref:System.Windows.Forms.ComboBox> de la **boîte à outils** vers l’aire de conception du contrôle utilisateur.

## <a name="add-the-required-data-binding-attribute"></a>Ajouter l’attribut de liaison de données requis

Pour des contrôles de recherche prenant en charge la liaison de données, vous pouvez implémenter l’attribut<xref:System.ComponentModel.LookupBindingPropertiesAttribute>.

1. Faites passer le contrôle **LookupBox** en mode Code. (Dans le menu **Affichage**, choisissez **Code**.)

2. Remplacez le code de `LookupBox` par le code suivant :

     [!code-vb[VbRaddataDisplaying#5](../data-tools/codesnippet/VisualBasic/create-a-windows-forms-user-control-that-supports-lookup-data-binding_1.vb)]
     [!code-csharp[VbRaddataDisplaying#5](../data-tools/codesnippet/CSharp/create-a-windows-forms-user-control-that-supports-lookup-data-binding_1.cs)]

3. Dans le menu **générer** , choisissez **générer la solution**.

## <a name="create-a-data-source-from-your-database"></a>Créer une source de données à partir de votre base de données

Cette étape crée une source de données à l’aide de l’Assistant **Configuration de source de données** basée sur les tables `Customers` et `Orders` de l’exemple de base de données Northwind.

1. Pour ouvrir la fenêtre **sources de données** , dans le menu **données** , cliquez sur Afficher les **sources de données**.

2. Dans la fenêtre **sources de données** , sélectionnez Ajouter une **nouvelle source de données** pour démarrer l’Assistant Configuration de source de **données** .

3. Sélectionnez **Base de données** dans la page **Choisir un type de source de données** , puis cliquez sur **Suivant**.

4. Dans la page **Choisir votre connexion de données**, effectuez l’une des opérations suivantes :

    - Si une connexion de données à l’exemple de base de données Northwind est disponible dans la liste déroulante, sélectionnez-la.

    - Sélectionnez **Nouvelle connexion** pour afficher la boîte de dialogue **Ajouter/Modifier la connexion**.

5. Si votre base de données nécessite un mot de passe, sélectionnez l’option pour inclure les données sensibles, puis cliquez sur **Suivant**.

6. Dans la page **enregistrer la chaîne de connexion dans le fichier de configuration de l’application** , cliquez sur **suivant**.

7. Dans la page **Choisir vos objets de base de données**, développez le nœud **Tables**.

8. Sélectionnez les tables `Customers` et `Orders`, puis cliquez sur **Terminer**.

     **NorthwindDataSet** est ajouté à votre projet et les `Customers` `Orders` tables et s’affichent dans la fenêtre sources de **données** .

## <a name="set-the-customerid-column-of-the-orders-table-to-use-the-lookupbox-control"></a>Définir la colonne CustomerID de la table Orders pour qu’elle utilise le contrôle LookupBox

Dans la fenêtre **Sources de données**, vous pouvez définir le contrôle à créer avant de faire glisser des éléments vers votre formulaire.

1. Ouvrez **Form1** dans le concepteur.

2. Développez le nœud **Customers** dans la fenêtre **Sources de données**.

3. Développez le nœud **Orders** (inclus dans le nœud **Customers** sous la colonne **Fax**).

4. Cliquez sur la flèche déroulante du nœud **Orders** et choisissez **Détails** dans la liste de contrôles.

5. Cliquez sur la flèche déroulante de la colonne **CustomerID** (dans le nœud **Orders**), puis choisissez **Personnaliser**.

6. Sélectionnez **LookupBox** dans la liste des **Contrôles associés** de la boîte de dialogue **Options de personnalisation de l’interface utilisateur des données**.

7. Cliquez sur **OK**.

8. Cliquez sur la flèche de déroulement de la colonne **CustomerID** et choisissez **LookupBox**.

## <a name="add-controls-to-the-form"></a>Ajouter des contrôles au formulaire

Pour créer des contrôles liés aux données, vous pouvez faire glisser des éléments depuis la fenêtre **Sources de données** vers **Form1**.

Pour créer des contrôles liés aux données dans le Windows Form, faites glisser le nœud **Orders** de la fenêtre **sources de données** vers le Windows Form, puis vérifiez que le contrôle **LookupBox** est utilisé pour afficher les données dans la `CustomerID` colonne.

## <a name="bind-the-control-to-look-up-companyname-from-the-customers-table"></a>Lier le contrôle pour rechercher CompanyName dans la table Customers

Pour configurer les liaisons de recherche, sélectionnez le nœud **Customers** principal dans la fenêtre **sources de données** , puis faites-le glisser sur la zone de liste déroulante dans **CustomerIDLookupBox** sur **Form1**.

Ceci configure la liaison des données pour afficher le `CompanyName` de la table `Customers` tout en conservant la valeur de `CustomerID` de la table `Orders`.

## <a name="run-the-application"></a>Exécution de l'application

- Appuyez sur **F5** pour exécuter l'application.

- Parcourez quelques enregistrements et vérifiez que le `CompanyName` apparaît dans le contrôle `LookupBox`.

## <a name="see-also"></a>Voir aussi

- [Lier des contrôles Windows Forms à des données dans Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
