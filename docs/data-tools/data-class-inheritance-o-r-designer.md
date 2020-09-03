---
title: Héritage de classes de données (Concepteur O-R)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: af32653c-f4e6-4217-8c5a-e32b322b4918
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 7172c868780aec61de8688614fbb93627dc23bf5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85462393"
---
# <a name="data-class-inheritance-or-designer"></a>Héritage de classes de données (Concepteur O/R)

Comme d’autres objets, les classes LINQ to SQL peuvent utiliser l’héritage et être dérivées d’autres classes. Dans le code, vous pouvez spécifier des relations d'héritage entre des objets en déclarant qu'une classe hérite d'une autre. Dans une base de données, les relations d'héritage sont créées de plusieurs façons. Le **Concepteur Objet Relationnel** (**Concepteur O/R**) prend en charge le concept d’héritage de table unique, car il est souvent implémenté dans les systèmes relationnels.

Dans l'héritage à table unique, une table de base de données contient des colonnes pour les classes de base et dérivées. Avec les données relationnelles, une colonne de discriminateur contient la valeur qui détermine à quelle classe appartient un enregistrement donné. Prenons l’exemple d’une `Persons` table qui contient tout le monde employé par une société. Certaines personnes sont des employés et d'autres des responsables. La `Persons` table contient une colonne nommée `Type` qui a une valeur de 1 pour les responsables et une valeur de 2 pour les employés. La `Type` colonne est la colonne de discriminateur. Dans ce scénario, vous pouvez créer une sous-classe d’employés et remplir la classe avec uniquement les enregistrements dont la `Type` valeur est 2.

Quand vous configurez l’héritage dans les classes d’entité à l’aide du [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], faites glisser la table unique qui contient les données d’héritage sur le concepteur à deux reprises : une pour chaque classe dans la hiérarchie d’héritage. Après avoir ajouté les tables au concepteur, associez-les à un élément Héritage de la boîte à outils **Concepteur Objet Relationnel**, puis définissez les quatre propriétés d’héritage dans la fenêtre **Propriétés**.

## <a name="inheritance-properties"></a>Propriétés d’héritage

Le tableau suivant répertorie les propriétés d'héritage et leurs descriptions :

|Propriété|Description|
|--------------|-----------------|
|**Propriété de discriminateur**|Propriété (mappée à la colonne) qui détermine à quelle classe appartient l'enregistrement actif.|
|**Valeur Discriminator de la classe de base**|Valeur (dans la colonne désignée comme propriété de **discriminateur**) qui détermine qu’un enregistrement est de la classe de base.|
|**Valeur Discriminator de la classe dérivée**|Valeur (dans la propriété désignée comme propriété de **discriminateur**) qui détermine qu’un enregistrement est de la classe dérivée.|
|**Valeur par défaut d'héritage**|La classe qui est remplie lorsque la valeur de la propriété désignée comme **propriété de discriminateur** ne correspond pas à la valeur de **discriminateur de classe de base** ou à la valeur de **discriminateur de classe dérivée**.|

La création d'un modèle objet qui utilise l'héritage et correspond aux données relationnelles peut prêter à confusion. Cette rubrique fournit des informations à propos des concepts de base et des propriétés individuelles requises pour configurer l'héritage. Les rubriques suivantes fournissent une explication plus claire sur la configuration de l’héritage avec le **Concepteur O/R**.

|Rubrique|Description|
|-----------|-----------------|
|[Guide pratique pour configurer l’héritage à l’aide du Concepteur O/R](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md)|Décrit comment configurer des classes d’entité qui utilisent l’héritage à table unique à l’aide du **Concepteur O/R**.|
|[Procédure pas à pas : création de classes LINQ to SQL à l’aide de l’héritage de table unique (Concepteur O/R)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)|Fournit des instructions pas à pas sur la façon de configurer des classes d’entité qui utilisent l’héritage de table unique à l’aide du **Concepteur O/R**.|

## <a name="see-also"></a>Voir aussi

- [Outils LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Procédure pas à pas : Création de classes LINQ to SQL (Concepteur O/R)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [Procédure pas à pas : création de classes LINQ to SQL à l’aide de l’héritage de table unique (Concepteur O/R)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)
- [Bien démarrer](/dotnet/framework/data/adonet/sql/linq/getting-started)