---
title: Lier des contrôles WPF à un service de données WCF
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio], walkthroughs
- WPF Designer, data binding
ms.assetid: 8823537c-82f0-41f7-bf30-705f0e5e59fd
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: eb6b9a9a213932662a548314bcc39c75e9d35bc3
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55909685"
---
# <a name="bind-wpf-controls-to-a-wcf-data-service"></a>Lier des contrôles WPF à un service de données WCF

Dans cette procédure pas à pas, vous allez créer une application WPF qui contient des contrôles liés aux données. Les contrôles sont liés aux enregistrements client encapsulés dans un Service de données WCF. Vous allez aussi ajouter des boutons utilisables par les clients pour afficher et mettre à jour des enregistrements.

Cette procédure pas à pas décrit les tâches suivantes :

- Création d'un Entity Data Model généré à partir des données de l'exemple de base de données AdventureWorksLT.

- Création d’un Service de données WCF qui expose les données dans l’Entity Data Model dans une application WPF.

- Création d’un ensemble de contrôles liés aux données en faisant glisser des éléments depuis la fenêtre **Sources de données** vers le Concepteur WPF.

- Création de boutons permettant d'avancer et de reculer dans les enregistrements client.

- Création d’un bouton qui enregistre les modifications apportées aux données dans les contrôles pour le Service de données WCF et la source de données sous-jacente.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="prerequisites"></a>Prérequis

Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :

- Visual Studio

- Accès à une instance en cours d'exécution de SQL Server ou SQL Server Express à laquelle est attaché l'exemple de base de données AdventureWorksLT. Vous pouvez télécharger la base de données AdventureWorksLT à partir de la [site Web CodePlex](http://go.microsoft.com/fwlink/?linkid=87843).

La connaissance préalable des concepts suivants s'avère également utile, mais n'est pas obligatoire pour suivre cette procédure pas à pas :

- Services de données WCF. Pour plus d’informations, consultez [vue d’ensemble](/dotnet/framework/data/wcf/wcf-data-services-overview).

- Modèles de données dans les [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)].

- Entity Data Models et ADO.NET Entity Framework. Pour plus d’informations, consultez [vue d’ensemble d’Entity Framework](/dotnet/framework/data/adonet/ef/overview).

- Liaison de données WPF. Pour plus d’informations, consultez [Vue d’ensemble de la liaison de données](/dotnet/framework/wpf/data/data-binding-overview).

## <a name="create-the-service-project"></a>Créer le projet de service

Démarrer cette procédure pas à pas en créant un projet pour un Service de données WCF :

1. Démarrez Visual Studio.

2. Dans le menu **Fichier** , pointez sur **Nouveau**, puis cliquez sur **Projet**.

3. Développez **Visual C#** ou **Visual Basic**, puis sélectionnez **Web**.

4. Sélectionnez le modèle de projet **Application web ASP.NET**.

5. Dans la zone **Nom**, tapez **AdventureWorksService**, puis cliquez sur **OK**.

     Visual Studio crée le projet **AdventureWorksService**.

6. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur **Default.aspx** et sélectionnez **Supprimer**. Ce fichier n'est pas nécessaire dans cette procédure pas à pas.

## <a name="create-an-entity-data-model-for-the-service"></a>Créer un Entity Data Model pour le service

Pour exposer des données à une application à l’aide d’un Service de données WCF, vous devez définir un modèle de données pour le service. Le Service de données WCF prend en charge deux types de modèles de données : Entity Data Models et modèles de données personnalisés qui sont définies à l’aide des objets common language runtime (CLR) qui implémentent le <xref:System.Linq.IQueryable%601> interface. Dans cette procédure pas à pas, vous allez créer un Entity Data Model comme modèle de données.

1. Dans le menu **Projet** , cliquez sur **Ajouter un nouvel élément**.

2. Dans la liste Modèles installés, cliquez sur **Données**, puis sélectionnez l’élément de projet **ADO.NET Entity Data Model**.

3. Remplacez le nom par `AdventureWorksModel.edmx`, puis cliquez sur **ajouter**.

     L’Assistant **Entity Data Model** s’ouvre.

4. Dans la page **Choisir le contenu du modèle**, cliquez sur **Générer à partir de la base de données**, puis sur **Suivant**.

5. Dans la page **Choisir votre connexion de données**, sélectionnez une des options suivantes :

    - Si une connexion de données à l’exemple de base de données AdventureWorksLT est disponible dans la liste déroulante, sélectionnez-la.

    - Cliquez sur **Nouvelle connexion** et créez une connexion à la base de données AdventureWorksLT.

6. Dans la page **Choisir votre connexion de données**, vérifiez que l’option **Enregistrer les paramètres de connexion de l’entité dans App.Config en tant que** est sélectionnée, puis cliquez sur **Suivant**.

7. Dans la page **Choisir vos objets de base de données**, développez **Tables**, puis sélectionnez la table **SalesOrderHeader**.

8. Cliquez sur **Terminer**.

## <a name="create-the-service"></a>Créer le service

Créer un Service de données WCF pour exposer les données dans l’Entity Data Model dans une application WPF :

1. Dans le menu **Projet**, sélectionnez **Ajouter un nouvel élément**.

2. Dans la liste **Modèles installés**, cliquez sur **Web**, puis sélectionnez l’élément de projet **Service de données WCF**.

3. Dans le **nom** , tapez `AdventureWorksService.svc`, puis cliquez sur **ajouter**.

     Visual Studio ajoute le `AdventureWorksService.svc` au projet.

## <a name="configure-the-service"></a>Configurer le service

Vous devez configurer le service pour qu’il fonctionne sur l’Entity Data Model que vous avez créé :

1. Dans le `AdventureWorks.svc` fichier de code, remplacez le **AdventureWorksService** déclaration avec le code suivant de classe.

     [!code-csharp[Data_WPFWCF#1](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_1.cs)]
     [!code-vb[Data_WPFWCF#1](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_1.vb)]

     Ce code met à jour le **AdventureWorksService** classe, afin qu’elle dérive un <xref:System.Data.Services.DataService%601> qui opère sur le `AdventureWorksLTEntities` de l’objet classe de contexte dans votre Entity Data Model. Il met également à jour la méthode `InitializeService` pour accorder aux clients du service un accès complet en lecture/écriture à l'entité `SalesOrderHeader`.

2. Générez le projet et vérifiez qu'aucune erreur ne se produit.

## <a name="create-the-wpf-client-application"></a>Créer l’application cliente WPF

Pour afficher les données à partir du Service de données WCF, créez une application WPF avec une source de données qui est basée sur le service. Plus loin dans cette procédure pas à pas, vous allez ajouter à l'application des contrôles liés aux données.

1. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le nœud de la solution, cliquez sur **Ajouter**, puis sélectionnez **Nouveau projet**.

2. Dans la boîte de dialogue **Nouveau projet**, développez **Visual C#** ou **Visual Basic**, puis sélectionnez **Windows**.

3. Sélectionnez le modèle de projet **Application WPF**.

4. Dans la zone **Nom**, tapez `AdventureWorksSalesEditor`, puis cliquez sur **OK**.

   Visual Studio ajoute le `AdventureWorksSalesEditor` projet à la solution.

5. Dans le menu **Données** , cliquez sur **Afficher les sources de données**.

   La fenêtre **Sources de données** s’ouvre.

6. Dans la fenêtre **Sources de données** , cliquez sur **Ajouter une nouvelle source de données**.

   L’Assistant **Configuration de source de données** s’ouvre.

7. Dans la page **Choisir un type de source de données** de l’Assistant, sélectionnez **Service**, puis cliquez sur **Suivant**.

8. Dans la boîte de dialogue **Ajouter une référence de service**, cliquez sur **Découvrir**.

   Visual Studio recherche la solution actuelle pour les services disponibles et ajoute `AdventureWorksService.svc` à la liste des services disponibles dans le **Services** boîte.

9. Dans la zone **Espace de noms**, tapez **AdventureWorksService**.

10. Dans la zone **Services**, cliquez sur **AdventureWorksService.svc**, puis sur **OK**.

    Visual Studio télécharge les informations du service et revient à l’Assistant **Configuration de source de données**.

11. Dans la boîte de dialogue **Ajouter une référence de service**, cliquez sur **Terminer**.

    Visual Studio ajoute des nœuds représentant les données retournées par le service dans la fenêtre **Sources de données**.

## <a name="define-the-user-interface"></a>Définir l’interface utilisateur

Ajoutez plusieurs boutons à la fenêtre en modifiant le code XAML dans le Concepteur WPF. Plus loin dans cette procédure pas à pas, vous allez ajouter du code permettant aux utilisateurs d'afficher et de mettre à jour les enregistrements de vente à l'aide de ces boutons.

1. Dans l’**Explorateur de solutions**, double-cliquez sur **MainWindow.xaml**.

   La fenêtre s'ouvre dans le Concepteur WPF.

2. Dans la vue [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] du concepteur, ajoutez le code suivant entre les étiquettes `<Grid>` :

   ```xaml
   <Grid.RowDefinitions>
       <RowDefinition Height="75" />
       <RowDefinition Height="525" />
   </Grid.RowDefinitions>
   <Button HorizontalAlignment="Left" Margin="22,20,0,24" Name="backButton" Width="75"><</Button>
   <Button HorizontalAlignment="Left" Margin="116,20,0,24" Name="nextButton" Width="75">></Button>
   <Button HorizontalAlignment="Right" Margin="0,21,46,24" Name="saveButton" Width="110">Save changes</Button>
   ```

3. Générez le projet.

## <a name="create-the-data-bound-controls"></a>Créer des contrôles liés aux données

Créer des contrôles qui affichent les enregistrements client en faisant glisser le `SalesOrderHeaders` nœud à partir de la **des Sources de données** fenêtre vers le concepteur.

1. Dans la fenêtre **Sources de données**, cliquez sur le menu déroulant pour le nœud **SalesOrderHeaders**, puis sélectionnez **Détails**.

2. Développez le nœud **SalesOrderHeaders**.

3. Pour cet exemple, certains champs ne vont pas s’afficher. Cliquez alors sur le menu déroulant situé à côté des nœuds suivants, puis sélectionnez **Aucun** :

    - **CreditCardApprovalCode**

    - **ModifiedDate**

    - **OnlineOrderFlag**

    - **RevisionNumber**

    - **rowguid**

    Cette action empêche Visual Studio de créer des contrôles liés aux données pour ces nœuds à l'étape suivante. Pour cette procédure pas à pas, supposez que l’utilisateur final n’a pas besoin d’afficher ces données.

4. Dans la fenêtre **Sources de données**, faites glisser le nœud **SalesOrderHeaders** dans la ligne de la grille située en dessous de la ligne contenant les boutons.

     Visual Studio génère du XAML et du code qui créent un ensemble de contrôles liés aux données de la table **Product**. Pour plus d’informations sur le XAML et le code généré, consultez [WPF de lier des contrôles à des données dans Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).

5. Dans le concepteur, cliquez sur la zone de texte à côté de l’étiquette **Customer ID**.

6. Dans la fenêtre **Propriétés**, cochez la case en regard de la propriété **IsReadOnly**.

7. Définissez la propriété **IsReadOnly** pour chacune des zones de texte suivantes :

    - **Purchase Order Number**

    - **Sales Order ID**

    - **Sales Order Number**

## <a name="load-the-data-from-the-service"></a>Charger les données à partir du service

Utilisez l’objet proxy de service pour charger les données de ventes à partir du service. Puis assignez les données retournées à la source de données pour la <xref:System.Windows.Data.CollectionViewSource> dans la fenêtre WPF.

1. Dans le concepteur, pour créer le `Window_Loaded` Gestionnaire d’événements, double-cliquez sur le texte qui lit : **MainWindow**.

2. Remplacez le gestionnaire d'événements par le code suivant. Remplacez l’adresse *localhost* dans ce code par l’adresse de l’hôte local de votre ordinateur de développement.

     [!code-csharp[Data_WPFWCF#2](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_2.cs)]
     [!code-vb[Data_WPFWCF#2](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_2.vb)]

## <a name="navigate-sales-records"></a>Parcourir des enregistrements de ventes

Ajoutez du code permettant aux utilisateurs de parcourir les enregistrements de vente à l’aide des boutons **\<** et **>**.

1. Dans le concepteur, double-cliquez sur le bouton **<** de la fenêtre.

     Visual Studio ouvre le fichier code-behind et crée un gestionnaire d’événements `backButton_Click` pour l’événement <xref:System.Windows.Controls.Primitives.ButtonBase.Click>.

2. Ajoutez le code suivant au gestionnaire d'événements `backButton_Click` généré :

     [!code-csharp[Data_WPFWCF#3](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_3.cs)]
     [!code-vb[Data_WPFWCF#3](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_3.vb)]

3. Revenez dans le concepteur et double-cliquez sur le bouton **>**.

     Visual Studio ouvre le fichier code-behind et crée un gestionnaire d’événements `nextButton_Click` pour l’événement <xref:System.Windows.Controls.Primitives.ButtonBase.Click>.

4. Ajoutez le code suivant au gestionnaire d'événements `nextButton_Click` généré :

     [!code-csharp[Data_WPFWCF#4](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_4.cs)]
     [!code-vb[Data_WPFWCF#4](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_4.vb)]

## <a name="save-changes-to-sales-records"></a>Enregistrer les modifications apportées aux enregistrements de vente

Ajoutez du code permettant aux utilisateurs d’afficher et d’enregistrer les modifications apportées aux enregistrements de vente à l’aide du bouton **Enregistrer les modifications** :

1. Dans le concepteur, double-cliquez sur le bouton **Enregistrer les modifications**.

     Visual Studio ouvre le fichier code-behind et crée un gestionnaire d’événements `saveButton_Click` pour l’événement <xref:System.Windows.Controls.Primitives.ButtonBase.Click>.

2. Ajoutez le code ci-après au gestionnaire d'événements `saveButton_Click`.

     [!code-csharp[Data_WPFWCF#5](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_5.cs)]
     [!code-vb[Data_WPFWCF#5](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_5.vb)]

## <a name="test-the-application"></a>Tester l’application

Générez et exécutez l’application pour vérifier que vous pouvez afficher et mettre à jour les enregistrements de clients :

1. Sur **Build** menu, cliquez sur **générer la Solution**. Vérifiez que la solution se génère sans erreur.

2. Appuyez sur **Ctrl**+**F5**.

     Visual Studio démarre le projet **AdventureWorksService** sans le déboguer.

3. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le projet **AdventureWorksSalesEditor**.

4. Dans le menu contextuel (menu contextuel), sous **déboguer**, cliquez sur **démarrer une nouvelle instance**.

     L'application s'exécute. Vérifiez ce qui suit :

    - Les zones de texte affichent différents champs de données du premier enregistrement de vente, qui a l’ID de commande **71774**.

    - Vous pouvez cliquez sur les boutons **>** ou **<** pour parcourir les autres enregistrements de vente.

5. Dans un des enregistrements de vente, tapez du texte dans la zone **Comment** (Commentaire), puis cliquez sur **Enregistrer les modifications**.

6. Fermez l'application, puis redémarrez-la à partir de Visual Studio.

7. Accédez à l'enregistrement de vente que vous avez modifié et vérifiez que la modification est toujours présente après avoir fermé et réouvert l'application.

8. Fermez l'application.

## <a name="next-steps"></a>Étapes suivantes

Une fois cette procédure pas à pas terminée, vous pouvez effectuer les tâches associées suivantes :

- Découvrez comment utiliser la fenêtre **Sources de données** dans Visual Studio pour lier des contrôles WPF à d’autres types de sources de données. Pour plus d’informations, consultez [WPF de lier des contrôles à un jeu de données](../data-tools/bind-wpf-controls-to-a-dataset.md).

- Découvrez comment utiliser la fenêtre **Sources de données** dans Visual Studio pour afficher des données associées (c’est-à-dire des données dans une relation parent-enfant) dans des contrôles WPF. Pour plus d’informations, consultez [procédure pas à pas : affichage de données liées dans une application WPF](../data-tools/display-related-data-in-wpf-applications.md).

## <a name="see-also"></a>Voir aussi

- [Lier des contrôles WPF à des données dans Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)
- [Lier des contrôles WPF à un dataset](../data-tools/bind-wpf-controls-to-a-dataset.md)
- [Vue d’ensemble WCF (.NET Framework)](/dotnet/framework/data/wcf/wcf-data-services-overview)
- [Présentation d’Entity Framework (.NET Framework)](/dotnet/framework/data/adonet/ef/overview)
- [Vue d’ensemble (.NET Framework) de liaison de données](/dotnet/framework/wpf/data/data-binding-overview)