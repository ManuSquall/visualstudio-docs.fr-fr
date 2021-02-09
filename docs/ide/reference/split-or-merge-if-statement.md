---
title: Fractionner ou fusionner des instructions if
description: Découvrez comment utiliser le menu actions rapides et refactorisations pour fractionner ou fusionner des instructions If.
ms.custom: SEO-VS-2020
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 30ec77382cf404bc74f2ff5fed71cff360b9f28e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99893384"
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