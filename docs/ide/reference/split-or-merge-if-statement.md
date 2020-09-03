---
title: Fractionner ou fusionner des instructions if
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
ms.openlocfilehash: a3b42f83faacda6be34b282150cf4fb4c0f379f1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "79093651"
---
# <a name="split-or-merge-if-statements"></a>Fractionner ou fusionner des instructions if

Cette refactorisation s’applique à :

- C#

- Visual Basic

**Quoi :** instructions **de fractionnement** ou de fusion [si](/dotnet/csharp/language-reference/keywords/if-else) .

Dans les **cas suivants :** Vous souhaitez fractionner une instruction `if` qui utilise les `&&` `||` opérateurs ou dans une instruction imbriquée `if` , ou fusionner une `if` instruction avec une `if` instruction externe.

**Pourquoi :** C’est une question de préférence de style.  

## <a name="how-to"></a>Procédures

Si vous souhaitez fractionner l’instruction `if` :

1. Placez votre curseur dans l’instruction `if` au niveau de l’opérateur `&&` ou `||`.

2. Appuyez sur **CTRL** + **.** pour afficher le menu **Actions rapides et refactorisations**.

    ![Instruction Split If](../media/split-if-statement.png)

3. Sélectionnez **Fractionner en instructions if imbriquées**.

    ![Instruction if fractionnée](../media/split-if-statement-complete.png)

Si vous souhaitez fusionner une instruction `if` interne avec une instruction `if` externe : 

1. Placez votre curseur dans le mot clé `if` interne.

2. Appuyez sur **CTRL** + **.** pour afficher le menu **Actions rapides et refactorisations**.

    ![Instruction Merge If](../media/merge-if-statement.png)

3. Sélectionnez **Fusionner avec instruction if externe**.

    ![Instruction if fusionnée](../media/merge-if-statement-complete.png)

## <a name="see-also"></a>Voir aussi

- [Refactorisation](../refactoring-in-visual-studio.md)