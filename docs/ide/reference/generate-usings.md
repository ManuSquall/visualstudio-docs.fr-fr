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
ms.openlocfilehash: 9124054dec08fde94ec98ca9e3ebdfb6e48d7384
ms.sourcegitcommit: 614d5b99576ea27a41957cd94062dc95cbd29c1c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2019
ms.locfileid: "65531631"
---
# <a name="generate-usings-in-visual-studio"></a>Générer des instructions using dans Visual Studio

Cette génération de code s’applique à :

- C#

**Quoi :** Permet d’ajouter immédiatement les importations ou [instructions using](/dotnet/csharp/language-reference/keywords/using-statement) nécessaires au code copié-collé.

**Quand :** Il est pratique courante de copier du code à partir de différents endroits d’un projet ou d’autres sources, puis de le coller dans le nouveau code. Cette action rapide recherche les instructions d’importation manquantes dans le code copié-collé et vous invite à les ajouter.

**Pourquoi :** Comme l’action rapide ajoute automatiquement les importations nécessaires, vous n’avez pas besoin de copier manuellement les instructions `using` nécessaires à votre code.

## <a name="generate-usings-refactoring"></a>Générer des instructions using (refactorisation)

1. Copiez le code d’un autre fichier et collez-le dans un nouveau fichier sans inclure les instructions `using` nécessaires. L’erreur qui s’affiche est accompagnée d’un correctif de code qui ajoute les instructions `using` manquantes.

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
