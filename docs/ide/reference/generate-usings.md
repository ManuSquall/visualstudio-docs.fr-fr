---
title: Générer des instructions using
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
helpviewer_keywords:
- add missing usings
ms.openlocfilehash: 903b160bac0e8096062e09fd78ff4c92c46cf8ee
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094310"
---
# <a name="add-missing-usings-in-visual-studio"></a>Ajouter des instructions using manquantes dans Visual Studio

Cette génération de code s’applique à :

- C#

- Visual Basic

**Quoi :** Vous permet d’ajouter immédiatement les importations nécessaires ou [d’utiliser des directives](/dotnet/csharp/language-reference/keywords/using-directive) pour le code copier-coller.

**Quand :** Il est courant de copier du code à partir de différents endroits de votre projet ou d’autres sources et de le coller dans le nouveau code. Cette action rapide trouve des directives d’importation manquantes pour le code copier-coller et vous invite ensuite à les ajouter. Ce correctif de code peut également ajouter des références d’un projet à l’autre.

**Pourquoi:** Étant donné que l’action rapide ajoute automatiquement les importations nécessaires, vous n’avez pas besoin de copier manuellement les `using` directives dont votre code a besoin.

## <a name="add-missing-usings-refactoring"></a>Ajouter des instructions using manquantes par refactorisation

1. Copiez le code d’un fichier et collez-le dans un nouveau sans inclure les directives nécessaires. `using` L’erreur résultante est accompagnée d’un `using` correctif de code qui ajoute les directives manquantes.

    > [!NOTE]
    > Vous devez activer cette suggestion dans **Outils > Options > Éditeur de texte > C# > Avancé > Directives Using**.

2. Sélectionnez Ctrl+. pour ouvrir le menu **Actions rapides et refactorisations**.

    ![Générer des instructions using](media/generate-using-codefix.png)

3. Sélectionnez **using \<votre référence\>;** pour ajouter la référence manquante.

    ![Générer des instructions using (résultat)](media/generate-using-result.png)

## <a name="see-also"></a>Voir aussi

- [Génération de codes](../code-generation-in-visual-studio.md)
- [Aperçu des modifications](../../ide/preview-changes.md)
- [Conseils pour les développeurs .NET](../csharp-developer-productivity.md)
