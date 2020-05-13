---
title: Extraire la fonction locale
description: Transformez un fragment de code en sa propre méthode en sélectionnant le code et en tapant Ctrl+R, Ctrl+M.
ms.date: 02/19/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 031fbe22ec61837d489df7a6af923ef0cd2454c7
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77515329"
---
# <a name="extract-local-function-refactoring"></a>Extraire la refactoration de la fonction locale

Cette refactorisation s’applique à :

- C#

**Quoi :** Permet de transformer un fragment de code à partir d’une méthode existante en une fonction locale.

**Quand :** Vous avez un fragment de code existant dans une méthode qui doit être appelé à partir d’une fonction locale.

**Pourquoi :** vous pouvez copier/coller ce code, mais cela entraîne une duplication. Une meilleure solution est de refactorer ce fragment dans sa propre fonction locale.

## <a name="how-to"></a>Procédures

1. Mettez en évidence le code à extraire.

2. Appuyez **sur Ctrl**+**.** pour afficher le menu **Actions rapides et refactorisations**. 

3. Sélectionnez **Extraire la fonction locale**.

    ![Extraire la fonction locale](media/extract-local-function.png)

## <a name="see-also"></a>Voir aussi

- [Refactorisation](../refactoring-in-visual-studio.md)
- [Aperçu des modifications](../../ide/preview-changes.md)
