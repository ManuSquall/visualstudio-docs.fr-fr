---
title: Extraire la fonction locale
description: Transformez un fragment de code en sa propre fonction en sélectionnant le code et en tapant Ctrl + R, Ctrl + M.
ms.date: 02/19/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 80ac8f23b5404d70b70166915cd791f2c0d7ed07
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99860969"
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
