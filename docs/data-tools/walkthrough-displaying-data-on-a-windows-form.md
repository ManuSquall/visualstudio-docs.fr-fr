---
title: "Proc&#233;dure pas &#224; pas&#160;: affichage de donn&#233;es sur un Windows Form | Microsoft Docs"
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
  - "données (Visual Studio), afficher sur les Windows Forms"
  - "liaison de données, Windows Forms"
  - "afficher des données sur des formulaires, procédures pas à pas"
  - "formulaires, afficher les données"
  - "applications Windows, afficher les données"
  - "Windows Forms, afficher les données"
ms.assetid: f6e08c2c-c792-43de-adf3-3e52c0100225
caps.latest.revision: 20
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Proc&#233;dure pas &#224; pas&#160;: affichage de donn&#233;es sur un Windows Form
L'un des scénarios les plus courants dans le développement d'application consiste à afficher des données dans un formulaire d'une application Windows.  Vous pouvez afficher des données dans un formulaire en faisant glisser des éléments depuis la [Sources de données \(fenêtre\)](../Topic/Data%20Sources%20Window.md) vers le formulaire.  Cette procédure pas à pas crée un formulaire simple qui affiche les données d'une seule table dans plusieurs contrôles individuels.  Cet exemple utilise la table `Customers` de l'exemple de base de données Northwind.  
  
 Cette procédure pas à pas décrit notamment les tâches suivantes :  
  
-   Création d'un projet d'**application Windows**.  
  
-   Création et configuration d'un dataset à l'aide de l'[Configuration de source de données \(Assistant\)](../data-tools/media/data-source-configuration-wizard.png).  
  
-   Sélection du contrôle à créer dans le formulaire pendant le déplacement d'éléments depuis la fenêtre **Sources de données**.  Pour plus d'informations, consultez [Définir le contrôle à créer lors d’une opération de glisser\-déplacer à partir de la fenêtre Sources de données](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
-   Création d'un contrôle lié aux données en faisant glisser des éléments depuis la fenêtre **Sources de données** vers votre formulaire.  
  
## Composants requis  
 Pour exécuter cette procédure pas à pas, vous avez besoin des éléments suivants :  
  
-   avoir accès à l'exemple de base de données Northwind.  Pour plus d'informations, consultez [Comment : installer des exemples de bases de données](../data-tools/how-to-install-sample-databases.md).  
  
## Création de l'application Windows  
 La première étape consiste à créer un projet d'**application Windows**.  
  
#### Pour créer le projet d'application Windows  
  
1.  Dans le menu **Fichier**, créez un nouveau projet.  
  
2.  Attribuez le nom `DisplayingDataonaWindowsForm` au projet.  
  
3.  Sélectionnez **Application Windows** et cliquez sur **OK**.  Pour plus d'informations, consultez [Applications clientes](../Topic/Developing%20Client%20Applications%20with%20the%20.NET%20Framework.md).  
  
     Le projet **DisplayingDataonaWindowsForm** est créé et ajouté à l'**Explorateur de solutions**.  
  
## Création de la source de données  
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
  
## Définition des contrôles à créer  
 Pour cette procédure pas à pas, les données de la table sont présentées dans une vue **Détails** où les données sont affichées dans des contrôles individuels.  \(L'autre approche est la vue **Grille** par défaut où les données sont affichées dans un contrôle <xref:System.Windows.Forms.DataGridView>.\)  
  
#### Pour définir le type de déplacement des éléments de la fenêtre Sources de données  
  
1.  Développez le nœud **Customers** dans la fenêtre **Sources de données**.  
  
2.  Remplacez le type de déplacement de la table **Customers** par **Détails** en sélectionnant **Détails** dans la liste déroulante du nœud **Customers**.  Pour plus d'informations, consultez [Définir le contrôle à créer lors d’une opération de glisser\-déplacer à partir de la fenêtre Sources de données](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
3.  Remplacez le type de déplacement de la colonne **CustomerID** par une étiquette en sélectionnant **Étiquette** dans la liste de contrôles du nœud **CustomerID**.  
  
## Création du formulaire  
 Créez les contrôles liés aux données en faisant glisser des éléments depuis la fenêtre **Sources de données** vers votre formulaire.  
  
#### Pour créer des contrôlés liés aux données dans le formulaire  
  
-   Faites glisser le nœud **Customers** principal depuis la fenêtre **Sources de données** vers le formulaire.  
  
     Les contrôles liés aux données assortis d'étiquettes descriptives apparaissent dans le formulaire, ainsi qu'une barre d'outils \(<xref:System.Windows.Forms.BindingNavigator>\) pour parcourir les enregistrements.  [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), [CustomersTableAdapter](../data-tools/tableadapter-overview.md), <xref:System.Windows.Forms.BindingSource> et <xref:System.Windows.Forms.BindingNavigator> s'affichent dans la barre d'état des composants.  
  
## Test de l'application  
  
#### Pour exécuter l'application  
  
-   Appuyez sur F5.  
  
-   Parcourez les enregistrements à l'aide du contrôle <xref:System.Windows.Forms.BindingNavigator>.  
  
## Étapes suivantes  
 Selon les spécifications de votre application, vous pouvez exécuter différentes étapes après la création d'un formulaire Windows lié aux données.  Vous pouvez apporter à cette procédure pas à pas les améliorations suivantes :  
  
-   Ajout d'une fonctionnalité de recherche au formulaire.  Pour plus d'informations, consultez [Comment : ajouter une requête paramétrable à une application Windows Forms](../Topic/How%20to:%20Add%20a%20Parameterized%20Query%20to%20a%20Windows%20Forms%20Application.md).  
  
-   Ajoutez une fonctionnalité pour renvoyer des mises à jour à la base de données.  Pour plus d'informations, consultez [Procédure pas à pas : enregistrement de données dans une base de données \(table unique\)](../Topic/Walkthrough:%20Saving%20Data%20to%20a%20Database%20\(Single%20Table\).md).  
  
-   Ajout de la table `Orders` au dataset en sélectionnant **Configurer le DataSet à l'aide de l'Assistant** dans la fenêtre **Sources de données**.  Ensuite, vous pouvez ajouter des contrôles affichant les données associées en faisant glisser le nœud **Orders** \(celui qui se trouve sous la colonne **Fax** dans la table **Customers**\) vers le formulaire.  Pour plus d'informations, consultez [Comment : afficher des données connexes dans une application Windows Forms](../Topic/How%20to:%20Display%20Related%20Data%20in%20a%20Windows%20Forms%20Application.md).  
  
## Voir aussi  
 [Procédures pas à pas relatives aux données](../Topic/Data%20Walkthroughs.md)   
 [Liaison de contrôles Windows Forms à des données dans Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Vue d'ensemble des sources de données](../data-tools/add-new-data-sources.md)   
 [Vue d'ensemble de TableAdapter](../data-tools/tableadapter-overview.md)