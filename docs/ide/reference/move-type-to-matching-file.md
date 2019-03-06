---
title: Déplacer un type vers un fichier correspondant (refactorisation)
ms.date: 01/26/2018
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 31e3b12f6a19ea64e43f7a5e00e3c795cc7358e0
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55941034"
---
# <a name="move-a-type-to-a-matching-file-refactoring"></a>Déplacer un type vers un fichier correspondant (refactorisation)

Cette refactorisation s’applique à :

- C#

- Visual Basic

**Quoi :** Vous permet de déplacer le type sélectionné vers un fichier distinct portant le même nom.

**Quand :** Vous avez plusieurs classes, structs, interfaces, etc. dans un même fichier et vous souhaitez les séparer.

**Pourquoi :** Placer plusieurs types dans un même fichier peut compliquer la recherche de ces types. En déplaçant les types vers des fichiers portant le même nom, le code devient plus lisible et cela facilite la navigation.

## <a name="how-to"></a>Procédure

1. Placez le curseur dans le nom du type dans lequel il est défini. Par exemple :

   ```csharp
   class Person
   ```

   ```vb
   Class Person
   ```

2. Effectuez ensuite l'une des opérations suivantes :

   - Appuyez sur **Ctrl**+**.**
   - Cliquez avec le bouton droit sur le nom du type et sélectionnez **Actions rapides et refactorisations**.

1. Sélectionnez **Déplacer le type vers *NomType*.cs** dans le menu, où *NomType* est le nom du type que vous avez sélectionné.

   Le type est déplacé vers un nouveau fichier, dans le projet, qui porte le même nom que le type.

   - C# :

      ![Résultat de l’action Inclure (C#)](media/movetype-result-cs.png)

   - Visual Basic :

      ![Résultat de l’action Inclure (Visual Basic)](media/movetype-result-vb.png)

## <a name="see-also"></a>Voir aussi

- [Refactorisation](../refactoring-in-visual-studio.md)
