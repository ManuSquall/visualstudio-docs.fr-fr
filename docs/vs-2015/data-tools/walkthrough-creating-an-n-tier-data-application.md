---
title: 'Procédure pas à pas : création d’une application de données multicouche | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- n-tier applications, creating
- n-tier applications, walkthroughs
ms.assetid: d15e4d31-2839-48d9-9e0e-2e73404d82a2
caps.latest.revision: 51
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 195a3a36b53e5f84f6052a15e01007bb5ed77fac
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75844198"
---
# <a name="walkthrough-creating-an-n-tier-data-application"></a>Procédure pas à pas : création d'une application de données multicouche
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les applications de données multicouches sont des applications qui accèdent aux données et qui sont réparties en plusieurs couches logiques, ou *niveaux*. La séparation des composants de l'application en couches distinctes favorise la possibilité de tenir à jour et de monter en charge l'application. Cela est possible grâce à une application plus facile des nouvelles technologies sur chaque couche sans avoir à reconcevoir toute la solution. L'architecture multicouche inclut une couche Présentation, une couche intermédiaire et une couche Données. La couche intermédiaire inclut généralement une couche d’accès aux données, une couche logique métier et des composants partagés tels que l’authentification et la validation. La couche Données inclut une base de données relationnelle. Les applications multicouches stockent généralement les informations sensibles dans la couche d'accès aux données de la couche intermédiaire, pour la tenir hors de portée des utilisateurs finaux qui accèdent à la couche Présentation. Pour plus d’informations, consultez [vue d’ensemble des applications de données multicouches](../data-tools/n-tier-data-applications-overview.md).

 Pour séparer plusieurs couches d'une application multicouche, il est possible de créer des projets distincts pour chaque couche que vous voulez inclure dans votre application. Les datasets typés contiennent une propriété `DataSet Project` qui détermine les projets dans lesquels le code du dataset et des `TableAdapter`s générés doit intervenir.

 Cette procédure pas à pas décrit comment séparer le code du dataset et `TableAdapter` en projets de bibliothèque de classes discrètes à l’aide du **Concepteur de DataSet**. Après avoir séparé le code du DataSet et du TableAdapter, vous allez créer un [Windows Communication Foundation services et WCF Data Services dans le service Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md) pour appeler la couche d’accès aux données. Enfin, vous créez une application Windows Forms en tant que couche Présentation. Cette couche accède aux données à partir du service de données.

 Dans cette procédure pas à pas, vous suivrez les étapes suivantes :

- créer une solution multicouche contenant plusieurs projets ;

- ajouter deux projets de bibliothèque de classes à la solution multicouche ;

- Créez un dataset typé à l’aide de l’**Assistant Configuration de source de données**.

- Séparez les [TableAdapters](https://msdn.microsoft.com/library/09416de9-134c-4dc7-8262-6c8d81e3f364) générés et le code du jeu de données en projets discrets.

- créer un service WCF (Windows Communication Foundation) pour appeler la couche d'accès aux données ;

- créer des fonctions dans le service pour récupérer les données de la couche d'accès aux données ;

- créer une application Windows Forms faisant office de couche Présentation ;

- créer des contrôles Windows Forms liés à la source de données ;

- écrire du code pour remplir les tables de données.

  ![lien vers la vidéo](../data-tools/media/playvideo.gif "PlayVideo") Pour obtenir une version vidéo de cette rubrique, consultez [vidéo : création d’une application de données multicouches](https://msdn2.microsoft.com/library/cc178916.aspx).

## <a name="prerequisites"></a>Configuration requise
 Pour exécuter cette procédure pas à pas, vous avez besoin des éléments suivants :

- avoir accès à l'exemple de base de données Northwind.

## <a name="creating-the-n-tier-solution-and-class-library-to-hold-the-dataset-dataentitytier"></a>Création de la solution multicouche et de la bibliothèque de classes pour contenir le dataset (DataEntityTier).
 La première étape de cette procédure pas à pas consiste à créer une solution et deux projets de bibliothèque de classes. La première bibliothèque de classes contient le dataset (la classe DataSet typée et les DataTables générées qui contiennent les données de l'application). Ce projet est utilisé comme couche d'entité de données de l'application et figure généralement dans la couche intermédiaire. Le Concepteur de DataSet permet de créer le jeu de données initial et de séparer automatiquement le code dans les deux bibliothèques de classes.

> [!NOTE]
> Nommez correctement le projet et la solution avant de cliquer sur **OK**. Il vous sera alors plus facile de terminer cette procédure pas à pas.

#### <a name="to-create-the-n-tier-solution-and-dataentitytier-class-library"></a>Pour créer la solution multicouche et la bibliothèque de classes DataEntityTier

1. Dans le menu **fichier** , créez un nouveau projet.

    > [!NOTE]
    > Le **Concepteur de DataSet** est pris en charge dans C# les [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] et les projets. Créez le projet dans l'un de ces langages.

2. Dans la boîte de dialogue **nouveau projet** , dans le volet **types de projets** , cliquez sur **fenêtres**.

3. Cliquez sur le modèle **bibliothèque de classes** .

4. Nommez le projet **DataEntityTier**.

5. Nommez la solution **NTierWalkthrough**.

6. Cliquez sur **OK**.

     Une solution NTierWalkthrough contenant le projet DataEntityTier est créée et ajoutée à l’**Explorateur de solutions**.

## <a name="creating-the-class-library-to-hold-the-tableadapters-dataaccesstier"></a>Création de la bibliothèque de classes pour contenir les TableAdapters (DataAccessTier)
 L'étape qui suit la création du projet DataEntityTier est la création d'un autre projet de bibliothèque de classes. Ce projet contiendra les `TableAdapter`générés et est appelé la *couche d’accès aux données* de l’application. La couche d'accès aux données contient les informations requises pour se connecter à la base de données et figure généralement dans la couche intermédiaire.

#### <a name="to-create-the-new-class-library-for-the-tableadapters"></a>Pour créer la bibliothèque de classes pour les TableAdapters

1. Dans le menu **fichier** , ajoutez un nouveau projet à la solution NTierWalkthrough.

2. Dans la boîte de dialogue **nouveau projet** , dans le volet **modèles** , cliquez sur **bibliothèque de classes**.

3. Nommez le projet **DataAccessTier** , puis cliquez sur **OK**.

     Le projet DataAccessTier est créé et ajouté à la solution NTierWalkthrough.

## <a name="creating-the-dataset"></a>Création du dataset
 L'étape qui suit consiste à créer le dataset typé. Les datasets typés sont créés avec la classe DataSet (y compris les classes DataTables) et les classes `TableAdapter` dans un projet unique. (Toutes les classes sont générées dans un seul fichier.) Lorsque vous séparez le DataSet et `TableAdapter`s dans des projets différents, il s’agit de la classe DataSet qui est déplacée vers l’autre projet, en laissant les classes `TableAdapter` dans le projet d’origine. Par conséquent, créez le dataset dans le projet qui contiendra les `TableAdapter`s (le projet DataAccessTier). Vous allez créer le DataSet à l’aide de l **'Assistant Configuration de source de données**.

> [!NOTE]
> Vous devez avoir accès à l'exemple de base de données Northwind pour créer la connexion.

#### <a name="to-create-the-dataset"></a>Pour créer le groupe de données

1. Cliquez sur DataAccessTier dans **Explorateur de solutions**.

2. Dans le menu **Données** , cliquez sur **Afficher les sources de données**.

3. Dans la fenêtre **sources de données** , cliquez sur Ajouter une **nouvelle source de données** pour démarrer l' **Assistant Configuration de source de données**.

4. Dans la page **choisir un type de source de données** , cliquez sur **base de données** , puis sur **suivant**.

5. Dans la page **Choisir votre connexion de données**, effectuez l’une des opérations suivantes :

     Si une connexion de données à l'exemple de base de données Northwind est disponible dans la liste déroulante, sélectionnez-la.

     \- ou -

     Cliquez sur **nouvelle connexion** pour ouvrir la boîte de dialogue **Ajouter une connexion** .

6. Si la base de données requiert un mot de passe, sélectionnez l'option permettant d'inclure les données sensibles, puis cliquez sur **Suivant**.

    > [!NOTE]
    > Si vous avez sélectionné un fichier de base de données local (au lieu de vous connecter à SQL Server), il vous sera peut-être demandé si vous souhaitez ajouter le fichier au projet. Cliquez sur **Oui** pour ajouter le fichier de base de données au projet.

7. Cliquez sur **suivant** dans la page **enregistrer la chaîne de connexion dans le fichier de configuration de l’application** .

8. Développez le nœud **Tables** dans la page **Choisir vos objets de base de données** .

9. Activez les cases à cocher correspondant aux tables **Customers** et **Orders** , puis cliquez sur **Finish**.

     NorthwindDataSet est ajouté au projet DataAccessTier et apparaît dans la fenêtre **Sources de données**.

## <a name="separating-the-tableadapters-from-the-dataset"></a>Séparation des TableAdapters et du dataset
 Une fois que vous avez créé le dataset, séparez la classe DataSet générée et les TableAdapters. Pour ce faire, définissez la propriété **Projet DataSet** sur le nom du projet dans lequel stocker la classe DataSet extraite.

#### <a name="to-separate-the-tableadapters-from-the-dataset"></a>Pour séparer les TableAdapters du dataset

1. Double-cliquez sur **NorthwindDataSet.xsd** dans l’**Explorateur de solutions** pour ouvrir le dataset dans le **Concepteur de DataSet**.

2. Cliquez sur une zone vide du concepteur.

3. Recherchez le nœud **Projet DataSet** dans la fenêtre **Propriétés**.

4. Dans la liste **projet de DataSet** , cliquez sur **DataEntityTier**.

5. Dans le menu **Générer** , cliquez sur **Générer la solution**.

   Le dataset et les TableAdapters sont divisés entre les deux projets de bibliothèque de classes. Le projet qui contenait initialement l'intégralité du dataset (DataAccessTier) ne contient désormais que les TableAdapters. Le projet désigné dans la propriété de **projet DataSet** (DataEntityTier) contient le DataSet typé : NorthwindDataSet. DataSet. Designer. vb (ou NorthwindDataSet.DataSet.Designer.cs).

> [!NOTE]
> Quand vous séparez les datasets et les TableAdapters (en définissant la propriété **Projet DataSet**), les classes DataSet partielles existantes dans le projet ne sont pas déplacées automatiquement. Les classes DataSet partielles existantes doivent être manuellement déplacées dans le projet DataSet.

## <a name="creating-a-new-service-application"></a>Création d'une application de service
 Cette procédure pas à pas décrivant comment accéder à la couche d'accès aux données à l'aide d'un service WCF, créez une application de service WCF.

#### <a name="to-create-a-new-wcf-service-application"></a>Pour créer une application de service WCF

1. Dans le menu **fichier** , ajoutez un nouveau projet à la solution NTierWalkthrough.

2. Dans la boîte de dialogue **nouveau projet** , dans le volet **types de projets** , cliquez sur **WCF**. Dans le volet **modèles** , cliquez sur **bibliothèque de services WCF**.

3. Nommez le projet **DataService** , puis cliquez sur **OK**.

     Le projet DataService est créé et ajouté à la solution NTierWalkthrough.

## <a name="creating-methods-in-the-data-access-tier-to-return-the-customers-and-orders-data"></a>Création de méthodes dans la couche d'accès aux données pour retourner les données Customers et Orders
 Le service de données doit appeler deux méthodes de la couche d'accès aux données : GetCustomers et GetOrders. Ces méthodes retournent les tables Customers et Orders de Northwind. Créez les méthodes GetCustomers et GetOrders dans le projet DataAccessTier.

#### <a name="to-create-a-method-in-the-data-access-tier-that-returns-the-customers-table"></a>Pour créer une méthode dans la couche d'accès aux données qui retourne la table Customers

1. Dans **Explorateur de solutions**, double-cliquez sur NorthwindDataSet. xsd pour ouvrir le jeu de données dans le concepteur de DataSet.

2. Cliquez avec le bouton droit sur CustomersTableAdapter, puis cliquez sur **Ajouter une requête** pour modifier le TableAdapter.

3. Dans la page **Choisir un type de commande**, conservez la valeur par défaut **Utiliser des instructions SQL**, puis cliquez sur **Suivant**.

4. Dans la page **Choisir un type de requête**, conservez la valeur par défaut **SELECT qui retourne des lignes**, puis cliquez sur **Suivant**.

5. Dans la page **Spécifier une instruction SQL SELECT**, conservez la requête par défaut et cliquez sur **Suivant**.

6. Dans la page **Choisir les méthodes à générer**, tapez **GetCustomers** dans le champ **Nom de la méthode** de la section **Retourner un DataTable**.

7. Cliquez sur **Finish**.

#### <a name="to-create-a-method-in-the-data-access-tier-that-returns-the-orders-table"></a>Pour créer une méthode dans la couche d'accès aux données qui retourne la table Orders

1. Cliquez avec le bouton droit sur OrdersTableAdapter, puis cliquez sur **Ajouter une requête**.

2. Dans la page **Choisir un type de commande**, conservez la valeur par défaut **Utiliser des instructions SQL**, puis cliquez sur **Suivant**.

3. Dans la page **Choisir un type de requête**, conservez la valeur par défaut **SELECT qui retourne des lignes**, puis cliquez sur **Suivant**.

4. Dans la page **Spécifier une instruction SQL SELECT**, conservez la requête par défaut et cliquez sur **Suivant**.

5. Dans la page **Choisir les méthodes à générer**, tapez **GetOrders** dans le champ **Nom de la méthode** de la section **Retourner un DataTable**.

6. Cliquez sur **Finish**.

7. Dans le menu **Générer** , cliquez sur **Générer la solution**.

## <a name="adding-a-reference-to-the-data-entity-and-data-access-tiers-to-the-data-service"></a>Ajout d'une référence vers les couches d'entité des données et d'accès aux données au service de données
 Le service de données nécessitant des informations du dataset et des TableAdapters, ajoutez des références vers les projets DataEntityTier et DataAccessTier.

#### <a name="to-add-references-to-the-data-service"></a>Pour ajouter des références au service de données

1. Cliquez avec le bouton droit sur DataService dans **Explorateur de solutions** , puis cliquez sur **Ajouter une référence**.

2. Cliquez sur l’onglet **Projets** de la boîte de dialogue **Ajouter une référence**.

3. Sélectionnez à la fois les projets **DataAccessTier** et **DataEntityTier**.

4. Cliquez sur **OK**.

## <a name="adding-functions-to-the-service-to-call-the-getcustomers-and-getorders-methods-in-the-data-access-tier"></a>Ajout de fonctions au service pour appeler les méthodes GetCustomers et GetOrders dans la couche d'accès aux données
 Maintenant que la couche d'accès aux données contient les méthodes permettant de retourner les données, créez des méthodes dans le service de données pour appeler les méthodes dans la couche d'accès aux données.

> [!NOTE]
> Pour les projets C#, vous devez ajouter une référence à l'assembly `System.Data.DataSetExtensions` pour la compilation du code suivant.

#### <a name="to-create-the-getcustomers-and-getorders-functions-in-the-data-service"></a>Pour créer les fonctions GetCustomers et GetOrders dans le service de données

1. Dans le projet **DataService** , double-cliquez sur IService1. vb ou IService1.cs.

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

3. Dans le projet DataService, double-cliquez sur Service1.vb (ou Service1.cs).

4. Ajoutez le code suivant à la classe Service1 :

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

## <a name="creating-a-presentation-tier-to-display-data-from-the-data-service"></a>Création d'une couche Présentation pour afficher les données du service de données
 Maintenant que la solution contient le service de données avec les méthodes permettant d'appeler la couche d'accès aux données, créez un autre projet pour appeler le service de données et présenter les données aux utilisateurs. Pour cette procédure pas à pas, créez une application Windows Forms. Il s’agit de la couche Présentation de l’application multicouche.

#### <a name="to-create-the-presentation-tier-project"></a>Pour créer le projet de couche Présentation

1. Dans le menu **fichier** , ajoutez un nouveau projet à la solution NTierWalkthrough.

2. Dans la boîte de dialogue **nouveau projet** , dans le volet **types de projets** , cliquez sur **fenêtres**. Dans le volet **Modèles** , cliquez sur **Application Windows Forms**.

3. Nommez le projet **PresentationTier** et cliquez sur **OK**.

4. Le projet PresentationTier est créé et ajouté à la solution NTierWalkthrough.

## <a name="setting-the-presentationtier-project-as-the-startup-project"></a>Définition du projet PresentationTier comme projet de démarrage
 La couche Présentation étant l'application réelle utilisée pour présenter les données et interagir avec ces dernières, vous devez définir le projet PresentationTier comme projet de démarrage.

#### <a name="to-set-the-new-presentation-tier-project-as-the-startup-project"></a>Pour définir le nouveau projet de couche Présentation comme projet de démarrage

- Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur **PresentationTier**, puis cliquez sur **Définir comme projet de démarrage**.

## <a name="adding-references-to-the-presentation-tier"></a>Ajout de références à la couche Présentation
 L'application cliente PresentationTier requiert une référence de service au service de données pour accéder aux méthodes du service. Par ailleurs, une référence au dataset est requise pour activer le partage de type par le service WCF. Tant que vous n'activez pas le partage de type via le service de données, le code ajouté à la classe DataSet partielle n'est pas disponible dans la couche Présentation. Comme généralement vous ajoutez du code tel que la validation aux événements de modification de ligne et de colonne d'une table de données, vous voudrez probablement accéder à ce code depuis le client.

#### <a name="to-add-a-reference-to-the-presentation-tier"></a>Pour ajouter une référence à la couche Présentation

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur PresentationTier, puis cliquez sur **Ajouter une référence**.

2. Dans la boîte de dialogue **Ajouter une référence** , cliquez sur l’onglet **projets** .

3. Sélectionnez **DataEntityTier** , puis cliquez sur **OK**.

#### <a name="to-add-a-service-reference-to-the-presentation-tier"></a>Pour ajouter une référence de service à la couche Présentation

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur PresentationTier, puis cliquez sur **Ajouter une référence de service**.

2. Dans la boîte de dialogue **Ajouter une référence de service**, cliquez sur **Découvrir**.

3. Sélectionnez **Service1** , puis cliquez sur **OK**.

    > [!NOTE]
    > Si vous disposez de plusieurs services sur l'ordinateur actuel, sélectionnez le service que vous avez créé précédemment dans cette procédure pas à pas (le service contenant les méthodes GetCustomers et GetOrders).

## <a name="adding-datagridviews-to-the-form-to-display-the-data-returned-by-the-data-service"></a>Ajout de DataGridViews au formulaire pour afficher les données retournées par le service de données
 Une fois que vous avez ajouté la référence de service au service de données, la fenêtre **Sources de données** est automatiquement remplie avec les données retournées par le service.

#### <a name="to-add-two-data-bound-datagridviews-to-the-form"></a>Pour ajouter au formulaire deux DataGridViews liés aux données

1. Dans **Explorateur de solutions**, sélectionnez le projet PresentationTier.

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

## <a name="increasing-the-maximum-message-size-allowed-by-the-service"></a>Augmentation de la taille maximale des messages autorisée par le service
 Le service retournant des données des tables Customers et Orders, la valeur par défaut de maxReceivedMessageSize n'est pas suffisante pour contenir les données et doit être augmentée. Pour cette procédure pas à pas, vous allez changer la valeur en 6553600. Vous allez modifier la valeur sur le client, ce qui mettra automatiquement à jour la référence de service.

> [!NOTE]
> La taille inférieure par défaut est destinée à limiter l'exposition aux attaques par déni de service. Pour plus d'informations, consultez <xref:System.ServiceModel.WSHttpBindingBase.MaxReceivedMessageSize%2A>.

#### <a name="to-increase-the-maxreceivedmessagesize-value"></a>Pour augmenter la valeur de maxReceivedMessageSize

1. Dans **Explorateur de solutions**, double-cliquez sur le fichier app. config dans le projet PresentationTier.

2. Accédez à l’attribut de taille **maxReceivedMessage** et changez la valeur en `6553600`.

## <a name="testing-the-application"></a>Test de l'application
 Exécutez l'application. Les données sont récupérées à partir du service de données et affichées dans le formulaire.

#### <a name="to-test-the-application"></a>Pour tester l'application

1. Appuyez sur la touche F5.

2. Les données des tables Customers et Orders sont récupérées à partir du service de données et affichées dans le formulaire.

## <a name="next-steps"></a>Étapes suivantes
 Selon les spécifications de votre application, vous pouvez exécuter différentes étapes après avoir enregistré les données associées dans l'application Windows. Par exemple, vous pouvez apporter les améliorations suivantes à cette application :

- Ajouter une validation au dataset. Pour plus d’informations, consultez [procédure pas à pas : ajout d’une validation à une application de données multicouches](https://msdn.microsoft.com/library/b35d072c-31f0-49ba-a225-69177592c265).

- Ajouter des méthodes supplémentaires au service pour la mise à jour des données dans la base de données.

## <a name="see-also"></a>Voir aussi
 [Utiliser des jeux de données dans des applications multicouches](../data-tools/work-with-datasets-in-n-tier-applications.md) [mise à jour hiérarchique](../data-tools/hierarchical-update.md) [accès aux données dans Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
