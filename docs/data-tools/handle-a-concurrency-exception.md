---
title: Gérer une exception d’accès concurrentiel
ms.date: 09/11/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- concurrency control, exceptions
- datasets [Visual Basic], errors
- exception handling, concurrency issues
- data concurrency, walkthroughs
- updating datasets, errors
- concurrency control, walkthroughs
ms.assetid: 73ee9759-0a90-48a9-bf7b-9d6fc17bff93
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 9d1c151b7f3afe977786ef3b308eff2de1c0857f
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85282356"
---
# <a name="handle-a-concurrency-exception"></a>Gérer une exception d’accès concurrentiel

Les exceptions d’accès concurrentiel ( <xref:System.Data.DBConcurrencyException?displayProperty=fullName> ) sont déclenchées lorsque deux utilisateurs essaient de modifier les mêmes données dans une base de données en même temps. Dans cette procédure pas à pas, vous allez créer une application Windows qui illustre comment intercepter un <xref:System.Data.DBConcurrencyException> , localiser la ligne à l’origine de l’erreur et apprendre une stratégie de gestion de celui-ci.

Cette procédure pas à pas vous guide tout au long du processus suivant :

1. Créez un projet d' **application de Windows Forms** .

2. Créez un nouveau jeu de données basé sur la table Customers de Northwind.

3. Créez un formulaire avec un <xref:System.Windows.Forms.DataGridView> pour afficher les données.

4. Remplir un DataSet avec les données de la table Customers dans la base de données Northwind.

5. Utilisez la fonctionnalité **afficher les données** de la table dans **Explorateur de serveurs** pour accéder aux données de la table Customers et modifier un enregistrement.

6. Remplacez le même enregistrement par une autre valeur, mettez à jour le DataSet et tentez d’écrire les modifications dans la base de données, ce qui entraîne le déclenchement d’une erreur d’accès concurrentiel.

7. Interceptez l’erreur, puis affichez les différentes versions de l’enregistrement, ce qui permet à l’utilisateur de déterminer s’il faut continuer et mettre à jour la base de données, ou annuler la mise à jour.

## <a name="prerequisites"></a>Prérequis

Cette procédure pas à pas utilise SQL Server Express base de données locale et l’exemple de base de données Northwind.

1. Si vous n’avez pas SQL Server Express base de données locale, installez-la à partir de la [page de téléchargement SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express)ou via le **Visual Studio installer**. Dans le **Visual Studio installer**, vous pouvez installer SQL Server Express base de données locale dans le cadre de la charge de travail de **stockage et de traitement des données** , ou en tant que composant individuel.

2. Installez l’exemple de base de données Northwind en procédant comme suit :

    1. Dans Visual Studio, ouvrez la fenêtre de **Explorateur d’objets SQL Server** . (Explorateur d’objets SQL Server est installé dans le cadre de la charge de travail **stockage et traitement des données** dans le Visual Studio installer.) Développez le nœud **SQL Server** . Cliquez avec le bouton droit sur votre instance de base de données locale, puis sélectionnez **nouvelle requête**.

       Une fenêtre de l’éditeur de requête s’ouvre.

    2. Copiez le [script Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) dans le presse-papiers. Ce script T-SQL crée la base de données Northwind à partir de zéro et la remplit avec des données.

    3. Collez le script T-SQL dans l’éditeur de requête, puis choisissez le bouton **exécuter** .

       Après un bref laps de temps, l’exécution de la requête se termine et la base de données Northwind est créée.

## <a name="create-a-new-project"></a>Création d'un projet

Commencez par créer une nouvelle Windows Forms application :

1. Dans Visual Studio, dans le menu **Fichier**, sélectionnez **Nouveau** > **Projet**.

2. Développez **Visual C#** ou **Visual Basic** dans le volet gauche, puis sélectionnez **Bureau Windows**.

3. Dans le volet central, sélectionnez le type de projet d' **application Windows Forms** .

4. Nommez le projet **ConcurrencyWalkthrough**, puis choisissez **OK**.

     Le projet **ConcurrencyWalkthrough** est créé et ajouté à **Explorateur de solutions**, et un nouveau formulaire s’ouvre dans le concepteur.

## <a name="create-the-northwind-dataset"></a>Créer le jeu de données Northwind

Ensuite, créez un jeu de données nommé **NorthwindDataSet**:

1. Dans le menu **données** , choisissez **Ajouter une nouvelle source de données**.

   L’Assistant Configuration de source de données s’ouvre.

2. Dans l’écran **choisir un type de source de données** , sélectionnez **base de**données.

   ![Assistant Configuration de source de données dans Visual Studio](media/data-source-configuration-wizard.png)

3. Sélectionnez une connexion à l’exemple de base de données Northwind dans la liste des connexions disponibles. Si la connexion n’est pas disponible dans la liste des connexions, sélectionnez **nouvelle connexion**.

    > [!NOTE]
    > Si vous vous connectez à un fichier de base de données local, sélectionnez **non** lorsque vous y êtes invité si vous souhaitez ajouter le fichier à votre projet.

4. Sur la page **enregistrer la chaîne de connexion dans le fichier de configuration de l’application** , sélectionnez **suivant**.

5. Développez le nœud **tables** et sélectionnez la table **Customers** . Le nom par défaut du jeu de données doit être **NorthwindDataSet**.

6. Sélectionnez **Terminer** pour ajouter le jeu de données au projet.

## <a name="create-a-data-bound-datagridview-control"></a>Créer un contrôle DataGridView lié aux données

Dans cette section, vous créez un <xref:System.Windows.Forms.DataGridView?displayProperty=nameWithType> en faisant glisser l’élément **Customers** de la fenêtre **sources de données** vers votre Windows Form.

1. Pour ouvrir la fenêtre **sources de données** , dans le menu **données** , choisissez afficher les **sources de données**.

2. Dans la fenêtre **sources de données** , développez le nœud **NorthwindDataSet** , puis sélectionnez la table **Customers** .

3. Sélectionnez la flèche vers le bas sur le nœud de la table, puis sélectionnez **DataGridView** dans la liste déroulante.

4. Faites glisser la table sur une zone vide de votre formulaire.

     Un <xref:System.Windows.Forms.DataGridView> contrôle nommé **CustomersDataGridView**et un <xref:System.Windows.Forms.BindingNavigator> **CustomersBindingNavigator**nommé sont ajoutés au formulaire qui est lié au <xref:System.Windows.Forms.BindingSource> . Cela est, à son tour, lié à la table Customers dans le NorthwindDataSet.

## <a name="test-the-form"></a>Tester le formulaire

Vous pouvez maintenant tester le formulaire pour vous assurer qu’il se comporte comme prévu jusqu’à ce point :

1. Appuyez sur **F5** pour exécuter l’application.

     Le formulaire s’affiche avec un <xref:System.Windows.Forms.DataGridView> contrôle qui est rempli avec les données de la table Customers.

2. Dans le menu **Déboguer**, sélectionnez **Arrêter le débogage**.

## <a name="handle-concurrency-errors"></a>Gérer les erreurs d’accès concurrentiel

La façon dont vous gérez les erreurs dépend des règles d’entreprise spécifiques qui régissent votre application. Pour cette procédure pas à pas, nous utilisons la stratégie suivante comme exemple pour gérer l’erreur d’accès concurrentiel.

L’application présente à l’utilisateur trois versions de l’enregistrement :

- Enregistrement actif dans la base de données

- Enregistrement d’origine chargé dans le jeu de données

- Modifications proposées dans le DataSet

L’utilisateur est alors en mesure de remplacer la base de données par la version proposée, ou d’annuler la mise à jour et d’actualiser le DataSet avec les nouvelles valeurs de la base de données.

### <a name="to-enable-the-handling-of-concurrency-errors"></a>Pour activer la gestion des erreurs d’accès concurrentiel

1. Créez un gestionnaire d’erreurs personnalisé.

2. Affichez les choix à l’utilisateur.

3. Traitez la réponse de l’utilisateur.

4. Renvoyez la mise à jour ou réinitialisez les données dans le DataSet.

### <a name="add-code-to-handle-the-concurrency-exception"></a>Ajouter du code pour gérer l’exception d’accès concurrentiel

Lorsque vous tentez d’effectuer une mise à jour et qu’une exception est levée, vous devez généralement effectuer une opération avec les informations fournies par l’exception levée. Dans cette section, vous allez ajouter du code qui tente de mettre à jour la base de données. Vous gérez également tout <xref:System.Data.DBConcurrencyException> ce qui peut être déclenché, ainsi que toutes les autres exceptions.

> [!NOTE]
> Les `CreateMessage` `ProcessDialogResults` méthodes et sont ajoutées plus loin dans la procédure pas à pas.

1. Ajoutez le code suivant sous la `Form1_Load` méthode :

   [!code-csharp[VbRaddataConcurrency#1](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_1.cs)]
   [!code-vb[VbRaddataConcurrency#1](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_1.vb)]

2. Remplacez la `CustomersBindingNavigatorSaveItem_Click` méthode pour appeler la `UpdateDatabase` méthode afin qu’elle ressemble à ce qui suit :

   [!code-csharp[VbRaddataConcurrency#2](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_2.cs)]
   [!code-vb[VbRaddataConcurrency#2](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_2.vb)]

### <a name="display-choices-to-the-user"></a>Afficher les choix à l’utilisateur

Le code que vous venez d’écrire appelle la `CreateMessage` procédure pour afficher les informations d’erreur à l’utilisateur. Pour cette procédure pas à pas, vous utilisez une boîte de message pour afficher les différentes versions de l’enregistrement à l’utilisateur. Cela permet à l’utilisateur de choisir s’il faut remplacer l’enregistrement par les modifications ou d’annuler la modification. Une fois que l’utilisateur a sélectionné une option (clique sur un bouton) dans la boîte de message, la réponse est transmise à la `ProcessDialogResult` méthode.

Créez le message en ajoutant le code suivant à l' **éditeur de code**. Entrez ce code sous la `UpdateDatabase` méthode :

[!code-csharp[VbRaddataConcurrency#4](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_3.cs)]
[!code-vb[VbRaddataConcurrency#4](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_3.vb)]

### <a name="process-the-users-response"></a>Traiter la réponse de l’utilisateur

Vous avez également besoin de code pour traiter la réponse de l’utilisateur à la boîte de message. Les options sont soit pour remplacer l’enregistrement en cours dans la base de données avec la modification proposée, soit pour abandonner les modifications locales et actualiser la table de données avec l’enregistrement qui se trouve actuellement dans la base de données. Si l’utilisateur choisit **Oui**, la <xref:System.Data.DataTable.Merge%2A> méthode est appelée avec l’argument *preserveChanges* défini sur **true**. Cela entraîne la réussite de la tentative de mise à jour, car la version d’origine de l’enregistrement correspond maintenant à l’enregistrement dans la base de données.

Ajoutez le code suivant sous le code qui a été ajouté dans la section précédente :

[!code-csharp[VbRaddataConcurrency#3](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_4.cs)]
[!code-vb[VbRaddataConcurrency#3](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_4.vb)]

## <a name="test-the-form"></a>Tester le formulaire

Vous pouvez maintenant tester le formulaire pour vous assurer qu’il se comporte comme prévu. Pour simuler une violation d’accès concurrentiel, vous modifiez les données dans la base de données après avoir rempli le NorthwindDataSet.

1. Appuyez sur **F5** pour exécuter l’application.

2. Une fois que le formulaire s’affiche, laissez-le s’exécuter et basculez vers l’IDE de Visual Studio.

3. Dans le menu **Affichage**, cliquez sur **Explorateur de serveurs**.

4. Dans **Explorateur de serveurs**, développez la connexion que votre application utilise, puis développez le nœud **tables** .

5. Cliquez avec le bouton droit sur la table **Customers** , puis sélectionnez **afficher les données**de la table.

6. Dans le premier enregistrement (**ALFKI**), remplacez **ContactName** par **Maria Anders2**.

    > [!NOTE]
    > Accédez à une autre ligne pour valider la modification.

7. Basculez vers le formulaire d’exécution du ConcurrencyWalkthrough.

8. Dans le premier enregistrement du formulaire (**ALFKI**), remplacez **ContactName** par **Maria Anders1**.

9. Sélectionnez le bouton **Enregistrer**.

     L’erreur d’accès concurrentiel est déclenchée et la boîte de message s’affiche.

   Si vous sélectionnez **non** , la mise à jour est annulée et le jeu de données est mis à jour avec les valeurs qui se trouvent actuellement dans la base de données. Si vous sélectionnez **Oui** , la valeur proposée est écrite dans la base de données.

## <a name="see-also"></a>Voir aussi

- [Enregistrer les données dans la base de données](../data-tools/save-data-back-to-the-database.md)
