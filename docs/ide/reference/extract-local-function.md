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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "77515329"
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

    ![Extraire la fonction locale](media/extract-local-function.png)

## <a name="see-also"></a>Voir aussi

- [Refactorisation](../refactoring-in-visual-studio.md)
- [Aperçu des modifications](../../ide/preview-changes.md)
