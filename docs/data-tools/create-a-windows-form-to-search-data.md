---
title: "Proc&#233;dure pas &#224; pas&#160;: cr&#233;ation d&#39;un Windows Form pour rechercher des donn&#233;es | Microsoft Docs"
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
  - "données (Visual Studio), paramétrer les requêtes"
  - "données (Visual Studio), rechercher"
  - "paramètres, afficher les données filtrées"
  - "Windows Forms, afficher les données"
  - "Windows Forms, rechercher les données"
ms.assetid: 65ca79a9-7458-466c-af55-978cd24c549e
caps.latest.revision: 28
caps.handback.revision: 25
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Proc&#233;dure pas &#224; pas&#160;: cr&#233;ation d&#39;un Windows Form pour rechercher des donn&#233;es
Un scénario d'application courant consiste à afficher les données sélectionnées dans un formulaire.  Par exemple, supposons que vous souhaitiez afficher les commandes d'un client spécifique ou les détails d'une commande spécifique.  Dans ce scénario, un utilisateur entre des informations dans un formulaire, puis une requête est exécutée prenant l'entrée de l'utilisateur comme paramètre. C'est\-à\-dire que les données sont sélectionnées selon une requête paramétrable.  La requête retourne uniquement les données répondant aux critères entrés par l'utilisateur.  Cette procédure pas à pas indique comment créer une requête retournant les clients d'une ville spécifique et modifier l'interface utilisateur de sorte que les utilisateurs puissent entrer un nom de ville et appuyer sur un bouton pour exécuter la requête.  
  
 L'utilisation des requêtes paramétrables renforce l'efficacité de votre application en utilisant la base de données de la meilleure manière possible : pour filtrer rapidement des enregistrements.  À l'inverse, si vous interrogez une table de base de données entière, que vous la transférer sur le réseau et que vous utilisez la logique d'application pour trouver les enregistrements souhaités, votre application peut devenir lente et perdre en efficacité.  
  
 Vous pouvez ajouter des requêtes paramétrables à n'importe quel TableAdapter \(et aux contrôles permettant d'accepter les valeurs de paramètre et d'exécuter la requête\) à l'aide de la [Générateur de critères de recherche, boîte de dialogue](../Topic/Search%20Criteria%20Builder%20Dialog%20Box.md).  Ouvrez la boîte de dialogue en sélectionnant la commande **Ajouter une requête** dans le menu **Données** \(ou dans n'importe quelle balise active de TableAdapter\).  
  
 Cette procédure pas à pas décrit notamment les tâches suivantes :  
  
-   Création d'un projet d'**application Windows**.  
  
-   Création et configuration d'une source de données dans votre application à l'aide de l'[Configuration de source de données \(Assistant\)](../data-tools/media/data-source-configuration-wizard.png).  
  
-   Définition du type de déplacement des éléments dans la [Sources de données \(fenêtre\)](../Topic/Data%20Sources%20Window.md).  Pour plus d'informations, consultez [Définir le contrôle à créer lors d’une opération de glisser\-déplacer à partir de la fenêtre Sources de données](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
-   Création de contrôles affichant les données en faisant glisser des éléments depuis la fenêtre **Sources de données** vers un formulaire.  
  
-   Ajout de contrôles pour afficher les données dans le formulaire.  
  
-   Utilisation de la [Générateur de critères de recherche, boîte de dialogue](../Topic/Search%20Criteria%20Builder%20Dialog%20Box.md).  
  
-   Entrée de paramètres dans le formulaire et exécution de la requête paramétrable.  
  
## Composants requis  
 Pour exécuter cette procédure pas à pas, vous avez besoin des éléments suivants :  
  
-   avoir accès à l'exemple de base de données Northwind.  Pour plus d'informations, consultez [Comment : installer des exemples de bases de données](../data-tools/how-to-install-sample-databases.md).  
  
## Création de l'application Windows  
 La première étape consiste à créer une **application Windows**.  L'attribution d'un nom au projet est facultative à ce stade, mais nous allons lui en donner un car nous avons l'intention de l'enregistrer ultérieurement.  
  
#### Pour créer le projet d'application Windows  
  
1.  Dans le menu **Fichier**, créez un nouveau projet.  
  
2.  Attribuez le nom `WindowsSearchForm` au projet.  
  
3.  Sélectionnez **Application Windows** et cliquez sur **OK**.  Pour plus d'informations, consultez [Applications clientes](../Topic/Developing%20Client%20Applications%20with%20the%20.NET%20Framework.md).  
  
     Le projet **WindowsSearchForm** est créé et ajouté à l'**Explorateur de solutions**.  
  
## Création de la source de données  
 Cette étape crée une source de données à partir d'une base de données à l'aide de l'**Assistant Configuration de source de données**.  Vous devez avoir accès à l'exemple de base de données Northwind pour créer la connexion.  Pour plus d'informations sur la configuration de l'exemple de base de données Northwind, consultez [Comment : installer des exemples de bases de données](../data-tools/how-to-install-sample-databases.md).  
  
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
  
## Création du formulaire  
 Pour créer des contrôles liés aux données, vous pouvez faire glisser des éléments depuis la fenêtre **Sources de données** vers votre formulaire.  
  
#### Pour créer des contrôlés liés aux données dans le formulaire  
  
1.  Développez le nœud **Customers** dans la fenêtre **Sources de données**.  
  
2.  Faites glisser le nœud **Customers** depuis la fenêtre **Sources de données** vers votre formulaire.  
  
     Un <xref:System.Windows.Forms.DataGridView> et une barre d'outils \(<xref:System.Windows.Forms.BindingNavigator>\) pour parcourir les enregistrements apparaissent sur le formulaire.  [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), [CustomersTableAdapter](../data-tools/tableadapter-overview.md), <xref:System.Windows.Forms.BindingSource> et <xref:System.Windows.Forms.BindingNavigator> s'affichent dans la barre d'état des composants.  
  
## Ajout du paramétrage \(fonctionnalité de recherche\) à la requête  
 Vous pouvez ajouter une clause WHERE à la requête d'origine à l'aide de la [Générateur de critères de recherche, boîte de dialogue](../Topic/Search%20Criteria%20Builder%20Dialog%20Box.md).  
  
#### Pour créer une requête paramétrable et des contrôles pour entrer les paramètres  
  
1.  Sélectionnez le contrôle <xref:System.Windows.Forms.DataGridView>, puis choisissez **Ajouter une requête** dans le menu **Données**.  
  
2.  Tapez `FillByCity` dans la zone **Nom de la nouvelle requête** de la [Générateur de critères de recherche, boîte de dialogue](../Topic/Search%20Criteria%20Builder%20Dialog%20Box.md).  
  
3.  Ajoutez `WHERE City = @City` à la requête dans la zone **Texte de la requête**.  
  
     La requête doit ressembler à la suivante :  
  
     `SELECT CustomerID, CompanyName, ContactName, ContactTitle, Address, City, Region, PostalCode, Country, Phone, Fax`  
  
     `FROM Customers`  
  
     `WHERE City = @City`  
  
    > [!NOTE]
    >  Les sources de données Access et OleDb utilisent le point d'interrogation « ? » pour désigner des paramètres, la clause WHERE sera donc de type : `WHERE City = ?`.  
  
4.  Cliquez sur **OK** pour fermer la boîte de dialogue **Générateur de critères de recherche**.  
  
     Un **FillByCityToolStrip** est ajouté au formulaire.  
  
## Test de l'application  
 L'exécution de l'application ouvre votre formulaire prêt à utiliser le paramètre comme entrée.  
  
#### Pour tester l'application  
  
1.  Appuyez sur F5 pour exécuter l'application.  
  
2.  Tapez London dans la zone de texte **City**, puis cliquez sur **FillByCity**.  
  
     La grille de données est remplie avec les clients correspondant aux critères du paramétrage.  Dans cet exemple, la grille de données n'affiche que les clients possédant une valeur **London** dans leur colonne **City**.  
  
## Étapes suivantes  
 Selon les spécifications de votre application, vous pouvez exécuter différentes étapes après la création d'un formulaire paramétrable.  Vous pouvez apporter à cette procédure pas à pas les améliorations suivantes :  
  
-   Ajout de contrôles affichant les données associées.  Pour plus d'informations, consultez [Comment : afficher des données connexes dans une application Windows Forms](../Topic/How%20to:%20Display%20Related%20Data%20in%20a%20Windows%20Forms%20Application.md).  
  
-   Modification du dataset pour ajouter ou supprimer des objets de base de données.  Pour plus d'informations, consultez [Comment : modifier un groupe de données](../Topic/How%20to:%20Edit%20a%20Dataset.md).  
  
## Voir aussi  
 [Procédures pas à pas relatives aux données](../Topic/Data%20Walkthroughs.md)   
 [Liaison de contrôles Windows Forms à des données dans Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Vue d'ensemble des sources de données](../data-tools/add-new-data-sources.md)   
 [Vue d'ensemble de TableAdapter](../data-tools/tableadapter-overview.md)   
 [Vue d'ensemble du composant BindingSource](../Topic/BindingSource%20Component%20Overview.md)   
 [Vue d'ensemble du contrôle BindingNavigator](../Topic/BindingNavigator%20Control%20Overview%20\(Windows%20Forms\).md)