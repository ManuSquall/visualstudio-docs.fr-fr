---
title: 'Procédure pas à pas : Création des Classes LINQ to SQL à l’aide d’héritage à Table unique (Concepteur O-R) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 63bc6328-e0df-4655-9ce3-5ff74dbf69a4
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a7dfd293f5b2219eab6c3a2896c800a1337f2c8c
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60111972"
---
# <a name="walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-or-designer"></a>Procédure pas à pas : Création des Classes LINQ to SQL à l’aide d’héritage à Table unique (Concepteur O/R)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le [outils LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) prend en charge l’héritage à table unique tel qu’il est généralement implémenté dans les systèmes relationnels. Cette procédure pas à pas développe les étapes génériques fournies dans le [Comment : Configurer l’héritage à l’aide du Concepteur O/R](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md) rubrique et des données réelles pour illustrer l’utilisation de l’héritage dans le [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].  
  
 Au cours de cette procédure, vous exécuterez les tâches suivantes :  
  
- Créer une table de base de données et ajouter des données.  
  
- Créer une application Windows Forms.  
  
- Ajouter un fichier [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] à un projet.  
  
- Créer de nouvelles classes d'entité.  
  
- Configurer les classes d'entité pour utiliser l'héritage.  
  
- Interroger la classe héritée.  
  
- Afficher les données sur un Windows Form.  
  
## <a name="create-a-table-to-inherit-from"></a>Création d'une table de laquelle hériter  
 Pour voir comment l'héritage fonctionne, vous allez créer une petite table Personnel que vous utiliserez comme classe de base, puis un objet Employé qui héritera de cette classe.  
  
#### <a name="to-create-a-base-table-to-demonstrate-inheritance"></a>Pour créer une table de base illustrant l'héritage  
  
1. Dans **Explorateur de serveurs**/**Database Explorer**, avec le bouton droit le **Tables** nœud et cliquez sur **ajouter une nouvelle Table**.  
  
    > [!NOTE]
    >  Vous pouvez utiliser la base de données Northwind ou toute autre base de données à laquelle vous pouvez ajouter une table.  
  
2. Dans le Concepteur de tables, ajoutez les colonnes suivantes à la table :  
  
    |Nom de la colonne|Type de données|Null autorisé|  
    |-----------------|---------------|-----------------|  
    |**ID**|**int**|**False**|  
    |**Type**|**int**|**True**|  
    |**FirstName**|**nvarchar(200)**|**False**|  
    |**LastName**|**nvarchar(200)**|**False**|  
    |**Manager**|**int**|**True**|  
  
3. Définissez la colonne d'ID comme clé primaire.  
  
4. Enregistrez la table et nommez-la **Personnel**.  
  
## <a name="add-data-to-the-table"></a>Ajout de données à la table  
 Pour pouvoir vérifier si l'héritage est configuré correctement, la table a besoin de données dans chaque classe de l'héritage à table unique.  
  
#### <a name="to-add-data-to-the-table"></a>Pour ajouter des données à la table  
  
1. Ouvrez la table dans la vue de données. (Avec le bouton droit le **personne** table **Explorateur de serveurs**/**Database Explorer** et cliquez sur **afficher les données de Table**.)  
  
2. Copiez les données suivantes dans la table. (Vous pourrez copiez-la et collez-la dans la table en sélectionnant la ligne entière dans le volet de résultats.)  
  
    ||||||  
    |-|-|-|-|-|  
    |**ID**|**Type**|**FirstName**|**LastName**|**Manager**|  
    |**1**|**1**|**Anne**|**Wallace**|**NULL**|  
    |**2**|**1**|**Carlos**|**Grilo**|**NULL**|  
    |**3**|**1**|**Yael**|**Peled**|**NULL**|  
    |**4**|**2**|**Gatis**|**Ozolins**|**1**|  
    |**5**|**2**|**Andreas**|**Hauser**|**1**|  
    |**6**|**2**|**Tiffany**|**Phuvasate**|**1**|  
    |**7**|**2**|**Alexey**|**Orekhov**|**2**|  
    |**8**|**2**|**Michał**|**Poliszkiewicz**|**2**|  
    |**9**|**2**|**Tai**|**Yee**|**2**|  
    |**10**|**2**|**Fabricio**|**Noriega**|**3**|  
    |**11**|**2**|**Mindy**|**Martin**|**3**|  
    |**12**|**2**|**Ken**|**Kwok**|**3**|  
  
## <a name="create-a-new-project"></a>Création d'un projet  
 Maintenant que vous avez créé la table, créez un nouveau projet pour voir la configuration de l'héritage.  
  
#### <a name="to-create-the-new-windows-application"></a>Pour créer une application Windows  
  
1. À partir de la **fichier** menu, créez un nouveau projet.  
  
2. Nommez le projet **InheritanceWalkthrough**.  
  
    > [!NOTE]
    >  Le [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] est pris en charge dans les projets Visual Basic et C#. Créez le projet dans l'un de ces langages.  
  
3. Cliquez sur le **Windows Forms Application** modèle, puis cliquez sur **OK**. Pour plus d’informations, consultez [les Applications clientes](http://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).  
  
4. Le projet InheritanceWalkthrough est créé et ajouté à **l’Explorateur de solutions**.  
  
## <a name="add-a-linq-to-sql-classes-file-to-the-project"></a>Ajout d'un fichier de classes LINQ to SQL au projet  
  
#### <a name="to-add-a-linq-to-sql-file-to-the-project"></a>Pour ajouter un fichier LINQ to SQL au projet  
  
1. Dans le menu **Projet** , cliquez sur **Ajouter un nouvel élément**.  
  
2. Cliquez sur le modèle **Classes LINQ to SQL**, puis sur **Ajouter**.  
  
     Le fichier .dbml est ajouté au projet et le [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] s'ouvre.  
  
## <a name="create-the-inheritance-by-using-the-or-designer"></a>Création de l'héritage avec le Concepteur O/R  
 Configurez l’héritage en faisant glisser un objet **Héritage** de la **Boîte à outils** vers l’aire de conception.  
  
#### <a name="to-create-the-inheritance"></a>Pour créer l'héritage  
  
1. Dans **Explorateur de serveurs**/**Database Explorer**, accédez à la **personne** table que vous avez créé précédemment.  
  
2. Faites glisser le **personne** table sur le [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] aire de conception.  
  
3. Faites glisser un deuxième **personne** table sur le [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] et remplacez son nom par **employé**.  
  
4. Supprimez la propriété **Manager** de l’objet **Personnel**.  
  
5. Supprimez les propriétés **Type**, **ID**, **FirstName** et **LastName** de l’objet **Employé**. (En d’autres termes, supprimez toutes les propriétés à l’exception de **Manager**.)  
  
6. À partir de l’onglet **Concepteur Objet Relationnel** de la **Boîte à outils**, créez un **Héritage** entre les objets **Personnel** et **Employé**. Pour cela, cliquez sur l’élément **Héritage** dans la **Boîte à outils** et relâchez le bouton de la souris. Ensuite, cliquez sur le **employé** objet, puis le **personne** de l’objet dans le [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. La flèche sur la ligne d’héritage pointe sur le **personne** objet.  
  
7. Cliquez sur la ligne **Héritage** dans l’aire de conception.  
  
8. Affectez à **Propriété de discriminateur** la valeur **Type**.  
  
9. Affectez à la propriété **Valeur de discriminateur de classe dérivée** la valeur **2**.  
  
10. Affectez à la propriété **Valeur de discriminateur de classe de base** la valeur **1**.  
  
11. Affectez à la propriété **Héritage par défaut** la valeur **Personnel**.  
  
12. Générez le projet.  
  
## <a name="query-the-inherited-class-and-display-the-data-on-the-form"></a>Interrogation de la classe héritée et affichage des données sur le formulaire  
 Vous ajouterez maintenant du code au formulaire qui interroge une classe spécifique dans le modèle objet.  
  
#### <a name="to-create-a-linq-query-and-display-the-results-on-the-form"></a>Pour créer une requête LINQ et afficher les résultats sur le formulaire  
  
1. Faites glisser un **ListBox** vers Form1.  
  
2. Double-cliquez sur le formulaire pour créer un gestionnaire d'événements `Form1_Load`.  
  
3. Ajoutez le code suivant au gestionnaire d'événements `Form1_Load` :  
  
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
  
1. Appuyez sur F5.  
  
2. Vérifiez que seuls les enregistrements qui ont une valeur 2 dans leur colonne de type sont affichés.  
  
3. Fermez le formulaire. (Dans le menu **Déboguer**, cliquez sur **Arrêter le débogage**.)  
  
## <a name="see-also"></a>Voir aussi  
 [Outils LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Guide pratique pour Ajouter LINQ to SQL Classes à un projet (Concepteur O-R)](http://msdn.microsoft.com/library/7bb184ab-ec54-4cda-b706-604b2b4a3ed6)   
 [Procédure pas à pas : Création des Classes LINQ to SQL (Concepteur O-R)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)   
 [Guide pratique pour Assigner des procédures stockées pour effectuer des mises à jour, insertions et suppressions (Concepteur O/R)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [Guide pratique pour générer le modèle objet en Visual Basic ou C#](http://msdn.microsoft.com/library/a0c73b33-5650-420c-b9dc-f49310c201ee)
