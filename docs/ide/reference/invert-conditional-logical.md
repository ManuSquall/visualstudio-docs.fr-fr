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
ms.openlocfilehash: 3931ae53fc29b0ffd8b8b6e96951a0f4786ff756
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "65531674"
---
# <a name="invert-conditional-expressions-and-conditional-andor-operators"></a>Inverser des expressions conditionnelles et des opérateurs AND/OR conditionnels

Cette refactorisation s’applique à :

- C#
- Visual Basic

**Quoi :** Vous permet d’inverser une expression conditionnelle ou un opérateur CONDITIONnel ET/OR.

**Quand :** Vous avez une expression conditionnelle ou un opérateur ET/OR conditionnel qui serait mieux compris s’il était inversé.

**Pourquoi:** Inverser une expression ou un opérateur ET/OR conditionnel à la main peut prendre beaucoup plus de temps et éventuellement introduire des erreurs. Ce correctif de code vous permet de faire cette refactorisation automatiquement.

## <a name="invert-conditional-expressions-and-conditional-andor-operators-refactoring"></a>Inverser des expressions conditionnelles et des opérateurs AND/OR conditionnels (refactorisation)

1. Placez votre curseur dans une expression conditionnelle ou un opérateur AND/OR conditionnel.
2. Appuyez **sur Ctrl**+**.** pour afficher le menu **Actions rapides et refactorisations**.
3. Sélectionnez **Inverser conditionnel** ou **Remplacer « && » par « || »**.

    ![Inverser un conditionnel](media/invert-conditional.png)

    ![Inverser un conditionnel](media/invert-logical-operator.png)

## <a name="see-also"></a>Voir aussi

- [Refactorisation](../refactoring-in-visual-studio.md)
- [Conseils pour les développeurs .NET](../csharp-developer-productivity.md)
