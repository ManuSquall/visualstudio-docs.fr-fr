---
title: "Proc&#233;dure pas &#224; pas&#160;: gestion d&#39;une exception d&#39;acc&#232;s concurrentiel | Microsoft Docs"
ms.custom: ""
ms.date: "09/21/2016"
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
  - "contrôle d'accès concurrentiel, exceptions"
  - "contrôle d'accès concurrentiel, procédures pas à pas"
  - "accès concurrentiel aux données, procédures pas à pas"
  - "groupes de données (Visual Basic), erreurs"
  - "gestion des exceptions, problèmes de simultanéité"
  - "mise à jour de groupes de données, erreurs"
ms.assetid: 73ee9759-0a90-48a9-bf7b-9d6fc17bff93
caps.latest.revision: 23
caps.handback.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Proc&#233;dure pas &#224; pas&#160;: gestion d&#39;une exception d&#39;acc&#232;s concurrentiel
Des exceptions d'accès concurrentiel \(<xref:System.Data.DBConcurrencyException>\) sont levées lorsque deux utilisateurs tentent de modifier simultanément les mêmes données dans une base de données.  Dans le cadre de cette procédure pas à pas, vous allez créer une application Windows qui illustre l'interception d'une exception <xref:System.Data.DBConcurrencyException>, la recherche de la ligne ayant provoqué l'erreur et le choix d'une stratégie pour la traiter.  
  
 Cette procédure pas à pas vous guide au sein du processus suivant :  
  
1.  Créez un nouveau projet **Application Windows**.  
  
2.  Créez un nouveau groupe de données basé sur la table `Customers` Northwind.  
  
3.  Créez un formulaire avec un <xref:System.Windows.Forms.DataGridView> pour afficher les données.  
  
4.  Remplissez un groupe de données avec les données provenant de la table `Customers` de la base de données Northwind.  
  
5.  Une fois le groupe de données rempli, utilisez [Visual Database Tools](http://msdn.microsoft.com/fr-fr/6b145922-2f00-47db-befc-bf351b4809a1) dans Visual Studio pour accéder directement à la table de données `Customers` et modifier un enregistrement.  
  
6.  Ensuite, modifiez la valeur de cet enregistrement sur le formulaire, mettez à jour le groupe de données et essayez d'enregistrer les modifications dans la base de données, ce qui entraîne le déclenchement d'une erreur d'accès concurrentiel.  
  
7.  Détectez l'erreur, puis affichez les différentes versions de l'enregistrement, permettant ainsi à l'utilisateur de déterminer s'il doit continuer à mettre à jour la base de données ou annuler la mise à jour.  
  
## Composants requis  
 Pour exécuter cette procédure pas à pas, vous devez :  
  
-   avoir accès à l'exemple de base de données Northwind avec l'autorisation d'effectuer des mises à jour.  Pour plus d'informations, consultez [Comment : installer des exemples de bases de données](../data-tools/how-to-install-sample-databases.md).  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Création d'un projet  
 La première étape de la procédure consiste à créer une nouvelle application Windows.  
  
#### Pour créer un projet d'application Windows  
  
1.  Dans le menu **Fichier**, créez un nouveau projet.  
  
2.  Sélectionnez un langage de programmation dans le volet **Types de projets**.  
  
3.  Sélectionnez **Application Windows** dans le volet **Modèles**.  
  
4.  Nommez le projet `ConcurrencyWalkthrough`, puis cliquez sur **OK**.  
  
     Visual Studio ajoute le projet à l'**Explorateur de solutions** et affiche un nouveau formulaire dans le concepteur.  
  
## Création du groupe de données Northwind  
 Dans cette section, vous allez créer un groupe de données nommé `NorthwindDataSet`.  
  
#### Pour créer NorthwindDataSet  
  
1.  Dans le menu **Données**, choisissez **Ajouter une nouvelle source de données**.  
  
     L'[Configuration de source de données \(Assistant\)](../data-tools/media/data-source-configuration-wizard.png) s'ouvre.  
  
2.  Sélectionnez **Base de données** dans la page **Choisir un type de source de données**.  
  
3.  Sélectionnez une connexion à l'exemple de base de données Northwind dans la liste des connexions disponibles, ou cliquez sur **Nouvelle connexion** si la connexion ne figure pas dans la liste.  
  
    > [!NOTE]
    >  Si vous vous connectez à un fichier de base de données local, sélectionnez **Non** lorsque vous êtes invité à spécifier si vous souhaitez ajouter le fichier à votre projet.  
  
4.  Cliquez sur **Suivant** dans la page **Enregistrer la chaîne de connexion dans le fichier de configuration de l'application**.  
  
5.  Développez le nœud **Tables** et sélectionnez la table `Customers`.  Le nom par défaut du groupe de données doit être `NorthwindDataSet`.  
  
6.  Cliquez sur **Terminer** pour ajouter le groupe de données au projet.  
  
## Création d'un contrôle DataGridView lié aux données  
 Dans cette section, vous créerez un <xref:System.Windows.Forms.DataGridView> en faisant glisser l'élément **Customers** depuis la fenêtre **Sources de données** jusqu'à votre Windows Form.  
  
#### Créer un contrôle DataGridView lié à la table Customers  
  
1.  Dans le menu **Données**, choisissez **Afficher les sources de données** pour ouvrir la fenêtre **Sources de données**.  
  
2.  Dans la fenêtre **Sources de données**, développez le nœud **NorthwindDataSet** et sélectionnez la table **Customers**.  
  
3.  Cliquez sur la flèche vers le bas du nœud de la table et sélectionnez **DataGridView** dans la liste déroulante.  
  
4.  Faites glisser la table sur une zone vide de votre formulaire.  
  
     Un contrôle <xref:System.Windows.Forms.DataGridView> nommé `CustomersDataGridView` et un <xref:System.Windows.Forms.BindingNavigator> nommé `CustomersBindingNavigator` sont ajoutés au formulaire lié au <xref:System.Windows.Forms.BindingSource> qui est lui\-même lié à la table `Customers` contenue dans le `NorthwindDataSet`.  
  
## Point de contrôle  
 Vous pouvez à présent tester le formulaire afin de vous assurer qu'il se comporte comme prévu jusqu'à ce point.  
  
#### Pour tester le formulaire  
  
1.  Appuyez sur F5 pour exécuter l'application.  
  
     Le formulaire s'affiche avec un contrôle <xref:System.Windows.Forms.DataGridView> rempli des données de la table `Customers`.  
  
2.  Dans le menu **Déboguer**, choisissez **Arrêter le débogage**.  
  
## Gestion des erreurs d'accès concurrentiel  
 La façon dont vous gérez les erreurs dépend des règles spécifiques à votre entreprise, qui gèrent votre application.  Dans le cadre de cette procédure pas à pas, après déclenchement d'une violation d'accès concurrentiel, la stratégie suivante est utilisée pour illustrer la gestion de l'erreur d'accès concurrentiel :  
  
 L'application présentera à l'utilisateur trois versions de l'enregistrement :  
  
-   L'enregistrement en cours dans la base de données.  
  
-   L'enregistrement d'origine chargé dans le groupe de données.  
  
-   Les modifications proposées dans le groupe de données.  
  
 L'utilisateur peut alors remplacer la base de données par la version proposée ou annuler la mise à jour et l'actualisation du groupe de données avec les nouvelles valeurs de la base de données.  
  
#### Pour activer la gestion des erreurs d'accès concurrentiel  
  
1.  Créez un gestionnaire d'erreurs personnalisé.  
  
2.  Affichez des choix pour l'utilisateur.  
  
3.  Traitez la réponse de l'utilisateur.  
  
4.  Renvoyez la mise à jour ou réinitialisez les données dans le groupe de données.  
  
### Ajout du code permettant de gérer l'exception d'accès concurrentiel  
 Si une exception est levée lorsque vous essayez d'exécuter une mise à jour, vous souhaiterez généralement vous servir des informations qu'elle fournit.  
  
 Dans cette section, vous ajouterez le code qui tentera de mettre à jour la base de données et de gérer toute exception <xref:System.Data.DBConcurrencyException> susceptible d'être levée, ainsi que toute autre exception.  
  
> [!NOTE]
>  Les méthodes `CreateMessage` et `ProcessDialogResults` seront ajoutées à une étape ultérieure de cette procédure.  
  
##### Pour ajouter la gestion des erreurs pour l'erreur d'accès concurrentiel  
  
1.  Ajoutez le code suivant sous la méthode `Form1_Load`:  
  
     [!code-cs[VbRaddataConcurrency#1](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_1.cs)]
     [!code-vb[VbRaddataConcurrency#1](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_1.vb)]  
  
2.  Remplacez la méthode `CustomersBindingNavigatorSaveItem_Click` pour appeler la méthode `UpdateDatabase` pour obtenir le code suivant :  
  
     [!code-cs[VbRaddataConcurrency#2](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_2.cs)]
     [!code-vb[VbRaddataConcurrency#2](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_2.vb)]  
  
### Affichage des choix pour l'utilisateur  
 Le code que vous venez de taper appelle la procédure `CreateMessage` qui va afficher les informations sur l'erreur pour l'utilisateur.  Dans cette procédure, vous utiliserez une boîte de message pour afficher les différentes versions de l'enregistrement pour l'utilisateur et lui permettre de choisir entre le remplacement de l'enregistrement avec les modifications et l'annulation des modifications.  Lorsque l'utilisateur sélectionne une option \(clique sur un bouton\) dans la boîte de message, la réponse est passée à la méthode `ProcessDialogResult`.  
  
##### Pour créer le message à afficher pour l'utilisateur  
  
-   Créez le message en ajoutant le code ci\-dessous dans l'**éditeur de code**.  Entrez ce code sous la méthode `UpdateDatabase`.  
  
     [!code-cs[VbRaddataConcurrency#4](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_3.cs)]
     [!code-vb[VbRaddataConcurrency#4](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_3.vb)]  
  
### Traitement de la réponse de l'utilisateur  
 Vous devrez également ajouter du code pour le traitement de la réponse de l'utilisateur à la boîte de message.  Vous pouvez choisir de remplacer l'enregistrement actuel dans la base de données par la modification proposée ou d'abandonner les modifications locales et actualiser la table de données avec l'enregistrement qui se trouve actuellement dans la base de données.  Si l'utilisateur choisit Oui, la méthode <xref:System.Data.DataTable.Merge%2A> est appelée avec l'argument *preserveChanges* à la valeur `true`.  La mise à jour fonctionnera alors correctement, car la version d'origine de l'enregistrement correspond désormais à l'enregistrement contenu dans la base de données.  
  
##### Pour traiter la réponse de l'utilisateur à la boîte de message  
  
-   Ajoutez le code suivant sous le code ajouté à la section précédente.  
  
     [!code-cs[VbRaddataConcurrency#3](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_4.cs)]
     [!code-vb[VbRaddataConcurrency#3](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_4.vb)]  
  
## Test  
 Vous pouvez à présent tester le formulaire afin de vous assurer qu'il se comporte comme prévu.  Pour simuler une violation de l'accès concurrentiel, vous devez modifier les données dans la base de données après avoir rempli le NorthwindDataSet.  
  
#### Pour tester le formulaire  
  
1.  Appuyez sur la touche F5 pour exécuter l’application.  
  
2.  Une fois le formulaire affiché, laissez\-le s'exécuter et basculez vers l'environnement IDE Visual Studio.  
  
3.  Dans le menu **Affichage**, choisissez **Explorateur de serveurs**.  
  
4.  Dans l'**Explorateur de serveurs**, développez la connexion que votre application utilise, puis développez le nœud **Tables**.  
  
5.  Cliquez avec le bouton droit sur la table **Customers** et sélectionnez **Afficher les données de la table**.  
  
6.  Dans le premier enregistrement \(`ALFKI`\), remplacez `ContactName` par `Maria Anders2`.  
  
    > [!NOTE]
    >  Naviguez vers une autre ligne pour valider la modification.  
  
7.  Basculez vers le formulaire en cours d'exécution de `ConcurrencyWalkthrough`.  
  
8.  Dans le premier enregistrement du formulaire \(`ALFKI`\), remplacez `ContactName` par `Maria Anders1`.  
  
9. Cliquez sur le bouton **Enregistrer**.  
  
     L'erreur d'accès concurrentiel est déclenchée et la boîte de message apparaît.  
  
10. Cliquez sur **Non** pour annuler la mise à jour et mettre à jour le groupe de données avec les valeurs actuellement contenues dans la base de données, ou cliquez sur **Oui** pour écrire la valeur proposée dans la base de données.  
  
## Voir aussi  
 [Procédures pas à pas relatives aux données](../Topic/Data%20Walkthroughs.md)   
 [Liaison de contrôles Windows Forms à des données dans Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Connexion aux données dans Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Préparation de votre application pour recevoir des données](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Extraction de données dans votre application](../data-tools/fetching-data-into-your-application.md)   
 [Liaison de contrôles à des données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modification des données dans votre application](../data-tools/editing-data-in-your-application.md)   
 [Validation des données](../Topic/Validating%20Data.md)   
 [Enregistrement des données](../data-tools/saving-data.md)