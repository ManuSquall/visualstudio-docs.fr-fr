---
title: 'Procédure pas à pas : Création des Classes LINQ to SQL à l’aide de l’héritage à Table unique (Concepteur O-R)'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
ms.assetid: 63bc6328-e0df-4655-9ce3-5ff74dbf69a4
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 8a21a84a9b8e96d771478415eae1a874d015572f
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34746284"
---
# <a name="walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-or-designer"></a>Procédure pas à pas : création de classes LINQ to SQL à l'aide d'un héritage de table individuelle (Concepteur O/R)
Le [LINQ to SQL Tools dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) prend en charge l’héritage à table unique tel qu’il est généralement implémenté dans les systèmes relationnels. Cette procédure pas à pas développe les étapes génériques fournis dans le [Comment : configurer l’héritage à l’aide du Concepteur O/R](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md) rubrique et fournit des données réelles pour illustrer l’utilisation de l’héritage dans le [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].

 Au cours de cette procédure, vous exécuterez les tâches suivantes :

-   Créer une table de base de données et ajouter des données.

-   Créer une application Windows Forms.

-   Ajouter un fichier [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] à un projet.

-   Créer de nouvelles classes d'entité.

-   Configurer les classes d'entité pour utiliser l'héritage.

-   Interroger la classe héritée.

-   Afficher les données sur un Windows Form.

## <a name="create-a-table-to-inherit-from"></a>Création d'une table de laquelle hériter
 Pour voir comment l'héritage fonctionne, vous allez créer une petite table Personnel que vous utiliserez comme classe de base, puis un objet Employé qui héritera de cette classe.

#### <a name="to-create-a-base-table-to-demonstrate-inheritance"></a>Pour créer une table de base illustrant l'héritage

1.  Dans **l’Explorateur de serveurs**/**l’Explorateur de base de données**, avec le bouton droit le **Tables** nœud et cliquez sur **ajouter une nouvelle Table**.

    > [!NOTE]
    >  Vous pouvez utiliser la base de données Northwind ou toute autre base de données à laquelle vous pouvez ajouter une table.

2.  Dans le Concepteur de tables, ajoutez les colonnes suivantes à la table :

    |Nom de la colonne|Type de données|Null autorisé|
    |-----------------|---------------|-----------------|
    |**ID**|**int**|**False**|
    |**Type**|**int**|**True**|
    |**Prénom**|**nvarchar(200)**|**False**|
    |**LastName**|**nvarchar(200)**|**False**|
    |**Gestionnaire**|**int**|**True**|

3.  Définissez la colonne d'ID comme clé primaire.

4.  Enregistrez la table et nommez-la **personne**.

## <a name="add-data-to-the-table"></a>Ajout de données à la table
 Pour pouvoir vérifier si l'héritage est configuré correctement, la table a besoin de données dans chaque classe de l'héritage à table unique.

#### <a name="to-add-data-to-the-table"></a>Pour ajouter des données à la table

1.  Ouvrez la table dans la vue de données. (Avec le bouton droit le **personne** table **l’Explorateur de serveurs**/**l’Explorateur de base de données** et cliquez sur **afficher les données de Table**.)

2.  Copiez les données suivantes dans la table. (Vous pouvez copier et coller ensuite dans la table en sélectionnant la ligne entière dans le volet de résultats.)

    ||||||
    |-|-|-|-|-|
    |**ID**|**Type**|**Prénom**|**LastName**|**Gestionnaire**|
    |**1**|**1**|**Anne**|**Wallace**|**NULL**|
    |**2**|**1**|**Carlos**|**Grilo**|**NULL**|
    |**3**|**1**|**Yael**|**Peled**|**NULL**|
    |**4**|**2**|**Gatis**|**Ozolins**|**1**|
    |**5**|**2**|**Andreas**|**Chor**|**1**|
    |**6**|**2**|**Tiffany**|**Phuvasate**|**1**|
    |**7**|**2**|**Alexey**|**Orekhov**|**2**|
    |**8**|**2**|**Michał**|**Poliszkiewicz**|**2**|
    |**9**|**2**|**Fin**|**YÉ**|**2**|
    |**10**|**2**|**Fabricio**|**Noriega**|**3**|
    |**11**|**2**|**Konstantinos**|**Martin**|**3**|
    |**12**|**2**|**Ken**|**Kwok**|**3**|

## <a name="create-a-new-project"></a>Création d'un projet
 Maintenant que vous avez créé la table, créez un nouveau projet pour voir la configuration de l'héritage.

#### <a name="to-create-the-new-windows-forms-application"></a>Pour créer la nouvelle Application Windows Forms

1. Dans Visual Studio, sur le **fichier** menu, sélectionnez **nouveau**, **projet...** .

2. Développez le **Visual C#** ou **Visual Basic** dans le volet gauche, puis sélectionnez **Windows Desktop**.

3. Dans le volet central, sélectionnez le **l’application Windows Forms** type de projet.

4. Nommez le projet **InheritanceWalkthrough**, puis choisissez **OK**.

     Le **InheritanceWalkthrough** projet est créé et ajouté à **l’Explorateur de solutions**.

## <a name="add-a-linq-to-sql-classes-file-to-the-project"></a>Ajout d'un fichier de classes LINQ to SQL au projet

#### <a name="to-add-a-linq-to-sql-file-to-the-project"></a>Pour ajouter un fichier LINQ to SQL au projet

1.  Dans le menu **Projet** , cliquez sur **Ajouter un nouvel élément**.

2.  Cliquez sur le **Classes LINQ to SQL** modèle, puis cliquez sur **ajouter**.

     Le fichier .dbml est ajouté au projet et le [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] s'ouvre.

## <a name="create-the-inheritance-by-using-the-or-designer"></a>Création de l'héritage avec le Concepteur O/R
 Configurez l’héritage en faisant glisser un **héritage** de l’objet à partir de la **boîte à outils** sur l’aire de conception.

#### <a name="to-create-the-inheritance"></a>Pour créer l'héritage

1.  Dans **l’Explorateur de serveurs**/**l’Explorateur de base de données**, accédez à la **personne** table que vous avez créé précédemment.

2.  Faites glisser le **personne** table sur le [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] aire de conception.

3.  Faites glisser un deuxième **personne** table sur le [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] et remplacez son nom par **employé**.

4.  Supprimer le **Manager** propriété à partir de la **personne** objet.

5.  Supprimer le **Type**, **ID**, **FirstName**, et **LastName** propriétés à partir de la **employé** objet. (En d’autres termes, supprimez toutes les propriétés à l’exception de **Manager**.)

6.  À partir de la **concepteur objet/relationnel** onglet de la **boîte à outils**, créer un **héritage** entre les **personne** et  **Employé** objets. Pour ce faire, cliquez sur le **héritage** d’élément dans le **boîte à outils** et relâchez le bouton de la souris. Ensuite, cliquez sur le **employé** objet, puis le **personne** de l’objet dans le [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. La flèche sur la ligne d’héritage pointe sur le **personne** objet.

7.  Cliquez sur le **héritage** ligne sur l’aire de conception.

8.  Définir le **propriété de discriminateur** propriété **Type**.

9. Définir le **valeur de discriminateur de classe dérivée** propriété **2**.

10. Définir le **valeur de discriminateur de classe de Base** propriété **1**.

11. Définir le **d’héritage par défaut** propriété **personne**.

12. Générez le projet.

## <a name="query-the-inherited-class-and-display-the-data-on-the-form"></a>Interrogation de la classe héritée et affichage des données sur le formulaire
 Vous ajouterez maintenant du code au formulaire qui interroge une classe spécifique dans le modèle objet.

#### <a name="to-create-a-linq-query-and-display-the-results-on-the-form"></a>Pour créer une requête LINQ et afficher les résultats sur le formulaire

1.  Faites glisser un **ListBox** vers Form1.

2.  Double-cliquez sur le formulaire pour créer un gestionnaire d'événements `Form1_Load`.

3.  Ajoutez le code suivant au gestionnaire d'événements `Form1_Load` :

    ```vb
    Dim dc As New DataClasses1DataContext
    Dim results = From emp In dc.Persons _
        Where TypeOf emp Is Employee _
        Select emp

    For Each Emp As Employee In results
        ListBox1.Items.Add(Emp.LastName)
    Next
    ```

    ```csharp
    NorthwindDataContext dc = new DataClasses1DataContext();
    var results = from emp in dc.Persons
                  where emp is Employee
                  select emp;

    foreach(Employee Emp in results)
    {
        listBox1.Items.Add(Emp.LastName)
    }
    ```

## <a name="test-the-application"></a>Test de l'application
 Exécutez l'application et vérifiez que les enregistrements affichés dans la zone de liste sont tous des employés (enregistrements qui ont une valeur 2 dans leur colonne de type).

#### <a name="to-test-the-application"></a>Pour tester l'application

1.  Appuyez sur F5.

2.  Vérifiez que seuls les enregistrements qui ont une valeur 2 dans leur colonne de type sont affichés.

3.  Fermez le formulaire. (Sur le **déboguer** menu, cliquez sur **arrêter le débogage**.)

## <a name="see-also"></a>Voir aussi

- [Outils LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Procédure pas à pas : Création des Classes LINQ to SQL (Concepteur O-R)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [Comment : assigner des procédures stockées pour effectuer des mises à jour, insertions et suppressions (Concepteur O/R)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Guide pratique pour générer le modèle objet en Visual Basic ou C#](/dotnet/framework/data/adonet/sql/linq/how-to-generate-the-object-model-in-visual-basic-or-csharp)