---
title: Conversion de type anonyme en classe
ms.date: 02/13/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: f29e31fb87d8b18e7f5a46d16f90217ee08d51f6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62968527"
---
# <a name="convert-anonymous-type-to-class"></a>Conversion de type anonyme en classe

Cette refactorisation s’applique à :

- C#

**Quoi :** convertir un type anonyme en classe.

**Quand :** vous disposez d’un type anonyme que vous voulez continuer de développer dans une classe.

**Pourquoi :** les types anonymes sont utiles si vous les utilisez uniquement en local. À mesure que votre code se développe, il est intéressant de disposer d’un moyen simple de le promouvoir en classe.

## <a name="how-to"></a>Procédure

1. Placez votre curseur dans un type anonyme.
2. Appuyez sur **Ctrl**+**.** pour afficher le menu **Actions rapides et refactorisations**.

   ![Conversion de type anonyme en classe](media/convert-anon-to-class.png)

2. Appuyez sur **Entrée** pour accepter la refactorisation.

   ![Conversion de type anonyme en classe acceptée](media/convert-anon-to-class-complete.png)

## <a name="see-also"></a>Voir aussi

- [Refactorisation](../refactoring-in-visual-studio.md)
