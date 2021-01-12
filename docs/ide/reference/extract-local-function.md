---
title: Extraire la fonction locale
description: Transformez un fragment de code en sa propre fonction en sélectionnant le code et en tapant Ctrl + R, Ctrl + M.
ms.date: 02/19/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: e007246b85671a0f4606bbdb3d1e9c4e0dc83541
ms.sourcegitcommit: cd7f122c6850cf442a4ca42d51d05c7a8fe9038d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/12/2021
ms.locfileid: "98129456"
---
# <a name="extract-local-function-refactoring"></a>Extraire la fonction locale refactorisation

Cette refactorisation s’applique à :

- C#

**Ce qui suit :** Vous permet de transformer un fragment de code d’une méthode existante en fonction locale.

Dans les **cas suivants :** Vous avez un fragment de code existant dans une méthode qui doit être appelée à partir d’une fonction locale.

**Pourquoi :** vous pouvez copier/coller ce code, mais cela entraîne une duplication. Une meilleure solution consiste à refactoriser ce fragment dans sa propre fonction locale.

## <a name="how-to"></a>Procédures

1. Mettez en surbrillance le code à extraire.

2. Appuyez sur **CTRL** + **.** pour afficher le menu **Actions rapides et refactorisations**. 

3. Sélectionnez **Extraire la fonction locale**.

    ![Capture d’écran de la fenêtre Visual Studio code avec une ligne mise en surbrillance. Le menu actions rapides et refactorisations est ouvert et l’option extraire la fonction locale est sélectionnée.](media/extract-local-function.png)

## <a name="see-also"></a>Voir aussi

- [Refactorisation](../refactoring-in-visual-studio.md)
- [Aperçu des modifications](../../ide/preview-changes.md)
