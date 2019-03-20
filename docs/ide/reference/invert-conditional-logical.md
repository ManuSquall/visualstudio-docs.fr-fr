---
title: Inversion des expressions conditionnelles et des opérations logiques
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
ms.openlocfilehash: 7d59b61cff622a9ba305ebfa86f7c0ebe3c00fe3
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58157358"
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
