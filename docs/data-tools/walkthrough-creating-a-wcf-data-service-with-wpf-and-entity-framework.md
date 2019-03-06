---
title: 'Procédure pas à pas : Création d’un service de données WCF avec WPF et Entity Framework'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data services in Visual Studio
- WCF Data Services, Visual Studio
- ADO.NET Data Services, Visual Studio
- WCF data services in Visual Studio
ms.assetid: da66ad1b-a25d-485c-af13-2d18f0422e3d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: d9e41de9fc395b673f38fa1f7b343594bf905a8d
ms.sourcegitcommit: 87d7123c09812534b7b08743de4d11d6433eaa13
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57223167"
---
# <a name="walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework"></a>Procédure pas à pas : Création d’un service de données WCF avec WPF et Entity Framework
Cette procédure pas à pas montre comment créer un [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] simple qui est hébergé dans une application web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], puis comment y accéder à partir d’une application Windows Forms.

Dans cette procédure pas à pas vous :

- Créez une application web pour héberger un [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)].

- Créer un [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] qui représente le `Customers` table dans la base de données Northwind.

- Créer un [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)].

- Créer une application cliente et ajouter une référence au [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)].

- Activer la liaison de données vers un service et générer l’interface utilisateur.

- Ajouter éventuellement des fonctions de filtrage à l'application.

## <a name="prerequisites"></a>Prérequis
Cette procédure pas à pas utilise SQL Server Express LocalDB et la base de données Northwind.

1. Si vous n’avez pas SQL Server Express LocalDB, installez-le à partir de la [page de téléchargement de SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), ou via le **le programme d’installation de Visual Studio**. Dans le **le programme d’installation de Visual Studio**, vous pouvez installer SQL Server Express LocalDB dans le cadre de la **stockage de données et de traitement** charge de travail, ou comme un composant individuel.

2. Installer la base de données Northwind en suivant ces étapes :

    1. Dans Visual Studio, ouvrez le **Explorateur d’objets SQL Server** fenêtre. (**Explorateur d’objets SQL Server** est installé dans le cadre de la **stockage de données et de traitement** charge de travail dans Visual Studio Installer.) Développez le **SQL Server** nœud. Avec le bouton droit sur votre instance de base de données locale et sélectionnez **nouvelle requête**.

       Une fenêtre d’éditeur de requête s’ouvre.

    2. Copie le [script Transact-SQL de Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) dans votre Presse-papiers. Ce script T-SQL crée la base de données Northwind à partir de zéro et la remplit avec des données.

    3. Collez le script T-SQL dans l’éditeur de requête, puis choisissez le **Execute** bouton.

       Après une courte période, la requête est terminée en cours d’exécution et la base de données Northwind est créé.

## <a name="creating-the-service"></a>Création du service
Pour créer un [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)], vous devez ajouter un projet web, créer un [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)], puis créer le service à partir du modèle.

Dans la première étape, vous ajoutez un projet web pour héberger le service.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-create-the-web-project"></a>Pour créer le projet web

1. Dans la barre de menus, choisissez **Fichier** > **Nouveau** > **Projet**.

2. Dans la boîte de dialogue **Nouveau projet**, développez les nœuds **Visual Basic** ou **Visual C#** et **Web**, puis choisissez le modèle **Application web ASP.NET**.

3. Dans la zone de texte **Nom**, entrez **NorthwindWeb**, puis choisissez le bouton **OK**.

4. Dans la boîte de dialogue **Nouveau projet ASP.NET**, dans la liste **Sélectionner un modèle**, choisissez **Vide**, puis le bouton **OK**.

Dans l’étape suivante, vous allez créer un [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] qui représente le `Customers` table dans la base de données Northwind.

### <a name="to-create-the-entity-data-model"></a>Pour créer le modèle EDM (Entity Data Model)

1. Dans la barre de menus, choisissez **Projet** > **Ajouter un nouvel élément**.

2. Dans la boîte de dialogue **Ajouter un nouvel élément**, choisissez le nœud **Données**, puis l’élément **ADO.NET Entity Data Model**.

3. Dans le **nom** texte, entrez `NorthwindModel`, puis choisissez le **ajouter** bouton.

     L'Assistant Entity Data Model s'affiche.

4. Dans l’Assistant EDM, dans la page **Choisir le contenu du modèle**, choisissez l’élément **Concepteur EF à partir d’une base de données**, puis cliquez sur le bouton **Suivant**.

5. Sur la page **Choisir votre connexion de données** , effectuez l'une des opérations suivantes :

    -   Si une connexion de données à l'exemple de base de données Northwind est disponible dans la liste déroulante, choisissez-la.

         - ou -

    -   Choisissez le bouton **Nouvelle connexion** pour configurer une nouvelle connexion de données. Pour plus d’informations, consultez [ajouter de nouvelles connexions](../data-tools/add-new-connections.md).

6. Si la base de données nécessite un mot de passe, choisissez la case d’option **Oui, inclure les données sensibles dans la chaîne de connexion**, puis cliquez sur le bouton **Suivant**.

    > [!NOTE]
    > Si une boîte de dialogue s’affiche, choisissez **Oui** pour enregistrer le fichier dans votre projet.

7. Dans la page **Choisir votre version**, choisissez la case d’option **Entity Framework 5.0**, puis le bouton **Suivant**.

    > [!NOTE]
    > Pour pouvoir utiliser la dernière version d’Entity Framework 6 avec les services WCF, vous devez installer le package NuGet du fournisseur Entity Framework de services de données WCF. Consultez [à l’aide de WCF Data Services 5.6.0 avec Entity Framework 6 +](https://devblogs.microsoft.com/odata/using-wcf-data-services-5-6-0-with-entity-framework-6/).

8. Dans la page **Choisir vos objets de base de données**, développez le nœud **Tables**, cochez la case **Customers**, puis choisissez le bouton **Terminer**.

     Le diagramme de modèle d’entité s’affiche et un *NorthwindModel.edmx* fichier est ajouté à votre projet.

Dans l’étape suivante, vous allez créer et tester le service de données.

### <a name="to-create-the-data-service"></a>Pour créer le service de données

1. Dans la barre de menus, choisissez **Projet** > **Ajouter un nouvel élément**.

2. Dans la boîte de dialogue **Ajouter un nouvel élément**, choisissez le nœud **Web**, puis l’élément **WCF Data Service 5.6**.

3. Dans le **nom** texte, entrez `NorthwindCustomers`, puis choisissez le **ajouter** bouton.

     Le fichier **NorthwindCustomers.svc** s’affiche dans l’**Éditeur de code**.

4. Dans l’**Éditeur de code**, localisez le premier commentaire `TODO:` et remplacez le code par celui-ci :

     [!code-vb[WCFDataServiceWalkthrough#1](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework_1.vb)]
     [!code-csharp[WCFDataServiceWalkthrough#1](../data-tools/codesnippet/CSharp/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework_1.cs)]

5. Remplacez les commentaires dans le gestionnaire d'événements `InitializeService` par le code suivant :

     [!code-vb[WCFDataServiceWalkthrough#2](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework_2.vb)]
     [!code-csharp[WCFDataServiceWalkthrough#2](../data-tools/codesnippet/CSharp/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework_2.cs)]

6. Dans la barre de menus, choisissez **déboguer** > **démarrer sans débogage** pour exécuter le service. Une fenêtre de navigateur s’ouvre et affiche le schéma XML pour le service.

7. Dans le **adresse** barre, entrez `Customers` à la fin de l’URL pour **NorthwindCustomers.svc**, puis choisissez le **entrée** clé.

     Une représentation XML des données dans le `Customers` table apparaît.

    > [!NOTE]
    > Dans certains cas, Internet Explorer interprétera par erreur les données comme un flux RSS. Vous devez vous assurer que l'option permettant d'afficher les flux RSS est désactivée. Pour plus d’informations, consultez [Dépannage des références de service](../data-tools/troubleshooting-service-references.md).

8. Fermez la fenêtre du navigateur.

Dans les étapes suivantes, vous créez une application cliente de Windows Forms pour consommer le service.

## <a name="creating-the-client-application"></a>Création de l'application cliente
 Pour créer l’application cliente, vous ajoutez un deuxième projet, une référence de service au projet, vous configurez une source de données et vous créez une interface utilisateur pour afficher les données provenant du service.

 Dans la première étape, vous allez ajouter un projet Windows Forms à la solution et définissez-le comme projet de démarrage.

### <a name="to-create-the-client-application"></a>Pour créer l'application cliente

1. Dans la barre de menus, choisissez Fichier, **ajouter** > **nouveau projet**.

2. Dans le **nouveau projet** boîte de dialogue, développez le **Visual Basic** ou **Visual C#**  nœud, choisissez le **Windows** nœud, puis choisissez **Windows Forms Application**.

3. Dans la zone de texte **Nom**, entrez `NorthwindClient`, puis choisissez le bouton **OK**.

4. Dans l’**Explorateur de solutions**, choisissez le nœud du projet **NorthwindClient**.

5. Dans la barre de menus, choisissez **Projet**, **Définir comme projet de démarrage**.

Dans l’étape suivante, vous ajoutez une référence de service à le [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] dans le projet web.

### <a name="to-add-a-service-reference"></a>Pour ajouter une référence de service.

1. Dans la barre de menus, choisissez **projet** > **ajouter une référence de Service**.

2. Dans la boîte de dialogue **Ajouter une référence de service**, choisissez le bouton **Découvrir**.

     L’URL pour le service NorthwindCustomers s’affiche dans le champ **Address**.

3. Choisissez le bouton **OK** pour ajouter la référence de service.

Dans l’étape suivante, vous configurez une source de données pour permettre la liaison de données au service.

### <a name="to-enable-data-binding-to-the-service"></a>Pour activer la liaison de données vers le service

1. Dans la barre de menus, choisissez **vue** > **Windows autres** > **des Sources de données**.

   La fenêtre **Sources de données** s’ouvre.

2. Dans la fenêtre **Sources de données**, choisissez le bouton **Ajouter une nouvelle source de données**.

3. Dans la page **Choisir un type de source de données** de l’**Assistant Configuration de source de données**, choisissez **Objet**, puis cliquez sur le bouton **Suivant**.

4. Dans la page **Sélectionner les objets de données**, développez le nœud **NorthwindClient**, puis le nœud **NorthwindClient.ServiceReference1**.

5. Cochez la case **Customer**, puis choisissez le bouton **Terminer**.

Dans l’étape suivante, vous créez l’interface utilisateur qui affiche les données à partir du service.

### <a name="to-create-the-user-interface"></a>Pour créer l'interface utilisateur

1. Dans la fenêtre **Sources de données**, ouvrez le menu contextuel pour le nœud **Customers** et choisissez **Copier**.

2. Dans le concepteur de formulaires **Form1.vb** ou **Form1.cs**, ouvrez le menu contextuel et choisissez **Coller**.

    Un contrôle <xref:System.Windows.Forms.DataGridView>, un composant <xref:System.Windows.Forms.BindingSource> et un composant <xref:System.Windows.Forms.BindingNavigator> sont ajoutés au formulaire.

3. Sélectionnez le contrôle **CustomersDataGridView** et, dans la fenêtre **Propriétés**, définissez la propriété **Dock** sur **Remplissage**.

4. Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour le **Form1** nœud et choisissez **afficher le Code** pour ouvrir l’éditeur de Code, ajoutez le code suivant `Imports` ou `Using`instruction en haut du fichier :

   ```vb
   Imports NorthwindClient.ServiceReference1
   ```

   ```csharp
   using NorthwindClient.ServiceReference1;
   ```

5. Ajoutez le code suivant au gestionnaire d'événements `Form1_Load` :

   ```vb
   Private Sub Form1_Load(sender As Object, e As EventArgs) Handles MyBase.Load
           Dim proxy As New NorthwindEntities _
   (New Uri("http://localhost:53161/NorthwindCustomers.svc/"))
           Me.CustomersBindingSource.DataSource = proxy.Customers
       End Sub
   ```

   ```csharp
   private void Form1_Load(object sender, EventArgs e)
   {
   NorthwindEntities proxy = new NorthwindEntities(new Uri("http://localhost:53161/NorthwindCustomers.svc/"));
   this.CustomersBindingSource.DataSource = proxy.Customers;
   }
   ```

6. Dans l’**Explorateur de solutions**, ouvrez le menu contextuel du fichier **NorthwindCustomers.svc** et choisissez **Afficher dans le navigateur**. Internet Explorer s’ouvre et affiche le schéma XML pour le service.

7. Copiez l'URL à partir de la barre d'adresses d'Internet Explorer.

8. Dans le code que vous avez ajouté à l'étape 4, sélectionnez `http://localhost:53161/NorthwindCustomers.svc/` et remplacez-le par l'URL que vous venez de copier.

9. Dans la barre de menus, choisissez **déboguer** > **démarrer le débogage** pour exécuter l’application. Les informations client sont affichées.

   Vous disposez désormais d'une application opérationnelle qui affiche une liste de clients à partir du service NorthwindCustomers. Si vous souhaitez exposer des données supplémentaires à travers le service, vous pouvez modifier l'[!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] pour inclure des tables supplémentaires à partir de la base de données Northwind.

Dans l’étape facultative suivante, vous allez apprendre à filtrer les données retournées par le service.

## <a name="adding-filtering-capabilities"></a>Ajout des fonctions de filtrage
 Dans cette étape, vous personnalisez l’application à filtrer les données selon la ville du client.

### <a name="to-add-filtering-by-city"></a>Pour ajouter le filtrage selon la ville

1. Dans l’**Explorateur de solutions**, ouvrez le menu contextuel du nœud **Form1.vb** ou **Form1.cs**, puis choisissez **Ouvrir**.

2. Ajoutez un contrôle <xref:System.Windows.Forms.TextBox> et un contrôle <xref:System.Windows.Forms.Button> au formulaire à partir de la **Boîte à outils**.

3. Ouvrez le menu contextuel pour le <xref:System.Windows.Forms.Button> contrôler, choisissez **afficher le Code**, puis ajoutez le code suivant dans le `Button1_Click` Gestionnaire d’événements :

    ```vb
    Private Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click
            Dim proxy As New northwindEntities _
    (New Uri("http://localhost:53161/NorthwindCustomers.svc"))
            Dim city As String = TextBox1.Text

            If city <> "" Then
                Me.CustomersBindingSource.DataSource = From c In _
             proxy.Customers Where c.City = city
            End If

        End Sub
    ```

    ```csharp
    private void Button1_Click(object sender, EventArgs e)
    {
    ServiceReference1.northwindModel.northwindEntities proxy = new northwindEntities(new Uri("http://localhost:53161/NorthwindCustomers.svc"));
    string city = TextBox1.Text;

    if (!string.IsNullOrEmpty(city)) {
    this.CustomersBindingSource.DataSource = from c in proxy.Customers where c.City == city;
    }

    }
    ```

4. Dans le code précédent, remplacez `http://localhost:53161/NorthwindCustomers.svc` par l'URL du gestionnaire d'événements `Form1_Load`.

5. Dans la barre de menus, choisissez **déboguer** > **démarrer le débogage** pour exécuter l’application.

6. Dans la zone de texte, tapez **London**, puis choisissez le bouton. Seuls les clients de Londres sont affichés.

## <a name="see-also"></a>Voir aussi

- [Services Windows Communication Foundation et services de données WCF dans Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
- [Guide pratique pour ajouter, mettre à jour ou supprimer une référence de service de données WCF](../data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference.md)