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
ms.openlocfilehash: 96064b16e53081e0456ed43275acd5edf7ead468
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58152952"
---
# <a name="convert-local-function-to-method"></a>Convertir une fonction locale en méthode

Cette refactorisation s’applique à :

- C#
- Visual Basic

**Quoi :** Convertir une fonction locale en méthode

**Quand :** Vous souhaitez définir une fonction locale en dehors de votre contexte local actuel.

**Pourquoi :** Vous pouvez convertir une fonction locale en méthode pour pouvoir l’appeler en dehors de votre contexte local. Si votre fonction locale devient trop longue, vous pouvez la convertir en méthode. Le fait de la définir dans une méthode distincte rend votre code plus facile à lire.

## <a name="convert-local-function-to-method-refactoring"></a>Convertir une fonction locale en méthode (refactorisation)

1. Placez votre curseur dans une fonction locale.

    ![Convertir une fonction locale en méthode](media/convert-local-function-to-method.png)

2. Appuyez sur **Ctrl**+**.** pour afficher le menu **Actions rapides et refactorisations**.

    ![Convertir une fonction locale en méthode (correctif de code)](media/convert-local-function-to-method-codefix.png)

2. Appuyez sur **Entrée** pour accepter la refactorisation.

    ![Convertir une fonction locale en méthode (résultat)](media/convert-local-function-to-method-result.png)

## <a name="see-also"></a>Voir aussi

- [Refactorisation](../refactoring-in-visual-studio.md)
- [Conseils pour les développeurs .NET](../../ide/visual-studio-2017-for-dotnet-developers.md)
