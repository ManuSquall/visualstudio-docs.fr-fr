---
title: Inversion des expressions conditionnelles et des opérations logiques
description: Découvrez comment utiliser le menu actions rapides et refactorisations pour inverser une expression conditionnelle ou un opérateur AND/OR conditionnel.
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
ms.openlocfilehash: 0bd75a40f52a6148a6c50b212183bb8dc7a52d56
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99852243"
---
# <a name="invert-conditional-expressions-and-conditional-andor-operators"></a>Inverser des expressions conditionnelles et des opérateurs AND/OR conditionnels

Cette refactorisation s’applique à :

- C#
- Visual Basic

**Ce qui suit :** Vous permet d’inverser une expression conditionnelle ou un opérateur AND/OR conditionnel.

Dans les **cas suivants :** Vous avez une expression conditionnelle ou un opérateur et/ou conditionnel qui serait mieux compréhensible en cas d’inversion.

**Pourquoi :** L’inversion d’une expression ou d’un opérateur conditionnel et/ou à la main peut prendre plus de temps et éventuellement introduire des erreurs. Ce correctif de code vous permet de faire cette refactorisation automatiquement.

## <a name="invert-conditional-expressions-and-conditional-andor-operators-refactoring"></a>Inverser des expressions conditionnelles et des opérateurs AND/OR conditionnels (refactorisation)

1. Placez votre curseur dans une expression conditionnelle ou un opérateur AND/OR conditionnel.
2. Appuyez sur **CTRL** + **.** pour afficher le menu **Actions rapides et refactorisations**.
3. Sélectionnez **Inverser conditionnel** ou **Remplacer « && » par « || »**.

    ![Capture d’écran de l’option inversée conditionnelle.](media/invert-conditional.png)

    ![Capture d’écran de la && de remplacement par | | option.](media/invert-logical-operator.png)

## <a name="see-also"></a>Voir aussi

- [Refactorisation](../refactoring-in-visual-studio.md)
- [Conseils pour les développeurs .NET](../csharp-developer-productivity.md)
