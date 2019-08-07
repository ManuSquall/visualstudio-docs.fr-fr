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
ms.sourcegitcommit: b56dc6fadc6c924beed36bb4c2ccc16cf6bcfa1c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/02/2019
ms.locfileid: "68740061"
---
# <a name="convert-switch-statement-to-switch-expression"></a>Convertir l’instruction switch en expression switch

Cette refactorisation s’applique à :

- C#

**Quoi :** Convertissez une [instruction switch](/dotnet/csharp/language-reference/keywords/switch) en [expression switch](/dotnet/csharp/whats-new/csharp-8#switch-expressions) C# 8.0.

**Quand :** Vous souhaitez convertir une instruction `switch` en expression `switch` et vice versa. 

**Pourquoi :** Si vous utilisez uniquement des expressions, cette refactorisation permet une transition facile à partir des instructions `switch` traditionnelles.

## <a name="how-to"></a>Procédure

1. Dans votre fichier de projet, [définissez la version du langage sur préversion](/dotnet/csharp/language-reference/configure-language-version#edit-the-project-file), car les expressions `switch` sont une nouvelle fonctionnalité de C# 8.0.
2. Placez votre curseur dans le mot clé `switch`, puis appuyez sur **Ctrl**+ **.** pour afficher le menu **Actions rapides et refactorisations**.
3. Sélectionnez **Convert l’instruction switch en expression**.

   ![Convertir l’instruction switch en expression switch](media/convert-switch-statement-to-switch-expression.png) 

## <a name="see-also"></a>Voir aussi

- [Refactorisation](../refactoring-in-visual-studio.md)
