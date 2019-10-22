---
title: 'Comment : étendre le code généré par le Concepteur O-R | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: d6d1122e-2f55-4607-8d8b-48c3c22600fb
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a1d60090ca16907e16bb58970d793124c5bb2dec
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665944"
---
# <a name="how-to-extend-code-generated-by-the-or-designer"></a>Comment : étendre le code généré le Concepteur O/R
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le code généré par le [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] est régénéré lorsque des modifications sont apportées aux classes d'entité et autres objets sur l'aire du concepteur. En raison de cette régénération de code par le concepteur, tout code ajouté au code généré est en général remplacé lors de cette opération. Le [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] offre la possibilité de générer des fichiers de classe partielle dans lesquels vous pouvez ajouter du code qui ne sera pas remplacé. L'ajout d'une capacité de validation des données à des classes LINQ to SQL (entité) est un exemple d'ajout de code personnel au code généré par le [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Pour plus d’informations, consultez [Comment : ajouter une validation à des classes d’entité](../data-tools/how-to-add-validation-to-entity-classes.md).

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

## <a name="adding-code-to-an-entity-class"></a>Ajout de code à une classe d'entité

#### <a name="to-create-a-partial-class-and-add-code-to-an-entity-class"></a>Pour créer une classe partielle et ajouter du code à une classe d'entité

1. Ouvrez ou créez un nouveau fichier de classes LINQ to SQL (fichier **. dbml** ) dans le [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. (Double-cliquez sur le fichier **. dbml** dans **Explorateur de solutions** **Explorateur de base de données**/.)

2. Dans le [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], cliquez avec le bouton droit sur la classe pour laquelle vous souhaitez ajouter une validation, puis cliquez sur **afficher le code**.

     Une classe partielle pour la classe d'entité sélectionnée s'ouvre dans l'éditeur de code.

3. Ajoutez votre code dans la déclaration de classe partielle pour la classe d'entité.

## <a name="adding-code-to-a-datacontext"></a>Ajout de code à un DataContext

#### <a name="to-create-a-partial-class-and-add-code-to-a-datacontext"></a>Pour créer une classe partielle et ajouter du code à un DataContext

1. Ouvrez ou créez un nouveau fichier de classes LINQ to SQL (fichier **. dbml** ) dans le [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. (Double-cliquez sur le fichier **. dbml** dans **Explorateur de solutions** **Explorateur de base de données**/.)

2. Dans le [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], cliquez avec le bouton droit sur une zone vide du concepteur, puis cliquez sur **afficher le code**.

     Une classe partielle pour le DataContext s'ouvre dans l'éditeur de code.

3. Ajoutez votre code dans la déclaration de classe partielle pour le DataContext.

## <a name="see-also"></a>Voir aussi
 [Outils de LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [procédure pas à pas : création de classes de LINQ to SQL (Concepteur O-R)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [procédure pas à pas : ajout d’une validation à des classes d’entité](https://msdn.microsoft.com/library/85b06a02-b2e3-4534-95b8-d077c8d4c1d7)
