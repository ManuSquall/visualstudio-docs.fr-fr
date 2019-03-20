---
title: Conversion de type anonyme en tuple
ms.date: 02/13/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: b6f5dd8e53ed2e0695370a1cdcb837609be30035
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58154437"
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
