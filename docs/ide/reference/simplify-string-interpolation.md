---
title: Simplifier l’interpolation de chaîne
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
ms.openlocfilehash: a8b0fd53164cb98921b111d49fa04a76c9d0d8a8
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094302"
---
# <a name="simplify-string-interpolation-refactoring"></a>Simplifier la refactorisation de l’interpolation des chaînes

Cette refactorisation s’applique à :

- C#

- Visual Basic

**Quoi :** Permet de simplifier une [interpolation des chaînes](https://docs.microsoft.com/dotnet/csharp/tutorials/string-interpolation).

**Quand :** Vous avez une interpolation des chaînes qui peut être simplifiée.

**Pourquoi:** La simplification d’une interpolation des cordes peut fournir plus de clarté et de syntaxe concise. Cet outil de refactoration effectuera la tâche automatiquement au lieu d’avoir à le faire manuellement.

## <a name="how-to"></a>Procédures

1. Placez votre caret sur l’interpolation de chaîne :

2. Appuyez **sur Ctrl**+**.** pour afficher le menu **Actions rapides et refactorisations**.

3. Sélectionnez **Simplifier l’interpolation**

    ![Simplifier l’interpolation de chaîne](media/simplify-string-interpolation.png)

## <a name="see-also"></a>Voir aussi

- [Refactorisation](../refactoring-in-visual-studio.md)