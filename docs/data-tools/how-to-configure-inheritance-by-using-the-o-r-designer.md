---
title: "Proc&#233;dure&#160;: configurer l&#39;h&#233;ritage &#224; l&#39;aide du Concepteur O/R | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e594af12-e777-434a-bc08-7dd2dac84cdc
caps.latest.revision: 4
caps.handback.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Proc&#233;dure&#160;: configurer l&#39;h&#233;ritage &#224; l&#39;aide du Concepteur O/R
Le [!INCLUDE[vs_ordesigner_long](../data-tools/includes/vs_ordesigner_long_md.md)] \([!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]\) prend en charge le concept d'héritage à table unique tel qu'il est souvent implémenté dans les systèmes relationnels. L'héritage à table unique fait appel à une seule table de base de données qui contient des champs pour les informations parent et enfant.Avec les données relationnelles, une colonne de discriminateur contient la valeur qui détermine à quelle classe tout enregistrement appartient.  
  
 Prenons par exemple une table Persons qui contient tous les employées d'une société.Certaines personnes sont des employés et d'autres des responsables.La table Persons contient une colonne nommée `EmployeeType` qui a une valeur de 1 pour les responsables et une valeur de 2 pour les employés ; c'est la colonne de discriminateur.Dans ce scénario, vous pouvez créer une sous\-classe d'employés et remplir la classe avec uniquement des enregistrements ayant une valeur `EmployeeType` de 2.Vous pouvez également supprimer les colonnes qui ne s'appliquent à aucune de ces classes.  
  
 La création d'un modèle objet qui utilise l'héritage \(et correspond aux données relationnelles\) peut prêter à confusion.La procédure suivante esquisse les étapes requises pour configurer l'héritage avec le Concepteur O\/R.Suivre les étapes génériques sans faire référence à une table existante et aux colonnes risque d'être difficile, c'est pourquoi une procédure pas à pas utilisant des données vous est proposée.Pour plus d'informations sur la configuration d'un héritage à l'aide du [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], consultez [Procédure pas à pas : création de classes LINQ to SQL à l'aide de l'héritage à table unique \(Concepteur O\/R\)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md).  
  
### Pour créer des classes de données héritées  
  
1.  Ouvrez le [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] en ajoutant un élément **Classes LINQ to SQL** à un projet Visual Basic ou C\# existant.  
  
2.  Faites glisser la table à utiliser comme classe de base vers le [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
3.  Faites glisser une deuxième copie de la table vers le [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] et renommez\-la.C'est la classe dérivée, ou sous\-classe.  
  
4.  Cliquez sur **Héritage** sous l'onglet **Concepteur Objet\/Relationnel** de la **Boîte à outils**, puis cliquez sur la sous\-classe \(la table que vous avez renommée\) et connectez\-la à la classe de base.  
  
    > [!NOTE]
    >  Cliquez sur l'élément **Héritage** dans la **Boîte à outils** et relâchez le bouton de la souris, cliquez sur la seconde copie de la classe que vous avez créée à l'étape 3, puis cliquez sur la première classe que vous avez créée à l'étape 2.La flèche sur la ligne d'héritage pointe sur la première classe.  
  
5.  Dans chaque classe, supprimez toutes les propriétés d'objet que vous ne souhaitez pas voir apparaître et qui ne sont pas utilisées pour des associations.Vous recevrez un message d'erreur si vous tentez de supprimer des propriétés d'objet utilisées pour des associations : [Impossible de supprimer la propriété \<nom de la propriété\> car elle participe à l'association \<nom de l'association\>](../data-tools/the-property-property-name-cannot-be-deleted-because-it-is-participating-in-the-association-association-name.md).  
  
    > [!NOTE]
    >  Comme une classe dérivée hérite des propriétés définies dans sa classe de base, les mêmes colonnes ne peuvent pas être définies dans chaque classe.\(Les colonnes sont implémentées sous forme de propriétés.\) Vous pouvez activer la création de colonnes dans la classe dérivée en définissant le Modificateur d'héritage sur la propriété dans la classe de base.Pour plus d'informations, consultez [NOT IN BUILD: Overriding Properties and Methods](http://msdn.microsoft.com/fr-fr/2167e8f5-1225-4b13-9ebd-02591ba90213).  
  
6.  Sélectionnez la ligne d'héritage dans le [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
7.  Dans la fenêtre **Propriétés**, affectez à **Propriété du discriminateur** le nom de colonne utilisée pour distinguer les enregistrements dans vos classes.  
  
8.  Affectez à la propriété **Valeur de discriminateur de classe dérivée** la valeur dans la base de données qui désigne l'enregistrement comme type hérité.\(Il s'agit de la valeur stockée dans la colonne de discriminateur et qui est utilisée pour désigner la classe héritée.\)  
  
9. Affectez à la propriété **Valeur de discriminateur de classe de base** la valeur qui désigne l'enregistrement comme type de base.\(Il s'agit de la valeur stockée dans la colonne de discriminateur et qui est utilisée pour désigner la classe de base.\)  
  
10. En option, vous pouvez également affecter à la propriété **Valeur d'héritage par défaut** la désignation d'un type dans une hiérarchie d'héritage utilisée lors du chargement des lignes ne correspondant à aucun code d'héritage défini.En d'autres termes, si une valeur dans la colonne de discriminateur d'un enregistrement ne correspond pas à la valeur de la propriété **Valeur de discriminateur de classe dérivée** ou **Valeur de discriminateur de classe de base**, l'enregistrement se charge selon le type désigné comme **Valeur d'héritage par défaut**.  
  
## Voir aussi  
 [Vue d'ensemble du Concepteur O\/R](../Topic/LINQ%20to%20SQL%20Tools%20in%20Visual%20Studio1.md)   
 [Procédure pas à pas : création de classes LINQ to SQL \(Concepteur O\/R\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)   
 [PAVE What's New for Data Application Development in Visual Studio 2012](http://msdn.microsoft.com/fr-fr/3d50d68f-5f44-4915-842f-6d42fce793f1)   
 [Accès aux données dans Visual Studio](../data-tools/accessing-data-in-visual-studio.md)   
 [LINQ à SQL](../Topic/LINQ%20to%20SQL.md)   
 [Procédure pas à pas : création de classes LINQ to SQL à l'aide de l'héritage à table unique \(Concepteur O\/R\)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)   
 [NOT IN BUILD: Inheritance in Visual Basic](http://msdn.microsoft.com/fr-fr/e5e6e240-ed31-4657-820c-079b7c79313c)   
 [Héritage](/dotnet/csharp/programming-guide/classes-and-structs/inheritance)