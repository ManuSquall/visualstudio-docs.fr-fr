---
title: 'Procédure pas à pas : création d’un service de données WCF avec WPF et Entity Framework | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
helpviewer_keywords:
- data services in Visual Studio
- WCF Data Services, Visual Studio
- ADO.NET Data Services, Visual Studio
- WCF data services in Visual Studio
ms.assetid: da66ad1b-a25d-485c-af13-2d18f0422e3d
caps.latest.revision: 28
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f26d81c3ac80b889f90e2a729545f0db0e52fa1a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660230"
---
# <a name="walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework"></a>Procédure pas à pas : Création d’un service de données WCF avec WPF et Entity Framework
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette procédure pas à pas montre comment créer un [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)] simple hébergé dans une application Web [!INCLUDE[vstecasp](../includes/vstecasp-md.md)], puis y accéder à partir d’une application Windows Forms.

 Dans cette procédure pas à pas, vous apprendrez à :

- Créer une application web pour héberger un [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)].

- Créer un [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] qui représente la table Customers dans la base de données Northwind.

- Créer un [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)].

- Créer une application cliente et ajouter une référence au [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)].

- Activer la liaison de données vers un service et générer l’interface utilisateur.

- Ajouter éventuellement des fonctions de filtrage à l'application.

## <a name="prerequisites"></a>Configuration requise
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :

- Exemple de base de données Northwind.

     Si cette base de données n’est pas disponible sur votre ordinateur de développement, vous pouvez la télécharger à partir du [Centre de téléchargement Microsoft](http://go.microsoft.com/fwlink/?LinkID=98088). Pour obtenir des instructions, consultez [téléchargement d’exemples de bases de données](https://msdn.microsoft.com/library/ef9d69a1-9461-43fe-94bb-7c836754bcb5).

## <a name="creating-the-service"></a>Création du service
 Pour créer un [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)], vous devez ajouter un projet Web, créer un [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)], puis créer le service à partir du modèle.

 Au cours de la première étape, vous allez ajouter un projet Web pour héberger le service.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

#### <a name="to-create-the-web-project"></a>Pour créer le projet Web

1. Dans la barre de menus, choisissez **fichier**, **nouveau**, **projet**.

2. Dans la boîte de dialogue **Nouveau projet**, développez les nœuds **Visual Basic** ou **Visual C#** et **Web**, puis choisissez le modèle **Application web ASP.NET**.

3. Dans la zone de texte **Nom**, entrez **NorthwindWeb**, puis choisissez le bouton **OK**.

4. Dans la boîte de dialogue **Nouveau projet ASP.NET**, dans la liste **Sélectionner un modèle**, choisissez **Vide**, puis le bouton **OK**.

   Dans cette étape, vous allez créer un [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] qui représente la table Customers dans la base de données Northwind.

#### <a name="to-create-the-entity-data-model"></a>Pour créer le modèle EDM (Entity Data Model)

1. Dans la barre de menus, choisissez **projet**, **Ajouter un nouvel élément**.

2. Dans la boîte de dialogue **Ajouter un nouvel élément**, choisissez le nœud **Données**, puis l’élément **ADO.NET Entity Data Model**.

3. Dans la zone de texte **nom** , entrez `NorthwindModel`, puis cliquez sur le bouton **Ajouter** .

    L'Assistant Entity Data Model s'affiche.

4. Dans l’Assistant EDM, dans la page **Choisir le contenu du modèle**, choisissez l’élément **Concepteur EF à partir d’une base de données**, puis cliquez sur le bouton **Suivant**.

5. Sur la page **Choisir votre connexion de données** , effectuez l'une des opérations suivantes :

   - Si une connexion de données à l'exemple de base de données Northwind est disponible dans la liste déroulante, choisissez-la.

        ou

   - Choisissez le bouton **Nouvelle connexion** pour configurer une nouvelle connexion de données. Pour plus d’informations, consultez [ajouter de nouvelles connexions](../data-tools/add-new-connections.md).

6. Si la base de données nécessite un mot de passe, choisissez la case d’option **Oui, inclure les données sensibles dans la chaîne de connexion**, puis cliquez sur le bouton **Suivant**.

   > [!NOTE]
   > Si une boîte de dialogue s’affiche, choisissez **Oui** pour enregistrer le fichier dans votre projet.

7. Dans la page **Choisir votre version**, choisissez la case d’option **Entity Framework 5.0**, puis le bouton **Suivant**.

   > [!NOTE]
   > Pour pouvoir utiliser la dernière version d’Entity Framework 6 avec les services WCF, vous devez installer le package NuGet du fournisseur Entity Framework de services de données WCF. Consultez [utilisation de WCF Data Services 5.6.0 avec Entity Framework 6 +](http://blogs.msdn.com/b/odatateam/archive/2013/10/02/using-wcf-data-services-5-6-0-with-entity-framework-6.aspx).

8. Dans la page **Choisir vos objets de base de données**, développez le nœud **Tables**, cochez la case **Customers**, puis choisissez le bouton **Terminer**.

    Le diagramme de modèle d'entité s'affichera et un fichier NorthwindModel.edmx sera ajouté à votre projet.

   Dans cette étape, vous allez créer et tester le service de données.

#### <a name="to-create-the-data-service"></a>Pour créer le service de données

1. Dans la barre de menus, choisissez **projet**, **Ajouter un nouvel élément**.

2. Dans la boîte de dialogue **Ajouter un nouvel élément**, choisissez le nœud **Web**, puis l’élément **WCF Data Service 5.6**.

3. Dans la zone de texte **nom** , entrez `NorthwindCustomers`, puis cliquez sur le bouton **Ajouter** .

    Le fichier NorthwindCustomers. svc s’affiche dans l' **éditeur de code**.

4. Dans l’**Éditeur de code**, localisez le premier commentaire `TODO:` et remplacez le code par celui-ci :

    [!code-csharp[WCFDataServiceWalkthrough#1](../snippets/csharp/VS_Snippets_VBCSharp/wcfdataservicewalkthrough/cs/northwindcustomers.svc.cs#1)]
    [!code-vb[WCFDataServiceWalkthrough#1](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfdataservicewalkthrough/vb/northwindcustomers.svc.vb#1)]

5. Remplacez les commentaires dans le gestionnaire d'événements `InitializeService` par le code suivant :

    [!code-csharp[WCFDataServiceWalkthrough#2](../snippets/csharp/VS_Snippets_VBCSharp/wcfdataservicewalkthrough/cs/northwindcustomers.svc.cs#2)]
    [!code-vb[WCFDataServiceWalkthrough#2](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfdataservicewalkthrough/vb/northwindcustomers.svc.vb#2)]

6. Dans la barre de menus, choisissez **Déboguer**, exécuter **sans débogage** pour exécuter le service. Une fenêtre de navigateur s'ouvre et le schéma XML pour le service s'affiche.

7. Dans la barre d' **adresses** , entrez `Customers` à la fin de l’URL pour NorthwindCustomers. svc, puis appuyez sur la touche **entrée** .

    Une représentation XML des données dans la table Customers s'affiche.

   > [!NOTE]
   > Dans certains cas, Internet Explorer interprétera par erreur les données comme un flux RSS. Vous devez vous assurer que l'option permettant d'afficher les flux RSS est désactivée. Pour plus d’informations, consultez [Dépannage des références de service](../data-tools/troubleshooting-service-references.md).

8. Fermez la fenêtre du navigateur.

   Au cours des étapes suivantes, vous devrez créer une application cliente Windows Forms pour consommer le service.

## <a name="creating-the-client-application"></a>Création de l'application cliente
 Pour créer l'application cliente, vous devrez ajouter un deuxième projet, une référence de service au projet, vous configurerez une source de données et créerez une interface utilisateur pour afficher les données à partir du service.

 Au cours de la première étape, vous allez ajouter un projet Windows Forms à la solution et allez le définir comme projet de démarrage.

#### <a name="to-create-the-client-application"></a>Pour créer l'application cliente

1. Dans la barre de menus, choisissez Fichier, **Ajouter**, **nouveau projet**.

2. Dans la boîte de dialogue **nouveau projet** , développez le nœud **Visual Basic** ou **visuel C#**  et choisissez le nœud **Windows** , puis choisissez **Windows Forms application**.

3. Dans la zone de texte **Nom**, entrez `NorthwindClient`, puis choisissez le bouton **OK**.

4. Dans l’**Explorateur de solutions**, choisissez le nœud du projet **NorthwindClient**.

5. Dans la barre de menus, choisissez **Projet**, **Définir comme projet de démarrage**.

   Dans cette étape, vous ajouterez une référence de service au [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)] dans le projet Web.

#### <a name="to-add-a-service-reference"></a>Pour ajouter une référence de service.

1. Dans la barre de menus, choisissez **projet**, **Ajouter une référence de service**.

2. Dans la boîte de dialogue **Ajouter une référence de service**, choisissez le bouton **Découvrir**.

    L’URL pour le service NorthwindCustomers s’affiche dans le champ **Address**.

3. Choisissez le bouton **OK** pour ajouter la référence de service.

   Au cours de cette étape, vous allez configurer une source de données pour activer la liaison de données vers le service.

#### <a name="to-enable-data-binding-to-the-service"></a>Pour activer la liaison de données vers le service

1. Dans la barre de menus, choisissez **Afficher**, **autres fenêtres**, **sources de données**.

2. Dans la fenêtre **Sources de données**, choisissez le bouton **Ajouter une nouvelle source de données**.

3. Dans la page **Choisir un type de source de données** de l’**Assistant Configuration de source de données**, choisissez **Objet**, puis cliquez sur le bouton **Suivant**.

4. Dans la page **Sélectionner les objets de données**, développez le nœud **NorthwindClient**, puis le nœud **NorthwindClient.ServiceReference1**.

5. Cochez la case **Customer**, puis choisissez le bouton **Terminer**.

   Au cours de cette étape, vous allez créer l'interface utilisateur qui affichera les données à partir du service.

#### <a name="to-create-the-user-interface"></a>Pour créer l'interface utilisateur

1. Dans la fenêtre **Sources de données**, ouvrez le menu contextuel pour le nœud **Customers** et choisissez **Copier**.

2. Dans le concepteur de formulaires **Form1.vb** ou **Form1.cs**, ouvrez le menu contextuel et choisissez **Coller**.

    Un contrôle <xref:System.Windows.Forms.DataGridView>, un composant <xref:System.Windows.Forms.BindingSource> et un composant <xref:System.Windows.Forms.BindingNavigator> sont ajoutés au formulaire.

3. Sélectionnez le contrôle **CustomersDataGridView** et, dans la fenêtre **Propriétés**, définissez la propriété **Dock** sur **Remplissage**.

4. Dans **Explorateur de solutions**, ouvrez le menu contextuel du nœud **Form1** et choisissez **afficher le code** pour ouvrir l’éditeur de code, puis ajoutez l’instruction Imports ou using suivante en haut du fichier :

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

6. Dans **Explorateur de solutions**, ouvrez le menu contextuel du fichier NorthwindCustomers. svc, puis choisissez **afficher dans le navigateur**. Internet Explorer s'ouvre et le schéma XML pour le service s'affiche.

7. Copiez l'URL à partir de la barre d'adresses d'Internet Explorer.

8. Dans le code que vous avez ajouté à l'étape 4, sélectionnez `http://localhost:53161/NorthwindCustomers.svc/` et remplacez-le par l'URL que vous venez de copier.

9. Dans la barre de menus, choisissez **Déboguer**, **Démarrer le débogage** pour exécuter l’application. Les informations client s'affichent.

   Vous disposez désormais d'une application opérationnelle qui affiche une liste de clients à partir du service NorthwindCustomers. Si vous souhaitez exposer des données supplémentaires à travers le service, vous pouvez modifier l'[!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] pour inclure des tables supplémentaires à partir de la base de données Northwind.

   Au cours de l'étape facultative suivante, vous allez apprendre à filtrer les données retournées par le service.

## <a name="adding-filtering-capabilities"></a>Ajout des fonctions de filtrage
 Au cours de cette étape, vous allez personnaliser l'application afin de filtrer les données selon la ville du client.

#### <a name="to-add-filtering-by-city"></a>Pour ajouter le filtrage selon la ville

1. Dans l’**Explorateur de solutions**, ouvrez le menu contextuel du nœud **Form1.vb** ou **Form1.cs**, puis choisissez **Ouvrir**.

2. Ajoutez un contrôle <xref:System.Windows.Forms.TextBox> et un contrôle <xref:System.Windows.Forms.Button> au formulaire à partir de la **Boîte à outils**.

3. Ouvrez le menu contextuel du contrôle <xref:System.Windows.Forms.Button>, puis choisissez **afficher le code**, puis ajoutez le code suivant dans le gestionnaire d’événements `Button1_Click` :

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

5. Dans la barre de menus, choisissez **Déboguer**, **Démarrer le débogage** pour exécuter l’application.

6. Dans la zone de texte, tapez **London**, puis choisissez le bouton. Seuls les clients de Londres sont affichés.

## <a name="see-also"></a>Voir aussi
 [Services et WCF Data Services de Windows Communication Foundation dans Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md) [Comment : ajouter, mettre à jour ou supprimer une référence de service de données WCF](../data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference.md)
