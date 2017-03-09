---
title: "Proc&#233;dure pas &#224; pas&#160;: cr&#233;ation d&#39;un TableAdapter avec plusieurs requ&#234;tes | Microsoft Docs"
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
  - "données (Visual Studio), TableAdapters"
  - "données (Visual Studio), procédures pas à pas"
  - "requêtes (Visual Studio), TableAdapters"
  - "requêtes TableAdapter, créer"
  - "TableAdapters, créer"
ms.assetid: f784dc4d-d514-4ade-8226-f8271c5b1ed8
caps.latest.revision: 18
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Proc&#233;dure pas &#224; pas&#160;: cr&#233;ation d&#39;un TableAdapter avec plusieurs requ&#234;tes
Dans cette procédure pas à pas, vous allez créer un TableAdapter dans un dataset à l'aide de l'[Configuration de source de données \(Assistant\)](../data-tools/media/data-source-configuration-wizard.png).  La procédure pas à pas vous guide dans la création d'une deuxième requête dans le [TableAdapter](../data-tools/tableadapter-overview.md) à l'aide de l'[Configuration de requête TableAdapter \(Assistant\)](../data-tools/editing-tableadapters.md) dans le [Concepteur de DataSet](../data-tools/creating-and-editing-typed-datasets.md).  
  
 Cette procédure pas à pas décrit notamment les tâches suivantes :  
  
-   Création d'un projet d'**application Windows**.  
  
-   Création et configuration d'une source de données dans votre application en générant un dataset avec l'**Assistant Configuration de source de données**.  
  
-   Ouverture du nouveau dataset dans le **Concepteur de DataSet**.  
  
-   Ajout de requêtes au TableAdapter avec l'**Assistant Configuration de requêtes TableAdapter**.  
  
## Composants requis  
 Pour exécuter cette procédure pas à pas, vous avez besoin des éléments suivants :  
  
-   Accès à l'exemple de base de données Northwind \(vers SQL Server ou Access\).  Pour plus d'informations, consultez [Comment : installer des exemples de bases de données](../data-tools/how-to-install-sample-databases.md).  
  
## Création d'une application Windows  
 La première étape consiste à créer une Application Windows.  
  
#### Pour créer le projet d'application Windows  
  
1.  Dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], dans le menu **Fichier**, créez un projet.  
  
2.  Choisissez un langage de programmation dans le volet **Types de projet**.  
  
3.  Cliquez sur **Application Windows** dans le volet **Modèles**.  
  
4.  Attribuez le nom `TableAdapterQueriesWalkthrough`, puis cliquez sur **OK**.  
  
     Visual Studio ajoute le projet l'**Explorateur de solutions** et affiche un nouveau formulaire dans le concepteur.  
  
## Création d'une source de données de base de données avec un TableAdapter  
 Cette étape permet de créer une source de données à l'aide de l'**Assistant Configuration de source de données** basée sur la table `Customers` de l'exemple de base de données Northwind.  Vous devez avoir accès à l'exemple de base de données Northwind pour créer la connexion.  Pour plus d'informations sur la configuration de l'exemple de base de données Northwind, consultez [Comment : installer des exemples de bases de données](../data-tools/how-to-install-sample-databases.md).  
  
#### Pour créer la source de données  
  
1.  Dans le menu **Données**, cliquez sur **Afficher les sources de données**.  
  
2.  Dans la fenêtre **Sources de données**, sélectionnez **Ajouter une nouvelle source de données** pour démarrer l'**Assistant Configuration de source de données**.  
  
3.  Sélectionnez **Base de données** dans la page **Choisir un type de source de données**, puis cliquez sur **Suivant**.  
  
4.  Dans la page **Choisir votre connexion de données**, effectuez l'une des opérations suivantes :  
  
    -   Si une connexion de données à l'exemple de base de données Northwind est disponible dans la liste déroulante, sélectionnez\-la.  
  
         ou  
  
    -   Sélectionnez **Nouvelle connexion** pour afficher la boîte de dialogue **Ajouter\/Modifier la connexion**.  
  
5.  Si votre base de données requiert un mot de passe, sélectionnez l'option pour inclure les données sensibles, puis cliquez sur **Suivant**.  
  
6.  Cliquez sur **Suivant** dans la page **Enregistrer la chaîne de connexion dans le fichier de configuration de l'application**.  
  
7.  Développez le nœud **Tables** dans la page **Choisir vos objets de base de données**.  
  
8.  Sélectionnez la table **Customers**, puis cliquez sur **Terminer**.  
  
     **NorthwindDataSet** est ajouté à votre projet et la table **Customers** apparaît dans la fenêtre **Sources de données**.  
  
## Ouverture du dataset dans le Concepteur de DataSet  
  
#### Pour ouvrir le dataset dans le Concepteur de DataSet  
  
1.  Cliquez avec le bouton droit sur **NorthwindDataset** dans la fenêtre **Sources de données**.  
  
2.  Dans le menu contextuel, choisissez **Modifier le DataSet à l'aide du concepteur**.  
  
     NorthwindDataset s'ouvre dans le **Concepteur de DataSet**.  
  
## Ajout d'une deuxième requête au CustomersTableAdapter  
 L'Assistant a créé le dataset avec une table de données **Customers** et **CustomersTableAdapter**.  Cette section de la procédure pas à pas ajoute une deuxième requête au **CustomersTableAdapter**.  
  
#### Pour ajouter une deuxième requête au CustomersTableAdapter  
  
1.  Faites glisser une **Requête** depuis l'onglet **DataSet** de la **Boîte à outils** vers la table **Customers**.  
  
     L'[Configuration de requête TableAdapter \(Assistant\)](../data-tools/editing-tableadapters.md) s'ouvre.  
  
2.  Sélectionnez **Utiliser des instructions SQL**, puis cliquez sur **Suivant**.  
  
3.  Sélectionnez **SELECT qui retourne des lignes**, puis cliquez sur **Suivant**.  
  
4.  Ajoutez une clause WHERE à la requête pour obtenir ce qui suit :  
  
    ```  
    SELECT CustomerID, CompanyName, ContactName, ContactTitle, Address, City, Region, PostalCode, Country, Phone, Fax   
    FROM Customers   
    WHERE City = @City  
    ```  
  
    > [!NOTE]
    >  Si vous utilisez la version Access de Northwind, remplacez le paramètre @City par un point d'interrogation.  \(`SELECT CustomerID, CompanyName, ContactName, ContactTitle, Address, City, Region, PostalCode, Country, Phone, Fax FROM Customers WHERE City = ?`\)  
  
5.  Dans la page **Choisir les méthodes à générer**, attribuez à la méthode **Remplir un DataTable** le nom `FillByCity`.  
  
    > [!NOTE]
    >  La méthode permettant de **Retourner un DataTable** n'est pas utilisée dans cette procédure pas à pas, vous pouvez donc décocher la case ou laisser le nom par défaut.  
  
6.  Cliquez sur **Suivant** pour terminer l'Assistant.  
  
     La requête **FillByCity** est ajoutée au **CustomersTableAdapter**.  
  
## Ajout de code pour exécuter la requête supplémentaire dans le formulaire  
  
#### Pour exécuter la requête  
  
1.  Sélectionnez **Form1** dans l'**Explorateur de solutions** et cliquez sur **Concepteur de vues**.  
  
2.  Faites glisser le nœud **Customers** depuis la fenêtre **Sources de données** vers **Form1**.  
  
3.  Passez au mode Code en sélectionnant **Code** dans le menu **Afficher**.  
  
4.  Remplacez le code dans le gestionnaire d'événements `Form1_Load` par ce qui suit pour exécuter la requête `FillByCity`.  
  
     [!CODE [VbRaddataTableAdapters#1](../CodeSnippet/VS_Snippets_VBCSharp/VbRaddataTableAdapters#1)]  
  
## Exécution de l'application  
  
#### Pour exécuter l'application  
  
-   Appuyez sur F5.  
  
-   La grille est remplie avec les clients dont la valeur `City` est `Seattle`.  
  
## Étapes suivantes  
  
### Pour ajouter une fonctionnalité à votre application  
  
-   Ajoutez des contrôles <xref:System.Windows.Forms.TextBox> et <xref:System.Windows.Forms.Button>, et passez la valeur de la zone de texte à la requête.  \(`CustomersTableAdapter.FillByCity(NorthwindDataSet.Customers, TextBox1.Text)`\).  
  
-   Ajoutez une logique de validation à l'événement <xref:System.Data.DataTable.ColumnChanging> ou <xref:System.Data.DataTable.RowChanging> des tables de données du dataset.  Pour plus d'informations, consultez [Validation de données dans des groupes de données](../data-tools/validate-data-in-datasets.md).  
  
## Voir aussi  
 [Vue d'ensemble de TableAdapter](../data-tools/tableadapter-overview.md)   
 [Comment : créer des TableAdapters](../data-tools/create-and-configure-tableadapters.md)   
 [Comment : créer des requêtes TableAdapter](../data-tools/how-to-create-tableadapter-queries.md)   
 [Procédures pas à pas relatives aux données](../Topic/Data%20Walkthroughs.md)   
 [Connexion aux données dans Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Préparation de votre application pour recevoir des données](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Extraction de données dans votre application](../data-tools/fetching-data-into-your-application.md)   
 [Liaison de contrôles à des données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modification des données dans votre application](../data-tools/editing-data-in-your-application.md)