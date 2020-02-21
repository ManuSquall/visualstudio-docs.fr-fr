---
title: Générer des instructions using
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
helpviewer_keywords:
- add missing usings
ms.openlocfilehash: f3b3435e10d6bb9a71fd16b9286759b136c167f4
ms.sourcegitcommit: ea5e02720d71185f8e27fbea205024371b0c7ceb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77544543"
---
# <a name="add-missing-usings-in-visual-studio"></a>Ajouter des instructions using manquantes dans Visual Studio

Cette génération de code s’applique à :

- C#

**Ce qui suit :** Vous permet d’ajouter immédiatement les importations nécessaires ou d' [utiliser des directives](/dotnet/csharp/language-reference/keywords/using-directive) pour le code copié et collé.

Dans les **cas suivants :** Il est courant de copier le code à partir de différents emplacements de votre projet ou d’autres sources et de le coller dans le nouveau code. Cette action rapide recherche des directives Imports manquantes pour le code copié et collé, puis vous invite à les ajouter. Ce correctif de code peut également ajouter des références du projet au projet.

**Pourquoi :** Étant donné que l’action rapide ajoute automatiquement les importations nécessaires, vous n’avez pas besoin de copier manuellement les directives de `using` dont votre code a besoin.

## <a name="add-missing-usings-refactoring"></a>Ajouter des instructions using manquantes par refactorisation

1. Copiez le code à partir d’un fichier et collez-le dans un nouveau fichier sans inclure les directives de `using` nécessaires. L’erreur obtenue est accompagnée d’un correctif de code qui ajoute les directives de `using` manquantes.

    > [!NOTE]
    > Vous devez activer cette suggestion dans **Outils > Options > Éditeur de texte > C# > Avancé > Directives Using**.

2. Sélectionnez Ctrl+. pour ouvrir le menu **Actions rapides et refactorisations**.

    ![Générer des instructions using](media/generate-using-codefix.png)

3. Sélectionnez **using \<votre référence\>;** pour ajouter la référence manquante.

    ![Générer des instructions using (résultat)](media/generate-using-result.png)

## <a name="see-also"></a>Voir aussi

- [Génération de code](../code-generation-in-visual-studio.md)
- [Aperçu des modifications](../../ide/preview-changes.md)
- [Conseils pour les développeurs .NET](../csharp-developer-productivity.md)
