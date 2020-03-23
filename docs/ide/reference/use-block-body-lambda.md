---
title: Utiliser un corps d’expression ou un corps de bloc pour les expressions lambda
ms.date: 02/14/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 5c46506e81e5334efea9060e957269e92e9d49cc
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "65531907"
---
# <a name="use-expression-body-or-block-body-for-lambda-expressions"></a>Utiliser un corps d’expression ou un corps de bloc pour les expressions lambda

Cette refactorisation s’applique à :

- C#

**Quoi :** Permet de refactorer une expression lambda pour utiliser un corps d’expression ou un corps de bloc.

**Quand :** Vous préférez que les expressions lambda utilisent un corps d’expression ou un corps en bloc.

**Pourquoi:** Les expressions Lambda peuvent être réfactorées pour améliorer la lisibilité selon vos préférences de l’utilisateur.

## <a name="lambda-expression-body-or-block-body-refactoring"></a>Corps d’expression ou corps de bloc pour les expressions lambda (refactorisation)

1. Placez votre curseur à droite d’un opérateur lambda.
2. Appuyez **sur Ctrl**+**.** pour afficher le menu **Actions rapides et refactorisations**.

  ![Utiliser un corps d’expression/de bloc pour les expressions lambda](media/block-body-lambda.png)

3. Sélectionnez **Utiliser un corps de bloc pour les expressions lambda** ou **Utiliser un corps d’expression pour les expressions lambda**.

## <a name="see-also"></a>Voir aussi

- [Refactorisation](../refactoring-in-visual-studio.md)
- [Conseils pour les développeurs .NET](../csharp-developer-productivity.md)