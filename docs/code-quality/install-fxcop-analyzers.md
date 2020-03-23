---
title: Installer des analyseurs FxCop
ms.date: 08/03/2018
ms.topic: conceptual
helpviewer_keywords:
- fxcop analyzers
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 1d734ea4d87dc5d1b8f2ca7f1a1891a4cf7d512b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79508769"
---
# <a name="install-fxcop-analyzers-in-visual-studio"></a>Installer des analyseurs FxCop dans Visual Studio

Microsoft a créé un ensemble d’analyseurs, appelé [Microsoft.CodeAnalysis.FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers), qui contient les règles les plus importantes "FxCop" de l’analyse héritée. Ces analyseurs vérifient votre code pour les problèmes de sécurité, de performance et de conception, entre autres.

Vous pouvez installer ces analyseurs FxCop soit sous forme de paquet NuGet, soit comme extension VSIX à Visual Studio. Pour en savoir plus sur les avantages et les inconvénients de chacun, voir [le forfait NuGet vs extension VSIX](roslyn-analyzers-overview.md#nuget-package-versus-vsix-extension).

## <a name="nuget-package"></a>Package NuGet

::: moniker range=">=vs-2019"

Dans Visual Studio 2019 version 16.3 et plus tard, vous pouvez installer le paquet [Microsoft.CodeAnalysis.FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) NuGet directement à partir de la page des propriétés d’analyse de code du projet :

1. Cliquez à droite sur le nœud de projet dans **Solution Explorer**, sélectionnez **les propriétés,** puis sélectionnez **l’onglet Analyse de code.**

   ![Installer le paquet d’analyseurs FxCop à partir de la page propriétés dans Visual Studio](media/install-fxcop-properties-page.png)

2. Sélectionnez **Installer**.

   Visual Studio installe la dernière version du package Microsoft.CodeAnalysis.FxCopAnalyzers. Les assemblages apparaissent dans **Solution Explorer** sous **References** > **Analyzers**.

   ![Analyseurs noeud dans Solution Explorer](media/solution-explorer-analyzers-node.png)

Si vous utilisez une ancienne version de Visual Studio 2019, installez le paquet en utilisant soit la [console Package Manager](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console) ou [l’interface utilisateur Package Manager](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console).

::: moniker-end

::: moniker range="vs-2017"

1. [Déterminez la version d’analyseur](#fxcopanalyzers-package-versions) à installer, en fonction de votre version de Visual Studio.

2. Installez le paquet dans Visual Studio en utilisant soit la [console Package Manager](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console) ou l’interface utilisateur Package [Manager](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console).

   > [!NOTE]
   > La page nuget.org pour chaque paquet d’analyseur vous montre la commande de coller dans la **console De gestionnaire de paquets**. Il y a même un bouton pratique pour copier le texte sur le presse-papiers.
   >
   > ![NuGet.org page montrant la commande de la console de gestionnaire de paquet](media/nuget-package-manager-command.png)

   Les assemblages d’analyseurs sont installés, et ils apparaissent dans **Solution Explorer** sous **References** > **Analyzers**.

::: moniker-end

### <a name="custom-installation"></a>Installation personnalisée

Pour l’installation personnalisée, par exemple pour spécifier une version différente du paquet, sélectionnez le bouton ellipsis (...) sur la page des propriétés d’analyse de code du projet. Ce bouton ouvre le gestionnaire de paquets NuGet avec "Microsoft.CodeAnalysis.FxCopAnalyzers" comme chaîne de recherche.

![Installer le paquet d’analyseurs FxCop personnalisés à partir de la page propriétés dans Visual Studio](media/install-fxcop-properties-page-ellipsis.png)

> [!TIP]
> Déterminez [la version d’analyseur](#fxcopanalyzers-package-versions) à installer, en fonction de votre version de Visual Studio. Vous pouvez également installer le paquet à partir de [l’interface utilisateur Package Manager](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console).

### <a name="fxcopanalyzers-package-versions"></a>Versions de paquets FxCopAnalyzers

Utilisez les lignes directrices suivantes pour déterminer quelle version du paquet d’analyseurs FxCop à installer pour votre version de Visual Studio :

| Version de Visual Studio | Version du paquet d’analyseur FxCop |
| - | - |
| Visual Studio 2019 (toutes versions)<br />Visual Studio 2017 version 15.8 et plus tard | [Dernière](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/) |
| Visual Studio 2017 version 15.5 à 15.7 | [2.6.3](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.6.3) |
| Visual Studio 2017 version 15.3 à 15.4 | [2.3.0-beta1](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.3.0-beta1) |
| Visual Studio 2017 version 15.0 à 15.2 | [2.0.0-beta2](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.0.0-beta2) |
| Visual Studio 2015 mise à jour 2 et 3 | [1.2.0-beta2](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.2.0-beta2) |
| Visual Studio 2015 Update 1 | [1.1.0](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.1.0) |
| Visual Studio 2015 RTW | [1.0.1](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.0.1) |

## <a name="vsix"></a>VSIX

::: moniker range="vs-2017"

Sur Visual Studio 2017 version 15.5 et plus tard, vous pouvez installer [l’extension Microsoft Code Analysis 2017](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2017) qui contient tous les analyseurs FxCop pour des projets gérés.

1. Dans Visual Studio, sélectionnez Des > **extensions d’outils et des mises à jour**. **Tools**

   La boîte de dialogue **Extensions et mises à jour** s’ouvre.

   > [!NOTE]
   > Alternativement, téléchargez l’extension directement à partir de [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2017).

2. Élargissez **en ligne** dans la vitre gauche, puis sélectionnez **Visual Studio Marketplace**.

3. Dans la boîte de recherche, tapez « analyse de code » et recherchez l’extension **Microsoft Code Analysis 2017.**

   ![Microsoft Code Analysis 2017 extension](media/extensions-and-updates-code-analysis.png)

::: moniker-end

::: moniker range=">=vs-2019"

[L’extension Microsoft Code Analysis 2019](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2019) contient tous les analyseurs FxCop pour les projets gérés. Pour installer cette extension :

1. Dans Visual Studio, sélectionnez **Extensions** > **Manage Extensions**.

   La boîte de dialogue **Manage Extensions** s’ouvre.

   > [!NOTE]
   > Alternativement, téléchargez l’extension directement à partir de [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2019).

2. Élargissez **en ligne** dans la vitre gauche, puis sélectionnez **Visual Studio Marketplace**.

3. Dans la boîte de recherche, tapez « analyse de code » et recherchez l’extension **Microsoft Code Analysis 2019.**

   ![Microsoft Code Analysis 2019 extension](media/manage-extensions-code-analysis.png)

::: moniker-end

4. Sélectionnez **Télécharger**.

   L’extension est téléchargée.

5. Sélectionnez **OK** pour fermer la boîte de dialogue, puis fermer toutes les instances de Visual Studio pour lancer **l’installateur VSIX**.

   La boîte de dialogue **VSIX Installer** s’ouvre.

   ::: moniker range="vs-2017"

   ![INSTALLateur VSIX pour Microsoft Code Analysis](media/vsix-installer-code-analysis.png)

   ::: moniker-end

6. Sélectionnez **Modifier** pour démarrer l’installation.

   Après une minute ou deux, l’installation se termine.

7. Sélectionnez **Close**, puis ouvrez Visual Studio à nouveau.

::: moniker range="vs-2017"

Si vous souhaitez vérifier si l’extension est installée, sélectionnez des > **extensions d’outils et des mises à jour**. **Tools** Dans la boîte de dialogue **Extensions et Mises à jour,** sélectionnez la catégorie **Installée** sur la gauche, puis recherchez l’extension par son nom.

::: moniker-end

::: moniker range=">=vs-2019"

Si vous souhaitez vérifier si l’extension est installée, sélectionnez **Extensions** > **Manage Extensions**. Dans la boîte de dialogue **Manage Extensions,** sélectionnez la catégorie **Installée** sur la gauche, puis recherchez l’extension par son nom.

::: moniker-end

## <a name="see-also"></a>Voir aussi

- [Aperçu des analyseurs de code dans Visual Studio](../code-quality/roslyn-analyzers-overview.md)
- [Utiliser des analyseurs de code dans Visual Studio](../code-quality/use-roslyn-analyzers.md)
- [Migrer de l’analyse héritée aux analyseurs de code](../code-quality/migrate-from-legacy-analysis-to-fxcop-analyzers.md)
