---
title: "Proc&#233;dure pas &#224; pas&#160;: cr&#233;ation d&#39;un contr&#244;le utilisateur Windows Forms prenant en charge la liaison de donn&#233;es de recherche | Microsoft Docs"
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
  - "liaison de données, contrôles utilisateur"
  - "LookupBindingPropertiesAttribute (classe), exemples"
  - "contrôles utilisateur (Visual Basic), créer"
ms.assetid: c48b4d75-ccfc-4950-8b14-ff8adbfe4208
caps.latest.revision: 14
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Proc&#233;dure pas &#224; pas&#160;: cr&#233;ation d&#39;un contr&#244;le utilisateur Windows Forms prenant en charge la liaison de donn&#233;es de recherche
Pour afficher des données dans des formulaires Windows, vous pouvez choisir des contrôles existants dans la Boîte à outils ou créer des contrôles personnalisés si votre application requiert des fonctionnalités qui ne sont pas disponibles dans les contrôles standard.  Cette procédure pas à pas vous indique comment créer un contrôle qui implémente l'objet <xref:System.ComponentModel.LookupBindingPropertiesAttribute>.  Les contrôles qui implémentent <xref:System.ComponentModel.LookupBindingPropertiesAttribute> peuvent contenir trois propriétés pouvant être liées aux données.  Ce type de contrôles est similaire à <xref:System.Windows.Forms.ComboBox>.  
  
 Pour plus d'informations sur la création de contrôles, consultez [Développement de contrôles Windows Forms au moment du design](../Topic/Developing%20Windows%20Forms%20Controls%20at%20Design%20Time.md).  
  
 Quand vous créez des contrôles utilisables dans des scénarios de liaison de données, vous devez implémenter l'un des attributs Databinding suivants :  
  
|Utilisation de l'attribut Databinding|  
|-------------------------------------------|  
|Implémentez <xref:System.ComponentModel.DefaultBindingPropertyAttribute> sur des contrôles simples, comme <xref:System.Windows.Forms.TextBox>, qui affichent une seule colonne \(ou propriété\) de données.  Pour plus d'informations, consultez [Procédure pas à pas : création d'un contrôle utilisateur Windows Forms prenant en charge la liaison de données simple](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).|  
|Implémentez <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> sur des contrôles, comme <xref:System.Windows.Forms.DataGridView>, qui affichent des listes \(ou tables\) de données.  Pour plus d'informations, consultez [Procédure pas à pas : création d'un contrôle utilisateur Windows Forms prenant en charge la liaison de données complexe](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md).|  
|Implémentez <xref:System.ComponentModel.LookupBindingPropertiesAttribute> sur des contrôles, comme <xref:System.Windows.Forms.ComboBox>, qui affichent des listes \(ou tables\) de données, mais doivent également présenter une seule colonne ou propriété.  \(Ce processus est décrit dans cette page de procédure pas à pas.\)|  
  
 Cette procédure pas à pas crée un contrôle de recherche qui effectue une liaison vers les données de deux tables.  Cet exemple utilise les tables `Customers` et `Orders` de l'exemple de base de données Northwind.  Le contrôle de recherche sera lié au champ `CustomerID` de la table `Orders`.  Il utilisera cette valeur pour rechercher le `CompanyName` dans la table `Customers`.  
  
 Pendant cette procédure pas à pas, vous allez apprendre à :  
  
-   Créer une **application Windows**.  
  
-   Ajouter un nouveau **Contrôle utilisateur** à votre projet.  
  
-   Concevoir visuellement le contrôle utilisateur.  
  
-   Implémenter l'attribut `LookupBindingProperty`.  
  
-   Créer un dataset à l'aide de l'[Configuration de source de données \(Assistant\)](../data-tools/media/data-source-configuration-wizard.png).  
  
-   Définir la colonne **CustomerID** de la table **Orders** dans la fenêtre **Sources de données** pour qu'elle utilise le nouveau contrôle.  
  
-   Créer un formulaire pour afficher des données dans le nouveau contrôle.  
  
## Composants requis  
 Pour exécuter cette procédure pas à pas, vous avez besoin des éléments suivants :  
  
-   avoir accès à l'exemple de base de données Northwind.  Pour plus d'informations, consultez [Comment : installer des exemples de bases de données](../data-tools/how-to-install-sample-databases.md).  
  
## Création d'une application Windows  
 La première étape consiste à créer une **application Windows**.  
  
#### Pour créer un projet Windows  
  
1.  Dans Visual Studio, dans le menu **Fichier**, créez un **Projet**.  
  
2.  Attribuez le nom LookupControlWalkthrough au projet.  
  
3.  Sélectionnez **Application Windows** et cliquez sur **OK**.  Pour plus d'informations, consultez [Applications clientes](../Topic/Developing%20Client%20Applications%20with%20the%20.NET%20Framework.md).  
  
     Le projet **LookupControlWalkthrough** est créé et ajouté à l'**Explorateur de solutions**.  
  
## Ajout d'un contrôle utilisateur au projet  
 Cette procédure pas à pas crée un contrôle de recherche à partir d'un **Contrôle utilisateur**, vous devez donc ajouter un élément **Contrôle utilisateur** au projet **LookupControlWalkthrough**.  
  
#### Pour ajouter un contrôle utilisateur au projet  
  
1.  Dans le menu **Projet**, choisissez **Ajouter un contrôle utilisateur**.  
  
2.  Tapez `LookupBox` dans la zone **Nom**, puis cliquez sur **Ajouter**.  
  
     Le contrôle **LookupBox** est ajouté à l'**Explorateur de solutions** et s'ouvre dans le concepteur.  
  
## Conception du contrôle LookupBox  
  
#### Pour concevoir le contrôle LookupBox  
  
-   Faites glisser un <xref:System.Windows.Forms.ComboBox> depuis la **Boîte à outils** vers l'aire de conception du contrôle utilisateur.  
  
## Ajout de l'attribut Databinding requis  
 Pour des contrôles de recherche prenant en charge la liaison de données, vous pouvez implémenter l'attribut<xref:System.ComponentModel.LookupBindingPropertiesAttribute>.  
  
#### Pour implémenter l'attribut LookupBindingProperties  
  
1.  Basculez le contrôle **LookupBox** sur le mode Code.  \(Dans le menu **Affichage**, choisissez **Code**.\)  
  
2.  Remplacez le code de `LookupBox` par le code suivant :  
  
     [!code-vb[VbRaddataDisplaying#5](../data-tools/codesnippet/VisualBasic/create-a-windows-forms-user-control-that-supports-lookup-data-binding_1.vb)]
     [!code-cs[VbRaddataDisplaying#5](../data-tools/codesnippet/CSharp/create-a-windows-forms-user-control-that-supports-lookup-data-binding_1.cs)]  
  
3.  Dans le menu **Générer**, cliquez sur **Générer la solution**.  
  
## Création d'une source de données à partir de votre base de données  
 Cette étape crée une source de données à l'aide de l'**Assistant Configuration de source de données** basée sur les tables `Customers` et `Orders` de l'exemple de base de données Northwind.  Vous devez avoir accès à l'exemple de base de données Northwind pour créer la connexion.  Pour plus d'informations sur la configuration de l'exemple de base de données Northwind, consultez [Comment : installer des exemples de bases de données](../data-tools/how-to-install-sample-databases.md).  
  
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
  
8.  Sélectionnez les tables `Customers` et `Orders`, puis cliquez sur **Terminer**.  
  
     **NorthwindDataSet** est ajouté à votre projet et les tables `Customers` et `Orders` apparaissent dans la fenêtre **Sources de données**.  
  
## Définition de la colonne CustomerID de la table Orders pour qu'elle utilise le contrôle LookupBox  
 Dans la fenêtre **Sources de données**, vous pouvez définir le contrôle à créer avant de faire glisser des éléments vers votre formulaire.  
  
#### Pour définir la colonne CustomerID pour qu'elle soit liée au contrôle LookupBox  
  
1.  Ouvrez **Form1** dans le concepteur.  
  
2.  Développez le nœud **Customers** dans la fenêtre **Sources de données**.  
  
3.  Développez le nœud **Orders** \(inclus dans le nœud **Customers** sous la colonne **Fax**\).  
  
4.  Cliquez sur la flèche déroulante du nœud **Orders** et choisissez **Détails** dans la liste de contrôles.  
  
5.  Cliquez sur la flèche déroulante de la colonne **CustomerID** \(dans le nœud **Orders**\) et choisissez **Personnaliser**.  
  
6.  Sélectionnez **LookupBox** dans la liste des **Contrôles associés** de la boîte de dialogue **Options de personnalisation de l'interface utilisateur du formulaire de données**.  
  
7.  Cliquez sur **OK**.  
  
8.  Cliquez sur la flèche déroulante de la colonne **CustomerID** et choisissez **LookupBox**.  
  
## Ajout de contrôles au formulaire  
 Pour créer des contrôles liés aux données, vous pouvez faire glisser des éléments depuis la fenêtre **Sources de données** vers **Form1**.  
  
#### Pour créer des contrôles liés aux données dans le formulaire Windows  
  
-   Faites glisser le nœud **Orders** de la fenêtre **Sources de données** vers le formulaire Windows et vérifiez que le contrôle **LookupBox** est utilisé pour afficher les données dans la colonne `CustomerID`.  
  
## Liaison du contrôle pour rechercher le CompanyName à partir de la table Customers  
  
#### Pour configurer les liaisons de recherche  
  
-   Sélectionnez le nœud **Customers** principal dans la fenêtre **Sources de données** et faites\-le glisser vers la zone de liste déroulante de **CustomerIDLookupBox** dans **Form1**.  
  
     Cela configure la liaison des données pour afficher le `CompanyName` dans la table `Customers` tout en conservant la valeur `CustomerID` dans la table `Orders`.  Pour plus d'informations, consultez [Comment : créer des tables de correspondance dans des applications Windows Forms](../data-tools/create-lookup-tables-in-windows-forms-applications.md).  
  
## Exécution de l'application  
  
#### Pour exécuter l'application  
  
-   Appuyez sur F5 pour exécuter l'application.  
  
-   Parcourez quelques enregistrements et vérifiez que le `CompanyName` apparaît dans le contrôle `LookupBox`.  
  
## Voir aussi  
 [Définir le contrôle à créer lors d’une opération de glisser\-déplacer à partir de la fenêtre Sources de données](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)   
 [Liaison de contrôles Windows Forms à des données dans Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Connexion aux données dans Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Préparation de votre application pour recevoir des données](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Extraction de données dans votre application](../data-tools/fetching-data-into-your-application.md)   
 [Liaison de contrôles à des données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modification des données dans votre application](../data-tools/editing-data-in-your-application.md)   
 [Validation des données](../Topic/Validating%20Data.md)   
 [Enregistrement des données](../data-tools/saving-data.md)