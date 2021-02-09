---
title: Personnaliser le comportement d’insertion/mise à jour/suppression
description: Dans cette procédure pas à pas, vous pouvez personnaliser le comportement d’insertion, de mise à jour et de suppression des classes d’entité à l’aide de LINQ (Language-Integrated Query) vers les outils SQL dans Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
ms.assetid: 03ff1146-706e-4780-91cb-56a83df63eea
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 1aba3b1f00ce65b90f61077673a0b88a3bab0f5e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99866136"
---
# <a name="walkthrough-customize-the-insert-update-and-delete-behavior-of-entity-classes"></a>Procédure pas à pas : personnaliser le comportement d’insertion, de mise à jour et de suppression de classes d’entité

Les [outils de LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) fournissent une aire de conception visuelle pour créer et modifier des classes LINQ to SQL (classes d’entité) basées sur des objets dans une base de données. En utilisant [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index), vous pouvez utiliser la technologie LINQ pour accéder aux bases de données SQL. Pour plus d’informations, consultez [LINQ (Language-Integrated Query)](/dotnet/csharp/linq/).

Par défaut, la logique d’exécution des mises à jour est fournie par le runtime LINQ to SQL. Le runtime crée les `Insert` instructions par défaut, `Update` et `Delete` en fonction du schéma de la table (les définitions de colonne et les informations de clé primaire). Si vous ne souhaitez pas utiliser le comportement par défaut, vous pouvez configurer le comportement de mise à jour et désigner des procédures stockées spécifiques pour exécuter les insertions, mises à jour et suppressions nécessaires à la manipulation des données dans la base de données. Vous pouvez également le faire lorsque le comportement par défaut n'est pas généré, par exemple lorsque vos classes d'entité mappent aux vues. En outre, vous pouvez substituer le comportement de mise à jour par défaut lorsque la base de données nécessite un accès aux tables via des procédures stockées. Pour plus d’informations, consultez [Personnalisation des opérations à l’aide de procédures stockées](/dotnet/framework/data/adonet/sql/linq/customizing-operations-by-using-stored-procedures).

> [!NOTE]
> Cette procédure pas à pas nécessite les procédures stockées **InsertCustomer**, **UpdateCustomer** et **DeleteCustomer** pour la base de données Northwind.

Cette procédure pas à pas fournit les étapes que vous devez suivre pour remplacer le comportement par défaut LINQ to SQL au moment de l’exécution pour enregistrer des données dans une base de données à l’aide de procédures stockées.

Au cours de cette procédure pas à pas, vous allez apprendre à effectuer les tâches suivantes :

- Créer une application de Windows Forms et y ajouter un fichier LINQ to SQL.

- Créez une classe d’entité mappée à la table Northwind `Customers` .

- Créez une source de données d’objet qui fait référence à la `Customer` classe LINQ to SQL.

- Créez un Windows Form qui contient un <xref:System.Windows.Forms.DataGridView> lié à la `Customer` classe.

- Implémenter une fonctionnalité d'enregistrement pour le formulaire.

- Créez <xref:System.Data.Linq.DataContext> des méthodes en ajoutant des procédures stockées au **Concepteur O/R**.

- Configurez la `Customer` classe pour utiliser des procédures stockées pour effectuer des insertions, des mises à jour et des suppressions.

## <a name="prerequisites"></a>Prérequis

Cette procédure pas à pas utilise SQL Server Express base de données locale et l’exemple de base de données Northwind.

1. Si vous n’avez pas SQL Server Express base de données locale, installez-la à partir de la [page de téléchargement SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express)ou via le **Visual Studio installer**. Dans le **Visual Studio installer**, vous pouvez installer SQL Server Express base de données locale dans le cadre de la charge de travail de **stockage et de traitement des données** , ou en tant que composant individuel.

2. Installez l’exemple de base de données Northwind en procédant comme suit :

    1. Dans Visual Studio, ouvrez la fenêtre de **Explorateur d’objets SQL Server** . (**Explorateur d’objets SQL Server** s’installe dans le cadre de la charge de travail **stockage et traitement des données** dans le **Visual Studio installer**.) Développez le nœud **SQL Server** . Cliquez avec le bouton droit sur votre instance de base de données locale, puis sélectionnez **nouvelle requête**.

       Une fenêtre de l’éditeur de requête s’ouvre.

    2. Copiez le [script Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) dans le presse-papiers. Ce script T-SQL crée la base de données Northwind à partir de zéro et la remplit avec des données.

    3. Collez le script T-SQL dans l’éditeur de requête, puis choisissez le bouton **exécuter** .

       Après un bref laps de temps, l’exécution de la requête se termine et la base de données Northwind est créée.

## <a name="creating-an-application-and-adding-linq-to-sql-classes"></a>Création d’une application et ajout de classes LINQ to SQL

Étant donné que vous travaillez avec des classes LINQ to SQL et que vous affichez les données sur un Windows Form, créez une nouvelle application Windows Forms et ajoutez un fichier de classes LINQ to SQL.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-create-a-new-windows-forms-application-project-that-contains-linq-to-sql-classes"></a>Pour créer un projet d’application de Windows Forms qui contient des classes LINQ to SQL

1. Dans Visual Studio, dans le menu **Fichier**, sélectionnez **Nouveau** > **Projet**.

2. Développez **Visual C#** ou **Visual Basic** dans le volet gauche, puis sélectionnez **Bureau Windows**.

3. Dans le volet central, sélectionnez le type de projet d' **application Windows Forms** .

4. Nommez le projet **UpdatingWithSProcsWalkthrough**, puis choisissez **OK**.

     Le projet **UpdatingWithSProcsWalkthrough** est créé et ajouté à l’**Explorateur de solutions**.

4. Dans le menu **Projet** , cliquez sur **Ajouter un nouvel élément**.

5. Cliquez sur le modèle **Classes LINQ to SQL** et tapez **Northwind.dbml** dans la zone **Nom**.

6. Cliquez sur **Add**.

     Un fichier de classes de LINQ to SQL vide (**Northwind. dbml**) est ajouté au projet et le **Concepteur O/R** s’ouvre.

## <a name="create-the-customer-entity-class-and-object-data-source"></a>Créer la classe d’entité client et la source de données d’objet

Créez LINQ to SQL classes mappées à des tables de base de données en faisant glisser des tables de **Explorateur de serveurs** ou **Explorateur de base de données** vers le **Concepteur O/R**. Les classes d'entité LINQ to SQL qui en résultent mappent aux tables de la base de données. Après avoir créé des classes d'entité, vous pouvez les utiliser en tant qu'objets sources de données comme toute autre classe ayant des propriétés publiques.

### <a name="to-create-a-customer-entity-class-and-configure-a-data-source-with-it"></a>Pour créer une classe d'entité client et configurer une source de données correspondante

1. Dans **Explorateur de serveurs** ou **Explorateur de base de données**, localisez la table **customer** dans la version SQL Server de l’exemple de base de données Northwind.

2. Faites glisser le nœud **Customers** de **Explorateur de serveurs** ou **Explorateur de base de données** vers l’aire du *Concepteur * O/R* .

     Une classe d’entité nommée **Customer** est créée. Elle comporte des propriétés qui correspondent aux colonnes de la table Customers. La classe d’entité est nommée **Customer** (et non **Customers**) parce qu’elle représente un seul client de la table Customers.

    > [!NOTE]
    > Ce comportement de renommage est appelé *pluralisation*. Il peut être activé ou désactivé dans la [boîte de dialogue Options](../ide/reference/options-dialog-box-visual-studio.md). Pour plus d’informations, consultez [Comment : activer et désactiver la pluralisation (Concepteur O/R)](../data-tools/how-to-turn-pluralization-on-and-off-o-r-designer.md).

3. Dans le menu **Générer**, cliquez sur **Générer UpdatingwithSProcsWalkthrough** pour générer le projet.

4. Pour ouvrir la fenêtre **sources de données** , dans le menu **données** , cliquez sur Afficher les **sources de données**.

5. Dans la fenêtre **Sources de données** , cliquez sur **Ajouter une nouvelle source de données**.

6. Dans la page **Choisir un type de source de données**, cliquez sur **Objet**, puis sur **Suivant**.

7. Développez le nœud **UpdatingwithSProcsWalkthrough**, puis localisez et sélectionnez la classe **Customer**.

    > [!NOTE]
    > Si la classe **Customer** n’est pas disponible, quittez l’Assistant, générez le projet et réexécutez l’Assistant.
8. Cliquez sur **Terminer** pour créer la source de données et ajouter la classe d’entité **Customer** à la fenêtre **Sources de données**.

## <a name="create-a-datagridview-to-display-the-customer-data-on-a-windows-form"></a>Créer un DataGridView pour afficher les données client sur un Windows Form

Créez des contrôles liés aux classes d’entité en faisant glisser LINQ to SQL éléments de source de données de la fenêtre **sources de données** vers un Windows Form.

### <a name="to-add-controls-that-are-bound-to-the-entity-classes"></a>Pour ajouter des contrôles liés aux classes d'entité

1. Ouvrez **Form1** en mode Création.

2. Depuis la fenêtre **Sources de données**, faites glisser le nœud **Customer** vers **Form1**.

    > [!NOTE]
    > Pour ouvrir la fenêtre **Sources de données**, cliquez sur **Afficher les sources de données** dans le menu **Données**.

3. Ouvrez **Form1** dans l’éditeur de code.

4. Ajoutez le code suivant au formulaire, global au formulaire, en dehors de toute méthode spécifique, mais à l’intérieur de la `Form1` classe :

    ```vb
    Private NorthwindDataContext1 As New NorthwindDataContext
    ```

    ```csharp
    private NorthwindDataContext northwindDataContext1
        = new NorthwindDataContext();
    ```

5. Créez un gestionnaire d'événements pour l'événement `Form_Load` et ajoutez le code suivant au gestionnaire :

    ```vb
    CustomerBindingSource.DataSource = NorthwindDataContext1.Customers
    ```

    ```csharp
    customerBindingSource.DataSource
        = northwindDataContext1.Customers;
    ```

## <a name="implement-save-functionality"></a>Implémenter la fonctionnalité d’enregistrement

Par défaut, le bouton d'enregistrement n'est pas activé et la fonctionnalité d'enregistrement n'est pas implémentée. En outre, le code n'est pas automatiquement ajouté pour enregistrer dans les bases de données des données modifiées lorsque les contrôles liés aux données sont créés pour les objets source de données. Cette section explique comment activer le bouton enregistrer et implémenter les fonctionnalités d’enregistrement pour les objets LINQ to SQL.

### <a name="to-implement-save-functionality"></a>Pour implémenter la fonctionnalité d'enregistrement

1. Ouvrez **Form1** en mode Création.

2. Sélectionnez le bouton d’enregistrement sur **CustomerBindingNavigator** (le bouton avec l’icône représentant une disquette).

3. Dans la fenêtre **Propriétés**, attribuez à la propriété **Enabled** la valeur **True**.

4. Double-cliquez sur le bouton d'enregistrement pour créer un gestionnaire d'événements et basculer vers l'éditeur de code.

5. Ajoutez le code suivant dans le gestionnaire d'événements du bouton d'enregistrement :

    ```vb
    NorthwindDataContext1.SubmitChanges()
    ```

    ```csharp
    northwindDataContext1.SubmitChanges();
    ```

## <a name="override-the-default-behavior-for-performing-updates-inserts-updates-and-deletes"></a>Remplacer le comportement par défaut pour l’exécution des mises à jour (insertions, mises à jour et suppressions)

### <a name="to-override-the-default-update-behavior"></a>Pour substituer le comportement de mise à jour par défaut

1. Ouvrez le fichier LINQ to SQL dans le **Concepteur O/R**. (Double-cliquez sur le fichier **Northwind.dbml** dans l’**Explorateur de solutions**.)

2. Dans l’**Explorateur de serveurs** ou l’**Explorateur de bases de données**, développez le nœud **Procédures stockées** de la base de données Northwind et localisez les procédures stockées **InsertCustomers**, **UpdateCustomers** et **DeleteCustomers**.

3. Faites glisser les trois procédures stockées vers le **Concepteur O/R**.

     Les procédures stockées sont ajoutées au volet de méthodes comme méthodes <xref:System.Data.Linq.DataContext>. Pour plus d’informations, consultez [méthodes DataContext (Concepteur O/R)](../data-tools/datacontext-methods-o-r-designer.md).

4. Sélectionnez la classe d’entité **Customer** dans le **Concepteur O/R**.

5. Dans la fenêtre **Propriétés**, sélectionnez la propriété **Insert**.

6. Cliquez sur les points de suspension (**...**) en regard de l’option **Utiliser le runtime** pour ouvrir la boîte de dialogue **Configurer le comportement**.

7. Sélectionnez **Personnaliser**.

8. Sélectionnez la méthode **InsertCustomers** dans la liste **Personnaliser**.

9. Cliquez sur **Appliquer** pour enregistrer la configuration de la classe et du comportement sélectionnés.

    > [!NOTE]
    > Vous pouvez continuer à configurer le comportement de chaque combinaison classe/comportement tant que vous cliquez sur **Appliquer** après chaque modification. Si vous modifiez la classe ou le comportement avant de cliquer sur **appliquer**, une boîte de dialogue d’avertissement donnant la possibilité d’appliquer toutes les modifications s’affiche.

10. Sélectionnez **Mettre à jour** dans la liste **Comportement**.

11. Sélectionnez **Personnaliser**.

12. Sélectionnez la méthode **UpdateCustomers** dans la liste **Personnaliser**.

     Inspectez la liste des **Arguments de méthode** et des **Propriétés de classe** ; remarquez qu’il y a deux **Arguments de méthode** et deux **Propriétés de classe** pour certaines colonnes de la table. Cela simplifie le suivi des modifications et la création des instructions qui vérifient les violations d'accès concurrentiel.

13. Mappez l’argument de méthode **Original_CustomerID** à la propriété de classe **CustomerID (Original)**.

    > [!NOTE]
    > Par défaut, les arguments de méthode sont mappés à des propriétés de classe lorsque les noms correspondent. Si les noms de propriété sont modifiés et ne correspondent plus entre la table et la classe d’entité, vous devrez peut-être sélectionner la propriété de classe équivalente à mapper si le **Concepteur O/R** ne peut pas déterminer le mappage correct. En outre, si les arguments de méthode n’ont pas de propriétés de classe valides à mapper, vous pouvez donner à **Propriétés de classe** la valeur **(Aucune)**.

14. Cliquez sur **Appliquer** pour enregistrer la configuration de la classe et du comportement sélectionnés.

15. Sélectionnez **Supprimer** dans la liste **Comportement**.

16. Sélectionnez **Personnaliser**.

17. Sélectionnez la méthode **DeleteCustomers** dans la liste **Personnaliser**.

18. Mappez l’argument de méthode **Original_CustomerID** à la propriété de classe **CustomerID (Original)**.

19. Cliquez sur **OK**.

> [!NOTE]
> Bien qu’il ne s’agisse pas d’un problème pour cette procédure pas à pas, il est intéressant de noter que LINQ to SQL gère automatiquement les valeurs générées par la base de données pour les colonnes Identity (incrémentation automatique), rowguidcol (GUID généré par la base de données) et timestamp pendant les insertions et les mises à jour. Les valeurs générées par une base de données dans les autres types de colonne entraînent une valeur null de manière inopinée. Pour retourner les valeurs générées par la base de données, vous devez affecter manuellement <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> à `true` et <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> à l’un des éléments suivants : [AutoSync. Always](<xref:System.Data.Linq.Mapping.AutoSync.Always>), [AutoSync. OnInsert](<xref:System.Data.Linq.Mapping.AutoSync.OnInsert>)ou [AutoSync. OnUpdate](<xref:System.Data.Linq.Mapping.AutoSync.OnUpdate>).

## <a name="test-the-application"></a>Tester l’application

Exécutez une nouvelle fois l’application pour vérifier que la procédure stockée **UpdateCustomers** met à jour correctement l’enregistrement Customer dans la base de données.

1. Appuyez sur **F5**.

2. Modifiez un enregistrement dans la grille pour tester le comportement de mise à jour.

3. Ajoutez un nouvel enregistrement pour tester le comportement d’insertion.

4. Cliquez sur le bouton d'enregistrement pour enregistrer les modifications dans la base de données.

5. Fermez le formulaire.

6. Appuyez sur **F5** et vérifiez que l’enregistrement mis à jour et l’enregistrement inséré persistent.

7. Supprimez le nouvel enregistrement que vous avez créé au cours de l’étape 3 pour tester le comportement de suppression.

8. Cliquez sur le bouton d’enregistrement pour valider les modifications et supprimer l’enregistrement effacé de la base de données.

9. Fermez le formulaire.

10. Appuyez sur **F5** et vérifiez que l’enregistrement supprimé a été supprimé de la base de données.

    > [!NOTE]
    > Si votre application utilise SQL Server Express Edition, selon la valeur de la propriété **Copier dans le répertoire de sortie** du fichier de base de données, les modifications peuvent ne pas paraître quand vous appuyez sur **F5** à l’étape 10.

## <a name="next-steps"></a>Étapes suivantes

Selon les spécifications de votre application, vous pouvez effectuer plusieurs étapes après avoir créé LINQ to SQL classes d’entité. Vous pouvez apporter à cette procédure pas à pas les améliorations suivantes :

- Implémenter la vérification des accès concurrentiels pendant les mises à jour. Pour plus d’informations, consultez [accès concurrentiel optimiste : vue d’ensemble](/dotnet/framework/data/adonet/sql/linq/optimistic-concurrency-overview).

- Ajouter des requêtes LINQ pour filtrer des données. Pour plus d’informations, consultez [Introduction aux requêtes LINQ (C#)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries).

## <a name="see-also"></a>Voir aussi

- [Outils de LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Méthodes DataContext](../data-tools/datacontext-methods-o-r-designer.md)
- [Comment : assigner des procédures stockées pour effectuer des mises à jour, des insertions et des suppressions](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Requêtes LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/linq-to-sql-queries)
