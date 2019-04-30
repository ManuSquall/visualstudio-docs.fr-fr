---
title: Convertir une fonction locale en méthode
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: a580077528c87e62f81e840ed6dee76ff1eac57f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62968275"
---
# <a name="convert-a-local-function-to-a-method"></a>Convertir une fonction locale en méthode

Cette refactorisation s’applique à :

- C#
- Visual Basic

**Quoi :** Convertir une fonction locale en méthode.

**Quand :** Vous souhaitez définir une fonction locale en dehors de votre contexte local actuel.

**Pourquoi :** Vous voulez convertir une fonction locale en méthode pour pouvoir l’appeler en dehors de votre contexte local. Si votre fonction locale devient trop longue, vous pouvez la convertir en méthode. Lorsque vous définissez la fonction dans une méthode distincte, votre code est plus facile à lire.

## <a name="convert-local-function-to-method-refactoring"></a>Convertir une fonction locale en méthode (refactorisation)

1. Placez votre curseur dans la fonction locale.

    ![Exemple de code, convertir une fonction locale en méthode](media/convert-local-function-to-method.png)

2. Appuyez sur **Ctrl**+**.** pour afficher le menu **Actions rapides et refactorisations**.

    ![Exemple, convertir une fonction locale en méthode (correctif de code)](media/convert-local-function-to-method-codefix.png)

2. Appuyez sur Entrée pour accepter la refactorisation.

    ![Exemple, convertir une fonction locale en méthode (résultat)](media/convert-local-function-to-method-result.png)

## <a name="see-also"></a>Voir aussi

- [Refactorisation](../refactoring-in-visual-studio.md)
- [Conseils pour les développeurs .NET](../../ide/visual-studio-2017-for-dotnet-developers.md)
