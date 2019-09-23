---
title: Mettre à la ligne et aligner des chaînes d’appels
description: Découvrez comment mettre à la ligne et aligner des chaînes d’appels de méthode.
ms.date: 08/13/2019
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 2a5b6bea4c915e029ca3ae448444decce0d7b041
ms.sourcegitcommit: b83fefa8177c5554cbe2c59c4d102cbc534f7cc6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69620011"
---
# <a name="wrap-and-align-call-chains"></a>Mettre à la ligne et aligner des chaînes d’appels

Cette refactorisation s’applique à :

- C#

**Quoi :** permet de mettre à la ligne et d’aligner des chaînes d’appels de méthode.

**Quand :** vous avez une longue chaîne composée de plusieurs appels de méthode dans une même instruction.

**Pourquoi :** il est plus facile de lire une longue liste de chaînes d’appel quand elles sont renvoyées à la ligne ou mises en retrait selon les préférences de l’utilisateur.

## <a name="how-to"></a>Procédure

1. Placez votre curseur dans une chaîne d’appel quelconque.
2. Appuyez sur **Ctrl**+ **.** pour afficher le menu **Actions rapides et refactorisations**.
3. Sélectionnez **Inclure la chaîne d’appel dans un wrapper** ou **Aligner la chaîne d’appel et l’inclure dans un wrapper** pour accepter la refactorisation.

   ![Mettre à la ligne et aligner des chaînes d’appels](media/wrap-call-chain.png)

## <a name="see-also"></a>Voir aussi

- [Refactorisation](../refactoring-in-visual-studio.md)
