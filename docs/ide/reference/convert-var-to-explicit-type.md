---
title: Refactoriser le code pour remplacer var par un type explicite
description: Découvrez comment utiliser des actions rapides pour remplacer var dans une expression de variable locale par un type explicite.
ms.custom: SEO-VS-2020
ms.date: 05/15/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: d45d4ffcbdedb456bde40b3fd1103fa8b21a8f9b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99919591"
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

## <a name="how-to-use-it"></a>Comment l’utiliser

1. Placez le signe insertion sur le mot clé `var`.

1. Appuyez sur **CTRL** + **.** ou cliquez sur l’icône en forme de tournevis ![Icône en forme de tournevis](../media/screwdriver-icon.png) dans la marge du fichier de code.

   ![Utilisez le menu des actions rapides de type explicite](media/use-explicit-type.png)

1. Sélectionnez **Utiliser un type explicite**. Vous pouvez aussi sélectionner **Aperçu des modifications** pour ouvrir la boîte de dialogue [Aperçu des modifications](../../ide/preview-changes.md), puis sélectionner **Appliquer**.

## <a name="see-also"></a>Voir aussi

- [Variables implicitement typées (C#)](/dotnet/csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables)
- [Refactorisation](../refactoring-in-visual-studio.md)
- [Aperçu des modifications](../../ide/preview-changes.md)
