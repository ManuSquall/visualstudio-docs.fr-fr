---
title: Déplacer un type vers un fichier correspondant (refactorisation)
description: Déplacez un type vers un fichier distinct portant le même nom. Cliquez avec le bouton droit sur le type, sélectionnez Actions rapides et refactorisations, puis sélectionnez Déplacer le type vers <TypeName>.
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 728b9e176a40d2bfd7ae36a329409cb27f80fc86
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99927953"
---
# <a name="move-a-type-to-a-matching-file-refactoring"></a>Déplacer un type vers un fichier correspondant (refactorisation)

Cette refactorisation s’applique à :

- C#

- Visual Basic

**Quoi :** vous permet de déplacer le type sélectionné vers un fichier distinct portant le même nom.

**Quand :** vous avez plusieurs classes, structures, interfaces, etc. dans un même fichier et que vous souhaitez les séparer.

**Pourquoi :** placer plusieurs types dans un même fichier peut ralentir la recherche de ces types. En déplaçant les types vers des fichiers portant le même nom, le code devient plus lisible et cela facilite la navigation.

## <a name="how-to"></a>Procédures

1. Placez le curseur dans le nom du type dans lequel il est défini. Par exemple :

   ```csharp
   class Person
   ```

   ```vb
   Class Person
   ```

2. Effectuez ensuite l'une des opérations suivantes :

   - Appuyez sur **CTRL** + **.**
   - Cliquez avec le bouton droit sur le nom du type et sélectionnez **Actions rapides et refactorisations**.

1. Sélectionnez **Déplacer le type vers *NomType*.cs** dans le menu, où *NomType* est le nom du type que vous avez sélectionné.

   Le type est déplacé vers un nouveau fichier, dans le projet, qui porte le même nom que le type.

   - C# :

      ![Résultat de l’action Inclure (C#)](media/movetype-result-cs.png)

   - Visual Basic :

      ![Résultat de l’action Inclure (Visual Basic)](media/movetype-result-vb.png)

## <a name="see-also"></a>Voir aussi

- [Refactorisation](../refactoring-in-visual-studio.md)
