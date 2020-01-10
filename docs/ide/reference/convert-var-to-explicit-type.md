---
title: Refactoriser le code pour remplacer var par un type explicite
ms.date: 05/15/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 4ec388564e1851402f085f6bbaefba08dbea212c
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595772"
---
# <a name="refactoring-to-replace-var-with-an-explicit-type"></a>Refactorisation pour remplacer var par un type explicite

Utilisez cette refactorisation pour remplacer [var](/dotnet/csharp/language-reference/keywords/var) dans une déclaration de variable locale par un type explicite.

Cette refactorisation s’applique à :

- C#

## <a name="why-to-use-an-explicit-type"></a>Pourquoi utiliser un type explicite ?

Voici quelques raisons de déclarer une variable avec un type explicite :

- Pour améliorer la lisibilité du code.

- Lorsque vous ne souhaitez pas initialiser la variable dans la déclaration.

Toutefois, [var](/dotnet/csharp/language-reference/keywords/var) doit être utilisé lorsqu’une variable est initialisée avec un type anonyme et que les propriétés de l’objet seront affichées ultérieurement. Pour plus d’informations, consultez [Variables locales implicitement typées (C#)](/dotnet/csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables).

## <a name="how-to-use-it"></a>Utilisation

1. Placez le signe insertion sur le mot clé `var`.

1. Appuyez sur **Ctrl**+ **.** ou cliquez sur l’icône en forme de tournevis ![Icône en forme de tournevis](../media/screwdriver-icon.png) dans la marge du fichier de code.

   ![Utilisez le menu des actions rapides de type explicite](media/use-explicit-type.png)

1. Sélectionnez **Utiliser un type explicite**. Vous pouvez aussi sélectionner **Aperçu des modifications** pour ouvrir la boîte de dialogue [Aperçu des modifications](../../ide/preview-changes.md), puis sélectionner **Appliquer**.

## <a name="see-also"></a>Voir aussi

- [Variables implicitement typées (C#)](/dotnet/csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables)
- [Refactorisation](../refactoring-in-visual-studio.md)
- [Aperçu des modifications](../../ide/preview-changes.md)
