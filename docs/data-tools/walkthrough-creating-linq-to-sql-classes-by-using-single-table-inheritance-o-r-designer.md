---
title: "Proc&#233;dure pas &#224; pas&#160;: cr&#233;ation de classes LINQ to SQL &#224; l&#39;aide de l&#39;h&#233;ritage &#224; table unique (Concepteur&#160;O/R) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 63bc6328-e0df-4655-9ce3-5ff74dbf69a4
caps.latest.revision: 4
caps.handback.revision: 1
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Proc&#233;dure pas &#224; pas&#160;: cr&#233;ation de classes LINQ to SQL &#224; l&#39;aide de l&#39;h&#233;ritage &#224; table unique (Concepteur&#160;O/R)
Tel qu'il est implémenté dans les systèmes relationnels, le [Concepteur Objet\/Relationnel \(Concepteur O\/R\)](../data-tools/linq-to-sql-tools-in-visual-studio2.md) prend en charge l'héritage à table unique.Cette procédure pas à pas se développe à partir des étapes génériques fournies dans la rubrique [Procédure : configurer l'héritage à l'aide du Concepteur O\/R](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md) et illustre l'utilisation d'héritage dans le [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] par des données réelles.  
  
 Au cours de cette procédure, vous exécuterez les tâches suivantes :  
  
-   Créer une table de base de données et ajouter des données.  
  
-   Créer une application Windows Forms.  
  
-   Ajouter un fichier [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] à un projet.  
  
-   Créer de nouvelles classes d'entité.  
  
-   Configurer les classes d'entité pour utiliser l'héritage.  
  
-   Interroger la classe héritée.  
  
-   Afficher les données sur un Windows Form.  
  
## Création d'une table de laquelle hériter  
 Pour voir comment l'héritage fonctionne, vous allez créer une petite table Personnel que vous utiliserez comme classe de base, puis un objet Employé qui héritera de cette classe.  
  
#### Pour créer une table de base illustrant l'héritage  
  
1.  Dans l'**Explorateur de serveurs**\/**Explorateur de bases de données**, cliquez avec le bouton droit sur le nœud **Tables** et cliquez **Ajouter une nouvelle table**.  
  
    > [!NOTE]
    >  Vous pouvez utiliser la base de données Northwind ou toute autre base de données à laquelle vous pouvez ajouter une table.  
  
2.  Dans le Concepteur de tables, ajoutez les colonnes suivantes à la table :  
  
    |Nom de la colonne|Type de données|Null autorisé|  
    |-----------------------|---------------------|-------------------|  
    |ID|int|False|  
    |Type|int|True|  
    |FirstName|nvarchar\(200\)|False|  
    |LastName|nvarchar\(200\)|False|  
    |Manager|int|True|  
  
3.  Définissez la colonne d'ID comme clé primaire.  
  
4.  Enregistrez la table et dénommez\-la Personnel.  
  
## Ajout de données à la table  
 Pour pouvoir vérifier si l'héritage est configuré correctement, la table a besoin de données dans chaque classe de l'héritage à table unique.  
  
#### Pour ajouter des données à la table  
  
1.  Ouvrez la table dans la vue de données.\(Cliquez avec le bouton droit sur la table **Personnel** dans l'**Explorateur de serveurs**\/**Explorateur de bases de données** et cliquez sur **Afficher les données de la table**.\)  
  
2.  Copiez les données suivantes dans la table.\(Vous pouvez les copier puis les coller dans la table en sélectionnant la ligne entière dans le [Results Pane](http://msdn.microsoft.com/fr-fr/3c712f20-7c9f-4021-b1ac-fdc6f534c95a).\)  
  
    ||||||  
    |-|-|-|-|-|  
    |ID|Type|FirstName|LastName|Manager|  
    |1|1|Anne|Wallace|NULL|  
    |2|1|Carlos|Grilo|NULL|  
    |3|1|Yael|Peled|NULL|  
    |4|2|Gatis|Ozolins|1|  
    |5|2|Andreas|Hauser|1|  
    |6|2|Tiffany|Phuvasate|1|  
    |7|2|Alexey|Orekhov|2|  
    |8|2|Michał|Poliszkiewicz|2|  
    |9|2|Tai|Yee|2|  
    |10|2|Fabricio|Noriega|3|  
    |11|2|Mindy|Martin|3|  
    |12|2|Ken|Kwok|3|  
  
## Création d'un projet  
 Maintenant que vous avez créé la table, créez un nouveau projet pour voir la configuration de l'héritage.  
  
#### Pour créer une application Windows  
  
1.  Dans le menu **Fichier**, créez un nouveau projet.  
  
2.  Nommez le projet InheritanceWalkthrough.  
  
    > [!NOTE]
    >  Le [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] est pris en charge dans les projets Visual Basic et C\#.Vous pouvez donc créer le projet dans l'un ou l'autre de ces langages.  
  
3.  Cliquez sur le modèle **Application Windows Forms**, puis sur **OK**.Pour plus d'informations, consultez [Applications clientes](../Topic/Developing%20Client%20Applications%20with%20the%20.NET%20Framework.md).  
  
4.  Le projet InheritanceWalkthrough est créé et ajouté à l'**Explorateur de solutions**.  
  
## Ajout d'un fichier de classes LINQ to SQL au projet  
  
#### Pour ajouter un fichier LINQ to SQL au projet  
  
1.  Dans le menu **Projet**, cliquez sur **Ajouter un nouvel élément**.  
  
2.  Cliquez sur le modèle **Classes LINQ to SQL**, puis cliquez sur **Ajouter**.  
  
     Le fichier .dbml est ajouté au projet et le [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] s'ouvre.  
  
## Création de l'héritage avec le Concepteur O\/R  
 Configurez l'héritage en faisant glisser un objet **Héritage** de la **Boîte à outils** vers l'aire de conception.  
  
#### Pour créer l'héritage  
  
1.  Dans l'**Explorateur de serveurs**\/**Explorateur de bases de données**, naviguez vers la table **Personnel** que vous avez créée précédemment.  
  
2.  Faites glisser la table **Personnel** sur l'aire de conception du [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
3.  Faites glisser un deuxième tableau **Personnel** dans le [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] et modifiez son nom en Employé.  
  
4.  Supprimez la propriété **Manager** de l'objet **Personnel**.  
  
5.  Supprimez les propriétés **Type**, **ID**, **FirstName**et **LastName** de l'objet **Employé**.\(En d'autres termes, supprimez toutes les propriétés à l'exception de **Manager**.\)  
  
6.  À partir de l'onglet **Concepteur Objet\/Relationnel** de la **Boîte à outils**, créez un **Héritage** entre les objets **Personnel** et **Employé**.Pour cela, cliquez sur l'élément **Héritage** dans la **Boîte à outils** et relâchez le bouton de la souris.Ensuite, cliquez sur l'objet **Employé**, puis sur l'objet **Personnel** dans le [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].La flèche sur la ligne d'héritage pointe sur l'objet **Personnel**.  
  
7.  Cliquez sur la ligne **Héritage** dans l'aire de conception.  
  
8.  Affectez à **Propriété de discriminateur**  la valeur **Type**.  
  
9. Affectez à la propriété **Valeur Discriminatoire de la classe dérivée** la valeur **2**.  
  
10. Affectez à la propriété **Valeur discriminatoire de la classe de base** la valeur **1**.  
  
11. Affectez à la propriété **Héritage par défaut** la valeur **Personnel**.  
  
12. Générez le projet.  
  
## Interrogation de la classe héritée et affichage des données sur le formulaire  
 Vous ajouterez maintenant du code au formulaire qui interroge une classe spécifique dans le modèle objet.  
  
#### Pour créer une requête LINQ et afficher les résultats sur le formulaire  
  
1.  Faites glisser une **Zone de liste** sur Form1.  
  
2.  Double\-cliquez sur le formulaire pour créer un gestionnaire d'événements `Form1_Load`.  
  
3.  Ajoutez le code suivant au gestionnaire d'événements `Form1_Load` :  
  
    ```vb#  
    Dim dc As New DataClasses1DataContext  
    Dim results = From emp In dc.Persons _  
        Where TypeOf emp Is Employee _  
        Select emp  
  
    For Each Emp As Employee In results  
        ListBox1.Items.Add(Emp.LastName)  
    Next  
    ```  
  
    ```c#  
    NorthwindDataContext dc = new DataClasses1DataContext();  
    var results = from emp in dc.Persons  
                  where emp is Employee  
                  select emp;  
  
    foreach(Employee Emp in results)  
    {  
        listBox1.Items.Add(Emp.LastName)  
    }  
    ```  
  
## Test de l'application  
 Exécutez l'application et vérifiez que les enregistrements affichés dans la zone de liste sont tous des employés \(enregistrements qui ont une valeur 2 dans leur colonne de type\).  
  
#### Pour tester l'application  
  
1.  Appuyez sur F5.  
  
2.  Vérifiez que seuls les enregistrements qui ont une valeur 2 dans leur colonne de type sont affichés.  
  
3.  Fermez le formulaire.Dans le menu **Déboguer**, cliquez sur **Arrêter le débogage**.  
  
## Voir aussi  
 [Vue d'ensemble du Concepteur O\/R](../Topic/LINQ%20to%20SQL%20Tools%20in%20Visual%20Studio1.md)   
 [Procédure : ajouter des classes LINQ to SQL à un projet \(Concepteur O\/R\)](../Topic/How%20to:%20Add%20LINQ%20to%20SQL%20Classes%20to%20a%20Project%20\(O-R%20Designer\).md)   
 [Procédure pas à pas : création de classes LINQ to SQL \(Concepteur O\/R\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)   
 [Procédure : assigner des procédures stockées pour effectuer des mises à jour, des insertions et des suppressions \(Concepteur O\/R\)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)   
 [LINQ à SQL](../Topic/LINQ%20to%20SQL.md)   
 [Procédure : générer le modèle objet en Visual Basic ou C\#](../Topic/How%20to:%20Generate%20the%20Object%20Model%20in%20Visual%20Basic%20or%20C%23.md)