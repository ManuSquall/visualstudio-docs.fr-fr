---
title: 'Procédure pas à pas : création d’une application de données multicouches'
description: Dans cette procédure pas à pas, créez une application de données multicouches. Les applications de données multicouches sont des applications qui accèdent aux données et sont divisées en plusieurs couches logiques, ou niveaux.
ms.custom: SEO-VS-2020
ms.date: 09/08/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- n-tier applications, creating
- n-tier applications, walkthroughs
ms.assetid: d15e4d31-2839-48d9-9e0e-2e73404d82a2
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: ed395c60ec16eeff6a5aac88a99698193e8bacbd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99866149"
---
# <a name="walkthrough-create-an-n-tier-data-application"></a>Procédure pas à pas : création d’une application de données multicouches
Les applications de données *multiniveaux* sont des applications qui accèdent aux données et sont divisées en plusieurs couches logiques, ou *niveaux*. La séparation des composants de l'application en couches distinctes favorise la possibilité de tenir à jour et de monter en charge l'application. Cela est possible grâce à une application plus facile des nouvelles technologies sur chaque couche sans avoir à reconcevoir toute la solution. L'architecture multicouche inclut une couche Présentation, une couche intermédiaire et une couche Données. La couche intermédiaire inclut généralement une couche d’accès aux données, une couche logique métier et des composants partagés tels que l’authentification et la validation. La couche Données inclut une base de données relationnelle. Les applications multicouches stockent généralement les informations sensibles dans la couche d'accès aux données de la couche intermédiaire, pour la tenir hors de portée des utilisateurs finaux qui accèdent à la couche Présentation. Pour plus d’informations, consultez [vue d’ensemble des applications de données multicouches](../data-tools/n-tier-data-applications-overview.md).

Pour séparer plusieurs couches d'une application multicouche, il est possible de créer des projets distincts pour chaque couche que vous voulez inclure dans votre application. Les datasets typés contiennent une propriété `DataSet Project` qui détermine les projets dans lesquels le code du dataset et des `TableAdapter`s générés doit intervenir.

Cette procédure pas à pas décrit comment séparer le code du dataset et `TableAdapter` en projets de bibliothèque de classes discrètes à l’aide du **Concepteur de DataSet**. Une fois que vous avez séparé le code du DataSet et du TableAdapter, vous créez un [Windows Communication Foundation services et services de données WCF dans le service Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md) pour appeler la couche d’accès aux données. Enfin, vous créez un Windows Forms application en tant que couche présentation. Cette couche accède aux données à partir du service de données.

Au cours de cette procédure pas à pas, vous effectuez les étapes suivantes :

- Créez une nouvelle solution multicouche qui contient plusieurs projets.

- ajouter deux projets de bibliothèque de classes à la solution multicouche ;

- Créez un dataset typé à l’aide de l’**Assistant Configuration de source de données**.

- Séparez les [TableAdapters](create-and-configure-tableadapters.md) générés et le code du jeu de données en projets discrets.

- créer un service WCF (Windows Communication Foundation) pour appeler la couche d'accès aux données ;

- créer des fonctions dans le service pour récupérer les données de la couche d'accès aux données ;

- créer une application Windows Forms faisant office de couche Présentation ;

- créer des contrôles Windows Forms liés à la source de données ;

- écrire du code pour remplir les tables de données.

![lien vers la vidéo](../data-tools/media/playvideo.gif) pour obtenir une version vidéo de cette rubrique, consultez [Video How to : Création d’une application de données multiniveaux](/previous-versions/visualstudio/visual-studio-2008/cc178916(v=vs.90)).

## <a name="prerequisites"></a>Prérequis
Cette procédure pas à pas utilise SQL Server Express base de données locale et l’exemple de base de données Northwind.

1. Si vous n’avez pas SQL Server Express base de données locale, installez-la à partir de la [page de téléchargement SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express)ou via le **Visual Studio installer**. Dans le **Visual Studio installer**, vous pouvez installer SQL Server Express base de données locale dans le cadre de la charge de travail **développement .net Desktop** , ou en tant que composant individuel.

2. Installez l’exemple de base de données Northwind en procédant comme suit :

    1. Dans Visual Studio, ouvrez la fenêtre de **Explorateur d’objets SQL Server** . (**Explorateur d’objets SQL Server** est installé dans le cadre de la charge de travail **stockage et traitement des données** dans le Visual Studio installer.) Développez le nœud **SQL Server** . Cliquez avec le bouton droit sur votre instance de base de données locale, puis sélectionnez **nouvelle requête**.

       Une fenêtre de l’éditeur de requête s’ouvre.

    2. Copiez le [script Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) dans le presse-papiers. Ce script T-SQL crée la base de données Northwind à partir de zéro et la remplit avec des données.

    3. Collez le script T-SQL dans l’éditeur de requête, puis choisissez le bouton **exécuter** .

       Après un bref laps de temps, l’exécution de la requête se termine et la base de données Northwind est créée.

## <a name="create-the-n-tier-solution-and-class-library-to-hold-the-dataset-dataentitytier"></a>Créer la solution multicouche et la bibliothèque de classes pour contenir le jeu de données (DataEntityTier)
La première étape de cette procédure pas à pas consiste à créer une solution et deux projets de bibliothèque de classes. La première bibliothèque de classes contient le DataSet (la classe typée générée `DataSet` et les DataTables qui contiennent les données de l’application). Ce projet est utilisé comme couche d'entité de données de l'application et figure généralement dans la couche intermédiaire. Le DataSet crée le jeu de données initial et sépare automatiquement le code en deux bibliothèques de classes.

> [!NOTE]
> Nommez correctement le projet et la solution avant de cliquer sur **OK**. Il vous sera alors plus facile de terminer cette procédure pas à pas.

### <a name="to-create-the-n-tier-solution-and-dataentitytier-class-library"></a>Pour créer la solution multicouche et la bibliothèque de classes DataEntityTier

1. Dans Visual Studio, dans le menu **Fichier**, sélectionnez **Nouveau** > **Projet**.

2. Développez **Visual C#** ou **Visual Basic** dans le volet gauche, puis sélectionnez **Bureau Windows**.

3. Dans le volet central, sélectionnez le type de projet **bibliothèque de classes** .

4. Nommez le projet **DataEntityTier**.

5. Nommez la solution **NTierWalkthrough**, puis choisissez **OK**.

     Une solution NTierWalkthrough contenant le projet DataEntityTier est créée et ajoutée à l’**Explorateur de solutions**.

## <a name="create-the-class-library-to-hold-the-tableadapters-dataaccesstier"></a>Créer la bibliothèque de classes pour contenir les TableAdapters (DataAccessTier)
L'étape qui suit la création du projet DataEntityTier est la création d'un autre projet de bibliothèque de classes. Ce projet contient les TableAdapters générés et est appelé la *couche d’accès aux données* de l’application. La couche d'accès aux données contient les informations requises pour se connecter à la base de données et figure généralement dans la couche intermédiaire.

### <a name="to-create-a-separate-class-library-for-the-tableadapters"></a>Pour créer une bibliothèque de classes distincte pour les TableAdapters

1. Cliquez avec le bouton droit sur la solution dans l’**Explorateur de solutions**, puis choisissez **Ajouter** > **Nouveau projet**.

2. Dans la boîte de dialogue **nouveau projet** , dans le volet central, sélectionnez **bibliothèque de classes**.

3. Nommez le projet **DataAccessTier** , puis choisissez **OK**.

     Le projet DataAccessTier est créé et ajouté à la solution NTierWalkthrough.

## <a name="create-the-dataset"></a>Créer le DataSet
L'étape qui suit consiste à créer le dataset typé. Les datasets typés sont créés avec la classe DataSet (y compris les `DataTables` classes) et les `TableAdapter` classes dans un projet unique. (Toutes les classes sont générées dans un seul fichier.) Lorsque vous séparez le DataSet et les TableAdapters dans des projets différents, il s’agit de la classe DataSet qui est déplacée vers l’autre projet, en laissant les `TableAdapter` classes dans le projet d’origine. Par conséquent, créez le DataSet dans le projet qui contiendra finalement les TableAdapters (le projet DataAccessTier). Vous créez le DataSet à l’aide de l **'Assistant Configuration de source de données**.

> [!NOTE]
> Vous devez avoir accès à l'exemple de base de données Northwind pour créer la connexion. Pour plus d’informations sur la configuration de l’exemple de base de données Northwind, consultez [Comment : installer des exemples de bases de données](../data-tools/installing-database-systems-tools-and-samples.md).

### <a name="to-create-the-dataset"></a>Pour créer le dataset

1. Sélectionnez le **DataAccessTier** dans **Explorateur de solutions**.

2. Dans le menu **données** , sélectionnez **afficher les sources de données**.

   La fenêtre **Sources de données** s’ouvre.

3. Dans la fenêtre **Sources de données**, sélectionnez **Ajouter une nouvelle source de données** pour démarrer l’**Assistant Configuration de source de données**.

4. Dans la page **choisir un type de source de données** , sélectionnez **base de** données, puis sélectionnez **suivant**.

5. Dans la page **Choisir votre connexion de données**, effectuez l’une des opérations suivantes :

     Si une connexion de données à l’exemple de base de données Northwind est disponible dans la liste déroulante, sélectionnez-la.

     -ou-

     Sélectionnez **nouvelle connexion** pour ouvrir la boîte de dialogue **Ajouter une connexion** .

6. Si la base de données requiert un mot de passe, sélectionnez l’option permettant d’inclure des données sensibles, puis choisissez **suivant**.

    > [!NOTE]
    > Si vous avez sélectionné un fichier de base de données local (au lieu de vous connecter à SQL Server), il vous sera peut-être demandé si vous souhaitez ajouter le fichier au projet. Choisissez **Oui** pour ajouter le fichier de base de données au projet.

7. Sélectionnez **suivant** dans la page **enregistrer la chaîne de connexion dans le fichier de configuration de l’application** .

8. Développez le nœud **Tables** dans la page **Choisir vos objets de base de données** .

9. Activez les cases à cocher pour les tables **Customers** et **Orders** , puis choisissez **Finish**.

     NorthwindDataSet est ajouté au projet DataAccessTier et apparaît dans la fenêtre **Sources de données**.

## <a name="separate-the-tableadapters-from-the-dataset"></a>Séparer les TableAdapters du DataSet
Une fois que vous avez créé le dataset, séparez la classe DataSet générée et les TableAdapters. Pour ce faire, définissez la propriété **Projet DataSet** sur le nom du projet dans lequel stocker la classe DataSet extraite.

### <a name="to-separate-the-tableadapters-from-the-dataset"></a>Pour séparer les TableAdapters du dataset

1. Double-cliquez sur **NorthwindDataSet.xsd** dans l’**Explorateur de solutions** pour ouvrir le dataset dans le **Concepteur de DataSet**.

2. Sélectionnez une zone vide dans le concepteur.

3. Recherchez le nœud **Projet DataSet** dans la fenêtre **Propriétés**.

4. Dans la liste **projet de DataSet** , sélectionnez **DataEntityTier**.

5. Dans le menu **Générer**, sélectionnez **Générer la solution**.

   Le dataset et les TableAdapters sont divisés entre les deux projets de bibliothèque de classes. Le projet qui contenait initialement le DataSet entier ( `DataAccessTier` ) contient désormais uniquement les TableAdapters. Le projet désigné dans la propriété de **projet DataSet** ( `DataEntityTier` ) contient le DataSet typé : *NorthwindDataSet. DataSet. Designer. vb* (ou *NorthwindDataSet.DataSet.Designer.cs*).

> [!NOTE]
> Quand vous séparez les datasets et les TableAdapters (en définissant la propriété **Projet DataSet**), les classes DataSet partielles existantes dans le projet ne sont pas déplacées automatiquement. Les classes DataSet partielles existantes doivent être manuellement déplacées dans le projet DataSet.

## <a name="create-a-new-service-application"></a>Créer une application de service
Cette procédure pas à pas montre comment accéder à la couche d’accès aux données à l’aide d’un service WCF. nous allons donc créer une application de service WCF.

### <a name="to-create-a-new-wcf-service-application"></a>Pour créer une application de service WCF

1. Cliquez avec le bouton droit sur la solution dans l’**Explorateur de solutions**, puis choisissez **Ajouter** > **Nouveau projet**.

2. Dans la boîte de dialogue **nouveau projet** , dans le volet gauche, sélectionnez **WCF**. Dans le volet central, sélectionnez **bibliothèque de services WCF**.

3. Nommez le projet **DataService** et sélectionnez **OK**.

     Le projet DataService est créé et ajouté à la solution NTierWalkthrough.

## <a name="create-methods-in-the-data-access-tier-to-return-the-customers-and-orders-data"></a>Créer des méthodes dans la couche d’accès aux données pour retourner les données Customers et Orders
Le service de données doit appeler deux méthodes dans la couche d’accès aux données : `GetCustomers` et `GetOrders` . Ces méthodes retournent `Customers` les `Orders` tables Northwind et. Créez les `GetCustomers` `GetOrders` méthodes et dans le `DataAccessTier` projet.

### <a name="to-create-a-method-in-the-data-access-tier-that-returns-the-customers-table"></a>Pour créer une méthode dans la couche d'accès aux données qui retourne la table Customers

1. Dans **Explorateur de solutions**, double-cliquez sur **NorthwindDataSet. xsd** pour ouvrir le jeu de données.

2. Cliquez avec le bouton droit sur **CustomersTableAdapter** , puis cliquez sur **Ajouter une requête**.

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

7. Dans le menu **Générer**, cliquez sur **Générer la solution**.

## <a name="add-a-reference-to-the-data-entity-and-data-access-tiers-to-the-data-service"></a>Ajouter une référence à l’entité de données et aux niveaux d’accès aux données dans le service de données
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

3. Dans le projet DataService, double-cliquez sur **Service1. vb** (ou **Service1.cs**).

4. Ajoutez le code suivant à la classe **Service1** :

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

5. Dans le menu **Générer**, cliquez sur **Générer la solution**.

## <a name="create-a-presentation-tier-to-display-data-from-the-data-service"></a>Créer une couche de présentation pour afficher des données à partir du service de données
Maintenant que la solution contient le service de données qui a des méthodes, qui appellent la couche d’accès aux données, créez un autre projet qui appelle le service de données et présentez les données aux utilisateurs. Pour cette procédure pas à pas, créez une application Windows Forms. Il s’agit de la couche Présentation de l’application multicouche.

### <a name="to-create-the-presentation-tier-project"></a>Pour créer le projet de couche Présentation

1. Cliquez avec le bouton droit sur la solution dans l’**Explorateur de solutions**, puis choisissez **Ajouter** > **Nouveau projet**.

2. Dans la boîte de dialogue **nouveau projet** , dans le volet gauche, sélectionnez **Bureau Windows**. Dans le volet central, sélectionnez **Windows Forms application**.

3. Nommez le projet **PresentationTier** et cliquez sur **OK**.

    Le projet PresentationTier est créé et ajouté à la solution NTierWalkthrough.

## <a name="set-the-presentationtier-project-as-the-startup-project"></a>Définir le projet PresentationTier comme projet de démarrage
Nous allons définir le projet **PresentationTier** comme projet de démarrage de la solution, car il s’agit de l’application cliente réelle qui présente et interagit avec les données.

### <a name="to-set-the-new-presentation-tier-project-as-the-startup-project"></a>Pour définir le nouveau projet de niveau Présentation comme projet de démarrage

- Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur **PresentationTier**, puis cliquez sur **Définir comme projet de démarrage**.

## <a name="add-references-to-the-presentation-tier"></a>Ajouter des références à la couche présentation
L’application cliente PresentationTier nécessite une référence de service au service de données pour accéder aux méthodes du service. Par ailleurs, une référence au dataset est requise pour activer le partage de type par le service WCF. Tant que vous n’activez pas le partage de type via le service de données, le code ajouté à la classe DataSet partielle n’est pas disponible pour la couche présentation. Étant donné que vous ajoutez généralement du code, tel que le code de validation aux événements de modification de ligne et de colonne d’une table de données, il est probable que vous souhaitiez accéder à ce code à partir du client.

### <a name="to-add-a-reference-to-the-presentation-tier"></a>Pour ajouter une référence à la couche Présentation

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur **PresentationTier** , puis sélectionnez **Ajouter une référence**.

2. Dans la boîte de dialogue **Ajouter une référence** , sélectionnez l’onglet **projets** .

3. Sélectionnez **DataEntityTier** et choisissez **OK**.

### <a name="to-add-a-service-reference-to-the-presentation-tier"></a>Pour ajouter une référence de service à la couche Présentation

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur **PresentationTier** et sélectionnez **Ajouter une référence de service**.

2. Dans la boîte de dialogue **Ajouter une référence de service** , sélectionnez **découvrir**.

3. Sélectionnez **Service1** et choisissez **OK**.

    > [!NOTE]
    > Si vous avez plusieurs services sur l’ordinateur actuel, sélectionnez le service que vous avez créé précédemment dans cette procédure pas à pas (le service qui contient les `GetCustomers` `GetOrders` méthodes et).

## <a name="add-datagridviews-to-the-form-to-display-the-data-returned-by-the-data-service"></a>Ajouter des DataGridViews au formulaire pour afficher les données retournées par le service de données
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

## <a name="increase-the-maximum-message-size-allowed-by-the-service"></a>Augmentez la taille maximale autorisée pour le message par le service
La valeur par défaut de `maxReceivedMessageSize` n’est pas assez grande pour contenir les données extraites des `Customers` `Orders` tables et. Dans les étapes suivantes, vous allez augmenter la valeur à 6553600. Vous modifiez la valeur sur le client, ce qui met automatiquement à jour la référence de service.

> [!NOTE]
> La taille inférieure par défaut est destinée à limiter l'exposition aux attaques par déni de service. Pour plus d’informations, consultez <xref:System.ServiceModel.WSHttpBindingBase.MaxReceivedMessageSize%2A>.

### <a name="to-increase-the-maxreceivedmessagesize-value"></a>Pour augmenter la valeur de maxReceivedMessageSize

1. Dans l’**Explorateur de solutions**, double-cliquez sur le fichier **app.config** du projet **PresentationTier**.

2. Accédez à l’attribut de taille **maxReceivedMessage** et changez la valeur en `6553600`.

## <a name="test-the-application"></a>Tester l’application
Exécutez l’application en appuyant sur **F5**. Les données des `Customers` tables et `Orders` sont récupérées à partir du service de données et affichées sur le formulaire.

## <a name="next-steps"></a>Étapes suivantes
Selon les spécifications de votre application, vous pouvez exécuter différentes étapes après avoir enregistré les données associées dans l'application Windows. Par exemple, vous pouvez apporter les améliorations suivantes à cette application :

- Ajouter une validation au dataset.

- Ajouter des méthodes supplémentaires au service pour la mise à jour des données dans la base de données.

## <a name="see-also"></a>Voir aussi

- [Utilisation de datasets dans des applications multiniveaux](../data-tools/work-with-datasets-in-n-tier-applications.md)
- [Mise à jour hiérarchique](../data-tools/hierarchical-update.md)
- [Accès aux données dans Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
