---
title: Mettre à la ligne, mettre en retrait et aligner des refactorisations
description: Découvrez comment mettre à la ligne et aligner des chaînes d’appels de méthode.
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: d801f052cb02e6a5b53189eeae342b9015d30f9b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79093886"
---
# <a name="wrap-indent-and-align-refactorings"></a>Mettre à la ligne, mettre en retrait et aligner des refactorisations

## <a name="wrap-and-align-call-chains"></a>Mettre à la ligne et aligner des chaînes d’appels

Cette refactorisation s’applique à :

- C#

- Visual Basic

**Quoi :** Vous permet d’envelopper et d’aligner des chaînes d’appels de méthode.

**Quand :** Vous avez une longue chaîne composée de plusieurs appels de méthode dans une seule déclaration.

**Pourquoi:** La lecture d’une longue liste est plus facile lorsqu’ils sont emballés ou en retrait selon la préférence de l’utilisateur.

### <a name="how-to"></a>Procédures

1. Placez votre curseur dans une chaîne d’appel quelconque.
2. Appuyez **sur Ctrl**+**.** pour afficher le menu **Actions rapides et refactorisations**.
3. Sélectionnez **Inclure la chaîne d’appel dans un wrapper** ou **Aligner la chaîne d’appel et l’inclure dans un wrapper** pour accepter la refactorisation.

   ![Mettre à la ligne et aligner des chaînes d’appels](media/wrap-call-chain.png)

## <a name="wrap-indent-and-align-parameters-or-arguments"></a>Renvoi à la ligne, mise en retrait et alignement des paramètres ou des arguments

Cette refactorisation s’applique à :

- C#

- Visual Basic

**Quoi :** Permet d’envelopper, d’enrouler et d’aligner des paramètres ou des arguments.

**Quand :** Vous avez une déclaration de méthode ou un appel qui comporte plusieurs paramètres ou arguments.

**Pourquoi:** La lecture d’une longue liste de paramètres ou d’arguments est plus facile lorsqu’ils sont enveloppés ou en retrait selon la préférence de l’utilisateur.

### <a name="how-to"></a>Procédures

1. Placez votre curseur dans une liste de paramètres.
2. Appuyez **sur Ctrl**+**.** pour afficher le menu **Actions rapides et refactorisations**.

   ![Mettre à la ligne, mettre en retrait et aligner des paramètres](media/wrap-parameters.png)

3. Sélectionnez **Enveloppez chaque paramètre** pour accepter la refactoration.

## <a name="wrap-binary-expressions"></a>Inclure des expressions binaires dans un wrapper

Cette refactorisation s’applique à :

- C#

- Visual Basic

**Quoi :** Vous permet d’enrouler les expressions binaires.

**Quand :** Vous avez une expression binaire.

**Pourquoi:** La lecture d’une expression binaire est plus facile lorsqu’elle est enveloppée à la préférence de l’utilisateur.

### <a name="how-to"></a>Procédures

1. Placez votre curseur dans l’expression binaire.
2. Appuyez **sur Ctrl**+**.** pour afficher le menu **Actions rapides et refactorisations**.
3. Sélectionnez **l’expression Wrap** pour accepter la refactoration.

   ![Mettre à la ligne et aligner des chaînes d’appels](media/wrap-binary-expression.png)

## <a name="see-also"></a>Voir aussi

- [Refactorisation](../refactoring-in-visual-studio.md)
