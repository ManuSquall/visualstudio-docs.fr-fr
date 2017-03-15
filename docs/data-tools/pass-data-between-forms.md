---
title: "Proc&#233;dure pas &#224; pas&#160;: passage de donn&#233;es entre Windows Forms | Microsoft Docs"
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
  - "données (Visual Studio), passer entre les formulaires"
  - "formulaires, passer des données entre"
  - "procédures pas à pas (Visual Studio), données"
  - "procédures pas à pas (Windows Forms), données"
  - "Windows Forms, procédures pas à pas"
ms.assetid: 78bf038b-9296-4fbf-b0e8-d881d1aff0df
caps.latest.revision: 14
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Proc&#233;dure pas &#224; pas&#160;: passage de donn&#233;es entre Windows Forms
Cette procédure pas à pas fournit des instructions détaillées pour passer des données d'un formulaire à l'autre.  L'utilisation des tables de clients et de commandes d'un formulaire de Northwind va permettre aux utilisateurs de sélectionner un client et d'afficher ses commandes dans un deuxième formulaire.  Cette procédure pas à pas indique comment créer une méthode sur un formulaire recevant des données d'un premier formulaire.  
  
> [!NOTE]
>  Cette procédure pas à pas n'indique qu'un seul moyen de passer les données entre formulaires.  Il existe d'autres options pour passer des données à un formulaire, parmi lesquelles : créer un deuxième constructeur pour recevoir les données ou créer une propriété publique pouvant être définie à l'aide des données du premier formulaire.  
  
 Cette procédure pas à pas décrit notamment les tâches suivantes :  
  
-   Création d'un projet d'**application Windows**.  
  
-   Création et configuration d'un dataset à l'aide de l'[Configuration de source de données \(Assistant\)](../data-tools/media/data-source-configuration-wizard.png).  
  
-   Sélection du contrôle à créer dans le formulaire pendant le déplacement d'éléments depuis la fenêtre **Sources de données**.  Pour plus d'informations, consultez [Définir le contrôle à créer lors d’une opération de glisser\-déplacer à partir de la fenêtre Sources de données](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
-   Création de contrôles liés aux données en faisant glisser des éléments depuis la fenêtre **Sources de données** vers un formulaire.  
  
-   Création d'un deuxième formulaire avec une grille pour afficher les données.  
  
-   Création d'une requête TableAdapter pour extraire les commandes d'un client spécifique.  
  
-   Transfert de données entre formulaires.  
  
## Composants requis  
 Pour exécuter cette procédure pas à pas, vous avez besoin des éléments suivants :  
  
-   avoir accès à l'exemple de base de données Northwind.  Pour plus d'informations, consultez [Comment : installer des exemples de bases de données](../data-tools/how-to-install-sample-databases.md).  
  
## Création de l'application Windows  
  
#### Pour créer un projet Windows  
  
1.  Dans le menu **Fichier**, créez un nouveau projet.  
  
2.  Attribuez le nom `PassingDataBetweenForms` au projet.  
  
3.  Sélectionnez **Application Windows Forms** et cliquez sur **OK**.  Pour plus d'informations, consultez [Applications clientes](../Topic/Developing%20Client%20Applications%20with%20the%20.NET%20Framework.md).  
  
     Le projet **PassingDataBetweenForms** est créé et ajouté à l'**Explorateur de solutions**.  
  
## Création de la source de données  
  
#### Pour créer la source de données  
  
1.  Dans le menu **Données**, cliquez sur **Afficher les sources de données**.  
  
2.  Dans la fenêtre **Sources de données**, sélectionnez **Ajouter une nouvelle source de données** pour démarrer l'**Assistant Configuration de source de données**.  
  
3.  Sélectionnez **Base de données** dans la page **Choisir un type de source de données**, puis cliquez sur **Suivant**.  
  
4.  Dans la page **Choisir un modèle de base de données**, vérifiez que **Dataset** est spécifié, puis cliquez sur **Suivant**.  
  
5.  Dans la page **Choisir votre connexion de données**, effectuez l'une des opérations suivantes :  
  
    -   Si une connexion de données à l'exemple de base de données Northwind est disponible dans la liste déroulante, sélectionnez\-la.  
  
         ou  
  
    -   Sélectionnez **Nouvelle connexion** pour afficher la boîte de dialogue **Ajouter\/Modifier la connexion**.  
  
6.  Si votre base de données requiert un mot de passe et si l'option permettant d'inclure les données sensibles est activée, sélectionnez l'option, puis cliquez sur **Suivant**.  
  
7.  Cliquez sur **Suivant** dans la page **Enregistrer la chaîne de connexion dans le fichier de configuration de l'application**.  
  
8.  Développez le nœud **Tables** dans la page **Choisir vos objets de base de données**.  
  
9. Sélectionnez les tables **Customers** et **Orders**, puis cliquez sur **Terminer**.  
  
     **NorthwindDataSet** est ajouté à votre projet et les tables **Customers** et Orders apparaissent dans la fenêtre **Sources de données**.  
  
## Création du premier formulaire \(Form1\)  
 Vous pouvez créer une grille liée aux données \(un contrôle <xref:System.Windows.Forms.DataGridView>\) en faisant glisser le nœud **Customers** depuis la fenêtre **Sources de données** vers le formulaire.  
  
#### Pour créer une grille liée aux données dans le formulaire  
  
-   Faites glisser le nœud **Customers** principal depuis la fenêtre **Sources de données** vers **Form1**.  
  
     Un <xref:System.Windows.Forms.DataGridView> et une barre d'outils \(<xref:System.Windows.Forms.BindingNavigator>\) pour parcourir les enregistrements apparaissent sur **Form1**.  [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), [CustomersTableAdapter](../data-tools/tableadapter-overview.md), <xref:System.Windows.Forms.BindingSource> et <xref:System.Windows.Forms.BindingNavigator> s'affichent dans la barre d'état des composants.  
  
## Création du deuxième formulaire \(Form2\)  
  
#### Pour créer un deuxième formulaire auquel passer les données  
  
1.  Dans le menu **Projet**, choisissez **Ajouter un formulaire Windows**.  
  
2.  Laissez le nom par défaut \(**Form2**\) et cliquez sur **Ajouter**.  
  
3.  Faites glisser le nœud **Orders** principal depuis la fenêtre **Sources de données** vers **Form2**.  
  
     Un <xref:System.Windows.Forms.DataGridView> et une barre d'outils \(<xref:System.Windows.Forms.BindingNavigator>\) pour parcourir les enregistrements apparaissent sur **Form2**.  [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), [CustomersTableAdapter](../data-tools/tableadapter-overview.md), <xref:System.Windows.Forms.BindingSource> et <xref:System.Windows.Forms.BindingNavigator> s'affichent dans la barre d'état des composants.  
  
4.  Supprimez **OrdersBindingNavigator** de la barre d'état des composants.  
  
     **OrdersBindingNavigator** disparaît de **Form2**.  
  
## Ajout d'une requête TableAdapter à Form2 pour charger les commandes du client sélectionné dans Form1  
  
#### Pour créer une requête TableAdapter  
  
1.  Double\-cliquez sur le fichier **NorthwindDataSet.xsd** dans l'**Explorateur de solutions**.  
  
2.  Cliquez avec le bouton droit sur **OrdersTableAdapter** et sélectionnez **Ajouter une requête**.  
  
3.  Laissez l'option par défaut \(**Utiliser des instructions SQL**\), puis cliquez sur **Suivant**.  
  
4.  Laissez l'option par défaut \(**SELECT qui retourne des lignes**\), puis cliquez sur **Suivant**.  
  
5.  Ajoutez une clause WHERE à la requête pour retourner `Orders` en fonction de `CustomerID`.  La requête doit ressembler à la suivante :  
  
    ```  
    SELECT OrderID, CustomerID, EmployeeID, OrderDate, RequiredDate, ShippedDate, ShipVia, Freight, ShipName, ShipAddress, ShipCity, ShipRegion, ShipPostalCode, ShipCountry  
    FROM Orders   
    WHERE CustomerID = @CustomerID  
    ```  
  
    > [!NOTE]
    >  Vérifiez que la syntaxe du paramètre est correcte pour votre base de données.  Par exemple, dans Microsoft Access, la clause WHERE est de type : `WHERE CustomerID = ?`.  
  
6.  Cliquez sur **Suivant**.  
  
7.  Pour le **Nom de la méthode Remplir un DataTable**, tapez `FillByCustomerID`.  
  
8.  Désactivez l'option **Retourner un DataTable**, puis cliquez sur **Suivant**.  
  
9. Cliquez sur **Terminer**.  
  
## Création d'une méthode sur Form2 pour y passer les données  
  
#### Pour créer une méthode pour y passer les données  
  
1.  Cliquez avec le bouton droit sur **Form2** et sélectionnez **Afficher le code** pour ouvrir **Form2** dans l'**Éditeur de texte**.  
  
2.  Ajoutez le code suivant à **Form2** après la méthode `Form2_Load` :  
  
     [!code-vb[VbRaddataDisplaying#1](../data-tools/codesnippet/VisualBasic/pass-data-between-forms_1.vb)]
     [!code-cs[VbRaddataDisplaying#1](../data-tools/codesnippet/CSharp/pass-data-between-forms_1.cs)]  
  
## Création d'une méthode sur Form1 pour passer les données et afficher Form2  
  
#### Pour créer une méthode pour passer les données à Form2  
  
1.  Dans **Form1**, cliquez avec le bouton droit sur la grille de données Customer, puis cliquez sur **Propriétés**.  
  
2.  Dans la fenêtre **Propriétés**, cliquez sur **Événements**.  
  
3.  Double\-cliquez sur l'événement **CellDoubleClick**.  
  
     L'éditeur de code apparaît.  
  
4.  Mettez à jour la définition de la méthode pour qu'elle corresponde à l'exemple suivant :  
  
     [!code-cs[VbRaddataDisplaying#2](../data-tools/codesnippet/CSharp/pass-data-between-forms_2.cs)]
     [!code-vb[VbRaddataDisplaying#2](../data-tools/codesnippet/VisualBasic/pass-data-between-forms_2.vb)]  
  
## Exécution de l'application  
  
#### Pour exécuter l'application  
  
-   Appuyez sur F5 pour exécuter l'application.  
  
-   Double\-cliquez sur un enregistrement client dans **Form1** pour ouvrir **Form2** avec les commandes de ce client.  
  
## Étapes suivantes  
 Selon les spécifications de votre application, vous pouvez exécuter différentes étapes après le transfert de données entre formulaires.  Vous pouvez apporter à cette procédure pas à pas les améliorations suivantes :  
  
-   Modification du dataset pour ajouter ou supprimer des objets de base de données.  Pour plus d'informations, consultez [Comment : modifier un groupe de données](../Topic/How%20to:%20Edit%20a%20Dataset.md).  
  
-   Ajout d'une fonctionnalité pour enregistrer des données dans la base de données.  Pour plus d'informations, consultez [Comment : enregistrer les modifications apportées à un groupe de données dans une base de données](../Topic/How%20to:%20Save%20Dataset%20Changes%20to%20a%20Database.md).  
  
## Voir aussi  
 [Procédures pas à pas relatives aux données](../Topic/Data%20Walkthroughs.md)   
 [Liaison de contrôles Windows Forms à des données dans Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Vue d'ensemble des sources de données](../data-tools/add-new-data-sources.md)   
 [Vue d'ensemble de TableAdapter](../data-tools/tableadapter-overview.md)   
 [Connexion aux données dans Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Préparation de votre application pour recevoir des données](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Extraction de données dans votre application](../data-tools/fetching-data-into-your-application.md)   
 [Liaison de contrôles à des données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modification des données dans votre application](../data-tools/editing-data-in-your-application.md)   
 [Validation des données](../Topic/Validating%20Data.md)   
 [Enregistrement des données](../data-tools/saving-data.md)