---
title: 'Procédure pas à pas : Personnalisation de l’insertion, mise à jour et supprimer le comportement des classes d’entité'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
ms.assetid: 03ff1146-706e-4780-91cb-56a83df63eea
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: fb01ef51c0a44047e2caf2f23634ebe741cd2dcb
ms.sourcegitcommit: f37affbc1b885dfe246d4b2c295a6538b383a0ca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37174972"
---
# <a name="walkthrough-customize-the-insert-update-and-delete-behavior-of-entity-classes"></a>Procédure pas à pas : Personnaliser l’insertion, mise à jour et comportement de suppression de classes d’entité

Le [des outils LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) fournit une aire de conception visuelle pour créer et modifier LINQ aux classes SQL (classes d’entité) basées sur des objets dans une base de données. À l’aide de [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index), vous pouvez utiliser la technologie LINQ pour les bases de données access SQL. Pour plus d’informations, consultez [LINQ (Language-Integrated query)](/dotnet/csharp/linq/).

Par défaut, la logique pour effectuer des mises à jour est fournie par l’exécution LINQ to SQL. Le runtime crée par défaut `Insert`, `Update`, et `Delete` instructions basés sur le schéma de la table (définitions de colonne et informations de clé primaire). Lorsque vous ne souhaitez pas utiliser le comportement par défaut, vous pouvez configurer le comportement de mise à jour et désigner des procédures stockées spécifiques pour l’exécution des instructions d’insertion, des mises à jour et des suppressions requises pour fonctionner avec les données dans la base de données. Vous pouvez également le faire lorsque le comportement par défaut n'est pas généré, par exemple lorsque vos classes d'entité mappent aux vues. En outre, vous pouvez substituer le comportement de mise à jour par défaut lorsque la base de données nécessite un accès aux tables via des procédures stockées. Pour plus d’informations, consultez [personnalisation d’opérations à l’aide de procédures stockées](/dotnet/framework/data/adonet/sql/linq/customizing-operations-by-using-stored-procedures).

> [!NOTE]
> Cette procédure pas à pas nécessite la disponibilité de la **InsertCustomer**, **UpdateCustomer**, et **DeleteCustomer** des procédures stockées pour la base de données Northwind.

Cette procédure pas à pas décrit les étapes à suivre pour substituer le comportement au moment de l'exécution par défaut de LINQ to SQL et enregistrer les données dans une base de données à l'aide de procédures stockées.

Au cours de cette procédure pas à pas, vous allez apprendre à effectuer les tâches suivantes :

-   Créer une application Windows Forms et ajouter LINQ au fichier SQL à ce dernier.

-   Créer une classe d’entité qui est mappée à Northwind `Customers` table.

-   Créer un objet source de données qui fait référence à LINQ to SQL `Customer` classe.

-   Créer un formulaire Windows qui contient un <xref:System.Windows.Forms.DataGridView> qui est lié à la `Customer` classe.

-   Implémenter une fonctionnalité d'enregistrement pour le formulaire.

-   Créer <xref:System.Data.Linq.DataContext> méthodes en ajoutant des procédures stockées pour le **Concepteur O/R**.

-   Configurer la `Customer` classe à utiliser des procédures stockées pour effectuer les insertions, mises à jour et supprime.

## <a name="prerequisites"></a>Prérequis

Cette procédure pas à pas utilise SQL Server Express LocalDB et la base de données Northwind.

1.  Si vous n’avez pas SQL Server Express LocalDB, installez-le à partir de la [page de téléchargement de SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), ou via le **le programme d’installation de Visual Studio**. Dans le **le programme d’installation de Visual Studio**, vous pouvez installer SQL Server Express LocalDB dans le cadre de la **stockage de données et de traitement** charge de travail, ou comme un composant individuel.

2.  Installer la base de données Northwind en suivant ces étapes :

    1. Dans Visual Studio, ouvrez le **Explorateur d’objets SQL Server** fenêtre. (**Explorateur d’objets SQL Server** installe dans le cadre de la **stockage de données et de traitement** charge de travail dans le **le programme d’installation de Visual Studio**.) Développez le **SQL Server** nœud. Avec le bouton droit sur votre instance de base de données locale et sélectionnez **nouvelle requête**.

       Une fenêtre d’éditeur de requête s’ouvre.

    2. Copie le [script Transact-SQL de Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) dans votre Presse-papiers. Ce script T-SQL crée la base de données Northwind à partir de zéro et la remplit avec des données.

    3. Collez le script T-SQL dans l’éditeur de requête, puis choisissez le **Execute** bouton.

       Après une courte période, la requête est terminée en cours d’exécution et la base de données Northwind est créé.

## <a name="creating-an-application-and-adding-linq-to-sql-classes"></a>Création d’une application et ajout de LINQ to SQL classes

Étant donné que vous travaillez avec LINQ aux classes SQL et afficher les données sur un formulaire Windows, créer une application Windows Forms et ajouter un LINQ vers le fichier de Classes SQL.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-create-a-new-windows-forms-application-project-that-contains-linq-to-sql-classes"></a>Pour créer un nouveau projet Windows Forms Application contenant LINQ aux classes SQL

1. Dans Visual Studio, sur le **fichier** menu, sélectionnez **New** > **projet**.

2. Développez le **Visual C#** ou **Visual Basic** dans le volet gauche, puis sélectionnez **Windows Desktop**.

3. Dans le volet central, sélectionnez le **Windows Forms application** type de projet.

4. Nommez le projet **UpdatingWithSProcsWalkthrough**, puis choisissez **OK**.

     Le **UpdatingWithSProcsWalkthrough** projet est créé et ajouté à **l’Explorateur de solutions**.

4.  Dans le menu **Projet** , cliquez sur **Ajouter un nouvel élément**.

5.  Cliquez sur le **Classes LINQ to SQL** modèle et le type **Northwind.dbml** dans le **nom** boîte.

6.  Cliquez sur **Ajouter**.

     Un vide fichier LINQ to SQL Classes (**Northwind.dbml**) est ajouté au projet et le **Concepteur O/R** s’ouvre.

## <a name="create-the-customer-entity-class-and-object-data-source"></a>Créer la source de données client entité classe et objet

Créer LINQ to SQL des classes qui sont mappées aux tables de base de données en faisant glisser des tables à partir de **Explorateur de serveurs** ou **Database Explorer** sur le **Concepteur O/R**. Les classes d'entité LINQ to SQL qui en résultent mappent aux tables de la base de données. Après avoir créé des classes d'entité, vous pouvez les utiliser en tant qu'objets sources de données comme toute autre classe ayant des propriétés publiques.

### <a name="to-create-a-customer-entity-class-and-configure-a-data-source-with-it"></a>Pour créer une classe d'entité client et configurer une source de données correspondante

1.  Dans **Explorateur de serveurs** ou **Database Explorer**, localisez le **client** table dans la version de SQL Server de la base de données Northwind.

2.  Faites glisser le **clients** nœud à partir de **Explorateur de serveurs** ou **l’Explorateur de base de données** sur le **Concepteur O/R* surface.

     Une classe d’entité nommée **client** est créé. Elle comporte des propriétés qui correspondent aux colonnes de la table Customers. La classe d’entité est nommée **client** (pas **clients**) parce qu’elle représente un seul client à partir de la table Customers.

    > [!NOTE]
    > Ce comportement de changement de nom est appelé *pluralisation*. Il peut être activée ou désactivée le [boîte de dialogue Options](../ide/reference/options-dialog-box-visual-studio.md). Pour plus d’informations, consultez [Comment : activer et désactiver (Concepteur O/R) la pluralisation](../data-tools/how-to-turn-pluralization-on-and-off-o-r-designer.md).

3.  Sur le **Build** menu, cliquez sur **générer UpdatingwithSProcsWalkthrough** pour générer le projet.

4.  Dans le menu **Données** , cliquez sur **Afficher les sources de données**.

5.  Dans la fenêtre **Sources de données** , cliquez sur **Ajouter une nouvelle source de données**.

6.  Cliquez sur **objet** sur le **choisir un Type de Source de données** page, puis cliquez sur **suivant**.

7.  Développez le **UpdatingwithSProcsWalkthrough** nœud puis localisez et sélectionnez le **client** classe.

    > [!NOTE]
    > Si le **client** classe n’est pas disponible, quittez l’Assistant, générez le projet, et réexécutez l’Assistant.
8.  Cliquez sur **Terminer** pour créer la source de données et ajouter la **client** classe d’entité à la **des Sources de données** fenêtre.

## <a name="create-a-datagridview-to-display-the-customer-data-on-a-windows-form"></a>Créer un DataGridView pour afficher les données des clients sur un formulaire Windows

Créer des contrôles qui sont liés aux classes d’entité en faisant glisser de LINQ pour les éléments de source de données SQL à partir de la **des Sources de données** fenêtre vers un formulaire Windows.

### <a name="to-add-controls-that-are-bound-to-the-entity-classes"></a>Pour ajouter des contrôles liés aux classes d'entité

1.  Ouvrez **Form1** en mode Design.

2.  À partir de la **des Sources de données** fenêtre, faites glisser le **client** nœud sur **Form1**.

    > [!NOTE]
    > Pour afficher le **des Sources de données** fenêtre, cliquez sur **afficher les Sources de données** sur le **données** menu.

3.  Ouvrez **Form1** dans l’éditeur de Code.

4.  Ajoutez le code suivant au formulaire, global au formulaire, en dehors de toute méthode spécifique, mais dans le `Form1` classe :

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

## <a name="implement-save-functionality"></a>Implémenter la fonctionnalité d’enregistrement

Par défaut, le bouton d'enregistrement n'est pas activé et la fonctionnalité d'enregistrement n'est pas implémentée. En outre, le code n'est pas automatiquement ajouté pour enregistrer dans les bases de données des données modifiées lorsque les contrôles liés aux données sont créés pour les objets source de données. Cette section explique comment activer l’enregistrement bouton et d’implémenter à la fonctionnalité d’enregistrement pour LINQ aux objets SQL.

### <a name="to-implement-save-functionality"></a>Pour implémenter la fonctionnalité d'enregistrement

1.  Ouvrez **Form1** en mode Design.

2.  Sélectionnez l’enregistrement bouton sur le **CustomerBindingNavigator** (le bouton avec l’icône de disquette).

3.  Dans le **propriétés** fenêtre, définissez la **activé** propriété **True**.

4.  Double-cliquez sur le bouton d'enregistrement pour créer un gestionnaire d'événements et basculer vers l'éditeur de code.

5.  Ajoutez le code suivant dans le gestionnaire d'événements du bouton d'enregistrement :

    ```vb
    NorthwindDataContext1.SubmitChanges()
    ```

    ```csharp
    northwindDataContext1.SubmitChanges();
    ```

## <a name="override-the-default-behavior-for-performing-updates-inserts-updates-and-deletes"></a>Remplacer le comportement par défaut pour effectuer des mises à jour (insertions, mises à jour et suppressions)

### <a name="to-override-the-default-update-behavior"></a>Pour substituer le comportement de mise à jour par défaut

1.  Ouvrez le fichier LINQ to SQL dans le **Concepteur O/R**. (Double-cliquez sur le **Northwind.dbml** fichier **l’Explorateur de solutions**.)

2.  Dans **Explorateur de serveurs** ou **Database Explorer**, développez les bases de données Northwind **Stored Procedures** nœud et recherchez le **InsertCustomers**, **UpdateCustomers**, et **DeleteCustomers** procédures stockées.

3.  Faites glisser les trois procédures stockées sur le **Concepteur O/R**.

     Les procédures stockées sont ajoutées au volet de méthodes comme méthodes <xref:System.Data.Linq.DataContext>. Pour plus d’informations, consultez [DataContext, méthodes (Concepteur O/R)](../data-tools/datacontext-methods-o-r-designer.md).

4.  Sélectionnez le **client** classe d’entité dans le **Concepteur O/R**.

5.  Dans le **propriétés** fenêtre, sélectionnez le **insérer** propriété.

6.  Cliquez sur le bouton de sélection (**...** ) à côté **utiliser le Runtime** pour ouvrir le **configurer le comportement** boîte de dialogue.

7.  Sélectionnez **personnaliser**.

8.  Sélectionnez le **InsertCustomers** méthode dans le **personnaliser** liste.

9. Cliquez sur **appliquer** pour enregistrer la configuration de la classe et le comportement sélectionné.

    > [!NOTE]
    > Vous pouvez continuer à configurer le comportement pour chaque combinaison classe/comportement tant que vous cliquez sur **appliquer** après chaque modification. Si vous modifiez la classe ou le comportement avant de cliquer sur **appliquer**, une boîte de dialogue d’avertissement offrant la possibilité d’appliquer toutes les modifications s’affiche.

10. Sélectionnez **mise à jour** dans le **comportement** liste.

11. Sélectionnez **personnaliser**.

12. Sélectionnez le **UpdateCustomers** méthode dans le **personnaliser** liste.

     Inspectez la liste de **Arguments de méthode** et **propriétés de la classe** et notez qu’il existe deux **Arguments de méthode** et deux **propriétés de la classe**pour certaines colonnes de la table. Cela simplifie le suivi des modifications et la création des instructions qui vérifient les violations d'accès concurrentiel.

13. Carte le **Original_CustomerID** argument de méthode à la **CustomerID (Original)** propriété de classe.

    > [!NOTE]
    > Par défaut, les arguments de méthode sont mappés à des propriétés de classe lorsque les noms correspondent. Si les noms de propriété sont modifiés et ne correspondent plus entre la table et la classe d’entité, vous devrez peut-être sélectionner la propriété de classe équivalente à mapper à if le **Concepteur O/R** ne peut pas déterminer le mappage correct. En outre, si les arguments de méthode n’ont pas de propriétés de classe valide pour mapper à, vous pouvez définir le **propriétés de la classe** valeur **(aucun)**.

14. Cliquez sur **appliquer** pour enregistrer la configuration de la classe et le comportement sélectionné.

15. Sélectionnez **supprimer** dans le **comportement** liste.

16. Sélectionnez **personnaliser**.

17. Sélectionnez le **DeleteCustomers** méthode dans le **personnaliser** liste.

18. Carte le **Original_CustomerID** argument de méthode à la **CustomerID (Original)** propriété de classe.

19. Cliquez sur **OK**.

> [!NOTE]
> Bien qu’il n’est pas un problème pour cette procédure pas à pas particulier, il est important de noter que LINQ to SQL gère une base de données générée automatiquement les valeurs pour identity (incrémentation automatique), rowguidcol (GUID généré par la base de données) et les colonnes timestamp pendant les insertions et met à jour. Les valeurs générées par une base de données dans les autres types de colonne entraînent une valeur null de manière inopinée. Pour retourner les valeurs générées à la base de données, vous devez définir manuellement <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> à `true` et <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> à une des opérations suivantes : [AutoSync.Always](<xref:System.Data.Linq.Mapping.AutoSync.Always>), [AutoSync.OnInsert](<xref:System.Data.Linq.Mapping.AutoSync.OnInsert>), ou [AutoSync.OnUpdate](<xref:System.Data.Linq.Mapping.AutoSync.OnUpdate>).

## <a name="test-the-application"></a>Tester l’application

Exécutez l’application à nouveau pour vérifier que le **UpdateCustomers** procédure stockée met correctement à jour l’enregistrement de client dans la base de données.

1.  Appuyez sur **F5**.

2.  Modifier un enregistrement dans la grille pour tester le comportement de mise à jour.

3.  Ajouter un nouvel enregistrement pour tester le comportement d’insertion.

4.  Cliquez sur le bouton d'enregistrement pour enregistrer les modifications dans la base de données.

5.  Fermez le formulaire.

6.  Appuyez sur **F5** et vérifiez que l’enregistrement mis à jour et l’enregistrement inséré qui vient d’être rendues persistantes.

7.  Supprimez le nouvel enregistrement que vous avez créé dans l’étape 3 pour tester le comportement de suppression.

8.  Cliquez sur l’enregistrement bouton pour soumettre les modifications et supprimer l’enregistrement supprimé de la base de données.

9. Fermez le formulaire.

10. Appuyez sur **F5** et vérifiez que l’enregistrement supprimé a été supprimé de la base de données.

    > [!NOTE]
    > Si votre application utilise SQL Server Express Edition, selon la valeur de la **Copy to Output Directory** propriété du fichier de base de données, les modifications n’apparaissent pas lorsque vous appuyez sur **F5** à l’étape 10.

## <a name="next-steps"></a>Étapes suivantes

Selon les exigences de votre application, il existe plusieurs étapes que vous pouvez effectuer après avoir créé LINQ aux classes d’entité SQL. Vous pouvez apporter à cette procédure pas à pas les améliorations suivantes :

- Implémenter la vérification des accès concurrentiels pendant les mises à jour. Pour plus d’informations, consultez [d’accès concurrentiel optimiste : vue d’ensemble](/dotnet/framework/data/adonet/sql/linq/optimistic-concurrency-overview).

- Ajouter des requêtes LINQ pour filtrer des données. Pour plus d’informations, consultez [Introduction aux requêtes LINQ (c#)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries).

## <a name="see-also"></a>Voir aussi

- [Outils LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Méthodes DataContext](../data-tools/datacontext-methods-o-r-designer.md)
- [Comment : assigner des procédures stockées pour effectuer des mises à jour, insertions et suppressions](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Requêtes LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/linq-to-sql-queries)