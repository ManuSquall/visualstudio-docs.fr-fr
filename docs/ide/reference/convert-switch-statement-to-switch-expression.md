---
title: Convertir l’instruction switch en expression switch
ms.date: 06/19/2019
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: cc13cffe8352d9fb57f5bb991c3af615eddb2a14
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68740061"
---
# <a name="convert-switch-statement-to-switch-expression"></a>Convertir l’instruction switch en expression switch

Cette refactorisation s’applique à :

- C#

**Ce qui suit :** Convertit une [instruction switch](/dotnet/csharp/language-reference/keywords/switch) en [expression de commutateur](/dotnet/csharp/whats-new/csharp-8#switch-expressions)C# 8,0.

Dans les **cas suivants :** Vous souhaitez convertir une `switch` instruction en `switch` expression, et vice versa. 

**Pourquoi :** Si vous utilisez uniquement des expressions, cette refactorisation permet une transition aisée des `switch` instructions traditionnelles.

## <a name="how-to"></a>Procédures

1. Dans votre fichier de projet, [définissez la version du langage sur préversion](/dotnet/csharp/language-reference/configure-language-version#edit-the-project-file), car les expressions `switch` sont une nouvelle fonctionnalité de C# 8.0.
2. Placez votre curseur dans le `switch` mot clé et appuyez sur **CTRL** + **.** pour afficher le menu **Actions rapides et refactorisations**.
3. Sélectionnez **Convert l’instruction switch en expression**.

   ![Convertir l’instruction switch en expression switch](media/convert-switch-statement-to-switch-expression.png) 

## <a name="see-also"></a>Voir aussi

- [Refactorisation](../refactoring-in-visual-studio.md)
