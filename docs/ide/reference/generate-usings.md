---
title: Générer des instructions using
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kendrahavens
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 9fd34b40bdd1167eca7fa1dff8ab60bcc787b7c7
ms.sourcegitcommit: 11337745c1aaef450fd33e150664656d45fe5bc5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57324754"
---
# <a name="generate-usings-in-visual-studio"></a>Générer des instructions using dans Visual Studio

Cette génération de code s’applique à :

- C#

**Quoi :** **Quoi :** Permet d’ajouter immédiatement les importations ou [instructions using](/dotnet/csharp/language-reference/keywords/using-statement) nécessaires du code copié-collé.

**Quand :** Il est pratique courante de copier-coller du code à partir de différents endroits d’un projet ou d’autres sources de code. Cette action rapide analyse les importations manquantes dans le code copié-collé et vous invite à les ajouter.

**Pourquoi :** Les importations nécessaires étant ajoutées automatiquement, l’utilisateur n’a pas besoin de copier manuellement les instructions `using` requises.

## <a name="generate-usings-refactoring"></a>Générer des instructions using (refactorisation)

1. Copiez le code d’un autre fichier et collez-le sans inclure les instructions `using` nécessaires. L’erreur est désormais accompagnée d’un correctif de code qui ajoute les instructions `using` manquantes.

    > [!NOTE] 
    > Cette suggestion doit être activée dans **Outils > Options > Éditeur de texte > C# > Avancé > Directives Using**.

2. Appuyez sur **Ctrl**+**.** pour ouvrir le menu **Actions rapides et refactorisations**. 

    ![Générer des instructions using](media/generate-using-codefix.png)

3. Sélectionnez **using \<votre référence\>;** pour ajouter la référence manquante.

    ![Générer des instructions using (résultat)](media/generate-using-result.png)

## <a name="see-also"></a>Voir aussi

- [Génération de code](../code-generation-in-visual-studio.md)
- [Aperçu des modifications](../../ide/preview-changes.md)
- [Conseils pour les développeurs .NET](../../ide/visual-studio-2017-for-dotnet-developers.md)