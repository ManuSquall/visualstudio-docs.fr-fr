---
title: "Proc&#233;dure pas &#224; pas&#160;: liaisons de contr&#244;les WPF &#224; un service de donn&#233;es&#160;WCF | Microsoft Docs"
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
ms.assetid: 8823537c-82f0-41f7-bf30-705f0e5e59fd
caps.latest.revision: 40
caps.handback.revision: 38
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Proc&#233;dure pas &#224; pas&#160;: liaisons de contr&#244;les WPF &#224; un service de donn&#233;es&#160;WCF
Dans cette procédure pas à pas, vous allez créer une application WPF qui contient des contrôles liés aux données.  Les contrôles sont liés aux enregistrements client encapsulés dans un [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)].  Vous allez aussi ajouter des boutons utilisables par les clients pour afficher et mettre à jour des enregistrements.  
  
 Cette procédure pas à pas décrit les tâches suivantes :  
  
-   Création d'un Entity Data Model généré à partir des données de l'exemple de base de données AdventureWorksLT.  
  
-   Création d'un [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] exposant les données de l'Entity Data Model à une application WPF.  
  
-   Création d'un ensemble de contrôles liés aux données en faisant glisser des éléments depuis la fenêtre **Sources de données** vers le Concepteur WPF.  
  
-   Création de boutons permettant d'avancer et de reculer dans les enregistrements client.  
  
-   Création d'un bouton permettant d'enregistrer les modifications des données dans les contrôles du [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] et la source de données sous\-jacente.  
  
     [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## Composants requis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]  
  
-   Accès à une instance en cours d'exécution de SQL Server ou SQL Server Express à laquelle est attaché l'exemple de base de données AdventureWorksLT.  Vous pouvez télécharger la base de données AdventureWorksLT à partir du [site web CodePlex](http://go.microsoft.com/fwlink/?linkid=87843).  
  
 La connaissance préalable des concepts suivants s'avère également utile, mais n'est pas obligatoire pour suivre cette procédure pas à pas :  
  
-   Services de données WCF.  Pour plus d'informations, consultez [Vue d'ensemble](../Topic/WCF%20Data%20Services%20Overview.md).  
  
-   Modèles de données dans les [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)].  
  
-   Entity Data Models et ADO.NET Entity Framework.  Pour plus d'informations, consultez [Vue d'ensemble d'Entity Framework](../Topic/Entity%20Framework%20Overview.md).  
  
-   Utilisation du Concepteur WPF.  Pour plus d'informations, consultez [Vue d'ensemble des concepteurs WPF et Silverlight](http://msdn.microsoft.com/fr-fr/570b7a5c-0c86-4326-a371-c9b63378fc62).  
  
-   Liaison de données WPF.  Pour plus d'informations, consultez [Vue d'ensemble de la liaison de données](../Topic/Data%20Binding%20Overview.md).  
  
## Création du projet de service  
 Commencez cette procédure pas à pas par la création d'un projet pour un [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)].  
  
#### Pour créer le projet de service  
  
1.  Démarrez Visual Studio.  
  
2.  Dans le menu **Fichier**, pointez sur **Nouveau**, puis cliquez sur **Projet**.  
  
3.  Développez **Visual C\#** ou **Visual Basic** et choisissez **Web**.  
  
4.  Sélectionnez le modèle de projet **Application web ASP.NET**.  
  
5.  Dans la zone **Nom**, tapez `AdventureWorksService`, puis cliquez sur **OK**.  
  
     Visual Studio crée le projet `AdventureWorksService`.  
  
6.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur **Default.aspx** et sélectionnez **Supprimer**.  Ce fichier n'est pas nécessaire dans cette procédure pas à pas.  
  
## Création d'un Entity Data Model pour le service  
 Pour exposer les données à une application à l'aide d'un [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)], vous devez définir un modèle de données pour le service.  Le [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] prend en charge deux types de modèles de données : Entity Data Model et les modèles de données personnalisés définis à l'aide des objets CLR \(Common Language Runtime\) qui implémentent l'interface <xref:System.Linq.IQueryable%601>.  Dans cette procédure pas à pas, vous allez créer un Entity Data Model comme modèle de données.  
  
#### Pour créer un Entity Data Model  
  
1.  Dans le menu **Projet**, cliquez sur **Ajouter un nouvel élément**.  
  
2.  Dans la liste des modèles installés, cliquez sur **Données**, puis sélectionnez l'élément de projet **ADO.NET Entity Data Model**.  
  
3.  Changez le nom en `AdventureWorksModel.edmx` et cliquez sur **Ajouter**.  
  
     L'**Assistant Entity Data Model** s'ouvre.  
  
4.  Dans la page **Choisissez le contenu du modèle**, cliquez sur **Générer à partir de la base de données**, puis sur **Suivant**.  
  
5.  Dans la page **Choisir votre connexion de données**, sélectionnez l'une des options suivantes :  
  
    -   Si une connexion de données à l'exemple de base de données AdventureWorksLT est disponible dans la liste déroulante, sélectionnez\-la.  
  
         ou  
  
    -   Cliquez sur **Nouvelle connexion** et créez une connexion à la base de données AdventureWorksLT.  
  
6.  Dans la page **Choisir votre connexion de données**, assurez\-vous que l'option **Enregistrer les paramètres de connexion de l'entité dans App.Config en tant que** est sélectionnée puis cliquez sur **Suivant**.  
  
7.  Dans la page **Choisir vos objets de base de données**, développez **Tables**, puis sélectionnez la table **SalesOrderHeader**.  
  
8.  Cliquez sur **Terminer**.  
  
## Création du service  
 Créez un [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] pour exposer les données de l'Entity Data Model à une application WPF.  
  
#### Pour créer le service  
  
1.  Dans le menu **Projet**, sélectionnez **Ajouter un nouvel élément**.  
  
2.  Dans la liste des modèles installés, cliquez sur **Web**, puis sélectionnez l'élément de projet **Service de données WCF**.  
  
3.  Dans la zone **Nom**, tapez `AdventureWorksService.svc` et cliquez sur **Ajouter**.  
  
     Visual Studio ajoute `AdventureWorksService.svc` au projet.  
  
## Configuration du service  
 Vous devez configurer le service pour qu'il fonctionne sur l'Entity Data Model que vous avez créé.  
  
#### Pour configurer le service  
  
1.  Dans le fichier de code `AdventureWorks.svc`, remplacez la déclaration de classe `AdventureWorksService` par le code suivant.  
  
     [!code-cs[Data_WPFWCF#1](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_1.cs)]
     [!code-vb[Data_WPFWCF#1](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_1.vb)]  
  
     Ce code met à jour la classe `AdventureWorksService` de sorte qu'elle dérive d'un <xref:System.Data.Services.DataService%601> qui fonctionne sur la classe du contexte de l'objet `AdventureWorksLTEntities` dans votre Entity Data Model.  Il met également à jour la méthode `InitializeService` pour accorder aux clients du service un accès complet en lecture\/écriture à l'entité `SalesOrderHeader`.  
  
2.  Générez le projet et vérifiez qu'aucune erreur ne se produit.  
  
## Création de l'application cliente WPF  
 Pour afficher les données du [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)], créez une application WPF avec une source de données basée sur le service.  Plus loin dans cette procédure pas à pas, vous allez ajouter à l'application des contrôles liés aux données.  
  
#### Pour créer l'application cliente WPF  
  
1.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur le nœud de la solution, cliquez sur **Ajouter**, puis sélectionnez **Nouveau projet**.  
  
2.  Dans la boîte de dialogue **Nouveau projet**, développez **Visual C\#** ou **Visual Basic**, puis sélectionnez **Windows**.  
  
3.  Sélectionnez le modèle de projet **Application WPF**.  
  
4.  Dans la zone **Nom**, tapez `AdventureWorksSalesEditor`, puis cliquez sur **OK**.  
  
     Visual Studio ajoute le projet `AdventureWorksSalesEditor` à la solution.  
  
5.  Dans le menu **Données**, cliquez sur **Afficher les sources de données**.  
  
     La fenêtre **Sources de données** s'ouvre.  
  
6.  Dans la fenêtre **Sources de données**, cliquez sur **Ajouter une nouvelle source de données**.  
  
     L'**Assistant Configuration de source de données** s'ouvre.  
  
7.  Dans la page **Choisir un type de source de données** de l'Assistant, sélectionnez **Service**, puis cliquez sur **Suivant**.  
  
8.  Dans la boîte de dialogue **Ajouter une référence de service**, cliquez sur **Découvrir**.  
  
     Visual Studio recherche la solution active pour les services disponibles et ajoute `AdventureWorksService.svc` à la liste des services disponibles dans la zone **Services**.  
  
9. Dans la zone **Espace de noms**, tapez `AdventureWorksService`.  
  
10. Dans la zone **Services**, cliquez sur **AdventureWorksService.svc**, puis sur **OK**.  
  
     Visual Studio télécharge les informations de service et revient à l'**Assistant Configuration de source de données**.  
  
11. Dans la boîte de dialogue **Ajouter une référence de service**, cliquez sur **Terminer**.  
  
     Visual Studio ajoute les nœuds représentant les données retournées par le service dans la fenêtre **Sources de données**.  
  
## Définition de l'interface utilisateur de la fenêtre  
 Ajoutez plusieurs boutons à la fenêtre en modifiant le code XAML dans le Concepteur WPF.  Plus loin dans cette procédure pas à pas, vous allez ajouter du code permettant aux utilisateurs d'afficher et de mettre à jour les enregistrements de vente à l'aide de ces boutons.  
  
#### Pour créer la disposition de fenêtre  
  
1.  Dans l'**Explorateur de solutions**, double\-cliquez sur MainWindow.xaml.  
  
     La fenêtre s'ouvre dans le Concepteur WPF.  
  
2.  Dans la vue [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] du concepteur, ajoutez le code suivant entre les balises `<Grid>` :  
  
    ```  
    <Grid.RowDefinitions>  
        <RowDefinition Height="75" />  
        <RowDefinition Height="525" />  
    </Grid.RowDefinitions>  
    <Button HorizontalAlignment="Left" Margin="22,20,0,24" Name="backButton" Width="75"><</Button>  
    <Button HorizontalAlignment="Left" Margin="116,20,0,24" Name="nextButton" Width="75">></Button>  
    <Button HorizontalAlignment="Right" Margin="0,21,46,24" Name="saveButton" Width="110">Save changes</Button>  
    ```  
  
3.  Générez le projet.  
  
## Création des contrôles liés aux données  
 Créez des contrôles affichant les enregistrements client en faisant glisser le nœud `SalesOrderHeaders` de la fenêtre **Sources de données** vers le concepteur.  
  
#### Pour créer des contrôles liés aux données  
  
1.  Dans la fenêtre **Sources de données**, cliquez sur le menu déroulant pour le nœud **SalesOrderHeaders** et sélectionnez **Détails**.  
  
2.  Développez le nœud **SalesOrderHeaders**.  
  
3.  Pour cet exemple, certains champs ne vont pas s'afficher. Cliquez alors sur le menu déroulant situé à côté des nœuds suivants et sélectionnez **Aucun** :  
  
    -   **CreditCardApprovalCode**  
  
    -   **ModifiedDate**  
  
    -   **OnlineOrderFlag**  
  
    -   **RevisionNumber**  
  
    -   **rowguid**  
  
     Cette action empêche Visual Studio de créer des contrôles liés aux données pour ces nœuds à l'étape suivante.  Pour cette procédure pas à pas, il est supposé que l'utilisateur final n'a pas besoin d'afficher ces données.  
  
4.  Dans la fenêtre **Sources de données**, faites glisser le nœud **SalesOrderHeaders** vers la ligne de la grille située en dessous de la ligne contenant les boutons.  
  
     Visual Studio génère du XAML et du code qui créent un ensemble de contrôles liés aux données de la table **Product**.  Pour plus d'informations sur le XAML et le code générés, consultez [Liaison de contrôles WPF avec des données dans Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
5.  Dans le concepteur, cliquez sur la zone de texte à côté de l'étiquette **Customer ID**.  
  
6.  Dans la fenêtre **Propriétés**, cochez la case à côté de la propriété **IsReadOnly**.  
  
7.  Définissez la propriété **IsReadOnly** pour chacune des zones de texte suivantes :  
  
    -   **Purchase Order Number**  
  
    -   **Sales Order ID**  
  
    -   **Sales Order Number**  
  
## Charger les données du service  
 Utilisez l'objet proxy du service pour charger les données de vente à partir du service, puis assignez les données retournées à la source de données pour le <xref:System.Windows.Data.CollectionViewSource> dans la fenêtre WPF.  
  
#### Pour charger les données du service  
  
1.  Dans le concepteur, double\-cliquez sur le texte **MainWindow** pour créer le gestionnaire d'événements `Window_Loaded`.  
  
2.  Remplacez le gestionnaire d'événements par le code suivant.  Assurez\-vous de remplacer l'adresse *localhost* dans ce code par l'adresse de l'hôte local de votre ordinateur de développement.  
  
     [!code-cs[Data_WPFWCF#2](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_2.cs)]
     [!code-vb[Data_WPFWCF#2](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_2.vb)]  
  
## Navigation dans les enregistrements de vente  
 Ajoutez du code permettant aux utilisateurs de parcourir les enregistrements de vente à l'aide des boutons **\<** et **\>**.  
  
#### Pour permettre aux utilisateurs de parcourir les enregistrements de vente  
  
1.  Dans le concepteur, double\-cliquez sur le bouton **\<** de la fenêtre.  
  
     Visual Studio ouvre le fichier code\-behind et crée un gestionnaire d'événements `backButton_Click` pour l'événement <xref:System.Windows.Controls.Primitives.ButtonBase.Click>.  
  
2.  Ajoutez le code suivant au gestionnaire d'événements `backButton_Click` généré :  
  
     [!code-cs[Data_WPFWCF#3](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_3.cs)]
     [!code-vb[Data_WPFWCF#3](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_3.vb)]  
  
3.  Revenez dans le concepteur et double\-cliquez sur le bouton **\>**.  
  
     Visual Studio ouvre le fichier code\-behind et crée un gestionnaire d'événements `nextButton_Click` pour l'événement <xref:System.Windows.Controls.Primitives.ButtonBase.Click>.  
  
4.  Ajoutez le code suivant au gestionnaire d'événements `nextButton_Click` généré :  
  
     [!code-cs[Data_WPFWCF#4](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_4.cs)]
     [!code-vb[Data_WPFWCF#4](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_4.vb)]  
  
## Enregistrement des modifications dans les enregistrements de vente  
 Ajoutez du code permettant aux utilisateurs d'afficher et enregistrer les modifications apportées aux enregistrements de vente à l'aide du bouton **Enregistrer les modifications**.  
  
#### Pour ajouter la possibilité d'enregistrer les modifications apportées aux enregistrements de vente  
  
1.  Dans le concepteur, double\-cliquez sur le bouton **Enregistrer les modifications**.  
  
     Visual Studio ouvre le fichier code\-behind et crée un gestionnaire d'événements `saveButton_Click` pour l'événement <xref:System.Windows.Controls.Primitives.ButtonBase.Click>.  
  
2.  Ajoutez le code ci\-après au gestionnaire d'événements `saveButton_Click`.  
  
     [!code-cs[Data_WPFWCF#5](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_5.cs)]
     [!code-vb[Data_WPFWCF#5](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_5.vb)]  
  
## Test de l'application  
 Générez et exécutez l'application pour vérifier que vous pouvez afficher et mettre à jour les enregistrements client.  
  
#### Pour tester l'application  
  
1.  Dans le menu **Générer**, cliquez sur **Générer la solution**.  Vérifiez que la solution se génère sans erreur.  
  
2.  Appuyez sur **CTRL\+F5**.  
  
     Visual Studio démarre le projet **AdventureWorksService** sans le déboguer.  
  
3.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur le projet **AdventureWorksSalesEditor**.  
  
4.  Dans le menu contextuel, sous **Déboguer**, cliquez sur **Démarrer une nouvelle instance**.  
  
     L'application s'exécute.  Vérifiez ce qui suit :  
  
    -   Les zones de texte affichent différents champs de données du premier enregistrement de vente, associé à l'ID de commande **71774**.  
  
    -   Vous pouvez cliquez sur les boutons **\>** ou **\<** pour parcourir les autres enregistrements de vente.  
  
5.  Dans l'un des enregistrements de vente, tapez du texte dans la zone **Commentaire**, puis cliquez sur **Enregistrer les modifications**.  
  
6.  Fermez l'application, puis redémarrez\-la à partir de Visual Studio.  
  
7.  Accédez à l'enregistrement de vente que vous avez modifié et vérifiez que la modification est toujours présente après avoir fermé et réouvert l'application.  
  
8.  Fermez l'application.  
  
## Étapes suivantes  
 Une fois cette procédure pas à pas terminée, vous pouvez effectuer les tâches associées suivantes :  
  
-   Découvrez comment utiliser la fenêtre **Sources de données** dans Visual Studio pour lier des contrôles WPF à d'autres types de sources de données.  Pour plus d'informations, consultez [Procédure pas à pas : liaison de contrôles WPF avec un groupe de données](../data-tools/bind-wpf-controls-to-a-dataset.md).  
  
-   Découvrez comment utiliser la fenêtre **Sources de données** dans Visual Studio pour afficher des données associées \(c'est\-à\-dire, des données dans une relation parent\-enfant\) dans des contrôles WPF.  Pour plus d'informations, consultez [Procédure pas à pas : affichage de données connexes dans une application WPF](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md).  
  
## Voir aussi  
 [Liaison de contrôles WPF avec des données dans Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)   
 [Comment : lier des contrôles WPF à des données dans Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md)   
 [Procédure pas à pas : liaison de contrôles WPF avec un groupe de données](../data-tools/bind-wpf-controls-to-a-dataset.md)   
 [Vue d'ensemble](../Topic/WCF%20Data%20Services%20Overview.md)   
 [Vue d'ensemble d'Entity Framework](../Topic/Entity%20Framework%20Overview.md)   
 [Vue d'ensemble des concepteurs WPF et Silverlight](http://msdn.microsoft.com/fr-fr/570b7a5c-0c86-4326-a371-c9b63378fc62)   
 [Vue d'ensemble de la liaison de données](../Topic/Data%20Binding%20Overview.md)