---
title: "Proc&#233;dure pas &#224; pas&#160;: affichage de donn&#233;es connexes dans une application WPF | Microsoft Docs"
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
  - "liaison de données WPF (Visual Studio), procédures pas à pas"
  - "concepteur WPF, liaison de données"
  - "WPF, liaison de données dans Visual Studio"
ms.assetid: 5c48f188-e9c4-40a6-97d9-67cdb2f90127
caps.latest.revision: 25
caps.handback.revision: 25
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Proc&#233;dure pas &#224; pas&#160;: affichage de donn&#233;es connexes dans une application WPF
Dans cette procédure pas à pas, vous créerez une application WPF qui affiche des données à partir des tables de base de données ayant une relation parent\/enfant.  Les données sont encapsulées dans des entités dans un Entity Data Model.  L'entité parente contient des informations d'ordre général sur un jeu de commandes.  Chaque propriété de cette entité est liée à un contrôle différent dans l'application.  L'entité enfant contient des détails pour chaque commande.  Ce groupe de données est lié à un contrôle <xref:System.Windows.Controls.DataGrid>.  
  
 Cette procédure pas à pas décrit les tâches suivantes :  
  
-   Création d'une application WPF et d'un Entity Data Model généré à partir de données de l'exemple de base de données AdventureWorksLT.  
  
-   Création d'un jeu de contrôles liés aux données qui affichent des informations d'ordre général sur un jeu de commandes.  Vous créez les contrôles en faisant glisser une entité parente de la fenêtre **Sources de données** vers le **Concepteur WPF**.  
  
-   Création d'un contrôle <xref:System.Windows.Controls.DataGrid> qui affiche des détails connexes pour chaque commande sélectionnée.  Vous créez les contrôles en faisant glisser une entité enfant de la fenêtre **Sources de données** vers une fenêtre du **Concepteur WPF**.  
  
     [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## Composants requis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
-   Accès à une instance en cours d'exécution de SQL Server ou SQL Server Express à laquelle l'exemple de base de données AdventureWorksLT est attaché  Vous pouvez télécharger la base de données AdventureWorksLT à partir du [site Web CodePlex](http://go.microsoft.com/fwlink/?linkid=87843).  
  
 Une connaissance préalable des concepts suivants est aussi utile, mais pas obligatoire, pour effectuer cette procédure pas à pas :  
  
-   Entity Data Models et ADO.NET Entity Framework.  Pour plus d'informations, consultez [Vue d'ensemble d'Entity Framework](../Topic/Entity%20Framework%20Overview.md).  
  
-   Utilisation du Concepteur WPF.  Pour plus d'informations, consultez [Vue d'ensemble des concepteurs WPF et Silverlight](http://msdn.microsoft.com/fr-fr/570b7a5c-0c86-4326-a371-c9b63378fc62).  
  
-   Liaison de données WPF.  Pour plus d'informations, consultez [Vue d'ensemble de la liaison de données](../Topic/Data%20Binding%20Overview.md).  
  
## Création du projet  
 Créez un projet WPF pour afficher les enregistrements de commandes.  
  
#### Pour créer un projet WPF  
  
1.  Démarrez Visual Studio.  
  
2.  Dans le menu **Fichier**, pointez sur **Nouveau**, puis cliquez sur **Projet**.  
  
3.  Développez **Visual C\#** ou **Visual Basic**, puis sélectionnez **Windows**.  
  
4.  Assurez\-vous que **.NET Framework 4** est sélectionné dans la zone de liste déroulante en haut de la boîte de dialogue.  Le contrôle <xref:System.Windows.Controls.DataGrid> que vous utilisez dans cette procédure pas à pas est uniquement disponible dans .NET Framework 4.  
  
5.  Sélectionnez le modèle de projet **Application WPF**.  
  
6.  Dans la zone **Nom**, tapez `AdventureWorksOrdersViewer`.  
  
7.  Cliquez sur **OK**.  
  
     Visual Studio crée le projet `AdventureWorksOrdersViewer`.  
  
## Création d'un Entity Data Model pour l'application  
 Avant de pouvoir créer des contrôles liés aux données, vous devez définir un modèle de données pour votre application et l'ajouter à la fenêtre **Sources de données**.  Dans cette procédure pas à pas, le modèle de données est un Entity Data Model.  
  
#### Pour créer un modèle EDM \(Entity Data Model\)  
  
1.  Dans le menu **Données**, cliquez sur **Ajouter une nouvelle source de données** pour lancer l'**Assistant Configuration de source de données**.  
  
2.  Dans la page **Choisir un type de source de données**, cliquez sur **Base de données**, puis sur **Suivant**.  
  
3.  Dans la page **Choisir un modèle de base de données**, cliquez sur **Entity Data Model**, puis sur **Suivant**.  
  
4.  Dans la page **Choisir le contenu du Model**, cliquez sur **Générer à partir de la base de données**, puis sur **Suivant**.  
  
5.  Dans la page **Choisir votre connexion de données**, effectuez l'une des opérations suivantes :  
  
    -   Si une connexion de données à l'exemple de base de données AdventureWorksLT est disponible dans la liste déroulante, sélectionnez\-la.  
  
         ou  
  
    -   Cliquez sur **Nouvelle connexion** et créez une connexion à la base de données AdventureWorksLT.  
  
     Assurez\-vous que l'option **Enregistrer les paramètres de connexion de l'entité dans App.Config en tant que** est sélectionnée, puis cliquez sur **Suivant**.  
  
6.  Dans la page **Choisir vos objets de base de données**, développez le nœud **Tables**, puis sélectionnez les tables suivantes :  
  
    -   **SalesOrderDetail**  
  
    -   **SalesOrderHeader**  
  
7.  Cliquez sur **Terminer**.  
  
8.  Générez le projet.  
  
## Création de contrôles liés aux données qui affichent les commandes  
 Créez des contrôles qui affichent les enregistrements de commandes en faisant glisser l'entité `SalesOrderHeaders` de la fenêtre **Sources de données** vers le Concepteur WPF.  
  
#### Pour créer des contrôles liés aux données qui affichent les enregistrements de commandes  
  
1.  Dans l'**Explorateur de solutions**, double\-cliquez sur MainWindow.xaml.  
  
     La fenêtre s'ouvre dans le Concepteur WPF.  
  
2.  Modifiez le code XAML afin que les propriétés **Height** et **Width** aient la valeur 800.  
  
3.  Dans la fenêtre **Sources de données**, cliquez sur le menu déroulant du nœud **SalesOrderHeaders** et sélectionnez **Détails**.  
  
4.  Développez le nœud **SalesOrderHeaders**.  
  
5.  Cliquez sur le menu déroulant en regard de **SalesOrderID** et sélectionnez **ComboBox**.  
  
6.  Pour chacun des nœuds enfants suivants du nœud **SalesOrderHeaders**, cliquez sur le menu déroulant en regard du nœud et sélectionnez **Aucun** :  
  
    -   **RevisionNumber**  
  
    -   **OnlineOrderFlag**  
  
    -   **ShipToAddressID**  
  
    -   **BillToAddressID**  
  
    -   **CreditCardApprovalCode**  
  
    -   **SubTotal**  
  
    -   **TaxAmt**  
  
    -   **Freight**  
  
    -   **rowguid**  
  
    -   **ModifiedDate**  
  
     Cette action empêche Visual Studio de créer des contrôles liés aux données pour ces nœuds à l'étape suivante.  Pour cette procédure pas à pas, on suppose que l'utilisateur final n'a pas besoin de voir ces données.  
  
7.  Depuis la fenêtre **Sources de données**, faites glisser le nœud **SalesOrderHeaders** vers la fenêtre du **Concepteur WPF**.  
  
     Visual Studio génère du code XAML qui crée un jeu de contrôles liés aux données dans l'entité **SalesOrderHeaders** et du code qui charge les données.  Pour plus d'informations sur le langage XAML et le code généré, consultez [Liaison de contrôles WPF avec des données dans Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
8.  Dans le concepteur, cliquez sur la zone de liste déroulante en regard de l'étiquette **Réf. commande client**.  
  
9. Dans la fenêtre **Propriétés**, activez la case à cocher en regard de la propriété **IsReadOnly**.  
  
## Création d'une grille de données qui affiche les détails des commandes  
 Créez un contrôle <xref:System.Windows.Controls.DataGrid> qui affiche les détails des commandes en faisant glisser l'entité `SalesOrderDetails` de la fenêtre **Sources de données** vers le Concepteur WPF.  
  
#### Pour créer une grille de données qui affiche les détails des commandes  
  
1.  Dans la fenêtre **Sources de données**, localisez le nœud **SalesOrderDetails** qui est un enfant du nœud **SalesOrderHeaders**.  
  
    > [!NOTE]
    >  La fenêtre contient également un nœud **SalesOrderDetails** qui est un pair du nœud **SalesOrderHeaders**.  Assurez\-vous que vous sélectionnez le nœud enfant du nœud **SalesOrderHeaders**.  
  
2.  Développez le nœud **SalesOrderDetails** enfant.  
  
3.  Pour chacun des nœuds enfants suivants du nœud **SalesOrderDetails**, cliquez sur le menu déroulant en regard du nœud et sélectionnez **Aucun** :  
  
    -   **SalesOrderID**  
  
    -   **SalesOrderDetailID**  
  
    -   **rowguid**  
  
    -   **ModifiedDate**  
  
     Cette action empêche Visual Studio d'inclure ces données dans le contrôle <xref:System.Windows.Controls.DataGrid> que vous allez créer à l'étape suivante.  Pour cette procédure pas à pas, on suppose que l'utilisateur final n'a pas besoin de voir ces données.  
  
4.  De la fenêtre **Sources de données**, faites glisser le nœud **SalesOrderDetails** enfant vers la fenêtre du **Concepteur WPF**.  
  
     Visual Studio génère du code XAML pour définir un nouveau contrôle <xref:System.Windows.Controls.DataGrid> lié aux données et le contrôle s'affiche dans le concepteur.  Visual Studio met également à jour la méthode `GetSalesOrderHeadersQuery` générée dans le fichier code\-behind pour inclure les données dans l'entité **SalesOrderDetails**.  
  
## Test de l'application  
 Générez et exécutez l'application pour vérifier qu'elle affiche les enregistrements de commandes.  
  
#### Pour tester l'application  
  
1.  Appuyez sur **F5**.  
  
     L'application est générée et exécutée.  Vérifiez les points suivants :  
  
    -   La zone de liste déroulante **Réf. commande client** affiche **71774**.  Il s'agit de la première référence de commande dans l'entité.  
  
    -   Pour chaque commande que vous sélectionnez dans la zone de liste déroulante **Réf. commande client**, des informations de commande détaillées sont affichées dans la <xref:System.Windows.Controls.DataGrid>.  
  
2.  Fermez l'application.  
  
## Étapes suivantes  
 Après avoir suivi cette procédure pas à pas, apprenez comment utiliser la fenêtre **Sources de données** dans Visual Studio pour lier des contrôles WPF à d'autres types de sources de données.  Pour plus d'informations, consultez [Procédure pas à pas : liaisons de contrôles WPF à un service de données WCF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md) et [Procédure pas à pas : liaison de contrôles WPF avec un groupe de données](../data-tools/bind-wpf-controls-to-a-dataset.md).  
  
## Voir aussi  
 [Liaison de contrôles WPF avec des données dans Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)   
 [Comment : afficher des données connexes dans des applications WPF](../data-tools/display-related-data-in-wpf-applications.md)