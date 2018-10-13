---
title: 'Procédure pas à pas : Personnalisation de l’insertion, mise à jour et supprimer le comportement des classes d’entité | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 03ff1146-706e-4780-91cb-56a83df63eea
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4d8ef69258d9c672bb5deb01b9c2e0972d4e8303
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49193542"
---
# <a name="walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes"></a>Procédure pas à pas : Personnalisation de l’insertion, mise à jour et supprimer le comportement des classes d’entité
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Le [outils LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) fournit une aire de conception visuelle pour créer et modifier [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] des classes (classes d’entité) basées sur des objets dans une base de données. À l’aide de [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655), vous pouvez utiliser la technologie LINQ pour les bases de données access SQL. Pour plus d’informations, consultez [LINQ (Language-Integrated Query)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d).  
  
 Par défaut, la logique d'exécution des mises à jour est fournie par le runtime de [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)]. Le runtime crée les instructions d'insertion, de mise à jour et de suppression par défaut en fonction du schéma de la table (définitions de colonne et informations de clé primaire). Si vous ne souhaitez pas utiliser le comportement par défaut, vous pouvez configurer le comportement de mise à jour et désigner des procédures stockées spécifiques pour exécuter les instructions d'insertion, de mise à jour et de suppression nécessaires à la manipulation des données dans la base de données. Vous pouvez également le faire lorsque le comportement par défaut n'est pas généré, par exemple lorsque vos classes d'entité mappent aux vues. En outre, vous pouvez substituer le comportement de mise à jour par défaut lorsque la base de données nécessite un accès aux tables via des procédures stockées. Pour plus d’informations, consultez [personnalisation des opérations par à l’aide de procédures stockées](http://msdn.microsoft.com/library/aedbecc1-c33c-4fb4-8861-fdf7e1dc6b8a).  
  
> [!NOTE]
>  Cette procédure pas à pas nécessite la disponibilité de la **InsertCustomer**, **UpdateCustomer**, et **DeleteCustomer** des procédures stockées pour la base de données Northwind. Pour plus d’informations sur la création de ces procédures stockées, consultez [procédure pas à pas : création de procédures stockées mise à jour pour la Table Customers de Northwind](../data-tools/walkthrough-creating-update-stored-procedures-for-the-northwind-customers-table.md).  
  
 Cette procédure pas à pas décrit les étapes à suivre pour substituer le comportement au moment de l'exécution par défaut de LINQ to SQL et enregistrer les données dans une base de données à l'aide de procédures stockées.  
  
 Pendant cette procédure pas à pas, vous allez apprendre à effectuer les tâches suivantes :  
  
-   Créer une application Windows Forms et lui ajouter un fichier [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)].  
  
-   Créer une classe d'entité mappée à la table Customers Northwind.  
  
-   Créer un objet source de données qui référence la classe Customer de LINQ to SQL.  
  
-   Créer un Windows Form qui contient un <xref:System.Windows.Forms.DataGridView> lié à la classe Customer.  
  
-   Implémenter une fonctionnalité d'enregistrement pour le formulaire.  
  
-   Créer des méthodes <xref:System.Data.Linq.DataContext> en ajoutant des procédures stockées au [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].  
  
-   Configurer la classe Customer pour utiliser des procédures stockées pour effectuer des insertions, des mises à jour et des suppressions.  
  
## <a name="prerequisites"></a>Prérequis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des éléments suivants :  
  
-   Accès à la version SQL Server de l'exemple de base de données Northwind. Pour plus d’informations, consultez [Comment : installer Sample Databases](../data-tools/how-to-install-sample-databases.md).  
  
-   Le **InsertCustomer**, **UpdateCustomer**, et **DeleteCustomer** des procédures stockées pour la base de données Northwind. Pour plus d’informations, consultez [procédure pas à pas : création de procédures stockées mise à jour pour la Table Customers de Northwind](../data-tools/walkthrough-creating-update-stored-procedures-for-the-northwind-customers-table.md).  
  
## <a name="creating-an-application-and-adding-linq-to-sql-classes"></a>Création d'une application et ajout de classes LINQ to SQL  
 Comme vous allez travailler avec les classes [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] et afficher les données sur un Windows Form, vous devez créer une application Windows Forms et ajouter un fichier de classes LINQ to SQL.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
#### <a name="to-create-a-new-windows-application-project-that-contains-linq-to-sql-classes"></a>Pour créer un nouveau projet d'application Windows qui contient des classes LINQ to SQL  
  
1.  À partir de la **fichier** menu, créez un nouveau projet.  
  
2.  Nommez le projet **UpdatingwithSProcsWalkthrough**.  
  
    > [!NOTE]
    >  Le [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] est pris en charge dans les projets [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] et C#. Par conséquent, vous pouvez créer le projet dans l'un ou l'autre de ces langages.  
  
3.  Cliquez sur le **Windows Forms Application** modèle et cliquez sur **OK**. Pour plus d’informations, consultez [les Applications clientes](http://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).  
  
     Le projet UpdateSingleTableWalkthrough est créé et ajouté à **l’Explorateur de solutions**.  
  
4.  Dans le menu **Projet** , cliquez sur **Ajouter un nouvel élément**.  
  
5.  Cliquez sur le **Classes LINQ to SQL** modèle et le type **Northwind.dbml** dans le **nom** boîte.  
  
6.  Cliquez sur **Ajouter**.  
  
     Un fichier de classes LINQ to SQL vide (Northwind.dbml) est ajouté au projet et le [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] s'ouvre.  
  
## <a name="creating-the-customer-entity-class-and-object-data-source"></a>Création de la classe d'entité du client et de l'objet source de données  
 Créer [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] les classes qui sont mappées aux tables de base de données en faisant glisser des tables à partir de **Explorateur de serveurs**/**Database Explorer** sur le [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Les classes d'entité LINQ to SQL qui en résultent mappent aux tables de la base de données. Après avoir créé des classes d'entité, vous pouvez les utiliser en tant qu'objets sources de données comme toute autre classe ayant des propriétés publiques.  
  
#### <a name="to-create-a-customer-entity-class-and-configure-a-data-source-with-it"></a>Pour créer une classe d'entité client et configurer une source de données correspondante  
  
1.  Dans **Explorateur de serveurs**/**Database Explorer**, localisez la table Customer dans la version de SQL Server de la base de données Northwind. Pour plus d’informations, consultez [Comment : se connecter à la base de données Northwind](../data-tools/how-to-connect-to-the-northwind-database.md).  
  
2.  Faites glisser le **clients** nœud à partir de **Explorateur de serveurs**/**l’Explorateur de base de données** sur la [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] surface.  
  
     Une classe d’entité nommée **client** est créé. Elle comporte des propriétés qui correspondent aux colonnes de la table Customers. La classe d’entité est nommée **client** (pas **clients**) parce qu’elle représente un seul client à partir de la table Customers.  
  
    > [!NOTE]
    >  Ce comportement de changement de nom est appelé *pluralisation*. Il peut être activée ou désactivée le [boîte de dialogue Options](../ide/reference/options-dialog-box-visual-studio.md). Pour plus d’informations, consultez [Comment : activer et désactiver (Concepteur O/R) la pluralisation](../data-tools/how-to-turn-pluralization-on-and-off-o-r-designer.md).  
  
3.  Sur le **Build** menu, cliquez sur **générer UpdatingwithSProcsWalkthrough** pour générer le projet.  
  
4.  Dans le menu **Données** , cliquez sur **Afficher les sources de données**.  
  
5.  Dans la fenêtre **Sources de données** , cliquez sur **Ajouter une nouvelle source de données**.  
  
6.  Cliquez sur **objet** sur le **choisir un Type de Source de données** page, puis cliquez sur **suivant**.  
  
7.  Développez le **UpdatingwithSProcsWalkthrough** nœud puis localisez et sélectionnez le **client** classe.  
  
    > [!NOTE]
    >  Si le **client** classe n’est pas disponible, quittez l’Assistant, générez le projet, et réexécutez l’Assistant.  
  
8.  Cliquez sur **Terminer** pour créer la source de données et ajouter la **client** classe d’entité à la **des Sources de données** fenêtre.  
  
## <a name="creating-a-datagridview-to-display-the-customer-data-on-a-windows-form"></a>Création d'un DataGridView pour afficher les données de Customer sur un Windows Form  
 Créer des contrôles qui sont liés aux classes d’entité en faisant glisser [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] éléments à partir de la source de données le **des Sources de données** fenêtre vers un formulaire Windows.  
  
#### <a name="to-add-controls-that-are-bound-to-the-entity-classes"></a>Pour ajouter des contrôles liés aux classes d'entité  
  
1.  Ouvrez Form1 en mode Design.  
  
2.  À partir de la **des Sources de données** fenêtre, faites glisser le **client** nœud vers Form1.  
  
    > [!NOTE]
    >  Pour afficher le **des Sources de données** fenêtre, cliquez sur **afficher les Sources de données** sur le **données** menu.  
  
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
 Par défaut, le bouton d'enregistrement n'est pas activé et la fonctionnalité d'enregistrement n'est pas implémentée. En outre, le code n'est pas automatiquement ajouté pour enregistrer dans les bases de données des données modifiées lorsque les contrôles liés aux données sont créés pour les objets source de données. Cette section explique comment activer le bouton d'enregistrement et implémenter la fonctionnalité d'enregistrement pour les objets [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)].  
  
#### <a name="to-implement-save-functionality"></a>Pour implémenter la fonctionnalité d'enregistrement  
  
1.  Ouvrez Form1 en mode Design.  
  
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
  
## <a name="overriding-the-default-behavior-for-performing-updates-inserts-updates-and-deletes"></a>Substitution du comportement par défaut pour effectuer des mises à jour (insertions, mises à jour et suppressions)  
  
#### <a name="to-override-the-default-update-behavior"></a>Pour substituer le comportement de mise à jour par défaut  
  
1.  Ouvrez le fichier LINQ to SQL dans le [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. (Double-cliquez sur le **Northwind.dbml** fichier **l’Explorateur de solutions**.)  
  
2.  Dans **Explorateur de serveurs**/**Database Explorer**, développez les bases de données Northwind **Stored Procedures** nœud et recherchez le  **InsertCustomers**, **UpdateCustomers**, et **DeleteCustomers** procédures stockées.  
  
3.  Faites glisser les trois procédures stockées vers le [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].  
  
     Les procédures stockées sont ajoutées au volet de méthodes comme méthodes <xref:System.Data.Linq.DataContext>. Pour plus d’informations, consultez [DataContext, méthodes (Concepteur O/R)](../data-tools/datacontext-methods-o-r-designer.md).  
  
4.  Sélectionnez le **client** classe d’entité dans le [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].  
  
5.  Dans le **propriétés** fenêtre, sélectionnez le **insérer** propriété.  
  
6.  Cliquez sur les points de suspension (...) à côté de **utiliser le Runtime** pour ouvrir le **configurer le comportement** boîte de dialogue.  
  
7.  Sélectionnez **personnaliser**.  
  
8.  Sélectionnez le **InsertCustomers** méthode dans le **personnaliser** liste.  
  
9. Cliquez sur **appliquer** pour enregistrer la configuration de la classe et le comportement sélectionné.  
  
    > [!NOTE]
    >  Vous pouvez continuer à configurer le comportement pour chaque combinaison classe/comportement tant que vous cliquez sur **appliquer** après chaque modification. Si vous modifiez la classe ou le comportement avant de cliquer sur **appliquer**, une boîte de dialogue d’avertissement offrant la possibilité d’appliquer toutes les modifications s’affiche.  
  
10. Sélectionnez **mise à jour** dans le **comportement** liste.  
  
11. Sélectionnez **personnaliser**.  
  
12. Sélectionnez le **UpdateCustomers** méthode dans le **personnaliser** liste.  
  
     Inspectez la liste de **Arguments de méthode** et **propriétés de la classe** et notez qu’il existe deux **Arguments de méthode** et deux **propriétés de la classe**pour certaines colonnes de la table. Cela simplifie le suivi des modifications et la création des instructions qui vérifient les violations d'accès concurrentiel.  
  
13. Carte le **Original_CustomerID** argument de méthode à la **CustomerID (Original)** propriété de classe.  
  
    > [!NOTE]
    >  Par défaut, les arguments de méthode sont mappés à des propriétés de classe lorsque les noms correspondent. Si les noms de propriété sont modifiés et ne correspondent plus entre la table et la classe d'entité, vous devrez peut-être sélectionner la propriété de classe équivalente à mapper si le Concepteur O/R ne peut pas déterminer le mappage correct. En outre, si les arguments de méthode n’ont pas de propriétés de classe valide pour mapper à, vous pouvez définir le **propriétés de la classe** valeur **(aucun)**.  
  
14. Cliquez sur **appliquer** pour enregistrer la configuration de la classe et le comportement sélectionné.  
  
15. Sélectionnez **supprimer** dans le **comportement** liste.  
  
16. Sélectionnez **personnaliser**.  
  
17. Sélectionnez le **DeleteCustomers** méthode dans le **personnaliser** liste.  
  
18. Carte le **Original_CustomerID** argument de méthode à la **CustomerID (Original)** propriété de classe.  
  
19. Cliquez sur **OK**.  
  
> [!NOTE]
>  Bien qu'il ne s'agisse pas d'un problème pour cette procédure pas à pas, notez que [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] gère automatiquement les valeurs générées par une base de données pour les colonnes identity (incrémentation automatique), rowguidcol (GUID généré par la base de données) et timestamp lors des insertions et des mises à jour. Les valeurs générées par une base de données dans les autres types de colonne entraînent une valeur null de manière inopinée. Pour retourner les valeurs générées par une base de données, vous devez affecter la valeur <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> à `true` et l'une des valeurs suivantes à <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> : <xref:System.Data.Linq.Mapping.AutoSync>, <xref:System.Data.Linq.Mapping.AutoSync> ou <xref:System.Data.Linq.Mapping.AutoSync>.  
  
## <a name="testing-the-application"></a>Test de l'application  
 Exécutez l’application à nouveau pour vérifier que le **UpdateCustomers** procédure stockée met correctement à jour l’enregistrement de client dans la base de données.  
  
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
    >  Si votre application utilise SQL Server Express Edition, selon la valeur de la **Copy to Output Directory** propriété du fichier de base de données, les modifications n’apparaissent pas lorsque vous appuyez sur F5 à l’étape 10. Pour plus d’informations, consultez [Comment : gérer les fichiers de données Local dans votre projet](../data-tools/how-to-manage-local-data-files-in-your-project.md).  
  
## <a name="next-steps"></a>Étapes suivantes  
 Selon les exigences de votre application, vous pouvez effectuer différentes étapes après avoir créé des classes d’entité [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)]. Vous pouvez apporter à cette procédure pas à pas les améliorations suivantes :  
  
-   Implémenter la vérification des accès concurrentiels pendant les mises à jour. Pour plus d’informations, consultez [d’accès concurrentiel optimiste : vue d’ensemble](http://msdn.microsoft.com/library/c2e38512-d0c8-4807-b30a-cb7e30338694).  
  
-   Ajouter des requêtes LINQ pour filtrer des données. Pour plus d’informations, consultez [Introduction aux requêtes LINQ (c#)](http://msdn.microsoft.com/library/37895c02-268c-41d5-be39-f7d936fa88a8).  
  
## <a name="see-also"></a>Voir aussi  
 [Outils LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [Requêtes LINQ to SQL](http://msdn.microsoft.com/library/f4897aaa-7f44-4c20-a471-b948c2971aae)   
 [Méthodes DataContext (Concepteur O/R)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Comment : assigner des procédures stockées pour effectuer des mises à jour, insertions et suppressions (Concepteur O/R)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)   
 [PAVE quelles sont les nouveautés pour le développement d’applications de données dans Visual Studio 2012](http://msdn.microsoft.com/en-us/3d50d68f-5f44-4915-842f-6d42fce793f1)

