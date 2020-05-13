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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "68740061"
---
# <a name="convert-switch-statement-to-switch-expression"></a>Convertir l’instruction switch en expression switch

Cette refactorisation s’applique à :

- C#

**Quoi :** Convertir une [déclaration de commutation](/dotnet/csharp/language-reference/keywords/switch) en expression de [commutateur](/dotnet/csharp/whats-new/csharp-8#switch-expressions)C 8.0 .

**Quand :** Vous voulez convertir `switch` une `switch` déclaration en expression et vice versa. 

**Pourquoi:** Si vous n’utilisez que des expressions, ce refactoring permet une transition facile des énoncés traditionnels. `switch`

## <a name="how-to"></a>Procédures

1. Dans votre fichier de projet, [définissez la version du langage sur préversion](/dotnet/csharp/language-reference/configure-language-version#edit-the-project-file), car les expressions `switch` sont une nouvelle fonctionnalité de C# 8.0.
2. Placez votre curseur `switch` dans le mot-clé et appuyez sur **Ctrl**+**.** pour afficher le menu **Actions rapides et refactorisations**.
3. Sélectionnez **Convert l’instruction switch en expression**.

   ![Convertir l’instruction switch en expression switch](media/convert-switch-statement-to-switch-expression.png) 

## <a name="see-also"></a>Voir aussi

- [Refactorisation](../refactoring-in-visual-studio.md)
