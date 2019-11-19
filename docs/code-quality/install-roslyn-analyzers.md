---
title: Installer des analyseurs Roslyn
ms.date: 08/03/2018
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 9013d7be60a8091f7ce4fc4fe92fa4acaef43720
ms.sourcegitcommit: f9f389e72787de30eb869a55ef7725a10a4011f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/06/2019
ms.locfileid: "73636535"
---
# <a name="install-net-compiler-platform-code-analyzers"></a>Installer .NET Compiler Platform analyseurs de code

Visual Studio comprend un ensemble principal d’analyseurs de .NET Compiler Platform (*Roslyn*). Ces analyseurs sont toujours activés. Vous pouvez installer des analyseurs supplémentaires en tant que packages NuGet ou en tant qu’extensions Visual Studio dans des fichiers *VSIX* .

## <a name="to-install-nuget-analyzer-packages"></a>Pour installer les packages de l’analyseur NuGet

1. Recherchez le package de l’analyseur que vous souhaitez installer sur www.nuget.org.

   Par exemple, vous souhaiterez peut-être [installer les analyseurs Microsoft FXCop](install-fxcop-analyzers.md#nuget-package) pour vérifier votre code en matière de problèmes de sécurité et de performances, entre autres. Ou installez [StyleCop. Analyzers](https://www.nuget.org/packages/stylecop.analyzers/) pour rechercher les problèmes de style dans votre base de code.

2. Installez le package dans Visual Studio, à l’aide de la [console du gestionnaire de package](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console) ou de l' [interface utilisateur du gestionnaire de package](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console).

   > [!NOTE]
   > La page www.nuget.org pour chaque package de l’analyseur vous indique la commande à coller dans la **console du gestionnaire de package**. Il y a même un bouton pratique pour copier le texte dans le presse-papiers.

   Les assemblys de l’analyseur sont installés et s’affichent dans **Explorateur de solutions** sous **références** > **analyseurs**.

## <a name="to-install-vsix-analyzers"></a>Pour installer les analyseurs VSIX

::: moniker range="vs-2017"

1. Dans Visual Studio, sélectionnez **outils** > **extensions et mises à jour**.

   La boîte de dialogue **Extensions et mises à jour** s’ouvre.

   > [!NOTE]
   > Vous pouvez également rechercher et télécharger l’extension de l’analyseur directement à partir de [Visual Studio Marketplace](https://marketplace.visualstudio.com).

::: moniker-end

::: moniker range=">=vs-2019"

1. Dans Visual Studio, sélectionnez **extensions** > **gérer les extensions**.

   La boîte de dialogue **gérer les extensions** s’ouvre.

   > [!NOTE]
   > Vous pouvez également rechercher et télécharger l’extension de l’analyseur directement à partir de [Visual Studio Marketplace](https://marketplace.visualstudio.com).

::: moniker-end

2. Développez **en ligne** dans le volet gauche, puis sélectionnez **Visual Studio Marketplace**.

3. Dans la zone de recherche, tapez le nom de l’extension de l’analyseur que vous souhaitez installer. Par exemple, vous souhaiterez peut-être [installer les analyseurs Microsoft FXCop](install-fxcop-analyzers.md#vsix) pour vérifier votre code en matière de problèmes de sécurité et de performances, entre autres.

4. Sélectionnez **Télécharger**.

   L’extension est téléchargée.

5. Sélectionnez **OK** pour fermer la boîte de dialogue, puis fermez toutes les instances de Visual Studio pour lancer le **programme d’installation VSIX**.

   La boîte de dialogue du **programme d’installation VSIX** s’ouvre.

   ![Programme d’installation VSIX pour l’analyse du code Microsoft](media/vsix-installer-code-analysis.png)

6. Sélectionnez **modifier** pour démarrer l’installation.

7. Après une minute ou deux, l’installation est terminée. Sélectionnez **Fermer**.

8. Rouvrez Visual Studio.

::: moniker range="vs-2017"

Si vous souhaitez vérifier si l’extension est installée, sélectionnez **outils** > **extensions et mises à jour**. Dans la boîte de dialogue **extensions et mises à jour** , sélectionnez la catégorie **installé** sur la gauche, puis recherchez l’extension par nom.

::: moniker-end

::: moniker range=">=vs-2019"

Si vous souhaitez vérifier si l’extension est installée, sélectionnez **extensions** > **gérer les extensions**. Dans la boîte de dialogue **gérer les extensions** , sélectionnez la catégorie **installé** sur la gauche, puis recherchez l’extension par nom.

::: moniker-end

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Utiliser des analyseurs de code dans Visual Studio](../code-quality/use-roslyn-analyzers.md)

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des analyseurs de code dans Visual Studio](../code-quality/roslyn-analyzers-overview.md)
- [Installer des analyseurs FxCop](../code-quality/install-fxcop-analyzers.md)
