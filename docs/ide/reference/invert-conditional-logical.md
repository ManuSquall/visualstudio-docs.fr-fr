---
title: Inversion des expressions conditionnelles et des opérations logiques
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kendrahavens
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: a35f5949bee6cb3c4fbcbf9ba6a9b501d54b2014
ms.sourcegitcommit: 11337745c1aaef450fd33e150664656d45fe5bc5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57324584"
---
# <a name="invert-conditional-expressions-and-conditional-andor-operators"></a>Inverser des expressions conditionnelles et des opérateurs AND/OR conditionnels

Cette refactorisation s’applique à :

- C#
- Visual Basic

**Quoi :** Permet d’inverser une expression conditionnelle ou un opérateur AND/OR conditionnel.

**Quand :** Vous avez une expression conditionnelle ou un opérateur AND/OR conditionnel qui serait plus facile à comprendre s’il était inversé.

**Pourquoi :** L’inversion manuelle d’une expression ou d’un opérateur AND/OR conditionnel peut prendre beaucoup plus de temps et introduire des erreurs. Ce correctif de code vous permet de faire cette refactorisation automatiquement.

## <a name="invert-conditional-expressions-and-conditional-andor-operators-refactoring"></a>Inverser des expressions conditionnelles et des opérateurs AND/OR conditionnels (refactorisation)

1. Placez votre curseur dans une expression conditionnelle ou un opérateur AND/OR conditionnel.
2. Appuyez sur **Ctrl**+**.** pour afficher le menu **Actions rapides et refactorisations**.
3. Sélectionnez **Inverser conditionnel** ou **Remplacer « && » par « || »**.

    ![Inverser un conditionnel](media/invert-conditional.png)

    ![Inverser un conditionnel](media/invert-logical-operator.png)

## <a name="see-also"></a>Voir aussi

- [Refactorisation](../refactoring-in-visual-studio.md)
- [Conseils pour les développeurs .NET](../../ide/visual-studio-2017-for-dotnet-developers.md)
