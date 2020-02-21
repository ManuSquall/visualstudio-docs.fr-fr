---
title: Encapsuler, mettre en retrait et aligner les refactorisations
description: Découvrez comment mettre à la ligne et aligner des chaînes d’appels de méthode.
ms.date: 02/19/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 349f2eeccfea4fea03967929b01114c0de1af155
ms.sourcegitcommit: 3c105990656cd509062ce60e52e776c794f6305d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77527667"
---
# <a name="wrap-indent-and-align-refactorings"></a>Encapsuler, mettre en retrait et aligner les refactorisations

## <a name="wrap-and-align-call-chains"></a>Mettre à la ligne et aligner des chaînes d’appels

Cette refactorisation s’applique à :

- C#

**Ce qui suit :** Vous permet d’encapsuler et d’aligner des chaînes d’appels de méthode.

Dans les **cas suivants :** Vous avez une longue chaîne composée de plusieurs appels de méthode dans une même instruction.

**Pourquoi :** La lecture d’une longue liste est plus facile quand elles sont encapsulées ou mises en retrait en fonction de la préférence de l’utilisateur.

### <a name="how-to"></a>Procédures

1. Placez votre curseur dans une chaîne d’appel quelconque.
2. Appuyez sur **Ctrl**+ **.** pour afficher le menu **Actions rapides et refactorisations**.
3. Sélectionnez **Inclure la chaîne d’appel dans un wrapper** ou **Aligner la chaîne d’appel et l’inclure dans un wrapper** pour accepter la refactorisation.

   ![Mettre à la ligne et aligner des chaînes d’appels](media/wrap-call-chain.png)

## <a name="wrap-indent-and-align-parameters-or-arguments"></a>Renvoi à la ligne, mise en retrait et alignement des paramètres ou des arguments

Cette refactorisation s’applique à :

- C#

- Visual Basic

**Ce qui suit :** Vous permet d’encapsuler, de mettre en retrait et d’aligner des paramètres ou des arguments.

Dans les **cas suivants :** Vous avez une déclaration ou un appel de méthode qui a plusieurs paramètres ou arguments.

**Pourquoi :** Il est plus facile de lire une longue liste de paramètres ou d’arguments lorsqu’ils sont enveloppés ou mis en retrait en fonction de la préférence de l’utilisateur.

### <a name="how-to"></a>Procédures

1. Placez votre curseur dans une liste de paramètres.
2. Appuyez sur **Ctrl**+ **.** pour afficher le menu **Actions rapides et refactorisations**.

   ![Mettre à la ligne, mettre en retrait et aligner des paramètres](media/wrap-parameters.png)

3. Sélectionnez **encapsuler chaque paramètre** pour accepter la refactorisation.

## <a name="wrap-binary-expressions"></a>Inclure des expressions binaires dans un wrapper

Cette refactorisation s’applique à :

- C#

**Ce qui suit :** Vous permet d’encapsuler des expressions binaires.

Dans les **cas suivants :** Vous avez une expression binaire.

**Pourquoi :** La lecture d’une expression binaire est plus facile lorsqu’elle est encapsulée dans la préférence de l’utilisateur.

### <a name="how-to"></a>Procédures

1. Placez votre curseur dans l’expression binaire.
2. Appuyez sur **Ctrl**+ **.** pour afficher le menu **Actions rapides et refactorisations**.
3. Sélectionnez **expression de retour** à la ligne pour accepter la refactorisation.

   ![Mettre à la ligne et aligner des chaînes d’appels](media/wrap-binary-expression.png)

## <a name="see-also"></a>Voir aussi

- [Refactorisation](../refactoring-in-visual-studio.md)
