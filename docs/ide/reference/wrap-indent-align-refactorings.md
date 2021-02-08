---
title: Mettre à la ligne, mettre en retrait et aligner des refactorisations
description: Découvrez comment mettre à la ligne et aligner des chaînes d’appels de méthode.
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 7c218d914bc234533af674fc5d138a1c102d85c3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99836266"
---
# <a name="wrap-indent-and-align-refactorings"></a>Mettre à la ligne, mettre en retrait et aligner des refactorisations

## <a name="wrap-and-align-call-chains"></a>Mettre à la ligne et aligner des chaînes d’appels

Cette refactorisation s’applique à :

- C#

- Visual Basic

**Ce qui suit :** Vous permet d’encapsuler et d’aligner des chaînes d’appels de méthode.

Dans les **cas suivants :** Vous avez une longue chaîne composée de plusieurs appels de méthode dans une même instruction.

**Pourquoi :** La lecture d’une longue liste est plus facile quand elles sont encapsulées ou mises en retrait en fonction de la préférence de l’utilisateur.

### <a name="how-to"></a>Procédures

1. Placez votre curseur dans une chaîne d’appel quelconque.
2. Appuyez sur **CTRL** + **.** pour afficher le menu **Actions rapides et refactorisations**.
3. Sélectionnez **Inclure la chaîne d’appel dans un wrapper** ou **Aligner la chaîne d’appel et l’inclure dans un wrapper** pour accepter la refactorisation.

   ![LinkedDataFormUpdated du menu actions rapides et refactorisations dans Visual Studio avec la chaîne d’appel Warap sélectionnée et les modifications du code C# affichées.](media/wrap-call-chain.png)

## <a name="wrap-indent-and-align-parameters-or-arguments"></a>Renvoi à la ligne, mise en retrait et alignement des paramètres ou des arguments

Cette refactorisation s’applique à :

- C#

- Visual Basic

**Ce qui suit :** Vous permet d’encapsuler, de mettre en retrait et d’aligner des paramètres ou des arguments.

Dans les **cas suivants :** Vous avez une déclaration ou un appel de méthode qui a plusieurs paramètres ou arguments.

**Pourquoi :** Il est plus facile de lire une longue liste de paramètres ou d’arguments lorsqu’ils sont enveloppés ou mis en retrait en fonction de la préférence de l’utilisateur.

### <a name="how-to"></a>Procédures

1. Placez votre curseur dans une liste de paramètres.
2. Appuyez sur **CTRL** + **.** pour afficher le menu **Actions rapides et refactorisations**.

   ![Mettre à la ligne, mettre en retrait et aligner des paramètres](media/wrap-parameters.png)

3. Sélectionnez **encapsuler chaque paramètre** pour accepter la refactorisation.

## <a name="wrap-binary-expressions"></a>Inclure des expressions binaires dans un wrapper

Cette refactorisation s’applique à :

- C#

- Visual Basic

**Ce qui suit :** Vous permet d’encapsuler des expressions binaires.

Dans les **cas suivants :** Vous avez une expression binaire.

**Pourquoi :** La lecture d’une expression binaire est plus facile lorsqu’elle est encapsulée dans la préférence de l’utilisateur.

### <a name="how-to"></a>Procédures

1. Placez votre curseur dans l’expression binaire.
2. Appuyez sur **CTRL** + **.** pour afficher le menu **Actions rapides et refactorisations**.
3. Sélectionnez **expression de retour** à la ligne pour accepter la refactorisation.

   ![LinkedDataFormUpdated du menu actions rapides et refactorisations dans Visual Studio avec l’expression Warap sélectionnée et les modifications du code C# affichées.](media/wrap-binary-expression.png)

## <a name="see-also"></a>Voir aussi

- [Refactorisation](../refactoring-in-visual-studio.md)
