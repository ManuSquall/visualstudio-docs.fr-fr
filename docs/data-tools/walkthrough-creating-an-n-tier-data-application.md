---
title: 'Procédure pas à pas : Création d’une application de données multiniveaux'
ms.date: 09/08/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- n-tier applications, creating
- n-tier applications, walkthroughs
ms.assetid: d15e4d31-2839-48d9-9e0e-2e73404d82a2
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: c3ee28514af9db5b0a03ce8b9805ef773c649a42
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54993163"
---
# <a name="walkthrough-create-an-n-tier-data-application"></a>Procédure pas à pas : Créer une application de données multiniveaux
Les applications de données *multiniveaux* sont des applications qui accèdent aux données et sont divisées en plusieurs couches logiques, ou *niveaux*. La séparation des composants de l'application en couches distinctes favorise la possibilité de tenir à jour et de monter en charge l'application. Cela est possible grâce à une application plus facile des nouvelles technologies sur chaque couche sans avoir à reconcevoir toute la solution. L'architecture multicouche inclut une couche Présentation, une couche intermédiaire et une couche Données. La couche intermédiaire inclut généralement une couche d'accès aux données, une couche logique métier et des composants partagés tels que l'authentification et la validation. La couche Données inclut une base de données relationnelle. Les applications multicouches stockent généralement les informations sensibles dans la couche d'accès aux données de la couche intermédiaire, pour la tenir hors de portée des utilisateurs finaux qui accèdent à la couche Présentation. Pour plus d’informations, consultez [vue d’ensemble des applications de données multicouches](../data-tools/n-tier-data-applications-overview.md).

Pour séparer plusieurs couches d'une application multicouche, il est possible de créer des projets distincts pour chaque couche que vous voulez inclure dans votre application. Les datasets typés contiennent une propriété `DataSet Project` qui détermine les projets dans lesquels le code du dataset et des `TableAdapter`s générés doit intervenir.

Cette procédure pas à pas décrit comment séparer le code du dataset et `TableAdapter` en projets de bibliothèque de classes discrètes à l’aide du **Concepteur de DataSet**. Une fois que vous séparez le jeu de données et le code du TableAdapter, vous créez un [Services Windows Communication Foundation et WCF Data Services dans Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md) service pour appeler la couche d’accès aux données. Enfin, vous créez une application Windows Forms en tant que la couche de présentation. Cette couche accède aux données à partir du service de données.

Au cours de cette procédure pas à pas, vous procédez comme suit :

-   Créer une solution multicouche contenant plusieurs projets.

-   ajouter deux projets de bibliothèque de classes à la solution multicouche ;

-   Créez un dataset typé à l’aide de l’**Assistant Configuration de source de données**.

-   Séparer le texte généré [TableAdapters](create-and-configure-tableadapters.md) et le code de jeu de données dans des projets distincts.

-   créer un service WCF (Windows Communication Foundation) pour appeler la couche d'accès aux données ;

-   créer des fonctions dans le service pour récupérer les données de la couche d'accès aux données ;

-   créer une application Windows Forms faisant office de couche Présentation ;

-   créer des contrôles Windows Forms liés à la source de données ;

-   écrire du code pour remplir les tables de données.

![lien vers la vidéo](../data-tools/media/playvideo.gif) pour obtenir une version vidéo de cette rubrique, consultez [Video How to : Création d’une application de données multiniveaux](http://go.microsoft.com/fwlink/?LinkId=115188).

## <a name="prerequisites"></a>Prérequis
Cette procédure pas à pas utilise SQL Server Express LocalDB et la base de données Northwind.

1. Si vous n’avez pas SQL Server Express LocalDB, installez-le à partir de la [page de téléchargement de SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), ou via le **le programme d’installation de Visual Studio**. Dans le **le programme d’installation de Visual Studio**, vous pouvez installer SQL Server Express LocalDB dans le cadre de la **développement .NET desktop** charge de travail, ou comme un composant individuel.

2. Installer la base de données Northwind en suivant ces étapes :

    1. Dans Visual Studio, ouvrez le **Explorateur d’objets SQL Server** fenêtre. (**Explorateur d’objets SQL Server** est installé dans le cadre de la **stockage de données et de traitement** charge de travail dans Visual Studio Installer.) Développez le **SQL Server** nœud. Avec le bouton droit sur votre instance de base de données locale et sélectionnez **nouvelle requête**.

       Une fenêtre d’éditeur de requête s’ouvre.

    2. Copie le [script Transact-SQL de Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) dans votre Presse-papiers. Ce script T-SQL crée la base de données Northwind à partir de zéro et la remplit avec des données.

    3. Collez le script T-SQL dans l’éditeur de requête, puis choisissez le **Execute** bouton.

       Après une courte période, la requête est terminée en cours d’exécution et la base de données Northwind est créé.

## <a name="create-the-n-tier-solution-and-class-library-to-hold-the-dataset-dataentitytier"></a>Créer la bibliothèque de classes et de solution de multiniveau pour contenir le dataset (DataEntityTier)
 La première étape de cette procédure pas à pas consiste à créer une solution et deux projets de bibliothèque de classes. La première bibliothèque de classes conserve le jeu de données (typé généré `DataSet` classe et les tables de données qui contiennent des données de l’application). Ce projet est utilisé comme couche d'entité de données de l'application et figure généralement dans la couche intermédiaire. Le jeu de données crée le jeu de données initial et automatiquement sépare le code en deux bibliothèques de classes.

> [!NOTE]
> Nommez correctement le projet et la solution avant de cliquer sur **OK**. Il vous sera alors plus facile de terminer cette procédure pas à pas.

### <a name="to-create-the-n-tier-solution-and-dataentitytier-class-library"></a>Pour créer la solution multicouche et la bibliothèque de classes DataEntityTier

1. Dans Visual Studio, sur le **fichier** menu, sélectionnez **New** > **projet**.

2. Développez le **Visual C#**  ou **Visual Basic** dans le volet gauche, puis sélectionnez **Windows Desktop**.

3. Dans le volet central, sélectionnez le **bibliothèque de classes** type de projet.

4. Nommez le projet **DataEntityTier**.

5. Nommez la solution **NTierWalkthrough**, puis choisissez **OK**.

     Une solution NTierWalkthrough contenant le projet DataEntityTier est créée et ajoutée à l’**Explorateur de solutions**.

## <a name="create-the-class-library-to-hold-the-tableadapters-dataaccesstier"></a>Créer la bibliothèque de classes pour contenir les TableAdapters (DataAccessTier)
 L'étape qui suit la création du projet DataEntityTier est la création d'un autre projet de bibliothèque de classes. Ce projet contient les TableAdapters générés et est appelé le *couche d’accès aux données* de l’application. La couche d'accès aux données contient les informations requises pour se connecter à la base de données et figure généralement dans la couche intermédiaire.

### <a name="to-create-a-separate-class-library-for-the-tableadapters"></a>Pour créer une bibliothèque de classes distinct pour les TableAdapters

1. Avec le bouton droit sur la solution dans **l’Explorateur de solutions** et choisissez **ajouter** > **nouveau projet**.

2. Dans le **nouveau projet** boîte de dialogue, dans le volet central, sélectionnez **bibliothèque de classes**.

3. Nommez le projet **DataAccessTier** et choisissez **OK**.

     Le projet DataAccessTier est créé et ajouté à la solution NTierWalkthrough.

## <a name="create-the-dataset"></a>Créer le jeu de données
 L'étape qui suit consiste à créer le dataset typé. Datasets typés sont créés avec la classe dataset (y compris `DataTables` classes) et le `TableAdapter` classes dans un projet unique. (Toutes les classes sont générées dans un seul fichier.) Lorsque vous séparez le jeu de données et les TableAdapters dans des projets différents, il est la classe de jeu de données est déplacée vers l’autre projet, en laissant le `TableAdapter` classes dans le projet d’origine. Par conséquent, créer le jeu de données dans le projet qui doit contenir les TableAdapters (le projet DataAccessTier). Vous créez le jeu de données à l’aide de la **Assistant de Configuration de Source de données**.

> [!NOTE]
> Vous devez avoir accès à l'exemple de base de données Northwind pour créer la connexion. Pour plus d’informations sur la façon de configurer la base de données Northwind, consultez [Comment : Installer les bases de données exemple](../data-tools/installing-database-systems-tools-and-samples.md).

### <a name="to-create-the-dataset"></a>Pour créer le groupe de données

1. Sélectionnez le **DataAccessTier** dans **l’Explorateur de solutions**.

2. Sur le **données** menu, sélectionnez **afficher les Sources de données**.

   La fenêtre **Sources de données** s’ouvre.

3. Dans la fenêtre **Sources de données**, sélectionnez **Ajouter une nouvelle source de données** pour démarrer l’**Assistant Configuration de source de données**.

4. Sur le **choisir un Type de Source de données** page, sélectionnez **base de données** , puis sélectionnez **suivant**.

5. Dans la page **Choisir votre connexion de données**, effectuez l’une des opérations suivantes :

     Si une connexion de données à l’exemple de base de données Northwind est disponible dans la liste déroulante, sélectionnez-la.

     - ou -

     Sélectionnez **nouvelle connexion** pour ouvrir le **ajouter une connexion** boîte de dialogue.

6. Si la base de données requiert un mot de passe, sélectionnez l’option pour inclure les données sensibles, puis choisissez **suivant**.

    > [!NOTE]
    > Si vous avez sélectionné un fichier de base de données local (au lieu de vous connecter à SQL Server), il vous sera peut-être demandé si vous souhaitez ajouter le fichier au projet. Choisissez **Oui** pour ajouter le fichier de base de données au projet.

7. Sélectionnez **suivant** sur le **enregistrer la chaîne de connexion au fichier de Configuration de l’Application** page.

8. Développez le nœud **Tables** dans la page **Choisir vos objets de base de données** .

9. Sélectionnez les cases à cocher pour le **clients** et **commandes** tables, puis choisissez **Terminer**.

     NorthwindDataSet est ajouté au projet DataAccessTier et apparaît dans la fenêtre **Sources de données**.

## <a name="separate-the-tableadapters-from-the-dataset"></a>Séparer les TableAdapters de Dataset
 Une fois que vous avez créé le dataset, séparez la classe DataSet générée et les TableAdapters. Pour ce faire, définissez la propriété **Projet DataSet** sur le nom du projet dans lequel stocker la classe DataSet extraite.

### <a name="to-separate-the-tableadapters-from-the-dataset"></a>Pour séparer les TableAdapters du dataset

1. Double-cliquez sur **NorthwindDataSet.xsd** dans l’**Explorateur de solutions** pour ouvrir le dataset dans le **Concepteur de DataSet**.

2. Sélectionnez une zone vide sur le concepteur.

3. Recherchez le nœud **Projet DataSet** dans la fenêtre **Propriétés**.

4. Dans le **DataSet Project** liste, sélectionnez **DataEntityTier**.

5. Dans le menu **Générer**, sélectionnez **Générer la solution**.

   Le dataset et les TableAdapters sont divisés entre les deux projets de bibliothèque de classes. Le projet qui contenait initialement l’ensemble du dataset (`DataAccessTier`) contient à présent que les TableAdapters. Le projet désigné dans la **DataSet Project** propriété (`DataEntityTier`) contient le dataset typé : *NorthwindDataSet.Dataset.Designer.vb* (ou *NorthwindDataSet.Dataset.Designer.cs*).

> [!NOTE]
> Quand vous séparez les datasets et les TableAdapters (en définissant la propriété **Projet DataSet**), les classes DataSet partielles existantes dans le projet ne sont pas déplacées automatiquement. Les classes DataSet partielles existantes doivent être manuellement déplacées dans le projet DataSet.

## <a name="create-a-new-service-application"></a>Créer une nouvelle Application de Service
Cette procédure pas à pas montre comment accéder à la couche d’accès aux données à l’aide d’un service WCF, nous allons donc créer une nouvelle application de service WCF.

### <a name="to-create-a-new-wcf-service-application"></a>Pour créer une application de service WCF

1. Avec le bouton droit sur la solution dans **l’Explorateur de solutions** et choisissez **ajouter** > **nouveau projet**.

2. Dans le **nouveau projet** boîte de dialogue, dans le volet gauche, sélectionnez **WCF**. Dans le volet central, sélectionnez **bibliothèque du Service WCF**.

3. Nommez le projet **DataService** et sélectionnez **OK**.

     Le projet DataService est créé et ajouté à la solution NTierWalkthrough.

## <a name="create-methods-in-the-data-access-tier-to-return-the-customers-and-orders-data"></a>Créez des méthodes dans la couche d’accès aux données pour retourner les données customers et orders
 Le service de données doit appeler deux méthodes dans la couche d’accès aux données : `GetCustomers` et `GetOrders`. Ces méthodes retournent Northwind `Customers` et `Orders` tables. Créer le `GetCustomers` et `GetOrders` méthodes dans le `DataAccessTier` projet.

### <a name="to-create-a-method-in-the-data-access-tier-that-returns-the-customers-table"></a>Pour créer une méthode dans la couche d'accès aux données qui retourne la table Customers

1. Dans **l’Explorateur de solutions**, double-cliquez sur **NorthwindDataset.xsd** pour ouvrir le jeu de données.

2. Avec le bouton droit **CustomersTableAdapter** et cliquez sur **ajouter une requête**.

3. Dans la page **Choisir un type de commande**, conservez la valeur par défaut **Utiliser des instructions SQL**, puis cliquez sur **Suivant**.

4. Dans la page **Choisir un type de requête**, conservez la valeur par défaut **SELECT qui retourne des lignes**, puis cliquez sur **Suivant**.

5. Dans la page **Spécifier une instruction SQL SELECT**, conservez la requête par défaut et cliquez sur **Suivant**.

6. Dans la page **Choisir les méthodes à générer**, tapez **GetCustomers** dans le champ **Nom de la méthode** de la section **Retourner un DataTable**.

7. Cliquez sur **Terminer**.

### <a name="to-create-a-method-in-the-data-access-tier-that-returns-the-orders-table"></a>Pour créer une méthode dans la couche d'accès aux données qui retourne la table Orders

1. Cliquez avec le bouton droit sur **OrdersTableAdapter**, puis cliquez sur **Ajouter une requête**.

2. Dans la page **Choisir un type de commande**, conservez la valeur par défaut **Utiliser des instructions SQL**, puis cliquez sur **Suivant**.

3. Dans la page **Choisir un type de requête**, conservez la valeur par défaut **SELECT qui retourne des lignes**, puis cliquez sur **Suivant**.

4. Dans la page **Spécifier une instruction SQL SELECT**, conservez la requête par défaut et cliquez sur **Suivant**.

5. Dans la page **Choisir les méthodes à générer**, tapez **GetOrders** dans le champ **Nom de la méthode** de la section **Retourner un DataTable**.

6. Cliquez sur **Terminer**.

7. Dans le menu **Générer** , cliquez sur **Générer la solution**.

## <a name="add-a-reference-to-the-data-entity-and-data-access-tiers-to-the-data-service"></a>Ajouter une référence à l’entité de données et les niveaux d’accès de données au service de données
 Le service de données nécessitant des informations du dataset et des TableAdapters, ajoutez des références aux projets **DataEntityTier** et **DataAccessTier**.

### <a name="to-add-references-to-the-data-service"></a>Pour ajouter des références au service de données

1. Cliquez avec le bouton droit sur **DataService** dans l’**Explorateur de solutions**, puis cliquez sur **Ajouter une référence**.

2. Cliquez sur l’onglet **Projets** de la boîte de dialogue **Ajouter une référence**.

3. Sélectionnez à la fois les projets **DataAccessTier** et **DataEntityTier**.

4. Cliquez sur **OK**.

## <a name="add-functions-to-the-service-to-call-the-getcustomers-and-getorders-methods-in-the-data-access-tier"></a>Ajouter des fonctions au service pour appeler les méthodes GetCustomers et GetOrders dans la couche d’accès aux données
 Maintenant que la couche d'accès aux données contient les méthodes permettant de retourner les données, créez des méthodes dans le service de données pour appeler les méthodes dans la couche d'accès aux données.

> [!NOTE]
> Pour les projets C#, vous devez ajouter une référence à l'assembly `System.Data.DataSetExtensions` pour la compilation du code suivant.

### <a name="to-create-the-getcustomers-and-getorders-functions-in-the-data-service"></a>Pour créer les fonctions GetCustomers et GetOrders dans le service de données

1. Dans le projet **DataService**, double-cliquez sur **IService1.vb** ou sur **IService1.cs**.

2. Ajoutez le code suivant sous le commentaire **Ajoutez vos opérations de service ici** :

    ```vb
    <OperationContract()> _
    Function GetCustomers() As DataEntityTier.NorthwindDataSet.CustomersDataTable

    <OperationContract()> _
    Function GetOrders() As DataEntityTier.NorthwindDataSet.OrdersDataTable
    ```

    ```csharp
    [OperationContract]
    DataEntityTier.NorthwindDataSet.CustomersDataTable GetCustomers();

    [OperationContract]
    DataEntityTier.NorthwindDataSet.OrdersDataTable GetOrders();
    ```

3. Dans le projet DataService, double-cliquez sur **Service1.vb** (ou sur **Service1.cs**).

4. Ajoutez le code suivant à la classe **Service1** :

    ```vb
    Public Function GetCustomers() As DataEntityTier.NorthwindDataSet.CustomersDataTable Implements IService1.GetCustomers
        Dim CustomersTableAdapter1 As New DataAccessTier.NorthwindDataSetTableAdapters.CustomersTableAdapter
        Return CustomersTableAdapter1.GetCustomers()
    End Function

    Public Function GetOrders() As DataEntityTier.NorthwindDataSet.OrdersDataTable Implements IService1.GetOrders
        Dim OrdersTableAdapter1 As New DataAccessTier.NorthwindDataSetTableAdapters.OrdersTableAdapter
        Return OrdersTableAdapter1.GetOrders()
    End Function
    ```

    ```csharp
    public DataEntityTier.NorthwindDataSet.CustomersDataTable GetCustomers()
    {
        DataAccessTier.NorthwindDataSetTableAdapters.CustomersTableAdapter
             CustomersTableAdapter1
            = new DataAccessTier.NorthwindDataSetTableAdapters.CustomersTableAdapter();
        return CustomersTableAdapter1.GetCustomers();
    }
    public DataEntityTier.NorthwindDataSet.OrdersDataTable GetOrders()
    {
        DataAccessTier.NorthwindDataSetTableAdapters.OrdersTableAdapter
             OrdersTableAdapter1
            = new DataAccessTier.NorthwindDataSetTableAdapters.OrdersTableAdapter();
        return OrdersTableAdapter1.GetOrders();
    }
    ```

5. Dans le menu **Générer** , cliquez sur **Générer la solution**.

## <a name="create-a-presentation-tier-to-display-data-from-the-data-service"></a>Créer une couche de présentation pour afficher des données à partir du service de données
 Maintenant que la solution contient le service de données qui possède des méthodes qui appellent dans les données de couche d’accès aux, créez un autre projet qui appelle le service de données et de présenter les données aux utilisateurs. Pour cette procédure pas à pas, créez une application Windows Forms. Il s’agit de la couche Présentation de l’application multicouche.

### <a name="to-create-the-presentation-tier-project"></a>Pour créer le projet de couche Présentation

1. Avec le bouton droit sur la solution dans **l’Explorateur de solutions** et choisissez **ajouter** > **nouveau projet**.

2. Dans le **nouveau projet** boîte de dialogue, dans le volet gauche, sélectionnez **Windows Desktop**. Dans le volet central, sélectionnez **Windows Forms application**.

3. Nommez le projet **PresentationTier** et cliquez sur **OK**.

    Le projet PresentationTier est créé et ajouté à la solution NTierWalkthrough.

## <a name="set-the-presentationtier-project-as-the-startup-project"></a>Définir le projet PresentationTier comme projet de démarrage
Nous allons définir le **PresentationTier** projet comme projet de démarrage de la solution, car c’est l’application client réel qui présente et interagit avec les données.

### <a name="to-set-the-new-presentation-tier-project-as-the-startup-project"></a>Pour définir le nouveau projet de niveau Présentation comme projet de démarrage

-   Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur **PresentationTier**, puis cliquez sur **Définir comme projet de démarrage**.

## <a name="add-references-to-the-presentation-tier"></a>Ajoutez des références à la couche de présentation
 L’application cliente PresentationTier nécessite une référence de service au service de données pour accéder aux méthodes du service. Par ailleurs, une référence au dataset est requise pour activer le partage de type par le service WCF. Jusqu'à ce que vous activez le partage de type via le service de données, le code ajouté à la classe dataset partielle n’est pas disponible pour la couche de présentation. Étant donné que vous ajoutez généralement le code, par exemple de code de validation à la ligne et colonne événements d’une table de données, de modification, il est probable que vous souhaitez accéder à ce code à partir du client.

### <a name="to-add-a-reference-to-the-presentation-tier"></a>Pour ajouter une référence à la couche Présentation

1. Dans **l’Explorateur de solutions**, avec le bouton droit **PresentationTier** et sélectionnez **ajouter une référence**.

2. Dans le **ajouter une référence** boîte de dialogue, sélectionnez le **projets** onglet.

3. Sélectionnez **DataEntityTier** et choisissez **OK**.

### <a name="to-add-a-service-reference-to-the-presentation-tier"></a>Pour ajouter une référence de service à la couche Présentation

1. Dans **l’Explorateur de solutions**, avec le bouton droit **PresentationTier** et sélectionnez **ajouter une référence de Service**.

2. Dans le **ajouter une référence de Service** boîte de dialogue, sélectionnez **Discover**.

3. Sélectionnez **Service1** et choisissez **OK**.

    > [!NOTE]
    > Si vous avez plusieurs services sur l’ordinateur actuel, sélectionnez le service que vous avez créé précédemment dans cette procédure pas à pas (le service qui contient le `GetCustomers` et `GetOrders` méthodes).

## <a name="add-datagridviews-to-the-form-to-display-the-data-returned-by-the-data-service"></a>Ajout de DataGridViews au formulaire pour afficher les données retournées par le service de données
 Une fois que vous avez ajouté la référence de service au service de données, la fenêtre **Sources de données** est automatiquement remplie avec les données retournées par le service.

### <a name="to-add-two-data-bound-datagridviews-to-the-form"></a>Pour ajouter au formulaire deux DataGridViews liés aux données

1. Dans l’**Explorateur de solutions**, sélectionnez le projet **PresentationTier**.

2. Dans la fenêtre **Sources de données**, développez **NorthwindDataSet** et accédez au nœud **Customers**.

3. Faites glisser le nœud **Customers** vers Form1.

4. Dans la fenêtre **Sources de données**, développez le nœud **Customers** et accédez au nœud **Orders** associé (le nœud **Orders** imbriqué dans le nœud **Customers**).

5. Faites glisser le nœud **Orders** associé vers Form1.

6. Créez un gestionnaire d'événements `Form1_Load` en double-cliquant sur une zone vide du formulaire.

7. Ajoutez le code ci-après au gestionnaire d'événements `Form1_Load`.

    ```vb
    Dim DataSvc As New ServiceReference1.Service1Client
    NorthwindDataSet.Customers.Merge(DataSvc.GetCustomers)
    NorthwindDataSet.Orders.Merge(DataSvc.GetOrders)
    ```

    ```csharp
    ServiceReference1.Service1Client DataSvc =
        new ServiceReference1.Service1Client();
    northwindDataSet.Customers.Merge(DataSvc.GetCustomers());
    northwindDataSet.Orders.Merge(DataSvc.GetOrders());
    ```

## <a name="increase-the-maximum-message-size-allowed-by-the-service"></a>Augmenter la taille de message maximale autorisée par le service
La valeur par défaut `maxReceivedMessageSize` n’est pas suffisamment grande pour contenir les données récupérées à partir de la `Customers` et `Orders` tables. Dans les étapes suivantes, vous augmentez la valeur en 6553600. Vous modifiez la valeur sur le client, ce qui met automatiquement à jour la référence de service.

> [!NOTE]
> La taille inférieure par défaut est destinée à limiter l'exposition aux attaques par déni de service. Pour plus d'informations, consultez <xref:System.ServiceModel.WSHttpBindingBase.MaxReceivedMessageSize%2A>.

### <a name="to-increase-the-maxreceivedmessagesize-value"></a>Pour augmenter la valeur de maxReceivedMessageSize

1. Dans l’**Explorateur de solutions**, double-cliquez sur le fichier **app.config** du projet **PresentationTier**.

2. Accédez à l’attribut de taille **maxReceivedMessage** et changez la valeur en `6553600`.

## <a name="test-the-application"></a>Tester l’application
Exécutez l’application en appuyant sur **F5**. Les données à partir de la `Customers` et `Orders` tables est récupéré à partir du service de données et affiché sur le formulaire.

## <a name="next-steps"></a>Étapes suivantes
 Selon les exigences de votre application, vous pouvez exécuter différentes étapes après avoir enregistré les données associées dans l’application Windows. Par exemple, vous pouvez apporter les améliorations suivantes à cette application :

-   Ajouter une validation au dataset.

-   Ajouter des méthodes supplémentaires au service pour la mise à jour des données dans la base de données.

## <a name="see-also"></a>Voir aussi

- [Utilisation de datasets dans des applications multiniveaux](../data-tools/work-with-datasets-in-n-tier-applications.md)
- [Mise à jour hiérarchique](../data-tools/hierarchical-update.md)
- [Accès aux données dans Visual Studio](../data-tools/accessing-data-in-visual-studio.md)