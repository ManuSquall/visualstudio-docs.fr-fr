---
title: 'Comment : configurer l’héritage à l’aide du Concepteur O-R'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e594af12-e777-434a-bc08-7dd2dac84cdc
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 8808100d2576a4b14b02975d49606ef5b215c216
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31925373"
---
# <a name="how-to-configure-inheritance-by-using-the-or-designer"></a>Comment : configurer l’héritage à l’aide du Concepteur O/R
L'[!INCLUDE[vs_ordesigner_long](../data-tools/includes/vs_ordesigner_long_md.md)] ([!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]) prend en charge le concept d'héritage à table unique qui est souvent implémenté dans les systèmes relationnels. L'héritage à table unique fait appel à une seule table de base de données qui contient des champs pour les informations parent et enfant. Avec les données relationnelles, une colonne de discriminateur contient la valeur qui détermine à quelle classe tout enregistrement appartient.

Prenons par exemple une table Persons qui contient tous les employées d'une société. Certaines personnes sont des employés et d'autres des responsables. La table Persons contient une colonne nommée `EmployeeType` qui a une valeur de 1 pour les responsables et une valeur de 2 pour les employés ; c'est la colonne de discriminateur. Dans ce scénario, vous pouvez créer une sous-classe d'employés et remplir la classe avec uniquement des enregistrements ayant une valeur `EmployeeType` de 2. Vous pouvez également supprimer les colonnes qui ne s'appliquent à aucune de ces classes.

La création d'un modèle objet qui utilise l'héritage (et correspond aux données relationnelles) peut prêter à confusion. La procédure suivante esquisse les étapes requises pour configurer l'héritage avec le Concepteur O/R. Suivre les étapes génériques sans faire référence à une table existante et aux colonnes risque d'être difficile, c'est pourquoi une procédure pas à pas utilisant des données vous est proposée. Pour obtenir des instructions détaillées pour configurer l’héritage à l’aide de la [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], consultez [procédure pas à pas : création de Classes LINQ to SQL par héritage à Table unique (Concepteur O/R) à l’aide de](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md).

## <a name="to-create-inherited-data-classes"></a>Pour créer des classes de données héritées

1.  Ouvrez le [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] en ajoutant un **Classes LINQ to SQL** élément à un projet Visual Basic ou c# existant.

2.  Faites glisser la table à utiliser comme classe de base vers le [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].

3.  Faites glisser une deuxième copie de la table vers le [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] et renommez-la. C'est la classe dérivée, ou sous-classe.

4.  Cliquez sur **héritage** dans les **concepteur objet/relationnel** onglet de la **boîte à outils**, puis cliquez sur la sous-classe (la table que vous avez renommé) et connectez-la à la classe de base.

    > [!NOTE]
    >  Cliquez sur le **héritage** d’élément dans le **boîte à outils** et relâchez le bouton de la souris, cliquez sur la deuxième copie de la classe que vous avez créé à l’étape 3, puis cliquez sur la première classe que vous avez créé à l’étape 2. La flèche sur la ligne d'héritage pointe sur la première classe.

5.  Dans chaque classe, supprimez toutes les propriétés d'objet que vous ne souhaitez pas voir apparaître et qui ne sont pas utilisées pour des associations. Vous recevez une erreur si vous tentez de supprimer les propriétés de l’objet utilisées pour les associations : [la propriété \<nom de la propriété > ne peut pas être supprimé, car il participe à l’association \<nom de l’association >](../data-tools/the-property-property-name-cannot-be-deleted-because-it-is-participating-in-the-association-association-name.md).

    > [!NOTE]
    >  Comme une classe dérivée hérite des propriétés définies dans sa classe de base, les mêmes colonnes ne peuvent pas être définies dans chaque classe. (Les colonnes sont implémentées sous forme de propriétés.) Vous pouvez activer la création de colonnes dans la classe dérivée en définissant le Modificateur d'héritage sur la propriété dans la classe de base. Pour plus d’informations, consultez [fondamentaux de l’héritage (Visual Basic)](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics).

6.  Sélectionnez la ligne d'héritage dans le [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].

7.  Dans le **propriétés** , configurez la **propriété de discriminateur** au nom de colonne qui est utilisé pour distinguer les enregistrements dans vos classes.

8.  Définir le **valeur de discriminateur de classe dérivée** valeur à la propriété dans la base de données qui désigne l’enregistrement comme type hérité. (Il s'agit de la valeur stockée dans la colonne de discriminateur et qui est utilisée pour désigner la classe héritée.)

9. Définir le **valeur de discriminateur de classe de Base** valeur à la propriété qui désigne l’enregistrement comme type de base. (Il s'agit de la valeur stockée dans la colonne de discriminateur et qui est utilisée pour désigner la classe de base.)

10. Si vous le souhaitez, vous pouvez également définir le **d’héritage par défaut** propriété pour désigner un type dans une hiérarchie d’héritage qui est utilisé lorsque le chargement des lignes qui ne correspondent pas à un code d’héritage défini. En d’autres termes, si un enregistrement a une valeur dans la colonne de discriminateur qui ne correspond pas la valeur de la **valeur de discriminateur de classe dérivée** ou **valeur de discriminateur de classe de Base** propriétés, l’enregistrement se charge selon le type désigné comme le **d’héritage par défaut**.

## <a name="see-also"></a>Voir aussi

- [Outils LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Procédure pas à pas : Création des Classes LINQ to SQL (Concepteur O-R)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [Accès aux données dans Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Procédure pas à pas : Création des Classes LINQ to SQL à l’aide de l’héritage à Table unique (Concepteur O/R)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)
- [Principes fondamentaux de l’héritage (Visual Basic)](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)
- [Héritage](/dotnet/csharp/programming-guide/classes-and-structs/inheritance)