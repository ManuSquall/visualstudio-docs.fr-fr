---
title: configurer l’héritage à l’aide du Concepteur O-R
description: Découvrez comment configurer l’héritage à l’aide du Concepteur Objet Relationnel (Concepteur O/R), qui prend en charge l’héritage d’une seule table. Classes de données héritées créées.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: e594af12-e777-434a-bc08-7dd2dac84cdc
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: fee2c42e6ec84280f4090a8ae1dfea83a81ee369
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99866825"
---
# <a name="how-to-configure-inheritance-by-using-the-or-designer"></a>Guide pratique pour configurer l’héritage à l’aide du Concepteur O/R
Le **Concepteur Objet Relationnel** (**Concepteur O/R**) prend en charge le concept d’héritage de table unique, car il est souvent implémenté dans les systèmes relationnels. L'héritage à table unique fait appel à une seule table de base de données qui contient des champs pour les informations parent et enfant. Avec les données relationnelles, une colonne de discriminateur contient la valeur qui détermine à quelle classe tout enregistrement appartient.

Prenons l’exemple d’une `Persons` table qui contient tout le monde employé par une société. Certaines personnes sont des employés et d'autres des responsables. La `Persons` table contient une colonne nommée `EmployeeType` qui a une valeur de 1 pour les responsables et une valeur de 2 pour les employés ; il s’agit de la colonne de discriminateur. Dans ce scénario, vous pouvez créer une sous-classe d'employés et remplir la classe avec uniquement des enregistrements ayant une valeur `EmployeeType` de 2. Vous pouvez également supprimer les colonnes qui ne s'appliquent à aucune de ces classes.

La création d'un modèle objet qui utilise l'héritage (et correspond aux données relationnelles) peut prêter à confusion. La procédure suivante décrit les étapes requises pour configurer l’héritage avec le **Concepteur O/R**. Les étapes génériques suivantes sans référence à une table et des colonnes existantes peuvent être difficiles, donc une procédure pas à pas qui utilise des données est fournie. Pour obtenir des instructions détaillées sur la configuration de l’héritage à l’aide du **Concepteur o/r**, consultez [procédure pas à pas : création de LINQ to SQL classes à l’aide de l’héritage de table unique (concepteur o/r)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md).

## <a name="to-create-inherited-data-classes"></a>Pour créer des classes de données héritées

1. Ouvrez le **Concepteur O/R** en ajoutant un élément **LINQ to SQL classes** à un projet Visual Basic ou C# existant.

2. Faites glisser la table que vous souhaitez utiliser comme classe de base vers le **Concepteur O/R**.

3. Faites glisser une deuxième copie de la table vers le **Concepteur O/R** et renommez-la. C'est la classe dérivée, ou sous-classe.

4. Cliquez sur **Héritage** sous l’onglet **Concepteur Objet Relationnel** de la **Boîte à outils**, puis sur la sous-classe (la table que vous avez renommée) et connectez-la à la classe de base.

    > [!NOTE]
    > Cliquez sur l’élément **Héritage** dans la **Boîte à outils** et relâchez le bouton de la souris, cliquez sur la seconde copie de la classe que vous avez créée à l’étape 3, puis cliquez sur la première classe que vous avez créée à l’étape 2. La flèche sur la ligne d’héritage pointe vers la première classe.

5. Dans chaque classe, supprimez toutes les propriétés d'objet que vous ne souhaitez pas voir apparaître et qui ne sont pas utilisées pour des associations. Vous recevez une erreur si vous tentez de supprimer des propriétés d’objet utilisées pour des associations : [la propriété \<property name> ne peut pas être supprimée \<association name> , car elle participe à l’Association ](../data-tools/the-property-property-name-cannot-be-deleted-because-it-is-participating-in-the-association-association-name.md).

    > [!NOTE]
    > Comme une classe dérivée hérite des propriétés définies dans sa classe de base, les mêmes colonnes ne peuvent pas être définies dans chaque classe. (Les colonnes sont implémentées en tant que propriétés.) Vous pouvez activer la création de colonnes dans la classe dérivée en définissant le modificateur d’héritage sur la propriété dans la classe de base. Pour plus d’informations, consultez [principes de base de l’héritage (Visual Basic)](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics).

6. Sélectionnez la ligne d’héritage dans le **Concepteur O/R**.

7. Dans la fenêtre **Propriétés** , définissez la **propriété de discriminateur** sur le nom de la colonne qui distingue les enregistrements dans vos classes.

8. Affectez à la propriété **Valeur de discriminateur de classe dérivée** la valeur dans la base de données qui désigne l’enregistrement comme type hérité. (Il s’agit de la valeur qui est stockée dans la colonne de discriminateur et qui est utilisée pour désigner la classe héritée.)

9. Affectez à la propriété **Valeur de discriminateur de classe de base** la valeur qui désigne l’enregistrement comme type de base. (Il s’agit de la valeur qui est stockée dans la colonne de discriminateur et qui est utilisée pour désigner la classe de base.)

10. En option, vous pouvez également affecter à la propriété **Valeur d’héritage par défaut** la désignation d’un type dans une hiérarchie d’héritage utilisée lors du chargement des lignes ne correspondant à aucun code d’héritage défini. En d’autres termes, si un enregistrement a une valeur dans sa colonne de discriminateur qui ne correspond pas à la valeur dans les propriétés valeur de **discriminateur de classe dérivée** ou **valeur de discriminateur de classe de base** , l’enregistrement se charge dans le type désigné comme valeur **par défaut d’héritage**.

## <a name="see-also"></a>Voir aussi

- [Outils de LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Procédure pas à pas : Création de classes LINQ to SQL (Concepteur O/R)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [Accès aux données dans Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Procédure pas à pas : création de classes LINQ to SQL à l’aide de l’héritage de table unique (Concepteur O/R)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)
- [Notions de base de l’héritage (Visual Basic)](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)
- [Héritage](/dotnet/csharp/programming-guide/classes-and-structs/inheritance)
