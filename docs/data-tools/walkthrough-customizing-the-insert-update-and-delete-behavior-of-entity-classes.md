---
title: "Procédure pas à pas : Personnalisation de l’instruction insert, update et supprimez le comportement des classes d’entité | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
ms.assetid: 03ff1146-706e-4780-91cb-56a83df63eea
caps.latest.revision: "3"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: f711c0fcdd4866a1b097585052cdcb3733e426d8
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes"></a>Procédure pas à pas : Personnalisation de l’instruction insert, update et supprimez le comportement des classes d’entité
Le [LINQ to SQL Tools dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) fournit une aire de conception visuelle pour créer et modifier [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] classes (classes d’entité) qui sont basées sur des objets dans une base de données. À l’aide de [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index), vous pouvez utiliser la technologie LINQ aux bases de données SQL. Pour plus d’informations, consultez [LINQ (Language-Integrated Query)](http://msdn.microsoft.com/Library/a73c4aec-5d15-4e98-b962-1274021ea93d).  
  
Par défaut, la logique d'exécution des mises à jour est fournie par le runtime de [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]. Le runtime crée les instructions d'insertion, de mise à jour et de suppression par défaut en fonction du schéma de la table (définitions de colonne et informations de clé primaire). Si vous ne souhaitez pas utiliser le comportement par défaut, vous pouvez configurer le comportement de mise à jour et désigner des procédures stockées spécifiques pour exécuter les instructions d'insertion, de mise à jour et de suppression nécessaires à la manipulation des données dans la base de données. Vous pouvez également le faire lorsque le comportement par défaut n'est pas généré, par exemple lorsque vos classes d'entité mappent aux vues. En outre, vous pouvez substituer le comportement de mise à jour par défaut lorsque la base de données nécessite un accès aux tables via des procédures stockées. Pour plus d’informations, consultez [personnalisation des opérations par à l’aide de procédures stockées](/dotnet/framework/data/adonet/sql/linq/customizing-operations-by-using-stored-procedures).  
  
> [!NOTE]
>  Cette procédure pas à pas requiert la disponibilité de la **InsertCustomer**, **UpdateCustomer**, et **DeleteCustomer** les procédures stockées pour la base de données Northwind.  
  
Cette procédure pas à pas décrit les étapes à suivre pour substituer le comportement au moment de l'exécution par défaut de LINQ to SQL et enregistrer les données dans une base de données à l'aide de procédures stockées.  
  
Pendant cette procédure pas à pas, vous allez apprendre à effectuer les tâches suivantes :  
  
-   Créer une application Windows Forms et lui ajouter un fichier [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)].  
  
-   Créer une classe d'entité mappée à la table Customers Northwind.  
  
-   Créer un objet source de données qui référence la classe Customer de LINQ to SQL.  
  
-   Créer un Windows Form qui contient un <xref:System.Windows.Forms.DataGridView> lié à la classe Customer.  
  
-   Implémenter une fonctionnalité d'enregistrement pour le formulaire.  
  
-   Créer des méthodes <xref:System.Data.Linq.DataContext> en ajoutant des procédures stockées au [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
-   Configurer la classe Customer pour utiliser des procédures stockées pour effectuer des insertions, des mises à jour et des suppressions.  
  
## <a name="prerequisites"></a>Conditions préalables  
Cette procédure pas à pas utilise SQL Server Express LocalDB et la base de données Northwind.  
  
1.  Si vous n’avez pas SQL Server Express LocalDB, installez-le à partir de la [page de téléchargement des éditions de SQL Server](https://www.microsoft.com/en-us/server-cloud/Products/sql-server-editions/sql-server-express.aspx), ou via le **le programme d’installation de Visual Studio**. Dans le programme d’installation Visual Studio, SQL Server Express LocalDB peut être installé dans le cadre de la **stockage de données et de traitement** charge de travail, ou sous la forme d’un composant individuel.  
  
2.  Installer la base de données Northwind en procédant comme suit :  

    1. Dans Visual Studio, ouvrez le **l’Explorateur d’objets SQL Server** fenêtre. (Explorateur d’objets SQL Server est installé dans le cadre de la **stockage de données et de traitement** charge de travail dans le programme d’installation Visual Studio.) Développez le **SQL Server** nœud. Avec le bouton droit sur votre instance de base de données locale et sélectionnez **nouvelle requête...** .  

       Une fenêtre d’éditeur de requête s’ouvre.  

    2. Copie le [script Transact-SQL de Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) dans le Presse-papiers. Ce script T-SQL crée la base de données Northwind à partir de zéro et la remplit avec des données.  

    3. Collez le script T-SQL dans l’éditeur de requête, puis choisissez le **Execute** bouton.  

       Après une courte période, la requête est terminée et la base de données Northwind est créé.  
  
## <a name="creating-an-application-and-adding-linq-to-sql-classes"></a>Création d'une application et ajout de classes LINQ to SQL  
Comme vous allez travailler avec les classes [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] et afficher les données sur un Windows Form, vous devez créer une application Windows Forms et ajouter un fichier de classes LINQ to SQL.  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### <a name="to-create-a-new-windows-forms-application-project-that-contains-linq-to-sql-classes"></a>Pour créer un nouveau projet d’Application Windows Forms qui contient LINQ to SQL classes  
  
1. Dans Visual Studio, sur le **fichier** menu, sélectionnez **nouveau**, **projet...** .  
  
2. Développez le **Visual C#** ou **Visual Basic** dans le volet gauche, puis sélectionnez **de bureau Windows classique**.  

3. Dans le volet central, sélectionnez le **l’application Windows Forms** type de projet.  

4. Nommez le projet **UpdatingWithSProcsWalkthrough**, puis choisissez **OK**. 
  
     Le **UpdatingWithSProcsWalkthrough** projet est créé et ajouté à **l’Explorateur de solutions**.  
  
4.  Dans le menu **Projet** , cliquez sur **Ajouter un nouvel élément**.  
  
5.  Cliquez sur le **Classes LINQ to SQL** modèle et le type **Northwind.dbml** dans les **nom** boîte.  
  
6.  Cliquez sur **Ajouter**.  
  
     Un fichier de classes LINQ to SQL vide (Northwind.dbml) est ajouté au projet et le [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] s'ouvre.  
  
## <a name="creating-the-customer-entity-class-and-object-data-source"></a>Création de la classe d'entité du client et de l'objet source de données  
 Créer [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] les classes qui sont mappées aux tables de base de données en faisant glisser des tables à partir de **l’Explorateur de serveurs**/**l’Explorateur de base de données** sur la [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. Les classes d'entité LINQ to SQL qui en résultent mappent aux tables de la base de données. Après avoir créé des classes d'entité, vous pouvez les utiliser en tant qu'objets sources de données comme toute autre classe ayant des propriétés publiques.  
  
#### <a name="to-create-a-customer-entity-class-and-configure-a-data-source-with-it"></a>Pour créer une classe d'entité client et configurer une source de données correspondante  
  
1.  Dans **l’Explorateur de serveurs**/**l’Explorateur de base de données**, localisez la table Customer dans la version de SQL Server de la base de données Northwind. 
  
2.  Faites glisser le **clients** nœud à partir de **l’Explorateur de serveurs**/**l’Explorateur de base de données** sur la [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] surface.  
  
     Une classe d’entité nommée **client** est créé. Elle comporte des propriétés qui correspondent aux colonnes de la table Customers. La classe d’entité est nommée **client** (pas **clients**), car elle représente un seul client à partir de la table Customers.  
  
    > [!NOTE]
    >  Ce comportement de changement de nom est appelé *pluralisation*. Il peut être activée ou désactivée le [boîte de dialogue Options](../ide/reference/options-dialog-box-visual-studio.md). Pour plus d’informations, consultez [Comment : activer et désactiver (Concepteur O/R) pluralisation](../data-tools/how-to-turn-pluralization-on-and-off-o-r-designer.md).  
  
3.  Sur le **générer** menu, cliquez sur **générer UpdatingwithSProcsWalkthrough** pour générer le projet.  
  
4.  Dans le menu **Données** , cliquez sur **Afficher les sources de données**.  
  
5.  Dans la fenêtre **Sources de données** , cliquez sur **Ajouter une nouvelle source de données**.  
  
6.  Cliquez sur **objet** sur la **choisir un Type de Source de données** page, puis cliquez sur **suivant**.  
  
7.  Développez le **UpdatingwithSProcsWalkthrough** nœud puis localisez et sélectionnez le **client** classe.  
  
    > [!NOTE]
    >  Si le **client** classe n’est pas disponible, quittez l’Assistant, générez le projet, et réexécutez l’Assistant.  
8.  Cliquez sur **Terminer** pour créer la source de données et ajouter la **client** classe d’entité à la **des Sources de données** fenêtre.  
  
## <a name="creating-a-datagridview-to-display-the-customer-data-on-a-windows-form"></a>Création d'un DataGridView pour afficher les données de Customer sur un Windows Form  
 Créer des contrôles liés aux classes d’entité en faisant glisser [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] éléments à partir de la source de données le **des Sources de données** fenêtre sur un Windows Form.  
  
#### <a name="to-add-controls-that-are-bound-to-the-entity-classes"></a>Pour ajouter des contrôles liés aux classes d'entité  
  
1.  Ouvrez Form1 en mode Design.  
  
2.  À partir de la **des Sources de données** fenêtre, faites glisser le **client** nœud vers Form1.  
  
    > [!NOTE]
    >  Pour afficher le **des Sources de données** fenêtre, cliquez sur **afficher les Sources de données** sur la **données** menu.  
  
3.  Ouvrez Form1 dans l'éditeur de code.  
  
4.  Ajoutez le code suivant au formulaire, global au formulaire, en dehors de toute méthode spécifique mais à l'intérieur de la classe Form1 :  
  
    ```vb  
    Private NorthwindDataContext1 As New NorthwindDataContext  
    ```  
  
    ```csharp  
    private NorthwindDataContext northwindDataContext1  
        = new NorthwindDataContext();    
    ```  
  
5.  Créez un gestionnaire d'événements pour l'événement `Form_Load` et ajoutez le code suivant au gestionnaire :  
  
    ```vb  
    CustomerBindingSource.DataSource = NorthwindDataContext1.Customers  
    ```  
  
    ```csharp  
    customerBindingSource.DataSource  
        = northwindDataContext1.Customers;    
    ```  
  
## <a name="implementing-save-functionality"></a>Implémentation de la fonctionnalité d'enregistrement  
 Par défaut, le bouton d'enregistrement n'est pas activé et la fonctionnalité d'enregistrement n'est pas implémentée. En outre, le code n'est pas automatiquement ajouté pour enregistrer dans les bases de données des données modifiées lorsque les contrôles liés aux données sont créés pour les objets source de données. Cette section explique comment activer le bouton d'enregistrement et implémenter la fonctionnalité d'enregistrement pour les objets [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)].  
  
#### <a name="to-implement-save-functionality"></a>Pour implémenter la fonctionnalité d'enregistrement  
  
1.  Ouvrez Form1 en mode Design.  
  
2.  Sélectionnez Enregistrer bouton sur le **CustomerBindingNavigator** (le bouton avec l’icône de disquette).  
  
3.  Dans le **propriétés** , configurez la **activé** propriété **True**.  
  
4.  Double-cliquez sur le bouton d'enregistrement pour créer un gestionnaire d'événements et basculer vers l'éditeur de code.  
  
5.  Ajoutez le code suivant dans le gestionnaire d'événements du bouton d'enregistrement :  
  
    ```vb  
    NorthwindDataContext1.SubmitChanges()  
    ```  
  
    ```csharp  
    northwindDataContext1.SubmitChanges();  
    ```  
  
## <a name="overriding-the-default-behavior-for-performing-updates-inserts-updates-and-deletes"></a>Substitution du comportement par défaut pour effectuer des mises à jour (insertions, mises à jour et suppressions)  
  
#### <a name="to-override-the-default-update-behavior"></a>Pour substituer le comportement de mise à jour par défaut  
  
1.  Ouvrez le fichier LINQ to SQL dans le [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. (Double-cliquez sur le **Northwind.dbml** fichier **l’Explorateur de solutions**.)  
  
2.  Dans **l’Explorateur de serveurs**/**l’Explorateur de base de données**, développez la base de données Northwind **de procédures stockées** nœud et recherchez le  **InsertCustomers**, **UpdateCustomers**, et **DeleteCustomers** des procédures stockées.  
  
3.  Faites glisser les trois procédures stockées vers le [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
     Les procédures stockées sont ajoutées au volet de méthodes comme méthodes <xref:System.Data.Linq.DataContext>. Pour plus d’informations, consultez [des méthodes DataContext (Concepteur O/R)](../data-tools/datacontext-methods-o-r-designer.md).  
  
4.  Sélectionnez le **client** classe d’entité dans le [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
5.  Dans le **propriétés** fenêtre, sélectionnez le **insérer** propriété.  
  
6.  Cliquez sur les points de suspension (...) à côté de **utiliser le Runtime** pour ouvrir le **configurer le comportement** boîte de dialogue.  
  
7.  Sélectionnez **personnaliser**.  
  
8.  Sélectionnez le **InsertCustomers** méthode dans le **personnaliser** liste.  
  
9. Cliquez sur **appliquer** pour enregistrer la configuration de la classe et le comportement sélectionnés.  
  
    > [!NOTE]
    >  Vous pouvez continuer à configurer le comportement de chaque combinaison classe/comportement tant que vous cliquez sur **appliquer** après chaque modification. Si vous modifiez la classe ou le comportement avant de cliquer sur **appliquer**, une boîte de dialogue d’avertissement qui fournit une opportunité pour appliquer les modifications s’affiche.  
  
10. Sélectionnez **mise à jour** dans les **comportement** liste.  
  
11. Sélectionnez **personnaliser**.  
  
12. Sélectionnez le **UpdateCustomers** méthode dans le **personnaliser** liste.  
  
     Inspectez la liste de **Arguments de méthode** et **propriétés de la classe** et notez qu’il existe deux **Arguments de méthode** et deux **propriétés de la classe**pour certaines colonnes de la table. Cela simplifie le suivi des modifications et la création des instructions qui vérifient les violations d'accès concurrentiel.  
  
13. Mappage de la **Original_CustomerID** argument de méthode le **CustomerID (Original)** propriété de classe.  
  
    > [!NOTE]
    >  Par défaut, les arguments de méthode sont mappés à des propriétés de classe lorsque les noms correspondent. Si les noms de propriété sont modifiés et ne correspondent plus entre la table et la classe d'entité, vous devrez peut-être sélectionner la propriété de classe équivalente à mapper si le Concepteur O/R ne peut pas déterminer le mappage correct. En outre, si les arguments de méthode n’ont pas de propriétés de classe valides à mapper, vous pouvez définir le **propriétés de la classe** valeur **(aucun)**.  
  
14. Cliquez sur **appliquer** pour enregistrer la configuration de la classe et le comportement sélectionnés.  
  
15. Sélectionnez **supprimer** dans les **comportement** liste.  
  
16. Sélectionnez **personnaliser**.  
  
17. Sélectionnez le **DeleteCustomers** méthode dans le **personnaliser** liste.  
  
18. Mappage de la **Original_CustomerID** argument de méthode le **CustomerID (Original)** propriété de classe.  
  
19. Cliquez sur **OK**.  
  
> [!NOTE]
>  Bien qu'il ne s'agisse pas d'un problème pour cette procédure pas à pas, notez que [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] gère automatiquement les valeurs générées par une base de données pour les colonnes identity (incrémentation automatique), rowguidcol (GUID généré par la base de données) et timestamp lors des insertions et des mises à jour. Les valeurs générées par une base de données dans les autres types de colonne entraînent une valeur null de manière inopinée. Pour retourner les valeurs générées par une base de données, vous devez affecter la valeur <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> à `true` et l'une des valeurs suivantes à <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> : <xref:System.Data.Linq.Mapping.AutoSync>, <xref:System.Data.Linq.Mapping.AutoSync> ou <xref:System.Data.Linq.Mapping.AutoSync>.  
  
## <a name="testing-the-application"></a>Test de l'application  
 Exécutez l’application à nouveau pour vérifier que le **UpdateCustomers** procédure stockée met à jour correctement l’enregistrement client dans la base de données.  
  
#### <a name="to-test-the-application"></a>Pour tester l'application  
  
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
    >  Si votre application utilise SQL Server Express Edition, selon la valeur de la **copier dans le répertoire de sortie** propriété du fichier de base de données, les modifications n’apparaissent pas lorsque vous appuyez sur F5 à l’étape 10. 
  
## <a name="next-steps"></a>Étapes suivantes  
Selon les spécifications de votre application, vous pouvez effectuer différentes étapes après avoir créé des classes d'entité [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]. Vous pouvez apporter à cette procédure pas à pas les améliorations suivantes :  
  
-   Implémenter la vérification des accès concurrentiels pendant les mises à jour. Pour plus d’informations, consultez [d’accès concurrentiel optimiste : vue d’ensemble](/dotnet/framework/data/adonet/sql/linq/optimistic-concurrency-overview).  
  
-   Ajouter des requêtes LINQ pour filtrer des données. Pour plus d’informations, consultez [Introduction aux requêtes LINQ (c#)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).  
  
## <a name="see-also"></a>Voir aussi
[LINQ to SQL des outils dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)     
[Méthodes DataContext](../data-tools/datacontext-methods-o-r-designer.md)   
[Comment : assigner des procédures stockées pour effectuer des mises à jour, insertions et suppressions](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)  
[LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)  
[Requêtes LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/linq-to-sql-queries)  
 