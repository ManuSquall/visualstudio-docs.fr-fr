---
title: Fractionner ou fusionner des instructions if
ms.date: 06/12/2019
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 405ccd4bc0197ce06aa14982a16dc02f6d13a537
ms.sourcegitcommit: d4920babfc3d24a3fe1d4bf446ed3fe73b344467
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2019
ms.locfileid: "67160735"
---
# <a name="split-or-merge-if-statements"></a>Fractionner ou fusionner des instructions if

Cette refactorisation s’applique à :

- C#

**Quoi :** **Quoi :** Fractionner ou fusionner les instructions [if](/dotnet/csharp/language-reference/keywords/if-else).

**Quand :** Vous souhaitez fractionner une instruction `if` qui utilise les opérateurs `&&` ou `||` dans une instruction `if` imbriquée, ou fusionner et une instruction `if` avec une instruction `if` externe.

**Pourquoi :** C’est une question de préférence de style.  

## <a name="how-to"></a>Procédure

Si vous souhaitez fractionner l’instruction `if` :

1. Placez votre curseur dans l’instruction `if` au niveau de l’opérateur `&&` ou `||`.

2. Appuyez sur **Ctrl**+ **.** pour afficher le menu **Actions rapides et refactorisations**.

    ![Instruction Split If](../media/split-if-statement.png)

3. Sélectionnez **Fractionner en instructions if imbriquées**.

    ![Instruction if fractionnée](../media/split-if-statement-complete.png)

Si vous souhaitez fusionner une instruction `if` interne avec une instruction `if` externe : 

1. Placez votre curseur dans le mot clé `if` interne.

2. Appuyez sur **Ctrl**+ **.** pour afficher le menu **Actions rapides et refactorisations**.

    ![Instruction Merge If](../media/merge-if-statement.png)

3. Sélectionnez **Fusionner avec instruction if externe**.

    ![Instruction if fusionnée](../media/merge-if-statement-complete.png)

## <a name="see-also"></a>Voir aussi

- [Refactorisation](../refactoring-in-visual-studio.md)