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
ms.sourcegitcommit: 9a3972eb85de5443ac2bc03964c5a251c39b2921
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/26/2019
ms.locfileid: "71301690"
---
# <a name="convert-a-local-function-to-a-method"></a>Convertir une fonction locale en méthode

Cette refactorisation s’applique à :

- C#

**Quoi :** Convertir une fonction locale en méthode.

**Quand :** Vous souhaitez définir une fonction locale en dehors de votre contexte local actuel.

**Pourquoi :** Vous voulez convertir une fonction locale en méthode pour pouvoir l’appeler en dehors de votre contexte local. Si votre fonction locale devient trop longue, vous pouvez la convertir en méthode. Lorsque vous définissez la fonction dans une méthode distincte, votre code est plus facile à lire.

## <a name="convert-local-function-to-method-refactoring"></a>Convertir une fonction locale en méthode (refactorisation)

1. Placez votre curseur dans la fonction locale.

    ![Exemple de code, convertir une fonction locale en méthode](media/convert-local-function-to-method.png)

2. Appuyez sur **Ctrl**+ **.** pour afficher le menu **Actions rapides et refactorisations**.

    ![Exemple, convertir une fonction locale en méthode (correctif de code)](media/convert-local-function-to-method-codefix.png)

2. Appuyez sur Entrée pour accepter la refactorisation.

    ![Exemple, convertir une fonction locale en méthode (résultat)](media/convert-local-function-to-method-result.png)

## <a name="see-also"></a>Voir aussi

- [Refactorisation](../refactoring-in-visual-studio.md)
- [Conseils pour les développeurs .NET](../csharp-developer-productivity.md)
