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
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 26a52b082d447a2a4f14d0d09036c6b5df63656a
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2018
---
# <a name="handle-a-concurrency-exception"></a>Gérer une exception d’accès concurrentiel
Exceptions d’accès concurrentiel (<xref:System.Data.DBConcurrencyException>) sont déclenchés lorsque deux utilisateurs tentent de modifier les mêmes données dans une base de données en même temps. Dans cette procédure pas à pas, vous créez une application Windows qui montre comment intercepter un <xref:System.Data.DBConcurrencyException>, recherchez la ligne qui a provoqué l’erreur et savoir comment la gérer une stratégie.

 Cette procédure pas à pas vous guide tout au long du processus suivant :

1.  Créez un projet d’**application Windows Forms**.

2.  Créez un dataset basé sur Northwind `Customers` table.

3.  Créer un formulaire avec un <xref:System.Windows.Forms.DataGridView> pour afficher les données.

4.  Remplir un dataset avec des données à partir de la `Customers` table dans la base de données Northwind.

5.  Utilisez le **afficher les données de Table** fonctionnalité dans **l’Explorateur de serveurs** pour accéder à la `Customers` données et modifier un enregistrement de la table.

6.  Modifier le même enregistrement sur une autre valeur, mettre à jour le jeu de données et tentez d’écrire les modifications apportées à la base de données, ce qui entraîne une erreur d’accès concurrentiel est déclenchée.

7.  Intercepter l’erreur, puis afficher les différentes versions de l’enregistrement, permettant à l’utilisateur déterminer s’il faut continuer et mettre à jour la base de données, ou annuler la mise à jour.

## <a name="prerequisites"></a>Prérequis
Cette procédure pas à pas utilise SQL Server Express LocalDB et la base de données Northwind.

1.  Si vous n’avez pas SQL Server Express LocalDB, installez-le à partir de la [page de téléchargement de SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), ou via le **le programme d’installation de Visual Studio**. Dans le programme d’installation Visual Studio, SQL Server Express LocalDB peut être installé dans le cadre de la **stockage de données et de traitement** charge de travail, ou sous la forme d’un composant individuel.

2.  Installer la base de données Northwind en procédant comme suit :

    1. Dans Visual Studio, ouvrez le **l’Explorateur d’objets SQL Server** fenêtre. (Explorateur d’objets SQL Server est installé dans le cadre de la **stockage de données et de traitement** charge de travail dans le programme d’installation Visual Studio.) Développez le **SQL Server** nœud. Avec le bouton droit sur votre instance de base de données locale et sélectionnez **nouvelle requête...** .

       Une fenêtre d’éditeur de requête s’ouvre.

    2. Copie le [script Transact-SQL de Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) dans le Presse-papiers. Ce script T-SQL crée la base de données Northwind à partir de zéro et la remplit avec des données.

    3. Collez le script T-SQL dans l’éditeur de requête, puis choisissez le **Execute** bouton.

       Après une courte période, la requête est terminée et la base de données Northwind est créé.

> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu affichées peuvent différer de celles décrites dans l’aide selon vos paramètres actifs ou de l’édition que vous utilisez. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="create-a-new-project"></a>Créer un nouveau projet
 Commencez votre procédure pas à pas par la création d’une application Windows Forms.

#### <a name="to-create-a-new-windows-forms-application-project"></a>Pour créer un projet d’application Windows Forms

1. Dans Visual Studio, sur le **fichier** menu, sélectionnez **nouveau**, **projet...** .

2. Développez le **Visual C#** ou **Visual Basic** dans le volet gauche, puis sélectionnez **de bureau Windows classique**.

3. Dans le volet central, sélectionnez le **l’application Windows Forms** type de projet.

4. Nommez le projet **ConcurrencyWalkthrough**, puis choisissez **OK**.

     Le **ConcurrencyWalkthrough** projet est créé et ajouté à **l’Explorateur de solutions**, et un nouveau formulaire s’ouvre dans le concepteur.

## <a name="create-the-northwind-dataset"></a>Créer le jeu de données Northwind
 Dans cette section, vous créez un dataset nommé `NorthwindDataSet`.

#### <a name="to-create-the-northwinddataset"></a>Pour créer NorthwindDataSet

1.  Sur le **données** menu, choisissez **ajouter nouvelle source de données**.

     Le [Assistant de Configuration de Source de données](../data-tools/media/data-source-configuration-wizard.png) s’ouvre.

2.  Sur le **choisir un Type de Source de données** écran, sélectionnez **base de données**.

3.  Sélectionnez une connexion à la base de données Northwind dans la liste des connexions disponibles. Si la connexion n’est pas disponible dans la liste des connexions, sélectionnez **nouvelle connexion**

    > [!NOTE]
    >  Si vous vous connectez à un fichier de base de données locale, sélectionnez **non** lorsque le système demande si vous souhaitez que vous souhaitez ajouter le fichier à votre projet.

4.  Sur le **enregistrer la chaîne de connexion dans le fichier de configuration d’application** écran, sélectionnez **suivant**.

5.  Développez le **Tables** nœud et sélectionnez le `Customers` table. Le nom par défaut pour le jeu de données doit être `NorthwindDataSet`.

6.  Sélectionnez **Terminer** pour ajouter le jeu de données au projet.

## <a name="create-a-data-bound-datagridview-control"></a>Créer un contrôle de DataGridView lié aux données
 Dans cette section, vous créez un <xref:System.Windows.Forms.DataGridView> en faisant glisser le **clients** d’élément à partir de la **des Sources de données** fenêtre sur votre Windows Form.

#### <a name="to-create-a-datagridview-control-that-is-bound-to-the-customers-table"></a>Pour créer un contrôle DataGridView lié à la table Customers

1.  Sur le **données** menu, choisissez **afficher les Sources de données** pour ouvrir le **fenêtre Sources de données**.

2.  Dans le **des Sources de données** fenêtre, développez le **NorthwindDataSet** nœud, puis sélectionnez le **clients** table.

3.  Sélectionnez la flèche bas sur le nœud de la table, puis **DataGridView** dans la liste déroulante.

4.  Faites glisser la table dans une zone vide de votre formulaire.

     A <xref:System.Windows.Forms.DataGridView> contrôle nommé `CustomersDataGridView` et un <xref:System.Windows.Forms.BindingNavigator> nommé `CustomersBindingNavigator` sont ajoutés au formulaire qui est lié à la <xref:System.Windows.Forms.BindingSource>. Est de, est tour lié à la `Customers` de table dans le `NorthwindDataSet`.

## <a name="test-the-form"></a>Le formulaire de test
 Vous pouvez maintenant tester le formulaire pour vous assurer qu’il se comporte comme prévu jusqu'à ce point.

#### <a name="to-test-the-form"></a>Pour tester le formulaire

1.  Sélectionnez **F5** pour exécuter l’application

     Le formulaire s’affiche avec un <xref:System.Windows.Forms.DataGridView> contrôle est remplie avec les données à partir de la `Customers` table.

2.  Sur le **déboguer** menu, sélectionnez **arrêter le débogage**.

## <a name="handle-concurrency-errors"></a>Gérer les erreurs d’accès concurrentiel
 Dépend de la gestion des erreurs sur les règles d’entreprise spécifiques qui gèrent votre application. Pour cette procédure pas à pas, nous utilisons la stratégie suivante comme exemple pour savoir comment gérer l’erreur d’accès concurrentiel.

 L’application propose trois versions de l’enregistrement de l’utilisateur :

-   L’enregistrement actif dans la base de données

-   L’enregistrement d’origine qui est chargé dans le jeu de données

-   Les modifications proposées dans le jeu de données

L’utilisateur est alors en mesure de remplacer la base de données avec la version proposée, ou d’annuler la mise à jour et actualiser le jeu de données avec les nouvelles valeurs à partir de la base de données.

#### <a name="to-enable-the-handling-of-concurrency-errors"></a>Pour activer la gestion des erreurs d’accès concurrentiel

1.  Créez un gestionnaire d’erreurs personnalisées.

2.  Afficher les choix à l’utilisateur.

3.  Traiter la réponse de l’utilisateur.

4.  Renvoyer la mise à jour, ou de réinitialiser les données dans le jeu de données.

### <a name="add-code-to-handle-the-concurrency-exception"></a>Ajoutez du code pour gérer l’exception d’accès concurrentiel
 Lorsque vous essayez d’effectuer une mise à jour et une exception est levée, vous souhaitez généralement faire quelque chose avec les informations fournies par l’exception levée.

 Dans cette section, vous ajoutez le code qui tente de mettre à jour la base de données. Vous permet également de gérer tous les <xref:System.Data.DBConcurrencyException> susceptible d’être levée, ainsi que toute autre exception.

> [!NOTE]
>  Le `CreateMessage` et `ProcessDialogResults` méthodes seront ajoutés ultérieurement dans cette procédure pas à pas.

##### <a name="to-add-error-handling-for-the-concurrency-error"></a>Pour ajouter la gestion des erreurs pour l’erreur d’accès concurrentiel

1.  Ajoutez le code suivant ci-dessous le `Form1_Load` méthode :

     [!code-csharp[VbRaddataConcurrency#1](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_1.cs)]
     [!code-vb[VbRaddataConcurrency#1](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_1.vb)]

2.  Remplacez le `CustomersBindingNavigatorSaveItem_Click` méthode à appeler le `UpdateDatabase` méthode afin d’obtenir les éléments suivants :

     [!code-csharp[VbRaddataConcurrency#2](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_2.cs)]
     [!code-vb[VbRaddataConcurrency#2](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_2.vb)]

### <a name="display-choices-to-the-user"></a>Afficher les choix à l’utilisateur
 Le code que vous venez de taper appelle la `CreateMessage` procédure pour afficher des informations sur l’erreur à l’utilisateur. Pour cette procédure pas à pas, une boîte de message vous permet d’afficher les différentes versions de l’enregistrement à l’utilisateur. Cela permet à l’utilisateur de choisir s’il faut remplacer l’enregistrement avec les modifications ou annuler la modification. Une fois que l’utilisateur sélectionne une option (clique sur un bouton) dans la boîte de message, la réponse est passée à la `ProcessDialogResult` (méthode).

##### <a name="to-create-the-message-to-display-to-the-user"></a>Pour créer le message à afficher à l’utilisateur

-   Créer le message en ajoutant le code suivant à la **éditeur de Code**. Entrez le code suivant sous le `UpdateDatabase` (méthode).

     [!code-csharp[VbRaddataConcurrency#4](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_3.cs)]
     [!code-vb[VbRaddataConcurrency#4](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_3.vb)]

### <a name="process-the-users-response"></a>Traiter la réponse de l’utilisateur
 Vous devez également le code pour traiter la réponse de l’utilisateur à la boîte de message. Les options sont soit pour remplacer l’enregistrement actif dans la base de données avec la modification proposée, ou abandonner les modifications locales et actualiser la table de données avec l’enregistrement qui est actuellement dans la base de données. Si l’utilisateur clique sur Oui, le <xref:System.Data.DataTable.Merge%2A> méthode est appelée avec le *preserveChanges* affectée à l’argument `true`. Cela entraîne la tentative de mise à jour aboutisse, car la version d’origine de l’enregistrement correspond désormais à l’enregistrement dans la base de données.

##### <a name="to-process-the-user-input-from-the-message-box"></a>Pour traiter l’utilisateur d’entrée à partir de la boîte de message

-   Ajoutez le code suivant sous le code qui a été ajouté dans la section précédente.

     [!code-csharp[VbRaddataConcurrency#3](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_4.cs)]
     [!code-vb[VbRaddataConcurrency#3](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_4.vb)]

## <a name="test-the-form"></a>Le formulaire de test
 Vous pouvez maintenant tester le formulaire pour vous assurer qu’il se comporte comme prévu. Pour simuler une violation d’accès concurrentiel, vous devez modifier des données dans la base de données après avoir rempli le NorthwindDataSet.

#### <a name="to-test-the-form"></a>Pour tester le formulaire

1.  Sélectionnez **F5** pour exécuter l’application.

2.  Une fois que le formulaire s’affiche, laissez-la en cours d’exécution et passer à l’IDE de Visual Studio.

3.  Sur le **vue** menu, choisissez **l’Explorateur de serveurs**.

4.  Dans **l’Explorateur de serveurs**, développez la connexion de votre application est à l’aide, puis le **Tables** nœud.

5.  Avec le bouton droit le **clients** de table, puis sélectionnez **afficher les données de Table**.

6.  Dans le premier enregistrement (`ALFKI`) modifier `ContactName` à `Maria Anders2`.

    > [!NOTE]
    >  Accédez à une autre ligne pour valider la modification.

7.  Basculez vers le `ConcurrencyWalkthrough`de l’exécution de formulaire.

8.  Dans le premier enregistrement dans le formulaire (`ALFKI`), modifiez`ContactName` à `Maria Anders1`.

9. Sélectionnez le **enregistrer** bouton.

     L’erreur d’accès concurrentiel est déclenchée, et le message s’affiche.

10. En sélectionnant **non** annule la mise à jour et met à jour le jeu de données avec les valeurs qui se trouvent actuellement dans la base de données. En sélectionnant **Oui** écrit la valeur proposée dans la base de données.

## <a name="see-also"></a>Voir aussi

- [Enregistrer les données dans la base de données](../data-tools/save-data-back-to-the-database.md)