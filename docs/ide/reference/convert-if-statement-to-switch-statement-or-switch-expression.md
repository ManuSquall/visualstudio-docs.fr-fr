---
title: Convertir l’instruction if en instruction switch ou en expression switch
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 93ad96809c77d5644b13e6221a41f0b182fb448f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094165"
---
# <a name="convert-if-statement-to-switch-statement-or-switch-expression"></a>Convertir l’instruction if en instruction switch ou en expression switch

Cette refactorisation s’applique à :

- C#

**Quoi :** Convertir une déclaration si en une [instruction de commutation](/dotnet/csharp/language-reference/keywords/switch) ou à l’expression de [commutateur](/dotnet/csharp/whats-new/csharp-8#switch-expressions)C 8.0 .

**Quand :** Vous souhaitez convertir `if` une `switch` déclaration en `switch` une déclaration ou une expression et vice versa. 

**Pourquoi:** Si vous utilisez `if` une déclaration, ce refactoring `switch` permet `switch` une transition facile vers des déclarations ou des expressions.

## <a name="how-to"></a>Procédures

1. Placez votre curseur dans le mot clé `if`.
2. Appuyez **sur Ctrl**+**.** pour afficher le menu **Actions rapides et refactorisations**.
3. Sélectionnez parmi les deux options suivantes : 

    Sélectionnez **Convertir à 'switch' instruction**.

   ![Convertir si l’instruction pour changer de relevé](media/convert-if-to-switch-statement.png) 

    Sélectionnez **Convertir en expression de « commutateur ».** 

    ![Convertir si l’énoncé pour changer d’expression](media/convert-if-to-switch-expression.png) 

## <a name="see-also"></a>Voir aussi

- [Refactorisation](../refactoring-in-visual-studio.md)
