---
title: "Proc&#233;dure pas &#224; pas&#160;: personnalisation du comportement d&#39;insertion, de mise &#224; jour et de suppression de classes d&#39;entit&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 03ff1146-706e-4780-91cb-56a83df63eea
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Proc&#233;dure pas &#224; pas&#160;: personnalisation du comportement d&#39;insertion, de mise &#224; jour et de suppression de classes d&#39;entit&#233;
Le [Concepteur Objet\/Relationnel \(Concepteur O\/R\)](../data-tools/linq-to-sql-tools-in-visual-studio2.md) fournit une aire de conception visuelle pour créer et modifier des classes [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] \(classes d'entité\) basées sur des objets dans une base de données.[LINQ à SQL](../Topic/LINQ%20to%20SQL.md) vous permet d'utiliser la technologie LINQ pour accéder aux bases de données SQL.Pour plus d'informations, consultez [LINQ \(Language\-Integrated Query\)](../Topic/LINQ%20\(Language-Integrated%20Query\).md).  
  
 Par défaut, la logique d'exécution des mises à jour est fournie par le runtime de [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)].Le runtime crée les instructions d'insertion, de mise à jour et de suppression par défaut en fonction du schéma de la table \(définitions de colonne et informations de clé primaire\).Si vous ne souhaitez pas utiliser le comportement par défaut, vous pouvez configurer le comportement de mise à jour et désigner des procédures stockées spécifiques pour exécuter les instructions d'insertion, de mise à jour et de suppression nécessaires à la manipulation des données dans la base de données.Vous pouvez également le faire lorsque le comportement par défaut n'est pas généré, par exemple lorsque vos classes d'entité mappent aux vues.En outre, vous pouvez substituer le comportement de mise à jour par défaut lorsque la base de données nécessite un accès aux tables via des procédures stockées.Pour plus d'informations, consultez [Personnalisation d'opérations à l'aide de procédures stockées](../Topic/Customizing%20Operations%20By%20Using%20Stored%20Procedures.md).  
  
> [!NOTE]
>  Cette procédure pas à pas nécessite les procédures stockées **InsertCustomer**, **UpdateCustomer** et **DeleteCustomer** pour la base de données Northwind.Pour plus d'informations sur la création de ces procédures stockées, consultez [Procédure pas à pas : création de procédures stockées de mise à jour pour la table Customers de Northwind](../data-tools/walkthrough-creating-update-stored-procedures-for-the-northwind-customers-table.md).  
  
 Cette procédure pas à pas décrit les étapes à suivre pour substituer le comportement au moment de l'exécution par défaut de LINQ to SQL et enregistrer les données dans une base de données à l'aide de procédures stockées.  
  
 Dans cette procédure pas à pas, vous allez apprendre à effectuer les tâches suivantes :  
  
-   Créer une application Windows Forms et lui ajouter un fichier [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)].  
  
-   Créer une classe d'entité mappée à la table Customers Northwind.  
  
-   Créer un objet source de données qui référence la classe Customer de LINQ to SQL.  
  
-   Créer un Windows Form qui contient un <xref:System.Windows.Forms.DataGridView> lié à la classe Customer.  
  
-   Implémenter une fonctionnalité d'enregistrement pour le formulaire.  
  
-   Créer des méthodes <xref:System.Data.Linq.DataContext> en ajoutant des procédures stockées au [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
-   Configurer la classe Customer pour utiliser des procédures stockées pour effectuer des insertions, des mises à jour et des suppressions.  
  
## Composants requis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des éléments suivants :  
  
-   Accès à la version SQL Server de l'exemple de base de données Northwind.Pour plus d'informations, consultez [Comment : installer des exemples de bases de données](../data-tools/how-to-install-sample-databases.md).  
  
-   Procédures stockées **InsertCustomer**, **UpdateCustomer** et **DeleteCustomer** pour la base de données Northwind.Pour plus d'informations, consultez [Procédure pas à pas : création de procédures stockées de mise à jour pour la table Customers de Northwind](../data-tools/walkthrough-creating-update-stored-procedures-for-the-northwind-customers-table.md).  
  
## Création d'une application et ajout de classes LINQ to SQL  
 Comme vous allez travailler avec les classes [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] et afficher les données sur un Windows Form, vous devez créer une application Windows Forms et ajouter un fichier de classes LINQ to SQL.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### Pour créer un nouveau projet d'application Windows qui contient des classes LINQ to SQL  
  
1.  Dans le menu **Fichier**, créez un nouveau projet.  
  
2.  Nommez le projet UpdatingwithSProcsWalkthrough.  
  
    > [!NOTE]
    >  Le [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] est pris en charge dans les projets [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] et C\#.Par conséquent, vous pouvez créer le projet dans l'un ou l'autre de ces langages.  
  
3.  Cliquez sur le modèle **Application Windows Forms**, puis sur **OK**.Pour plus d'informations, consultez [Applications clientes](../Topic/Developing%20Client%20Applications%20with%20the%20.NET%20Framework.md).  
  
     Le projet UpdateSingleTableWalkthrough est créé et ajouté à l'**Explorateur de solutions**.  
  
4.  Dans le menu **Projet**, cliquez sur **Ajouter un nouvel élément**.  
  
5.  Cliquez sur le modèle **Classes LINQ to SQL** et tapez Northwind.dbml dans la zone **Nom**.  
  
6.  Cliquez sur **Ajouter**.  
  
     Un fichier de classes LINQ to SQL vide \(Northwind.dbml\) est ajouté au projet et le [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] s'ouvre.  
  
## Création de la classe d'entité du client et de l'objet source de données  
 Créez des classes [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] mappées aux tables de base de données en faisant glisser des tables de l'**Explorateur de serveurs**\/**Explorateur de bases de données** vers le [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].Les classes d'entité LINQ to SQL qui en résultent mappent aux tables de la base de données.Après avoir créé des classes d'entité, vous pouvez les utiliser en tant qu'objets sources de données comme toute autre classe ayant des propriétés publiques.  
  
#### Pour créer une classe d'entité client et configurer une source de données correspondante  
  
1.  Dans l'**Explorateur de serveurs**\/**Explorateur de bases de données**, localisez la table Customer dans la version SQL Server de l'exemple de base de données Northwind.Pour plus d'informations, consultez [Comment : se connecter à la base de données Northwind](../data-tools/how-to-connect-to-the-northwind-database.md).  
  
2.  Faites glisser le nœud **Customers** de l'**Explorateur de serveurs**\/**Explorateur de bases de données** vers l'aire du [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
     Une classe d'entité nommée **Customer** est créée.Elle comporte des propriétés qui correspondent aux colonnes de la table Customers.La classe d'entité est nommée **Customer** \(et non **Customers**\) parce qu'elle représente un seul client de la table Customers.  
  
    > [!NOTE]
    >  Ce comportement de changement de nom est appelé *pluralisation*.Il peut être activé ou désactivé dans la boîte de dialogue Options \(voir [Options, boîte de dialogue](../ide/reference/options-dialog-box-visual-studio.md)\).Pour plus d'informations, consultez [Procédure : activer et désactiver la pluralisation \(Concepteur O\/R\)](../data-tools/how-to-turn-pluralization-on-and-off-o-r-designer.md).  
  
3.  Dans le menu **Générer**, cliquez sur **Générer UpdatingwithSProcsWalkthrough** pour générer le projet.  
  
4.  Dans le menu **Données**, cliquez sur **Afficher les sources de données**.  
  
5.  Dans la fenêtre **Sources de données**, cliquez sur **Ajouter une nouvelle source de données**.  
  
6.  Dans la page **Choisir un type de source de données**, cliquez sur **Objet**, puis sur **Suivant**.  
  
7.  Développez le nœud **UpdatingwithSProcsWalkthrough**, puis localisez et sélectionnez la classe **Customer**.  
  
    > [!NOTE]
    >  Si la classe **Customer** n'est pas disponible, quittez l'Assistant, générez le projet et lancez une nouvelle fois l'Assistant.  
  
8.  Cliquez sur **Terminer** pour créer la source de données et ajouter la classe d'entité **Customer** à la fenêtre **Sources de données**.  
  
## Création d'un DataGridView pour afficher les données de Customer sur un Windows Form  
 Créez des contrôles liés aux classes d'entité en faisant glisser des éléments de la source de données [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] de la fenêtre **Sources de données** vers un Windows Form.  
  
#### Pour ajouter des contrôles liés aux classes d'entité  
  
1.  Ouvrez Form1 en mode Design.  
  
2.  Depuis la fenêtre **Sources de données**, faites glisser le nœud **Customer** vers Form1.  
  
    > [!NOTE]
    >  Pour ouvrir la fenêtre **Sources de données**, cliquez sur **Afficher les sources de données** dans le menu **Données**.  
  
3.  Ouvrez Form1 dans l'éditeur de code.  
  
4.  Ajoutez le code suivant au formulaire, global au formulaire, en dehors de toute méthode spécifique mais à l'intérieur de la classe Form1 :  
  
    ```vb#  
    Private NorthwindDataContext1 As New NorthwindDataContext  
    ```  
  
    ```c#  
    private NorthwindDataContext northwindDataContext1  
        = new NorthwindDataContext();  
  
    ```  
  
5.  Créez un gestionnaire d'événements pour l'événement `Form_Load` et ajoutez le code suivant au gestionnaire :  
  
    ```vb#  
    CustomerBindingSource.DataSource = NorthwindDataContext1.Customers  
    ```  
  
    ```c#  
    customerBindingSource.DataSource  
        = northwindDataContext1.Customers;  
  
    ```  
  
## Implémentation de la fonctionnalité d'enregistrement  
 Par défaut, le bouton d'enregistrement n'est pas activé et la fonctionnalité d'enregistrement n'est pas implémentée.En outre, le code n'est pas automatiquement ajouté pour enregistrer dans les bases de données des données modifiées lorsque les contrôles liés aux données sont créés pour les objets source de données.Cette section explique comment activer le bouton d'enregistrement et implémenter la fonctionnalité d'enregistrement pour les objets [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)].  
  
#### Pour implémenter la fonctionnalité d'enregistrement  
  
1.  Ouvrez Form1 en mode Design.  
  
2.  Sélectionnez le bouton d'enregistrement sur **CustomerBindingNavigator** \(le bouton avec l'icône de disquette\).  
  
3.  Dans la fenêtre **Propriétés**, attribuez à la propriété **Enabled** la valeur **True**.  
  
4.  Double\-cliquez sur le bouton d'enregistrement pour créer un gestionnaire d'événements et basculer vers l'éditeur de code.  
  
5.  Ajoutez le code suivant dans le gestionnaire d'événements du bouton d'enregistrement :  
  
    ```vb#  
    NorthwindDataContext1.SubmitChanges()  
    ```  
  
    ```c#  
    northwindDataContext1.SubmitChanges();  
    ```  
  
## Substitution du comportement par défaut pour effectuer des mises à jour \(insertions, mises à jour et suppressions\)  
  
#### Pour substituer le comportement de mise à jour par défaut  
  
1.  Ouvrez le fichier LINQ to SQL dans le [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].\(Double\-cliquez sur le fichier **Northwind.dbml** dans l'**Explorateur de solutions**.\)  
  
2.  Dans l'**Explorateur de serveurs**\/**Explorateur de bases de données**, développez le nœud **Procédures stockées** de la base de données Northwind et localisez les procédures stockées **InsertCustomers**, **UpdateCustomers** et **DeleteCustomers**.  
  
3.  Faites glisser les trois procédures stockées vers le [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
     Les procédures stockées sont ajoutées au volet de méthodes comme méthodes <xref:System.Data.Linq.DataContext>.Pour plus d'informations, consultez [Méthodes DataContext \(Concepteur O\/R\)](../data-tools/datacontext-methods-o-r-designer.md).  
  
4.  Sélectionnez la classe d'entité **Customer** dans le [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
5.  Dans la fenêtre **Propriétés**, sélectionnez la propriété **Insert**.  
  
6.  Cliquez sur les points de suspension \(…\) de l'option **Utiliser le runtime** pour ouvrir la boîte de dialogue **Configurer le comportement**.  
  
7.  Sélectionnez **Personnaliser**.  
  
8.  Sélectionnez la méthode **InsertCustomers** dans la liste **Personnaliser**.  
  
9. Cliquez sur **Appliquer** pour enregistrer la configuration de la classe et du comportement sélectionnés..  
  
    > [!NOTE]
    >  Vous pouvez continuer à configurer le comportement de chaque combinaison classe\/comportement tant que vous cliquez sur **Appliquer** après chaque modification.Si vous modifiez la classe ou le comportement avant de cliquer sur **Appliquer**, une boîte de dialogue d'avertissement s'affiche pour vous donner la possibilité d'appliquer toutes les modifications.  
  
10. Sélectionnez **Mettre à jour** dans la liste **Comportement**.  
  
11. Sélectionnez **Personnaliser**.  
  
12. Sélectionnez la méthode **UpdateCustomers** dans la liste **Personnaliser**.  
  
     Inspectez la liste d' **Arguments de méthode** et de **Propriétés de classe** ; remarquez qu'il y a deux **Arguments de méthode** et deux **Propriétés de classe** pour certaines colonnes de la table.Cela simplifie le suivi des modifications et la création des instructions qui vérifient les violations d'accès concurrentiel.  
  
13. Mappez l'argument de méthode **Original\_CustomerID** à la propriété de classe **CustomerID \(Original\)**.  
  
    > [!NOTE]
    >  Par défaut, les arguments de méthode sont mappés à des propriétés de classe lorsque les noms correspondent.Si les noms de propriété sont modifiés et ne correspondent plus entre la table et la classe d'entité, vous devrez peut\-être sélectionner la propriété de classe équivalente à mapper si le Concepteur O\/R ne peut pas déterminer le mappage correct.En outre, si les arguments de méthode n'ont pas de propriétés de classe valides à mapper, vous pouvez donner à **Propriétés de classe** la valeur **\(Aucune\)**.  
  
14. Cliquez sur **Appliquer** pour enregistrer la configuration de la classe et du comportement sélectionnés.  
  
15. Sélectionnez **Supprimer** dans la liste **Comportement**.  
  
16. Sélectionnez **Personnaliser**.  
  
17. Sélectionnez la méthode **DeleteCustomers** dans la liste **Personnaliser**.  
  
18. Mappez l'argument de méthode **Original\_CustomerID** à la propriété de classe **CustomerID \(Original\)**.  
  
19. Cliquez sur **OK**.  
  
> [!NOTE]
>  Bien qu'il ne s'agisse pas d'un problème pour cette procédure pas à pas, notez que [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] gère automatiquement les valeurs générées par une base de données pour les colonnes identity \(incrémentation automatique\), rowguidcol \(GUID généré par la base de données\) et timestamp lors des insertions et des mises à jour.Les valeurs générées par une base de données dans les autres types de colonne entraînent une valeur null de manière inopinée.Pour retourner les valeurs générées par une base de données, vous devez affecter la valeur `true` à <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> et l'une des valeurs suivantes à <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> : <xref:System.Data.Linq.Mapping.AutoSync>, <xref:System.Data.Linq.Mapping.AutoSync> ou <xref:System.Data.Linq.Mapping.AutoSync>.  
  
## Test de l'application  
 Exécutez une nouvelle fois l'application pour vérifier que la procédure stockée **UpdateCustomers** met à jour correctement l'enregistrement Customer dans la base de données.  
  
#### Pour tester l'application  
  
1.  Appuyez sur F5.  
  
2.  Modifiez un enregistrement dans la grille pour tester le comportement de mise à jour.  
  
3.  Ajoutez un nouvel enregistrement pour tester le comportement d'insertion.  
  
4.  Cliquez sur le bouton d'enregistrement pour enregistrer les modifications dans la base de données.  
  
5.  Fermez le formulaire.  
  
6.  Appuyez sur F5 et vérifiez que l'enregistrement mis à jour et l'enregistrement inséré persistent.  
  
7.  Supprimez le nouvel enregistrement que vous avez créé au cours de l'étape 3 pour tester le comportement de suppression.  
  
8.  Cliquez sur le bouton d'enregistrement pour valider les modifications et supprimer l'enregistrement effacé de la base de données  
  
9. Fermez le formulaire.  
  
10. Appuyez sur F5 et vérifiez que l'enregistrement effacé a été bien supprimé de la base de données.  
  
    > [!NOTE]
    >  Si votre application utilise SQL Server Express Edition, selon la valeur de la propriété **Copier dans le répertoire de sortie** du fichier de base de données, les modifications peuvent ne pas paraître lorsque vous appuyez sur F5 à l'étape 10.Pour plus d'informations, consultez [Comment : gérer des fichiers de données locaux dans votre projet](../data-tools/how-to-manage-local-data-files-in-your-project.md).  
  
## Étapes suivantes  
 Selon les spécifications de votre application, vous pouvez effectuer différentes étapes après avoir créé des classes d'entité [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)].Plusieurs améliorations peuvent être apportées à cette application, notamment :  
  
-   Implémenter la vérification des accès concurrentiels pendant les mises à jour.Pour plus d'informations, consultez [Accès concurrentiel optimiste : vue d'ensemble](../Topic/Optimistic%20Concurrency:%20Overview.md).  
  
-   Ajouter des requêtes LINQ pour filtrer des données.Pour plus d'informations, consultez [Introduction to LINQ Queries \(C\#\)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries).  
  
## Voir aussi  
 [Concepteur Objet\/Relationnel \(Concepteur O\/R\)](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ à SQL](../Topic/LINQ%20to%20SQL.md)   
 [Requêtes LINQ to SQL](../Topic/LINQ%20to%20SQL%20Queries.md)   
 [Méthodes DataContext \(Concepteur O\/R\)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Procédure : assigner des procédures stockées pour effectuer des mises à jour, des insertions et des suppressions \(Concepteur O\/R\)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)   
 [PAVE What's New for Data Application Development in Visual Studio 2012](http://msdn.microsoft.com/fr-fr/3d50d68f-5f44-4915-842f-6d42fce793f1)