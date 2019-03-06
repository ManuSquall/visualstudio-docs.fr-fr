---
title: Conversion de type anonyme en tuple
ms.date: 02/13/2019
ms.topic: reference
author: kendrahavens
ms.author: kendrahavens
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: b7a53aa8f329c1cdedc0cedff7e56b3f6dfa2f2a
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/18/2019
ms.locfileid: "56335778"
---
# <a name="convert-anonymous-type-to-tuple"></a>Conversion de type anonyme en tuple

Cette refactorisation s’applique à :

- C#

**Quoi :** convertir un type anonyme en tuple.

**Quand :** vous disposez d’un type anonyme qui peut être converti en tuple.

**Pourquoi :** les [tuples](/dotnet/csharp/tuples) sont utiles pour maintenir une syntaxe légère. Cette action rapide permet de tirer plus facilement parti de cette fonctionnalité C#.

## <a name="how-to"></a>Procédure

1. Placez votre curseur dans un type anonyme.
2. Appuyez sur **Ctrl**+**.** pour afficher le menu **Actions rapides et refactorisations**.

   ![Conversion de type anonyme en tuple](media/convert-anon-to-tuple.png)

2. Appuyez sur **Entrée** pour accepter la refactorisation.

   ![Conversion de type anonyme en tuple](media/convert-anon-to-tuple-complete.png)

## <a name="see-also"></a>Voir aussi

- [Refactorisation](../refactoring-in-visual-studio.md)
