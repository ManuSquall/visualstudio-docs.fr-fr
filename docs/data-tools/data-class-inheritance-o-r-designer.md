---
title: Héritage de classes de données (Concepteur O-R)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: af32653c-f4e6-4217-8c5a-e32b322b4918
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 6c6b17ad38e9aae78975e43797931a326955712d
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36756735"
---
# <a name="data-class-inheritance-or-designer"></a>Héritage de classes de données (Concepteur O/R)

Comme d’autres objets, les classes LINQ to SQL peut utiliser l’héritage et être dérivée d’autres classes. Dans le code, vous pouvez spécifier des relations d'héritage entre des objets en déclarant qu'une classe hérite d'une autre. Dans une base de données, les relations d'héritage sont créées de plusieurs façons. Le **concepteur objet/relationnel** (**Concepteur O/R**) prend en charge le concept d’héritage à table unique tel qu’il est souvent implémenté dans les systèmes relationnels.

Dans l'héritage à table unique, une table de base de données contient des colonnes pour les classes de base et dérivées. Avec les données relationnelles, une colonne de discriminateur contient la valeur qui détermine à quelle classe appartient un enregistrement donné. Par exemple, considérez un `Persons` table qui contient tous les employées par une société. Certaines personnes sont des employés et d'autres des responsables. Le `Persons` table contient une colonne nommée `Type` qui a la valeur 1 pour les responsables et une valeur de 2 pour les employés. Le `Type` est la colonne de discriminateur. Dans ce scénario, vous pouvez créer une sous-classe d’employés et remplir la classe avec uniquement les enregistrements ayant une `Type` valeur 2.

Lorsque vous configurez l’héritage dans les classes d’entité à l’aide de la [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], faites glisser la table unique qui contient les données d’héritage sur le Concepteur de deux fois : une fois pour chaque classe dans la hiérarchie d’héritage. Après avoir ajouté les tables au concepteur, associez-les à un élément de l’héritage à partir de la **concepteur objet/relationnel** boîte à outils, puis définissez les quatre propriétés d’héritage dans le **propriétés** fenêtre.

## <a name="inheritance-properties"></a>Propriétés d’héritage

Le tableau suivant répertorie les propriétés d'héritage et leurs descriptions :

|Propriété|Description|
|--------------|-----------------|
|**Propriété de discriminateur**|Propriété (mappée à la colonne) qui détermine à quelle classe appartient l'enregistrement actif.|
|**Valeur de discriminateur de classe de base**|La valeur (dans la colonne désignée comme la **propriété de discriminateur**) qui détermine qu’un enregistrement est la classe de base.|
|**Valeur de discriminateur de classe dérivée**|La valeur (dans la propriété désignée comme la **propriété de discriminateur**) qui détermine qu’un enregistrement est de la classe dérivée.|
|**Par défaut de l’héritage**|La classe qui est remplie lorsque la valeur dans la propriété désignée comme la **propriété de discriminateur** ne correspond pas à la **valeur de discriminateur de classe de Base** ou **classe dérivée Valeur de discriminateur**.|

La création d'un modèle objet qui utilise l'héritage et correspond aux données relationnelles peut prêter à confusion. Cette rubrique fournit des informations à propos des concepts de base et des propriétés individuelles requises pour configurer l'héritage. Les rubriques suivantes fournissent une explication plus claire de la configuration de l’héritage avec les **Concepteur O/R**.

|Rubrique|Description|
|-----------|-----------------|
|[Comment : configurer l’héritage à l’aide du Concepteur O/R](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md)|Décrit comment configurer des classes d’entité qui utilisent l’héritage à table unique à l’aide de la **Concepteur O/R**.|
|[Procédure pas à pas : Création de LINQ aux classes SQL à l’aide d’héritage à table unique (Concepteur O/R)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)|Fournit des instructions détaillées sur la façon de configurer des classes d’entité qui utilisent l’héritage à table unique à l’aide de la **Concepteur O/R**.|

## <a name="see-also"></a>Voir aussi

- [Outils LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Procédure pas à pas : Création de LINQ to SQL classes (Concepteur O-R)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [Procédure pas à pas : Création de LINQ aux classes SQL à l’aide d’héritage à table unique (Concepteur O/R)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)
- [Prise en main](/dotnet/framework/data/adonet/sql/linq/getting-started)