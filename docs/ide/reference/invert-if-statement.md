---
title: Inverser une instruction if
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 5a809eee1eb5460e245f64156385f759870adbd3
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58159099"
---
# <a name="invert-if-statement"></a>Inverser une instruction if

Cette refactorisation s’applique à :

- C#
- Visual Basic

**Quoi :** Permet d’inverser une instruction `if` ou `if else` sans changer la signification du code.

**Quand :** Vous avez une instruction `if` ou `if else` qui serait plus facile à comprendre si elle était inversée.

**Pourquoi :** L’inversion manuelle d’une instruction `if` ou `if else` peut prendre beaucoup plus de temps et introduire des erreurs. Ce correctif de code vous permet de faire cette refactorisation automatiquement.

## <a name="invert-if-statement-refactoring"></a>Inverser une instruction if (refactorisation)

1. Placez votre curseur dans une instruction `if` ou `if else`.

    ![Inverser if else](media/invert-if.png)

2. Appuyez sur **Ctrl**+**.** pour afficher le menu **Actions rapides et refactorisations**.

    ![Inverser if else (correctif de code)](media/invert-if-codefix.png)

3. Sélectionnez **Inverser if**.

    ![Inverser if else (résultat)](media/invert-if-codefix-result.png)

## <a name="see-also"></a>Voir aussi

- [Refactorisation](../refactoring-in-visual-studio.md)
- [Conseils pour les développeurs .NET](../../ide/visual-studio-2017-for-dotnet-developers.md)
