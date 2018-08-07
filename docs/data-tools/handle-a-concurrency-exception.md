---
title: Gérer une exception d’accès concurrentiel
ms.date: 09/11/2017
ms.topic: conceptual
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
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 6aca4815672d700fbea9d489f6316b8b0337f8df
ms.sourcegitcommit: 3a11feebad45a0dd4ac45efcbfdf172fce46e1de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2018
ms.locfileid: "39582331"
---
# <a name="handle-a-concurrency-exception"></a>Gérer une exception d’accès concurrentiel

Exceptions d’accès concurrentiel (<xref:System.Data.DBConcurrencyException?displayProperty=fullName>) sont déclenchés lorsque deux utilisateurs tentent de modifier les mêmes données dans une base de données en même temps. Dans cette procédure pas à pas, vous créez une application Windows qui montre comment intercepter une <xref:System.Data.DBConcurrencyException>, localisez la ligne qui a provoqué l’erreur et découvrez une stratégie pour son traitement.

Cette procédure pas à pas vous accompagne tout au long du processus suivant :

1. Créez un projet d’**application Windows Forms**.

2. Créer un nouveau jeu de données en fonction de la table Customers de Northwind.

3. Créer un formulaire avec un <xref:System.Windows.Forms.DataGridView> pour afficher les données.

4. Remplir un dataset avec des données à partir de la table Customers dans la base de données Northwind.

5. Utilisez le **afficher les données de Table** fonctionnalité dans **Explorateur de serveurs** pour accéder aux données de la table clients et de modifier un enregistrement.

6. Modifier le même enregistrement à une valeur différente, mettre à jour le jeu de données et essaient d’écrire les modifications dans la base de données, ce qui entraîne le déclenchement d’une erreur d’accès concurrentiel.

7. Intercepter l’erreur, puis afficher les différentes versions de l’enregistrement, permettant à l’utilisateur déterminer s’il faut continuer et mettre à jour de la base de données ou annuler la mise à jour.

## <a name="prerequisites"></a>Prérequis

Cette procédure pas à pas utilise SQL Server Express LocalDB et la base de données Northwind.

1. Si vous n’avez pas SQL Server Express LocalDB, installez-le à partir de la [page de téléchargement de SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), ou via le **le programme d’installation de Visual Studio**. Dans le **le programme d’installation de Visual Studio**, vous pouvez installer SQL Server Express LocalDB dans le cadre de la **stockage de données et de traitement** charge de travail, ou comme un composant individuel.

2. Installer la base de données Northwind en suivant ces étapes :

    1. Dans Visual Studio, ouvrez le **Explorateur d’objets SQL Server** fenêtre. (Explorateur d’objets SQL Server est installé dans le cadre de la **stockage de données et de traitement** charge de travail dans Visual Studio Installer.) Développez le **SQL Server** nœud. Avec le bouton droit sur votre instance de base de données locale et sélectionnez **nouvelle requête**.

       Une fenêtre d’éditeur de requête s’ouvre.

    2. Copie le [script Transact-SQL de Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) dans votre Presse-papiers. Ce script T-SQL crée la base de données Northwind à partir de zéro et la remplit avec des données.

    3. Collez le script T-SQL dans l’éditeur de requête, puis choisissez le **Execute** bouton.

       Après une courte période, la requête est terminée en cours d’exécution et la base de données Northwind est créé.

> [!NOTE]
> Les boîtes de dialogue et commandes de menu affichées peuvent différer de celles décrites dans l’aide selon vos paramètres actifs ou de l’édition que vous utilisez. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="create-a-new-project"></a>Créer un nouveau projet

Commencez par créer une application Windows Forms :

1. Dans Visual Studio, sur le **fichier** menu, sélectionnez **New** > **projet**.

2. Développez le **Visual C#** ou **Visual Basic** dans le volet gauche, puis sélectionnez **Windows Desktop**.

3. Dans le volet central, sélectionnez le **Windows Forms application** type de projet.

4. Nommez le projet **ConcurrencyWalkthrough**, puis choisissez **OK**.

     Le **ConcurrencyWalkthrough** projet est créé et ajouté à **l’Explorateur de solutions**, et un nouveau formulaire s’ouvre dans le concepteur.

## <a name="create-the-northwind-dataset"></a>Créer le jeu de données Northwind

Ensuite, créez un dataset nommé **NorthwindDataSet**:

1. Sur le **données** menu, choisissez **ajouter nouvelle source de données**.

   L’Assistant de Configuration de Source de données s’ouvre.

2. Sur le **choisir un Type de Source de données** s’affiche, sélectionnez **base de données**.

   ![Assistant de Configuration de Source de données dans Visual Studio](media/data-source-configuration-wizard.png)

3. Sélectionnez une connexion à la base de données Northwind dans la liste des connexions disponibles. Si la connexion n’est pas disponible dans la liste des connexions, sélectionnez **nouvelle connexion**.

    > [!NOTE]
    > Si vous vous connectez à un fichier de base de données locale, sélectionnez **non** lorsque vous le feriez pour vous confirmer ajouter le fichier à votre projet.

4. Sur le **enregistrer la chaîne de connexion au fichier de configuration de l’application** s’affiche, sélectionnez **suivant**.

5. Développez le **Tables** nœud et sélectionnez le **clients** table. Le nom par défaut pour le jeu de données doit être **NorthwindDataSet**.

6. Sélectionnez **Terminer** pour ajouter le jeu de données au projet.

## <a name="create-a-data-bound-datagridview-control"></a>Créer un contrôle de DataGridView lié aux données

Dans cette section, vous allez créer un <xref:System.Windows.Forms.DataGridView?displayProperty=nameWithType> en faisant glisser le **clients** d’élément à partir de la **des Sources de données** fenêtre sur votre formulaire Windows.

1. Sur le **données** menu, choisissez **afficher les Sources de données** pour ouvrir le **fenêtre Sources de données**.

2. Dans le **des Sources de données** fenêtre, développez le **NorthwindDataSet** nœud, puis sélectionnez le **clients** table.

3. Sélectionnez la flèche bas sur le nœud de la table, puis **DataGridView** dans la liste déroulante.

4. Faites glisser la table dans une zone vide de votre formulaire.

     Un <xref:System.Windows.Forms.DataGridView> contrôle nommé **CustomersDataGridView**et un <xref:System.Windows.Forms.BindingNavigator> nommé **CustomersBindingNavigator**, sont ajoutés au formulaire qui est lié à la <xref:System.Windows.Forms.BindingSource>. Cela est, à son tour, lié à la table Customers dans NorthwindDataSet.

## <a name="test-the-form"></a>Le formulaire de test

Vous pouvez maintenant tester le formulaire pour vous assurer qu’il se comporte comme prévu jusqu'à ce point :

1. Sélectionnez **F5** pour exécuter l’application.

     Le formulaire s’affiche avec un <xref:System.Windows.Forms.DataGridView> contrôle sur ce dernier qui est rempli avec des données à partir de la table Customers.

2. Sur le **déboguer** menu, sélectionnez **arrêter le débogage**.

## <a name="handle-concurrency-errors"></a>Gérer les erreurs d’accès concurrentiel

Gestion des erreurs varie selon les règles d’entreprise spécifiques qui régissent votre application. Pour cette procédure pas à pas, nous utilisons la stratégie suivante comme exemple pour savoir comment gérer l’erreur d’accès concurrentiel.

L’application présente à l’utilisateur avec trois versions de l’enregistrement :

- L’enregistrement actif dans la base de données

- L’enregistrement d’origine qui est chargé dans le jeu de données

- Les modifications proposées dans le jeu de données

L’utilisateur peut ensuite remplacer la base de données avec la version proposée, ou d’annuler la mise à jour et actualiser le jeu de données avec les nouvelles valeurs à partir de la base de données.

### <a name="to-enable-the-handling-of-concurrency-errors"></a>Pour activer la gestion des erreurs d’accès concurrentiel

1. Créer un gestionnaire d’erreurs personnalisé.

2. Afficher les choix à l’utilisateur.

3. Traiter la réponse de l’utilisateur.

4. Renvoyez la mise à jour ou réinitialiser les données dans le jeu de données.

### <a name="add-code-to-handle-the-concurrency-exception"></a>Ajoutez du code pour gérer l’exception d’accès concurrentiel

Lorsque vous tentez d’effectuer une mise à jour et une exception est levée, vous souhaitez généralement faire quelque chose avec les informations fournies par l’exception levée. Dans cette section, vous ajoutez le code qui tente de mettre à jour de la base de données. Vous permet également de gérer les <xref:System.Data.DBConcurrencyException> qui peut être levée, ainsi que toute autre exception.

> [!NOTE]
> Le `CreateMessage` et `ProcessDialogResults` méthodes sont ajoutées ultérieurement dans la procédure pas à pas.

1. Ajoutez le code suivant ci-dessous le `Form1_Load` méthode :

     [!code-csharp[VbRaddataConcurrency#1](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_1.cs)]
     [!code-vb[VbRaddataConcurrency#1](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_1.vb)]

2. Remplacez le `CustomersBindingNavigatorSaveItem_Click` méthode à appeler le `UpdateDatabase` méthode afin qu’il ressemble à ce qui suit :

     [!code-csharp[VbRaddataConcurrency#2](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_2.cs)]
     [!code-vb[VbRaddataConcurrency#2](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_2.vb)]

### <a name="display-choices-to-the-user"></a>Afficher les choix à l’utilisateur

Le code que vous venez de taper appelle le `CreateMessage` procédure pour afficher des informations d’erreur à l’utilisateur. Pour cette procédure pas à pas, vous utilisez une boîte de message pour afficher les différentes versions de l’enregistrement à l’utilisateur. Cela permet à l’utilisateur de choisir s’il faut remplacer l’enregistrement avec les modifications ou annuler la modification. Une fois que l’utilisateur sélectionne une option (clique sur un bouton) dans la boîte de message, la réponse est transmise à la `ProcessDialogResult` (méthode).

Créer le message en ajoutant le code suivant à la **éditeur de Code**. Entrez le code suivant sous le `UpdateDatabase` méthode :

     [!code-csharp[VbRaddataConcurrency#4](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_3.cs)]
     [!code-vb[VbRaddataConcurrency#4](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_3.vb)]

### <a name="process-the-users-response"></a>Traiter la réponse de l’utilisateur

Vous devez également le code permettant de traiter la réponse de l’utilisateur à la boîte de message. Les options sont soit pour remplacer l’enregistrement actif dans la base de données par la modification proposée, ou abandonner les modifications locales et actualiser la table de données avec l’enregistrement qui se trouve actuellement dans la base de données. Si l’utilisateur choisit **Oui**, le <xref:System.Data.DataTable.Merge%2A> méthode est appelée avec le *preserveChanges* affectée à l’argument **true**. Cela entraîne la tentative de mise à jour aboutisse, car la version d’origine de l’enregistrement correspond désormais à l’enregistrement dans la base de données.

Ajoutez le code suivant sous le code qui a été ajouté dans la section précédente :

     [!code-csharp[VbRaddataConcurrency#3](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_4.cs)]
     [!code-vb[VbRaddataConcurrency#3](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_4.vb)]

## <a name="test-the-form"></a>Le formulaire de test

Vous pouvez maintenant tester le formulaire pour vous assurer qu’il se comporte comme prévu. Pour simuler une violation d’accès concurrentiel, vous modifiez les données dans la base de données après avoir rempli le NorthwindDataSet.

1. Sélectionnez **F5** pour exécuter l’application.

2. Une fois que le formulaire s’affiche, laissez-la en cours d’exécution et basculer vers l’IDE Visual Studio.

3. Sur le **vue** menu, choisissez **Explorateur de serveurs**.

4. Dans **Explorateur de serveurs**, développez la connexion de votre application est à l’aide, puis développez le **Tables** nœud.

5. Avec le bouton droit le **clients** table, puis sélectionnez **afficher les données de Table**.

6. Dans le premier enregistrement (**ALFKI**), modifiez **ContactName** à **Maria Anders2**.

    > [!NOTE]
    > Accédez à une autre ligne pour valider la modification.

7. Basculez vers le formulaire en cours d’exécution le ConcurrencyWalkthrough.

8. Dans le premier enregistrement sur le formulaire (**ALFKI**), modifiez **ContactName** à **Maria Anders1**.

9. Sélectionnez le **enregistrer** bouton.

     L’erreur d’accès concurrentiel est levée, et la boîte de message s’affiche.

   En sélectionnant **non** annule la mise à jour et met à jour le jeu de données avec les valeurs qui se trouvent actuellement dans la base de données. En sélectionnant **Oui** écrit la valeur proposée dans la base de données.

## <a name="see-also"></a>Voir aussi

- [Enregistrer les données dans la base de données](../data-tools/save-data-back-to-the-database.md)