---
title: Inverser une instruction if
description: Découvrez comment utiliser le menu actions rapides et refactorisations pour inverser une instruction if ou if else sans modifier la signification du code.
ms.custom: SEO-VS-2020
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: cf4ad7c25030e4a331ee67f4957ddac59afdd966
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99852230"
---
# <a name="invert-if-statement"></a>Inverser une instruction if

Cette refactorisation s’applique à :

- C#
- Visual Basic

**Ce qui suit :** Vous permet d’inverser une `if` `if else` instruction ou sans modifier la signification du code.

Dans les **cas suivants :** Lorsque vous avez une `if` `if else` instruction ou qui serait mieux comprise lors de l’inversion.

**Pourquoi :** L’inversion d’une `if` `if else` instruction ou manuellement peut prendre plus de temps et éventuellement introduire des erreurs. Ce correctif de code vous permet de faire cette refactorisation automatiquement.

## <a name="invert-if-statement-refactoring"></a>Inverser une instruction if (refactorisation)

1. Placez votre curseur dans une instruction `if` ou `if else`.

    ![Inverser if else](media/invert-if.png)

2. Appuyez sur **CTRL** + **.** pour afficher le menu **Actions rapides et refactorisations**.

    ![Inverser if else (correctif de code)](media/invert-if-codefix.png)

3. Sélectionnez **Inverser if**.

    ![Inverser if else (résultat)](media/invert-if-codefix-result.png)

## <a name="see-also"></a>Voir aussi

- [Refactorisation](../refactoring-in-visual-studio.md)
- [Conseils pour les développeurs .NET](../csharp-developer-productivity.md)
