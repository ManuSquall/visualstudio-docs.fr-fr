---
title: Convertir l’instruction if en instruction switch ou expression Switch
ms.date: 02/12/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: cb0c06fe0493f973ea9cf0a566ffda45a49eeeff
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/15/2020
ms.locfileid: "77280781"
---
# <a name="convert-if-statement-to-switch-statement-or-switch-expression"></a>Convertir l’instruction if en instruction switch ou expression Switch

Cette refactorisation s’applique à :

- C#

**Ce qui suit :** Convertit une instruction if en une [instruction switch](/dotnet/csharp/language-reference/keywords/switch) ou C# en une [expression de commutateur](/dotnet/csharp/whats-new/csharp-8#switch-expressions)8,0.

Dans les **cas suivants :** Vous souhaitez convertir une instruction `if` en une instruction `switch` ou une expression `switch` et vice versa. 

**Pourquoi :** Si vous utilisez une instruction `if`, cette refactorisation permet une transition facile vers des instructions `switch` ou des expressions `switch`.

## <a name="how-to"></a>Procédures

1. Placez votre curseur dans le mot clé `if`.
2. Appuyez sur **Ctrl**+ **.** pour afficher le menu **Actions rapides et refactorisations**.
3. Sélectionnez **convertir en instruction « switch »** .

   ![Convertir l’instruction if en instruction switch ou expression Switch](media/convert-if-statement-to-switch-statement-or-switch-expression.png) 

## <a name="see-also"></a>Voir aussi

- [Refactorisation](../refactoring-in-visual-studio.md)
