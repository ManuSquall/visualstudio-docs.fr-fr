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
ms.openlocfilehash: a0419100cbc5fcd543eb250fa85cbfe2ebd1c97f
ms.sourcegitcommit: 614d5b99576ea27a41957cd94062dc95cbd29c1c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2019
ms.locfileid: "65531588"
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
- [Conseils pour les développeurs .NET](../csharp-developer-productivity.md)
