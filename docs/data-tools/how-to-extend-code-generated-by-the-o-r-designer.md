---
title: Guide pratique pour étendre le code généré par le Concepteur O/R
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d6d1122e-2f55-4607-8d8b-48c3c22600fb
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: e89410d224adf0980e51c691dbf581655cc2ff3e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648360"
---
# <a name="how-to-extend-code-generated-by-the-or-designer"></a>Guide pratique pour étendre le code généré par le Concepteur O/R
Le code généré par le **Concepteur O/R** est régénéré lorsque des modifications sont apportées aux classes d’entité et à d’autres objets sur l’aire du concepteur. En raison de cette régénération de code par le concepteur, tout code ajouté au code généré est en général remplacé lors de cette opération. Le **Concepteur O/R** offre la possibilité de générer des fichiers de classe partielle dans lesquels vous pouvez ajouter du code qui n’est pas remplacé. Un exemple d’ajout de votre propre code au code généré par le **Concepteur O/R** consiste à ajouter la validation de données aux classes LINQ to SQL (entité). Pour plus d’informations, consultez [Comment : ajouter une validation à des classes d’entité](../data-tools/how-to-add-validation-to-entity-classes.md).

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="add-code-to-an-entity-class"></a>Ajouter du code à une classe d’entité

### <a name="to-create-a-partial-class-and-add-code-to-an-entity-class"></a>Pour créer une classe partielle et ajouter du code à une classe d'entité

1. Ouvrez ou créez un fichier de classes LINQ to SQL (fichier **. dbml** ) dans le **Concepteur O/R**. (Double-cliquez sur le fichier **. dbml** dans **Explorateur de solutions** ou **Explorateur de base de données**.)

2. Dans le **Concepteur O/R**, cliquez avec le bouton droit sur la classe à laquelle vous souhaitez ajouter la validation, puis cliquez sur **Afficher le code**.

     Une classe partielle pour la classe d'entité sélectionnée s'ouvre dans l'éditeur de code.

3. Ajoutez votre code dans la déclaration de classe partielle pour la classe d'entité.

## <a name="add-code-to-a-datacontext"></a>Ajouter du code à un DataContext

### <a name="to-create-a-partial-class-and-add-code-to-a-datacontext"></a>Pour créer une classe partielle et ajouter du code à un DataContext

1. Ouvrez ou créez un fichier de classes LINQ to SQL (fichier **. dbml** ) dans le **Concepteur O/R**. (Double-cliquez sur le fichier **. dbml** dans **Explorateur de solutions** ou **Explorateur de base de données**.)

2. Dans le **Concepteur O/R**, cliquez avec le bouton droit sur une zone vide du concepteur, puis cliquez sur **afficher le code**.

     Une classe partielle pour le DataContext s'ouvre dans l'éditeur de code.

3. Ajoutez votre code dans la déclaration de classe partielle pour le DataContext.

## <a name="see-also"></a>Voir aussi

- [Outils LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Procédure pas à pas : Création de classes LINQ to SQL (Concepteur O/R)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)