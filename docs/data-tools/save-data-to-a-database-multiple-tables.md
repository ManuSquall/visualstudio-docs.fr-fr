---
title: "Proc&#233;dure pas &#224; pas&#160;: enregistrement de donn&#233;es dans une base de donn&#233;es (plusieurs tables) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "données (Visual Studio), enregistrer"
  - "données (Visual Studio), mettre à jour"
  - "enregistrer les données, procédures pas à pas"
  - "mise à jour de groupes de données, procédures pas à pas"
ms.assetid: 7ebe03da-ce8c-4cbc-bac0-a2fde4ae4d07
caps.latest.revision: 24
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Proc&#233;dure pas &#224; pas&#160;: enregistrement de donn&#233;es dans une base de donn&#233;es (plusieurs tables)
L'un des scénarios les plus courants dans le développement d'applications consiste à afficher des données dans un formulaire d'une application Windows, à modifier ces données, puis à renvoyer les données mises à jour à la base de données.  Cette procédure pas à pas crée un formulaire affichant les données de deux tables associées et indique comment modifier les enregistrements et enregistrer les modifications dans la base de données.  Cet exemple utilise les tables `Customers` et `Orders` de l'exemple de base de données Northwind.  
  
 Vous pouvez enregistrer des données de votre application dans la base de données en appelant la méthode `Update` d'un TableAdapter.  Quand vous faites glisser des éléments depuis la fenêtre **Sources de données**, du code permettant d'enregistrer les données est automatiquement ajouté pour la première table déplacée dans un formulaire.  Toutes les tables supplémentaires ajoutées à un formulaire requièrent l'ajout manuel du code requis pour enregistrer les données.  Cette procédure pas à pas indique comment ajouter du code pour enregistrer les mises à jour de plusieurs tables.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Cette procédure pas à pas décrit notamment les tâches suivantes :  
  
-   Création d'un projet d'**application Windows**.  
  
-   Création et configuration d'une source de données dans votre application à l'aide de l'[Configuration de source de données \(Assistant\)](../data-tools/media/data-source-configuration-wizard.png).  
  
-   Définition des contrôles des éléments dans la [Sources de données \(fenêtre\)](../Topic/Data%20Sources%20Window.md).  Pour plus d'informations, consultez [Définir le contrôle à créer lors d’une opération de glisser\-déplacer à partir de la fenêtre Sources de données](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
-   Création de contrôles liés aux données en faisant glisser des éléments depuis la fenêtre **Sources de données** vers votre formulaire.  
  
-   Modification d'une paire d'enregistrements dans chaque table du dataset.  
  
-   Modification du code pour renvoyer les données mises à jour dans le dataset à la base de données.  
  
## Composants requis  
 Pour exécuter cette procédure pas à pas, vous avez besoin des éléments suivants :  
  
-   avoir accès à l'exemple de base de données Northwind.  Pour plus d'informations, consultez [Comment : installer des exemples de bases de données](../data-tools/how-to-install-sample-databases.md).  
  
## Création de l'application Windows  
 La première étape consiste à créer une **application Windows**.  L'attribution d'un nom au projet est facultative à ce stade, mais nous allons lui en donner un car nous avons l'intention de l'enregistrer ultérieurement.  
  
#### Pour créer le projet d'application Windows  
  
1.  Dans le menu **Fichier**, créez un nouveau projet.  
  
2.  Attribuez le nom `UpdateMultipleTablesWalkthrough` au projet.  
  
3.  Sélectionnez **Application Windows** et cliquez sur **OK**.  Pour plus d'informations, consultez [Applications clientes](../Topic/Developing%20Client%20Applications%20with%20the%20.NET%20Framework.md).  
  
     Le projet **UpdateMultipleTablesWalkthrough** est créé et ajouté à l'**Explorateur de solutions**.  
  
## Création de la source de données  
 Cette étape crée une source de données à partir de la base de données Northwind à l'aide de l'**Assistant Configuration de source de données**.  Vous devez avoir accès à l'exemple de base de données Northwind pour créer la connexion.  Pour plus d'informations sur la configuration de l'exemple de base de données Northwind, consultez [Comment : installer des exemples de bases de données](../data-tools/how-to-install-sample-databases.md).  
  
#### Pour créer la source de données  
  
1.  Dans le menu **Données**, cliquez sur **Afficher les sources de données**.  
  
2.  Dans la fenêtre **Sources de données**, cliquez sur **Ajouter une nouvelle source de données** pour démarrer l'**Assistant Configuration de source de données**.  
  
3.  Sélectionnez **Base de données** dans la page **Choisir un type de source de données**, puis cliquez sur **Suivant**.  
  
4.  Dans la page **Choisir votre connexion de données**, effectuez l'une des opérations suivantes :  
  
    -   Si une connexion de données à l'exemple de base de données Northwind est disponible dans la liste déroulante, sélectionnez\-la.  
  
         ou  
  
    -   Sélectionnez **Nouvelle connexion** pour ouvrir la boîte de dialogue **Ajouter\/Modifier la connexion**.  
  
5.  Si votre base de données requiert un mot de passe, sélectionnez l'option pour inclure les données sensibles, puis cliquez sur **Suivant**.  
  
6.  Cliquez sur **Suivant** dans la page **Enregistrer la chaîne de connexion dans le fichier de configuration de l'application**.  
  
7.  Développez le nœud **Tables** dans la page **Choisir vos objets de base de données**.  
  
8.  Sélectionnez les tables **Customers** et **Orders**, puis cliquez sur **Terminer**.  
  
     **NorthwindDataSet** est ajouté à votre projet et les tables apparaissent dans la fenêtre **Sources de données**.  
  
## Définition des contrôles à créer  
 Pour cette procédure pas à pas, les données de la table `Customers` sont présentées dans une vue **Détails** où les données sont affichées dans des contrôles individuels.  Les données de la table `Orders` sont présentées dans une vue **Grille** affichée dans un contrôle <xref:System.Windows.Forms.DataGridView>.  
  
#### Pour définir le type de déplacement des éléments de la fenêtre Sources de données  
  
1.  Développez le nœud **Customers** dans la fenêtre **Sources de données**.  
  
2.  Remplacez le contrôle de la table **Customers** par des contrôles individuels en sélectionnant **Détails** dans la liste de contrôles du nœud **Customers**.  Pour plus d'informations, consultez [Définir le contrôle à créer lors d’une opération de glisser\-déplacer à partir de la fenêtre Sources de données](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
## Création du formulaire lié aux données  
 Pour créer des contrôles liés aux données, vous pouvez faire glisser des éléments depuis la fenêtre **Sources de données** vers votre formulaire.  
  
#### Pour créer des contrôlés liés aux données dans le formulaire  
  
1.  Faites glisser le nœud **Customers** principal depuis la fenêtre **Sources de données** vers **Form1**.  
  
     Les contrôles liés aux données assortis d'étiquettes descriptives apparaissent dans le formulaire, ainsi qu'une barre d'outils \(<xref:System.Windows.Forms.BindingNavigator>\) pour parcourir les enregistrements.  [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), [CustomersTableAdapter](../data-tools/tableadapter-overview.md), <xref:System.Windows.Forms.BindingSource> et <xref:System.Windows.Forms.BindingNavigator> s'affichent dans la barre d'état des composants.  
  
2.  Faites glisser le nœud **Orders** associé depuis la fenêtre **Sources de données** vers **Form1**.  
  
    > [!NOTE]
    >  Le nœud **Orders** associé est situé sous la colonne **Fax** et constitue un nœud enfant du nœud **Customers**.  
  
     Un contrôle <xref:System.Windows.Forms.DataGridView> et une barre d'outils \(<xref:System.Windows.Forms.BindingNavigator>\) pour parcourir les enregistrements apparaissent dans le formulaire.  Un [OrdersTableAdapter](../data-tools/tableadapter-overview.md) et un <xref:System.Windows.Forms.BindingSource> apparaissent dans la barre d'état des composants.  
  
## Ajout de code pour mettre à jour la base de données  
 Vous pouvez mettre à jour la base de données en appelant les méthodes `Update` des TableAdapters **Customers** et **Orders**.  Par défaut, un gestionnaire d'événements est ajouté au code du formulaire pour le bouton **Enregistrer** de <xref:System.Windows.Forms.BindingNavigator> afin d'envoyer des mises à jour à la base de données.  Cette procédure modifie ce code pour envoyer les mises à jour dans l'ordre approprié afin d'éliminer le risque de lever des erreurs d'intégrité référentielle.  Le code implémente également la gestion des erreurs en enveloppant l'appel de mise à jour dans un bloc try\-catch.  Vous pouvez modifier le code pour répondre aux besoins de votre application.  
  
> [!NOTE]
>  Dans un souci de clarté, cette procédure pas à pas n'utilise pas de transaction, mais si vous mettez à jour au moins deux tables associées, vous devez inclure toute la logique de mise à jour dans une transaction.  Une transaction est un processus qui garantit que toutes les modifications associées apportées à une base de données sont réussies avant de les valider.  Pour plus d'informations, consultez [Transactions et concurrence](../Topic/Transactions%20and%20Concurrency.md).  
  
#### Pour ajouter une logique de mise à jour à l'application  
  
1.  Double\-cliquez sur le bouton **Enregistrer** de <xref:System.Windows.Forms.BindingNavigator> pour ouvrir l'Éditeur de code sur le gestionnaire d'événements `bindingNavigatorSaveItem_Click`.  
  
2.  Remplacez le code dans le gestionnaire d'événements pour appeler les méthodes `Update` des TableAdapters associés.  Le code suivant crée d'abord trois tables de données temporaires pour contenir les informations mises à jour pour chaque <xref:System.Data.DataRowState> \(<xref:System.Data.DataRowState>, <xref:System.Data.DataRowState> et <xref:System.Data.DataRowState>\).  Les mises à jour sont ensuite exécutées dans l'ordre approprié.  Le code doit se présenter comme suit :  
  
     [!code-vb[VbRaddataSaving#10](../data-tools/codesnippet/VisualBasic/save-data-to-a-database-multiple-tables_1.vb)]
     [!code-cs[VbRaddataSaving#10](../data-tools/codesnippet/CSharp/save-data-to-a-database-multiple-tables_1.cs)]  
  
## Test de l'application  
  
#### Pour tester l'application  
  
1.  Appuyez sur F5.  
  
2.  Apportez quelques modifications aux données d'un ou plusieurs enregistrements dans chaque table.  
  
3.  Appuyez sur le bouton **Enregistrer**.  
  
4.  Vérifiez les valeurs figurant dans la base de données pour confirmer que les modifications ont bien été enregistrées.  
  
## Étapes suivantes  
 Selon les spécifications de votre application, vous pouvez exécuter différentes étapes après la création d'un formulaire lié aux données dans votre application Windows.  Vous pouvez apporter à cette procédure pas à pas les améliorations suivantes :  
  
-   Ajout d'une fonctionnalité de recherche au formulaire.  Pour plus d'informations, consultez [Comment : ajouter une requête paramétrable à une application Windows Forms](../Topic/How%20to:%20Add%20a%20Parameterized%20Query%20to%20a%20Windows%20Forms%20Application.md).  
  
-   Modification de la source de données dans le but d'ajouter ou de supprimer des objets de base de données.  Pour plus d'informations, consultez [Comment : modifier un groupe de données](../Topic/How%20to:%20Edit%20a%20Dataset.md).  
  
## Voir aussi  
 [Procédures pas à pas relatives aux données](../Topic/Data%20Walkthroughs.md)   
 [Liaison de contrôles Windows Forms à des données dans Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Vue d'ensemble d'applications de données dans Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Connexion aux données dans Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Préparation de votre application pour recevoir des données](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Extraction de données dans votre application](../data-tools/fetching-data-into-your-application.md)   
 [Liaison de contrôles à des données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modification des données dans votre application](../data-tools/editing-data-in-your-application.md)   
 [Validation des données](../Topic/Validating%20Data.md)   
 [Enregistrement des données](../data-tools/saving-data.md)