---
title: "Proc&#233;dure pas &#224; pas&#160;: cr&#233;ation d&#39;un contr&#244;le utilisateur Windows Forms prenant en charge la liaison de donn&#233;es simple | Microsoft Docs"
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
  - "contrôles personnalisés (Visual Studio), Sources de données (fenêtre)"
  - "Sources de données (fenêtre), contrôles"
ms.assetid: b1488366-6dfb-454e-9751-f42fd3f3ddfb
caps.latest.revision: 14
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Proc&#233;dure pas &#224; pas&#160;: cr&#233;ation d&#39;un contr&#244;le utilisateur Windows Forms prenant en charge la liaison de donn&#233;es simple
Pour présenter des données dans des formulaires d'applications Windows, vous pouvez choisir des contrôles existants dans la **Boîte à outils** ou créer des contrôles personnalisés si votre application requiert des fonctionnalités qui ne sont pas disponibles dans les contrôles standard.  Cette procédure pas à pas vous indique comment créer un contrôle qui implémente l'objet <xref:System.ComponentModel.DefaultBindingPropertyAttribute>.  Les contrôles qui implémentent <xref:System.ComponentModel.DefaultBindingPropertyAttribute> peuvent contenir une propriété pouvant être liée aux données.  Ce type de contrôles est similaire à <xref:System.Windows.Forms.TextBox> ou <xref:System.Windows.Forms.CheckBox>.  
  
 Pour plus d'informations sur la création de contrôles, consultez [Développement de contrôles Windows Forms au moment du design](../Topic/Developing%20Windows%20Forms%20Controls%20at%20Design%20Time.md).  
  
 Quand vous créez des contrôles utilisables dans des scénarios de liaison de données, vous devez implémenter l'un des attributs Databinding suivants :  
  
|Utilisation de l'attribut Databinding|  
|-------------------------------------------|  
|Implémentez <xref:System.ComponentModel.DefaultBindingPropertyAttribute> sur des contrôles simples, comme <xref:System.Windows.Forms.TextBox>, qui affichent une seule colonne \(ou propriété\) de données.  \(Ce processus est décrit dans cette page de procédure pas à pas.\)|  
|Implémentez <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> sur des contrôles, comme <xref:System.Windows.Forms.DataGridView>, qui affichent des listes \(ou tables\) de données.  Pour plus d'informations, consultez [Procédure pas à pas : création d'un contrôle utilisateur Windows Forms prenant en charge la liaison de données complexe](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md).|  
|Implémentez l'objet <xref:System.ComponentModel.LookupBindingPropertiesAttribute> sur des contrôles, comme <xref:System.Windows.Forms.ComboBox>, qui affichent des listes \(ou tables\) de données, mais doivent également présenter une seule colonne ou propriété.  Pour plus d'informations, consultez [Procédure pas à pas : création d'un contrôle utilisateur Windows Forms prenant en charge la liaison de données de recherche](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).|  
  
 Cette procédure pas à pas crée un contrôle simple qui affiche les données d'une seule colonne dans une table.  Cet exemple utilise la colonne `Phone` de la table `Customers` de l'exemple de base de données Northwind.  Le contrôle utilisateur simple affiche les numéros de téléphone des clients dans un format de numéro de téléphone standard à l'aide d'un <xref:System.Windows.Forms.MaskedTextBox> et en définissant le masque sur un numéro de téléphone.  
  
 Pendant cette procédure pas à pas, vous allez apprendre à :  
  
-   Créer une **application Windows**.  
  
-   Ajouter un nouveau **Contrôle utilisateur** à votre projet.  
  
-   Concevoir visuellement le contrôle utilisateur.  
  
-   Implémenter l'attribut `DefaultBindingProperty`.  
  
-   Créer un dataset à l'aide de l'[Configuration de source de données \(Assistant\)](../data-tools/media/data-source-configuration-wizard.png).  
  
-   Définir la colonne **Phone** dans la fenêtre **Sources de données** pour qu'elle utilise le nouveau contrôle.  
  
-   Créer un formulaire pour afficher des données dans le nouveau contrôle.  
  
## Composants requis  
 Pour exécuter cette procédure pas à pas, vous avez besoin des éléments suivants :  
  
-   avoir accès à l'exemple de base de données Northwind.  Pour plus d'informations, consultez [Comment : installer des exemples de bases de données](../data-tools/how-to-install-sample-databases.md).  
  
## Création d'une application Windows  
 La première étape consiste à créer une **application Windows**.  
  
#### Pour créer un projet Windows  
  
1.  Dans Visual Studio, dans le menu **Fichier**, créez un **Projet**.  
  
2.  Attribuez le nom **SimpleControlWalkthrough** au projet.  
  
3.  Sélectionnez **Application Windows** et cliquez sur **OK**.  Pour plus d'informations, consultez [Applications clientes](../Topic/Developing%20Client%20Applications%20with%20the%20.NET%20Framework.md).  
  
     Le projet **SimpleControlWalkthrough** est créé et ajouté à l'**Explorateur de solutions**.  
  
## Ajout d'un contrôle utilisateur au projet  
 Cette procédure pas à pas crée un contrôle simple pouvant être lié aux données à partir d'un **Contrôle utilisateur**, vous devez donc ajouter un élément **Contrôle utilisateur** au projet **SimpleControlWalkthrough**.  
  
#### Pour ajouter un contrôle utilisateur au projet  
  
1.  Dans le menu **Projet**, choisissez **Ajouter un contrôle utilisateur**.  
  
2.  Tapez `PhoneNumberBox` dans la zone Nom, puis cliquez sur **Ajouter**.  
  
     Le contrôle **PhoneNumberBox** est ajouté à l'**Explorateur de solutions** et s'ouvre dans le concepteur.  
  
## Conception du contrôle PhoneNumberBox  
 Cette procédure pas à pas s'appuie sur le <xref:System.Windows.Forms.MaskedTextBox> existant pour créer le contrôle `PhoneNumberBox`.  
  
#### Pour concevoir le contrôle PhoneNumberBox  
  
1.  Faites glisser un <xref:System.Windows.Forms.MaskedTextBox> depuis la **Boîte à outils** vers l'aire de conception du contrôle utilisateur.  
  
2.  Sélectionnez la balise active du <xref:System.Windows.Forms.MaskedTextBox> que vous venez de faire glisser et choisissez **Définir le masque**.  
  
3.  Sélectionnez **Numéro de téléphone** dans la boîte de dialogue **Masque de saisie** et cliquez sur **OK** pour définir le masque.  
  
## Ajout de l'attribut Databinding requis  
 Pour des contrôles simples prenant en charge la liaison de données, implémentez l'attribut <xref:System.ComponentModel.DefaultBindingPropertyAttribute>.  
  
#### Pour implémenter l'attribut DefaultBindingProperty  
  
1.  Basculez le contrôle `PhoneNumberBox` sur le mode Code.  \(Dans le menu **Affichage**, choisissez **Code**.\)  
  
2.  Remplacez le code de `PhoneNumberBox` par le code suivant :  
  
     [!code-cs[VbRaddataDisplaying#3](../data-tools/codesnippet/CSharp/create-a-windows-forms-user-control-that-supports-simple-data-binding_1.cs)]
     [!code-vb[VbRaddataDisplaying#3](../data-tools/codesnippet/VisualBasic/create-a-windows-forms-user-control-that-supports-simple-data-binding_1.vb)]  
  
3.  Dans le menu **Générer**, cliquez sur **Générer la solution**.  
  
## Création d'une source de données à partir de votre base de données  
 Cette étape utilise l'**Assistant Configuration de source de données** pour créer une source de données basée sur la table `Customers` de l'exemple de base de données Northwind.  Vous devez avoir accès à l'exemple de base de données Northwind pour créer la connexion.  Pour plus d'informations sur la configuration de l'exemple de base de données Northwind, consultez [Comment : installer des exemples de bases de données](../data-tools/how-to-install-sample-databases.md).  
  
#### Pour créer la source de données  
  
1.  Dans le menu **Données**, cliquez sur **Afficher les sources de données**.  
  
2.  Dans la fenêtre **Sources de données**, sélectionnez **Ajouter une nouvelle source de données** pour démarrer l'**Assistant Configuration de source de données**.  
  
3.  Sélectionnez **Base de données** dans la page **Choisir un type de source de données**, puis cliquez sur **Suivant**.  
  
4.  Dans la page **Choisir votre connexion de données**, effectuez l'une des opérations suivantes :  
  
    -   Si une connexion de données à l'exemple de base de données Northwind est disponible dans la liste déroulante, sélectionnez\-la.  
  
         Ou  
  
    -   Sélectionnez **Nouvelle connexion** pour afficher la boîte de dialogue **Ajouter\/Modifier la connexion**.  
  
5.  Si votre base de données requiert un mot de passe, sélectionnez l'option pour inclure les données sensibles, puis cliquez sur **Suivant**.  
  
6.  Cliquez sur **Suivant** dans la page **Enregistrer la chaîne de connexion dans le fichier de configuration de l'application**.  
  
7.  Développez le nœud **Tables** dans la page **Choisir vos objets de base de données**.  
  
8.  Sélectionnez la table `Customers`, puis cliquez sur **Terminer**.  
  
     **NorthwindDataSet** est ajouté à votre projet et la table `Customers` apparaît dans la fenêtre **Sources de données**.  
  
## Définition de la colonne Phone pour qu'elle utilise le contrôle PhoneNumberBox  
 Dans la fenêtre **Sources de données**, vous pouvez définir le contrôle à créer avant de faire glisser des éléments vers votre formulaire.  
  
#### Pour définir la colonne Phone pour qu'elle soit liée au contrôle PhoneNumberBox  
  
1.  Ouvrez **Form1** dans le concepteur.  
  
2.  Développez le nœud **Customers** dans la fenêtre **Sources de données**.  
  
3.  Cliquez sur la flèche déroulante du nœud **Customers** et choisissez **Détails** dans la liste de contrôles.  
  
4.  Cliquez sur la flèche déroulante de la colonne **Phone** et choisissez **Personnaliser**.  
  
5.  Sélectionnez **PhoneNumberBox** dans la liste des **Contrôles associés** de la boîte de dialogue **Options de personnalisation de l'interface utilisateur du formulaire de données**.  
  
6.  Cliquez sur la flèche déroulante de la colonne **Phone** et choisissez **PhoneNumberBox**.  
  
## Ajout de contrôles au formulaire  
 Pour créer des contrôles liés aux données, vous pouvez faire glisser des éléments depuis la fenêtre **Sources de données** vers le formulaire.  
  
#### Pour créer des contrôlés liés aux données dans le formulaire  
  
-   Faites glisser le nœud **Customers** principal depuis la fenêtre **Sources de données** vers le formulaire et vérifiez que le contrôle `PhoneNumberBox` est utilisé pour afficher les données dans la colonne `Phone`.  
  
     Les contrôles liés aux données assortis d'étiquettes descriptives apparaissent dans le formulaire, ainsi qu'une barre d'outils \(<xref:System.Windows.Forms.BindingNavigator>\) pour parcourir les enregistrements.  [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), [CustomersTableAdapter](../data-tools/tableadapter-overview.md), <xref:System.Windows.Forms.BindingSource> et <xref:System.Windows.Forms.BindingNavigator> s'affichent dans la barre d'état des composants.  
  
## Exécution de l'application  
  
#### Pour exécuter l'application  
  
-   Appuyez sur F5 pour exécuter l'application.  
  
## Étapes suivantes  
 Selon les spécifications de votre application, vous pouvez exécuter différentes étapes après la création d'un contrôle prenant en charge la liaison de données.  Les étapes ultérieures sont habituellement celles\-ci :  
  
-   Positionnement de vos contrôles personnalisés dans une bibliothèque de contrôles pour pouvoir les réutiliser dans d'autres applications.  
  
-   Création de contrôles prenant en charge des scénarios de liaison de données plus complexes.  Pour plus d’informations, consultez [Procédure pas à pas : création d'un contrôle utilisateur Windows Forms prenant en charge la liaison de données complexe](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md) et [Procédure pas à pas : création d'un contrôle utilisateur Windows Forms prenant en charge la liaison de données de recherche](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).  
  
## Voir aussi  
 [Définir le contrôle à créer lors d’une opération de glisser\-déplacer à partir de la fenêtre Sources de données](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)   
 [Liaison de contrôles Windows Forms à des données dans Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Vue d'ensemble d'applications de données dans Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Connexion aux données dans Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Préparation de votre application pour recevoir des données](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Extraction de données dans votre application](../data-tools/fetching-data-into-your-application.md)   
 [Liaison de contrôles à des données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modification des données dans votre application](../data-tools/editing-data-in-your-application.md)   
 [Validation des données](../Topic/Validating%20Data.md)   
 [Enregistrement des données](../data-tools/saving-data.md)