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
ms.openlocfilehash: ecb7750301101a2607c17e68b5e919623a03caba
ms.sourcegitcommit: 7eb2fb21805d92f085126f3a820ac274f2216b4e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/22/2019
ms.locfileid: "67329066"
---
# <a name="convert-switch-statement-to-switch-expression"></a>Convertir l’instruction switch en expression switch

Cette refactorisation s’applique à :

- C#

**Quoi :** Convertissez une [instruction switch](/dotnet/csharp/language-reference/keywords/switch) en [expression switch](/dotnet/csharp/whats-new/csharp-8#switch-expressions) C# 8.0.

**Quand :** Vous souhaitez convertir une instruction `switch` en expression `switch` et vice versa. 

**Pourquoi :** Si vous utilisez uniquement des expressions, cette refactorisation permet une transition facile à partir des instructions `switch` traditionnelles.

## <a name="how-to"></a>Procédure

1. Dans votre fichier de projet, [définissez la version du langage sur préversion](/dotnet/csharp/language-reference/configure-language-version#set-the-language-version-in-visual-studio), car les expressions `switch` sont une nouvelle fonctionnalité de C# 8.0.
2. Placez votre curseur dans le mot clé `switch`, puis appuyez sur **Ctrl**+ **.** pour afficher le menu **Actions rapides et refactorisations**.
3. Sélectionnez **Convert l’instruction switch en expression**.

   ![Convertir l’instruction switch en expression switch](media/convert-switch-statement-to-switch-expression.png) 

## <a name="see-also"></a>Voir aussi

- [Refactorisation](../refactoring-in-visual-studio.md)
