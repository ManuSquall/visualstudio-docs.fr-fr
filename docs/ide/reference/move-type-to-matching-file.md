---
title: Déplacer un type vers un fichier correspondant (refactorisation)
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 997cf31d14acd65abd003bcb00cce4a9797b394a
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53059637"
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
