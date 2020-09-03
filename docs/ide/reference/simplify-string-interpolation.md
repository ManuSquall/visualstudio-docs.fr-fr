---
title: Simplifier l’interpolation de chaîne
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: a8b0fd53164cb98921b111d49fa04a76c9d0d8a8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "79094302"
---
# <a name="simplify-string-interpolation-refactoring"></a>Simplifier la refactorisation de l’interpolation de chaîne

Cette refactorisation s’applique à :

- C#

- Visual Basic

**Ce qui suit :** Vous permet de simplifier une [interpolation de chaîne](https://docs.microsoft.com/dotnet/csharp/tutorials/string-interpolation).

Dans les **cas suivants :** Vous avez une interpolation de chaîne qui peut être simplifiée.

**Pourquoi :** La simplification d’une interpolation de chaîne peut fournir une plus grande clarté et une syntaxe concise. Cet outil de refactorisation effectuera automatiquement la tâche au lieu de devoir le faire manuellement.

## <a name="how-to"></a>Procédures

1. Placez le signe insertion sur l’interpolation de chaîne :

2. Appuyez sur **CTRL** + **.** pour afficher le menu **Actions rapides et refactorisations**.

3. Sélectionner **simplifier l’interpolation**

    ![Simplifier l’interpolation de chaîne](media/simplify-string-interpolation.png)

## <a name="see-also"></a>Voir aussi

- [Refactorisation](../refactoring-in-visual-studio.md)