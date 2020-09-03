---
title: Conversion de type anonyme en tuple
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
ms.openlocfilehash: f7e89c5b5a05900fe42af62ef87f70292e94e662
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "79094280"
---
# <a name="convert-anonymous-type-to-tuple"></a>Conversion de type anonyme en tuple

Cette refactorisation s’applique à :

- C#

- Visual Basic

**Ce qui suit :** Convertit un type anonyme en Tuple.

Dans les **cas suivants :** Vous avez un type anonyme qui qualifie comme Tuple.

**Pourquoi :** les [tuples](/dotnet/csharp/tuples) sont utiles pour conserver votre syntaxe légère. Cette action rapide permet de tirer plus facilement parti de cette fonctionnalité C#.

## <a name="how-to"></a>Procédures

1. Placez votre curseur dans un type anonyme.
2. Appuyez sur **CTRL** + **.** pour afficher le menu **Actions rapides et refactorisations**.

   ![Conversion de type anonyme en tuple](media/convert-anon-to-tuple.png)

2. Appuyez sur **Entrée** pour accepter la refactorisation.

   ![Conversion de type anonyme en tuple](media/convert-anon-to-tuple-complete.png)

## <a name="see-also"></a>Voir aussi

- [Refactorisation](../refactoring-in-visual-studio.md)
