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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "79094165"
---
# <a name="convert-if-statement-to-switch-statement-or-switch-expression"></a>Convertir l’instruction if en instruction switch ou en expression switch

Cette refactorisation s’applique à :

- C#

**Ce qui suit :** Convertit une instruction if en une [instruction switch](/dotnet/csharp/language-reference/keywords/switch) ou en une [expression de commutateur](/dotnet/csharp/whats-new/csharp-8#switch-expressions)C# 8,0.

Dans les **cas suivants :** Vous souhaitez convertir une `if` instruction en une `switch` instruction ou une `switch` expression, et vice versa. 

**Pourquoi :** Si vous utilisez une `if` instruction, cette refactorisation permet une transition facile vers des `switch` instructions ou des `switch` expressions.

## <a name="how-to"></a>Procédures

1. Placez votre curseur dans le mot clé `if`.
2. Appuyez sur **CTRL** + **.** pour afficher le menu **Actions rapides et refactorisations**.
3. Sélectionnez l’une des deux options suivantes : 

    Sélectionnez **convertir en instruction « switch »**.

   ![Convertir l’instruction if en instruction switch](media/convert-if-to-switch-statement.png) 

    Sélectionnez **convertir en expression « Switch »**. 

    ![Convertir l’instruction if en expression Switch](media/convert-if-to-switch-expression.png) 

## <a name="see-also"></a>Voir aussi

- [Refactorisation](../refactoring-in-visual-studio.md)
