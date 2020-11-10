---
title: Créer une application de données simple à l’aide d’ADO.NET
description: Apprenez à créer une application Forms-Data simple à l’aide de Windows Forms et ADO.NET dans Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 08/23/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
ms.assetid: 2222841f-e443-4a3d-8c70-4506aa905193
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 44205f7f8f12d453a7c1d93ec8fee6ed1a3c1765
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94436795"
---
# <a name="create-a-simple-data-application-by-using-adonet"></a>Créer une application de données simple à l’aide d’ADO.NET

Quand vous créez une application qui manipule les données d’une base de données, vous effectuez des tâches élémentaires, comme définir les chaînes de connexion, insérer les données et exécuter les procédures stockées. En suivant cette rubrique, vous pouvez découvrir comment interagir avec une base de données à partir d’une application simple Windows Forms « formulaires de données » à l’aide de Visual C# ou Visual Basic et ADO.NET.  Toutes les technologies de données .NET (y compris les jeux de données, les LINQ to SQL et les Entity Framework) effectuent au final des étapes qui sont très similaires à celles indiquées dans cet article.

Cet article présente un moyen simple de récupérer des données d’une base de données de manière rapide. Si votre application doit modifier des données de manière non triviale et mettre à jour la base de données, vous devez envisager d’utiliser des Entity Framework et d’utiliser la liaison de données pour synchroniser automatiquement les contrôles d’interface utilisateur avec les modifications apportées aux données sous-jacentes.

> [!IMPORTANT]
> Pour que le code reste simple, il n’inclut pas la gestion des exceptions prête à la production.

## <a name="prerequisites"></a>Prérequis

Pour créer l'application, vous aurez besoin des éléments suivants :

- Visual Studio.

- SQL Server Express LocalDB. Si vous n’avez pas SQL Server Express base de données locale, vous pouvez l’installer à partir de la [page de téléchargement SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express).

Cette rubrique suppose que vous êtes familiarisé avec les fonctionnalités de base de l’IDE de Visual Studio et que vous pouvez créer une application Windows Forms, ajouter des formulaires au projet, placer des boutons et d’autres contrôles sur les formulaires, définir les propriétés des contrôles et coder des événements simples. Si vous n’êtes pas familiarisé avec ces tâches, nous vous suggérons de suivre la rubrique [prise en main de Visual C# et de Visual Basic](../ide/quickstart-visual-basic-console.md) avant de commencer cette procédure pas à pas.

## <a name="set-up-the-sample-database"></a>Installer l'exemple de base de données

Créez l’exemple de base de données en procédant comme suit :

1. Dans Visual Studio, ouvrez la fenêtre de **Explorateur de serveurs** .

2. Cliquez avec le bouton droit sur **connexions de données** et choisissez **créer une nouvelle SQL Server base de données**.

3. Dans la zone de texte **nom du serveur** , entrez **(\mssqllocaldb)**.

4. Dans la zone **de texte nom de la nouvelle base de données** , entrez **Sales** , puis choisissez **OK**.

     La base de données des **ventes** vide est créée et ajoutée au nœud Connexions de données dans Explorateur de serveurs.

5. Cliquez avec le bouton droit sur la connexion de données de **vente** , puis sélectionnez **nouvelle requête**.

     Une fenêtre de l’éditeur de requête s’ouvre.

6. Copiez le [script Transact-SQL Sales](https://github.com/MicrosoftDocs/visualstudio-docs/raw/master/docs/data-tools/samples/sales.sql) dans le presse-papiers.

7. Collez le script T-SQL dans l’éditeur de requête, puis choisissez le bouton **exécuter** .

     Après un bref laps de temps, l’exécution de la requête se termine et les objets de base de données sont créés. La base de données contient deux tables : Customer et Orders. Ces tables ne contiennent pas de données initialement, mais vous pouvez ajouter des données lorsque vous exécutez l’application que vous allez créer. La base de données contient également quatre procédures stockées simples.

## <a name="create-the-forms-and-add-controls"></a>Créer les formulaires et ajouter les contrôles

1. Créez un projet pour une application Windows Forms, puis nommez-le **SimpleDataApp**.

    Visual Studio crée le projet et plusieurs fichiers, dont un formulaire Windows vide nommé **Form1**.

2. Ajoutez deux formulaires Windows à votre projet afin qu’il comporte trois formulaires, puis attribuez-leur les noms suivants :

   - **Navigation**

   - **NewCustomer**

   - **FillOrCancel**

3. Pour chaque formulaire, ajoutez les zones de texte, les boutons et les autres contrôles indiqués dans les illustrations suivantes. Pour chaque contrôle, définissez les propriétés que les tables décrivent.

   > [!NOTE]
   > La zone de groupe et les contrôles d'étiquette ajoutent de la clarté mais ne sont pas utilisés dans le code.

   **Formulaire Navigation**

   ![Boîte de dialogue Navigation](../data-tools/media/simpleappnav.png)

|Contrôles du formulaire Navigation|Propriétés|
| - |----------------|
|Bouton|Name = btnGoToAdd|
|Bouton|Name = btnGoToFillOrCancel|
|Bouton|Name = btnExit|

**Formulaire NewCustomer**

![Ajouter un nouveau client et passer une commande](../data-tools/media/simpleappnewcust.png)

|Contrôles du formulaire NewCustomer|Propriétés|
| - |----------------|
|TextBox|Name = txtCustomerName|
|TextBox|Name = txtCustomerID<br /><br /> Readonly = True|
|Bouton|Name = btnCreateAccount|
|NumericUpdown|DecimalPlaces = 0<br /><br /> Maximum = 5000<br /><br /> Name = numOrderAmount|
|DateTimePicker|Format = Short<br /><br /> Name = dtpOrderDate|
|Bouton|Name = btnPlaceOrder|
|Bouton|Name = btnAddAnotherAccount|
|Bouton|Name = btnAddFinish|

**Formulaire FillOrCancel**

![remplir ou annuler les commandes](../data-tools/media/simpleappcancelfill.png)

|Contrôles du formulaire FillOrCancel|Propriétés|
| - |----------------|
|TextBox|Name = txtOrderID|
|Bouton|Name = btnFindByOrderID|
|DateTimePicker|Format = Short<br /><br /> Name = dtpFillDate|
|DataGridView|Name = dgvCustomerOrders<br /><br /> Readonly = True<br /><br /> RowHeadersVisible = False|
|Bouton|Name = btnCancelOrder|
|Bouton|Name = btnFillOrder|
|Bouton|Name = btnFinishUpdates|

## <a name="store-the-connection-string"></a>Stocker la chaîne de connexion
Quand votre application tente d'ouvrir une connexion à la base de données, elle doit avoir accès à la chaîne de connexion. Pour éviter d’entrer la chaîne manuellement sur chaque formulaire, stockez la chaîne dans le fichier *App.config* de votre projet, puis créez une méthode qui retourne la chaîne lorsque la méthode est appelée à partir de n’importe quel formulaire de votre application.

Vous pouvez trouver la chaîne de connexion en cliquant avec le bouton droit sur la connexion de données de **vente** dans **Explorateur de serveurs** et en choisissant **Propriétés**. Recherchez la propriété **ConnectionString** , puis utilisez **CTRL** + **A** , **CTRL** + **C** pour sélectionner et copier la chaîne dans le presse-papiers.

1. Si vous utilisez C#, dans **Explorateur de solutions** , développez le nœud **Propriétés** sous le projet, puis ouvrez le fichier **Settings. Settings** .
    Si vous utilisez Visual Basic, dans **Explorateur de solutions** , cliquez sur **Afficher tous les fichiers** , développez le nœud **mon projet** , puis ouvrez le fichier **Settings. Settings** .

2. Dans la colonne **nom** , entrez `connString` .

3. Dans la liste **type** , sélectionnez **(chaîne de connexion)**.

4. Dans la liste **étendue** , sélectionnez **application**.

5. Dans la colonne **valeur** , entrez votre chaîne de connexion (sans guillemets extérieurs), puis enregistrez vos modifications.

> [!NOTE]
> Dans une application réelle, vous devez stocker la chaîne de connexion en toute sécurité, comme décrit dans [chaînes de connexion et fichiers de configuration](/dotnet/framework/data/adonet/connection-strings-and-configuration-files).

## <a name="write-the-code-for-the-forms"></a>Écrire le code des formulaires

Cette section contient des vues d’ensemble succinctes de ce que fait chaque formulaire. Il fournit également le code qui définit la logique sous-jacente lorsqu’un clic est effectué sur un bouton du formulaire.

### <a name="navigation-form"></a>Formulaire Navigation

Le formulaire Navigation s'ouvre quand vous exécutez l'application. Le bouton **Ajouter un compte** ouvre le formulaire NewCustomer. Le bouton **Remplir ou annuler les commandes** ouvre le formulaire FillOrCancel. Le bouton **Quitter** ferme l’application.

#### <a name="make-the-navigation-form-the-startup-form"></a>Faire du formulaire Navigation le formulaire de démarrage

Si vous utilisez C#, dans l’ **Explorateur de solutions** , ouvrez **Program.cs** , puis remplacez la ligne `Application.Run` par `Application.Run(new Navigation());`

Si vous utilisez Visual Basic, dans **Explorateur de solutions** , ouvrez la fenêtre **Propriétés** , sélectionnez l’onglet **application** , puis sélectionnez **SimpleDataApp. navigation** dans la liste **formulaire de démarrage** .

#### <a name="create-auto-generated-event-handlers"></a>Créer des gestionnaires d’événements générés automatiquement

Double-cliquez sur les trois boutons du formulaire de navigation pour créer des méthodes de gestionnaire d’événements vides. Le double-clic sur les boutons ajoute également du code généré automatiquement dans le fichier de code du concepteur qui active un clic de bouton pour déclencher un événement.

#### <a name="add-code-for-the-navigation-form-logic"></a>Ajouter du code pour la logique du formulaire de navigation

Dans la page de codes du formulaire de navigation, complétez les corps des méthodes pour les trois gestionnaires d’événements Click du bouton, comme indiqué dans le code suivant.

[!code-csharp[Navigation#1](../data-tools/codesnippet/CSharp/SimpleDataApp/Navigation.cs#1)]
[!code-vb[Navigation#1](../data-tools/codesnippet/VisualBasic/SimpleDataApp/Navigation.vb#1)]

### <a name="newcustomer-form"></a>Formulaire NewCustomer

Lorsque vous entrez un nom de client, puis sélectionnez le bouton **créer un compte** , le formulaire NewCustomer crée un compte client et SQL Server retourne une valeur d’identité en tant que nouvel ID client. Vous pouvez ensuite passer une commande pour le nouveau compte en spécifiant une quantité et une date de commande, puis en sélectionnant le bouton **passer une commande** .

#### <a name="create-auto-generated-event-handlers"></a>Créer des gestionnaires d’événements générés automatiquement

Créez un gestionnaire d’événements Click vide pour chaque bouton du formulaire NewCustomer en double-cliquant sur chacun des quatre boutons. Le double-clic sur les boutons ajoute également du code généré automatiquement dans le fichier de code du concepteur qui active un clic de bouton pour déclencher un événement.

#### <a name="add-code-for-the-newcustomer-form-logic"></a>Ajouter du code pour la logique de formulaire NewCustomer

Pour terminer la logique du formulaire NewCustomer, procédez comme suit.

1. Mettez l' `System.Data.SqlClient` espace de noms dans la portée afin de ne pas avoir à qualifier complètement les noms de ses membres.

     ```csharp
     using System.Data.SqlClient;
     ```

     ```vb
     Imports System.Data.SqlClient
     ```

2. Ajoutez des variables et des méthodes d’assistance à la classe, comme indiqué dans le code suivant.

     [!code-csharp[NewCustomer#1](../data-tools/codesnippet/CSharp/SimpleDataApp/NewCustomer.cs#1)]
     [!code-vb[NewCustomer#1](../data-tools/codesnippet/VisualBasic/SimpleDataApp/NewCustomer.vb#1)]

3. Complétez les corps des méthodes pour les gestionnaires d’événements Click du bouton à quatre, comme indiqué dans le code suivant.

     [!code-csharp[NewCustomer#2](../data-tools/codesnippet/CSharp/SimpleDataApp/NewCustomer.cs#2)]
     [!code-vb[NewCustomer#2](../data-tools/codesnippet/VisualBasic/SimpleDataApp/NewCustomer.vb#2)]

### <a name="fillorcancel-form"></a>Formulaire FillOrCancel

Le formulaire FillOrCancel exécute une requête pour retourner une commande lorsque vous entrez un ID de commande, puis clique sur le bouton **Rechercher un ordre** . La ligne retournée apparaît dans une grille de données en lecture seule. Vous pouvez marquer la commande comme annulée (X) si vous sélectionnez le bouton **annuler la commande** , ou vous pouvez marquer la commande comme remplie (F) si vous sélectionnez le bouton remplir l' **ordre** . Si vous cliquez de nouveau sur le bouton **Rechercher un ordre** , la ligne mise à jour apparaît.

#### <a name="create-auto-generated-event-handlers"></a>Créer des gestionnaires d’événements générés automatiquement

Créez des gestionnaires d’événements Click vides pour les quatre boutons du formulaire FillOrCancel en double-cliquant sur les boutons. Le double-clic sur les boutons ajoute également du code généré automatiquement dans le fichier de code du concepteur qui active un clic de bouton pour déclencher un événement.

#### <a name="add-code-for-the-fillorcancel-form-logic"></a>Ajouter du code pour la logique de formulaire FillOrCancel

Pour terminer la logique du formulaire FillOrCancel, procédez comme suit.

1. Placez les deux espaces de noms suivants dans l’étendue afin de ne pas avoir à qualifier complètement les noms de leurs membres.

     ```csharp
     using System.Data.SqlClient;
     using System.Text.RegularExpressions;
     ```

     ```vb
     Imports System.Data.SqlClient
     Imports System.Text.RegularExpressions
     ```

2. Ajoutez une variable et une méthode d’assistance à la classe, comme indiqué dans le code suivant.

     [!code-csharp[FillOrCancel#1](../data-tools/codesnippet/CSharp/SimpleDataApp/FillOrCancel.cs#1)]
     [!code-vb[FillOrCancel#1](../data-tools/codesnippet/VisualBasic/SimpleDataApp/FillOrCancel.vb#1)]

3. Complétez les corps des méthodes pour les gestionnaires d’événements Click du bouton à quatre, comme indiqué dans le code suivant.

     [!code-csharp[FillOrCancel#2](../data-tools/codesnippet/CSharp/SimpleDataApp/FillOrCancel.cs#2)]
     [!code-vb[FillOrCancel#2](../data-tools/codesnippet/VisualBasic/SimpleDataApp/FillOrCancel.vb#2)]

## <a name="test-your-application"></a>Tester votre application

Sélectionnez la touche **F5** pour générer et tester votre application après avoir codé chaque gestionnaire d’événements Click et avoir terminé le codage.

## <a name="see-also"></a>Voir aussi

- [Outils de données Visual Studio pour .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
