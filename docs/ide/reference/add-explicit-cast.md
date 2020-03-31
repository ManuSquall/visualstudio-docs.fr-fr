---
title: Ajouter un cast explicite
ms.date: 03/26/2020
ms.topic: reference
author: y87feng
ms.author: t-yufen
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 78a61a8ed782df935a146b111bbc4107fa7c6d82
ms.sourcegitcommit: 0ba0cbff77eac15feab1a73eeee3667006794b29
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/31/2020
ms.locfileid: "80417321"
---
# <a name="add-explicit-cast"></a>Ajouter un cast explicite

Cette génération de code s’applique à :

- C#

**Quoi :** Vous permet d’ajouter automatiquement un casting explicite à une expression, basée sur l’utilisation.

**Quand :** Vous devez ajouter un casting explicite à une expression et souhaitez l’attribuer correctement automatiquement.

**Pourquoi:** Vous pouvez ajouter un casting explicite à une expression manuellement, mais cette fonctionnalité l’ajoute automatiquement en fonction du contexte du code.

## <a name="how-to-use-it"></a>Comment l’utiliser ?

1. Placez votre caret sur l’erreur.
2. Appuyez **sur Ctrl**+**.** pour afficher le menu **Actions rapides et refactorisations**.
3. Sélectionnez **Ajouter un casting explicite**.

   ![Ajouter une action rapide explicite dans Visual Studio](media/add-explicit-cast.png)

## <a name="see-also"></a>Voir aussi

- [Génération de codes](../code-generation-in-visual-studio.md)
- [Refactorisation](../refactoring-in-visual-studio.md)
