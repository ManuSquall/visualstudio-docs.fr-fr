---
title: Convertir une fonction locale en méthode
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 3572682fe68d9b0b1bc4adee537de5cd056a8906
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "71301690"
---
# <a name="convert-a-local-function-to-a-method"></a>Convertir une fonction locale en méthode

Cette refactorisation s’applique à :

- C#

**Quoi :** Convertir une fonction locale en méthode.

**Quand :** Vous avez une fonction locale que vous souhaitez définir en dehors de votre contexte local actuel.

**Pourquoi:** Vous souhaitez convertir une fonction locale en méthode afin que vous puissiez l’appeler en dehors de votre contexte local. Si votre fonction locale devient trop longue, vous pouvez la convertir en méthode. Lorsque vous définissez la fonction dans une méthode distincte, votre code est plus facile à lire.

## <a name="convert-local-function-to-method-refactoring"></a>Convertir une fonction locale en méthode (refactorisation)

1. Placez votre curseur dans la fonction locale.

    ![Exemple de code, convertir une fonction locale en méthode](media/convert-local-function-to-method.png)

2. Appuyez **sur Ctrl**+**.** pour afficher le menu **Actions rapides et refactorisations**.

    ![Exemple, convertir une fonction locale en méthode (correctif de code)](media/convert-local-function-to-method-codefix.png)

2. Appuyez sur Entrée pour accepter la refactorisation.

    ![Exemple, convertir une fonction locale en méthode (résultat)](media/convert-local-function-to-method-result.png)

## <a name="see-also"></a>Voir aussi

- [Refactorisation](../refactoring-in-visual-studio.md)
- [Conseils pour les développeurs .NET](../csharp-developer-productivity.md)
