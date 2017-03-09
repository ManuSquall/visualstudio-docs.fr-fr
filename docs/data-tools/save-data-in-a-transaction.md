---
title: "Proc&#233;dure pas &#224; pas&#160;: enregistrement de donn&#233;es dans une transaction | Microsoft Docs"
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
  - "données (Visual Studio), enregistrer dans une transaction"
  - "enregistrer les données"
  - "System.Transactions (espace de noms)"
  - "Transactions (espace de noms)"
  - "transactions, enregistrer les données"
ms.assetid: 80260118-08bc-4b37-bfe5-9422ee7a1e4e
caps.latest.revision: 15
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Proc&#233;dure pas &#224; pas&#160;: enregistrement de donn&#233;es dans une transaction
Cette procédure pas à pas décrit comment enregistrer les données dans une transaction à l'aide de l'espace de noms <xref:System.Transactions>.  Cet exemple utilise les tables `Customers` et `Orders` de l'exemple de base de données Northwind.  
  
## Composants requis  
 Cette procédure pas à pas requiert un accès à l'exemple de base de données Northwind.  Pour plus d'informations sur la configuration de l'exemple de base de données Northwind, consultez [Comment : installer des exemples de bases de données](../data-tools/how-to-install-sample-databases.md).  
  
## Création d'une application Windows  
 La première étape consiste à créer une **application Windows**.  
  
#### Pour créer un projet Windows  
  
1.  Dans Visual Studio, dans le menu **Fichier**, créez un **Projet**.  
  
2.  Attribuez le nom SavingDataInATransactionWalkthrough au projet.  
  
3.  Sélectionnez **Application Windows** et cliquez sur **OK**.  Pour plus d'informations, consultez [Applications clientes](../Topic/Developing%20Client%20Applications%20with%20the%20.NET%20Framework.md).  
  
     Le projet **SavingDataInATransactionWalkthrough** est créé et ajouté à l'**Explorateur de solutions**.  
  
## Création d'une source de base de données  
 Cette étape utilise l'[Configuration de source de données \(Assistant\)](../data-tools/media/data-source-configuration-wizard.png) pour créer une source de données basée sur les tables `Customers` et `Orders` de l'exemple de base de données Northwind.  
  
#### Pour créer la source de données  
  
1.  Dans le menu **Données**, cliquez sur **Afficher les sources de données**.  
  
2.  Dans la fenêtre **Sources de données**, sélectionnez **Ajouter une nouvelle source de données** pour démarrer l'**Assistant Configuration de source de données**.  
  
3.  Sélectionnez **Base de données** dans la page **Choisir un type de source de données**, puis cliquez sur **Suivant**.  
  
4.  Dans la page **Choisir votre connexion de données**, effectuez l'une des opérations suivantes :  
  
    -   Si une connexion de données à l'exemple de base de données Northwind est disponible dans la liste déroulante, sélectionnez\-la.  
  
         ou  
  
    -   Sélectionnez **Nouvelle connexion** pour lancer la boîte de dialogue **Ajouter\/Modifier une connexion** et créez une connexion à la base de données Northwind.  
  
5.  Si votre base de données requiert un mot de passe, sélectionnez l'option pour inclure les données sensibles, puis cliquez sur **Suivant**.  
  
6.  Cliquez sur **Suivant** dans la page **Enregistrer la chaîne de connexion dans le fichier de configuration de l'application**.  
  
7.  Développez le nœud **Tables** dans la page **Choisir vos objets de base de données**.  
  
8.  Sélectionnez les tables `Customers` et `Orders`, puis cliquez sur **Terminer**.  
  
     **NorthwindDataSet** est ajouté à votre projet et les tables `Customers` et `Orders` apparaissent dans la fenêtre **Sources de données**.  
  
## Ajout de contrôles au formulaire  
 Pour créer des contrôles liés aux données, vous pouvez faire glisser des éléments depuis la fenêtre **Sources de données** vers votre formulaire.  
  
#### Pour créer des contrôles liés aux données dans le formulaire Windows  
  
-   Développez le nœud **Customers** dans la fenêtre **Sources de données**.  
  
-   Faites glisser le nœud **Customers** principal depuis la fenêtre **Sources de données** vers **Form1**.  
  
     Un contrôle <xref:System.Windows.Forms.DataGridView> et une barre d'outils \(<xref:System.Windows.Forms.BindingNavigator>\) pour parcourir les enregistrements apparaissent dans le formulaire.  [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), [CustomersTableAdapter](../data-tools/tableadapter-overview.md), <xref:System.Windows.Forms.BindingSource> et <xref:System.Windows.Forms.BindingNavigator> s'affichent dans la barre d'état des composants.  
  
-   Faites glisser le nœud **Orders** associé \(le nœud de la table enfant associée figurant sous la colonne **Fax**, et non le nœud **Orders** principal\) vers le formulaire sous le **CustomersDataGridView**.  
  
     Un <xref:System.Windows.Forms.DataGridView> s'affiche dans le formulaire.  Un [OrdersTableAdapter](../data-tools/tableadapter-overview.md) et un <xref:System.Windows.Forms.BindingSource> apparaissent dans la barre d'état des composants.  
  
## Ajout d'une référence à l'assembly System.Transactions  
 Les transactions utilisent l'espace de noms <xref:System.Transactions>.  Une référence de project vers l'assembly system.transactions n'est pas ajoutée par défaut, vous devez donc l'ajouter manuellement.  
  
#### Pour ajouter une référence au fichier DLL System.Transactions  
  
1.  Dans le menu **Projet**, choisissez **Ajouter une référence**.  
  
2.  Sélectionnez **System.Transactions** \(sous l'onglet **.NET**\) et cliquez sur **OK**.  
  
     Une référence à **System.Transactions** est ajoutée au projet.  
  
## Modification du code du bouton SaveItem de BindingNavigator  
 Par défaut, pour la première table déplacée dans votre formulaire, du code est ajouté à l'événement `click` du bouton d'enregistrement sur le <xref:System.Windows.Forms.BindingNavigator>.  Vous devez manuellement ajouter du code pour mettre à jour toutes les tables supplémentaires.  Pour cette procédure pas à pas, nous refactorisons le code d'enregistrement existant en dehors du gestionnaire d'événements Click du bouton d'enregistrement et créons quelques méthodes supplémentaires pour fournir une fonctionnalité de mise à jour spécifique selon que la ligne nécessite d'être ajoutée ou supprimée.  
  
#### Pour modifier le code d'enregistrement généré automatiquement  
  
1.  Double\-cliquez sur le bouton **Enregistrement** du **CustomersBindingNavigator** \(le bouton avec une icône en forme de disquette\).  
  
2.  Remplacez la méthode `CustomersBindingNavigatorSaveItem_Click` par le code suivant :  
  
     [!code-vb[VbRaddataSaving#4](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_1.vb)]
     [!code-cs[VbRaddataSaving#4](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_1.cs)]  
  
 L'ordre de rapprochement des modifications des données associées est comme suit :  
  
-   Supprimer des enregistrements enfants \(dans ce cas, supprimer des enregistrements de la table `Orders`\)  
  
-   Supprimer des enregistrements parents \(dans ce cas, supprimer des enregistrements de la table `Customers`\)  
  
-   Insérer des enregistrements parents \(dans ce cas, insérer des enregistrements dans la table `Customers`\)  
  
-   Insérer des enregistrements enfants \(dans ce cas, insérer des enregistrements dans la table `Orders`\)  
  
#### Pour supprimer des commandes existantes  
  
-   Ajoutez la méthode `DeleteOrders` suivante à **Form1** :  
  
     [!code-vb[VbRaddataSaving#5](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_2.vb)]
     [!code-cs[VbRaddataSaving#5](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_2.cs)]  
  
#### Pour supprimer des clients existants  
  
-   Ajoutez la méthode `DeleteCustomers` suivante à **Form1** :  
  
     [!code-vb[VbRaddataSaving#6](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_3.vb)]
     [!code-cs[VbRaddataSaving#6](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_3.cs)]  
  
#### Pour ajouter de nouveaux clients  
  
-   Ajoutez la méthode `AddNewCustomers` suivante à **Form1** :  
  
     [!code-vb[VbRaddataSaving#7](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_4.vb)]
     [!code-cs[VbRaddataSaving#7](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_4.cs)]  
  
#### Pour ajouter de nouvelles commandes  
  
-   Ajoutez la méthode `AddNewOrders` suivante à **Form1** :  
  
     [!code-vb[VbRaddataSaving#8](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_5.vb)]
     [!code-cs[VbRaddataSaving#8](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_5.cs)]  
  
## Exécution de l'application  
  
#### Pour exécuter l'application  
  
-   Appuyez sur F5 pour exécuter l'application.  
  
## Voir aussi  
 [Transactions et concurrence](../Topic/Transactions%20and%20Concurrency.md)   
 [Transactions distribuées Oracle](../Topic/Oracle%20Distributed%20Transactions.md)   
 [Comment : enregistrer des données à l'aide d'une transaction](../data-tools/save-data-by-using-a-transaction.md)   
 [Intégration de System.Transactions à SQL Server](../Topic/System.Transactions%20Integration%20with%20SQL%20Server.md)   
 [Connexion aux données dans Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Préparation de votre application pour recevoir des données](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Extraction de données dans votre application](../data-tools/fetching-data-into-your-application.md)   
 [Liaison de contrôles à des données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modification des données dans votre application](../data-tools/editing-data-in-your-application.md)   
 [Validation des données](../Topic/Validating%20Data.md)   
 [Enregistrement des données](../data-tools/saving-data.md)