---
title: 'Comment : configurer l’héritage à l’aide du Concepteur O-R | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: e594af12-e777-434a-bc08-7dd2dac84cdc
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7f8c08546fdf96c755b3adb80021ab7269509739
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72654706"
---
# <a name="how-to-configure-inheritance-by-using-the-or-designer"></a>Guide pratique pour configurer l’héritage à l’aide du Concepteur O/R
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L'[!INCLUDE[vs_ordesigner_long](../includes/vs-ordesigner-long-md.md)] ([!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]) prend en charge le concept d'héritage à table unique qui est souvent implémenté dans les systèmes relationnels. L'héritage à table unique fait appel à une seule table de base de données qui contient des champs pour les informations parent et enfant. Avec les données relationnelles, une colonne de discriminateur contient la valeur qui détermine à quelle classe tout enregistrement appartient.

 Prenons par exemple une table Persons qui contient tous les employées d'une société. Certaines personnes sont des employés et d'autres des responsables. La table Persons contient une colonne nommée `EmployeeType` qui a une valeur de 1 pour les responsables et une valeur de 2 pour les employés ; c'est la colonne de discriminateur. Dans ce scénario, vous pouvez créer une sous-classe d'employés et remplir la classe avec uniquement des enregistrements ayant une valeur `EmployeeType` de 2. Vous pouvez également supprimer les colonnes qui ne s'appliquent à aucune de ces classes.

 La création d'un modèle objet qui utilise l'héritage (et correspond aux données relationnelles) peut prêter à confusion. La procédure suivante esquisse les étapes requises pour configurer l'héritage avec le Concepteur O/R. Suivre les étapes génériques sans faire référence à une table existante et aux colonnes risque d'être difficile, c'est pourquoi une procédure pas à pas utilisant des données vous est proposée. Pour obtenir des instructions pas à pas détaillées sur la configuration de l’héritage à l’aide de [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] , consultez [procédure pas à pas : création de LINQ to SQL classes à l’aide de l’héritage de table unique (Concepteur O/R)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md).

### <a name="to-create-inherited-data-classes"></a>Pour créer des classes de données héritées

1. Ouvrez la [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] en ajoutant un élément **LINQ to SQL classes** à un projet Visual Basic ou C# existant.

2. Faites glisser la table à utiliser comme classe de base vers le [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

3. Faites glisser une deuxième copie de la table sur le [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] et renommez-la. C'est la classe dérivée, ou sous-classe.

4. Cliquez sur **Héritage** sous l’onglet **Concepteur Objet Relationnel** de la **Boîte à outils**, puis sur la sous-classe (la table que vous avez renommée) et connectez-la à la classe de base.

    > [!NOTE]
    > Cliquez sur l’élément **Héritage** dans la **Boîte à outils** et relâchez le bouton de la souris, cliquez sur la seconde copie de la classe que vous avez créée à l’étape 3, puis cliquez sur la première classe que vous avez créée à l’étape 2. La flèche sur la ligne d'héritage pointe sur la première classe.

5. Dans chaque classe, supprimez toutes les propriétés d'objet que vous ne souhaitez pas voir apparaître et qui ne sont pas utilisées pour des associations. Vous recevrez une erreur si vous tentez de supprimer des propriétés d’objet utilisées pour des associations : [la propriété \<property name> ne peut pas être supprimée \<association name> , car elle participe à l’Association ](../data-tools/the-property-property-name-cannot-be-deleted-because-it-is-participating-in-the-association-association-name.md).

    > [!NOTE]
    > Comme une classe dérivée hérite des propriétés définies dans sa classe de base, les mêmes colonnes ne peuvent pas être définies dans chaque classe. (Les colonnes sont implémentées en tant que propriétés.) Vous pouvez activer la création de colonnes dans la classe dérivée en définissant le modificateur d’héritage sur la propriété dans la classe de base. Pour plus d’informations, consultez [not in Build : substitution de propriétés et de méthodes](https://msdn.microsoft.com/2167e8f5-1225-4b13-9ebd-02591ba90213).

6. Sélectionnez la ligne d'héritage dans le [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

7. Dans la fenêtre **Propriétés** , définissez la **propriété de discriminateur** sur le nom de colonne utilisé pour distinguer les enregistrements dans vos classes.

8. Affectez à la propriété **Valeur de discriminateur de classe dérivée** la valeur dans la base de données qui désigne l’enregistrement comme type hérité. (Il s'agit de la valeur stockée dans la colonne de discriminateur et qui est utilisée pour désigner la classe héritée.)

9. Affectez à la propriété **Valeur de discriminateur de classe de base** la valeur qui désigne l’enregistrement comme type de base. (Il s'agit de la valeur stockée dans la colonne de discriminateur et qui est utilisée pour désigner la classe de base.)

10. En option, vous pouvez également affecter à la propriété **Valeur d’héritage par défaut** la désignation d’un type dans une hiérarchie d’héritage utilisée lors du chargement des lignes ne correspondant à aucun code d’héritage défini. En d’autres termes, si un enregistrement a une valeur dans sa colonne de discriminateur qui ne correspond pas à la valeur dans les propriétés valeur de **discriminateur de classe dérivée** ou **valeur de discriminateur de classe de base** , l’enregistrement est chargé dans le type désigné comme valeur **par défaut d’héritage**.

## <a name="see-also"></a>Voir aussi
 [Outils de LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [procédure pas à pas : création de classes de LINQ to SQL (Concepteur O-R)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233) [préparer nouveautés pour le développement d’applications de données dans Visual Studio 2012](https://msdn.microsoft.com/3d50d68f-5f44-4915-842f-6d42fce793f1) [accès aux données dans Visual Studio](../data-tools/accessing-data-in-visual-studio.md) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [procédure pas à pas : création de classes LINQ to SQL à l’aide de l’héritage de table unique (concepteur o/R)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md) [not in Build : héritage dans Visual Basic](https://msdn.microsoft.com/e5e6e240-ed31-4657-820c-079b7c79313c) [héritage](https://msdn.microsoft.com/library/81d64ee4-50f9-4d6c-a8dc-257c348d2eea)
