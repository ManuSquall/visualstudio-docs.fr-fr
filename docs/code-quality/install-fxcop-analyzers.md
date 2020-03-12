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
ms.openlocfilehash: 78935673dbf57f75988d4c0a9e862b11e2fe855f
ms.sourcegitcommit: 514f0f7d1a61d292c7dbc80ec73a36bda960d6ce
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/09/2020
ms.locfileid: "78937530"
---
# <a name="install-fxcop-analyzers-in-visual-studio"></a>Installer les analyseurs FxCop dans Visual Studio

Microsoft a créé un ensemble d’analyseurs, appelé [Microsoft. CodeAnalysis. FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers), qui contient les règles « FxCop » les plus importantes de l’analyse héritée. Ces analyseurs vérifient votre code pour la sécurité, les performances et les problèmes de conception, entre autres.

Vous pouvez installer ces analyseurs FxCop en tant que package NuGet ou extension VSIX dans Visual Studio. Pour en savoir plus sur les avantages et les inconvénients de chacun, consultez [extension de package NuGet et extension VSIX](roslyn-analyzers-overview.md#nuget-package-versus-vsix-extension).

## <a name="nuget-package"></a>Package NuGet

::: moniker range=">=vs-2019"

Dans Visual Studio 2019 version 16,3 et versions ultérieures, vous pouvez installer le package NuGet [Microsoft. CodeAnalysis. FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) directement à partir de la page de propriétés de l’analyse du code du projet :

1. Cliquez avec le bouton droit sur le nœud du projet dans **Explorateur de solutions**, sélectionnez **Propriétés**, puis sélectionnez l’onglet **analyse du code** .

   ![Installer le package des analyseurs FxCop à partir de la page Propriétés dans Visual Studio](media/install-fxcop-properties-page.png)

2. Sélectionnez **Installer**.

   Visual Studio installe la dernière version du package Microsoft. CodeAnalyzers. FxCopAnalyzers. Les assemblys apparaissent dans **Explorateur de solutions** sous **références** > des **analyseurs**.

   ![Nœud analyseurs dans Explorateur de solutions](media/solution-explorer-analyzers-node.png)

Si vous utilisez une version antérieure de Visual Studio 2019, installez le package à l’aide de la [console du gestionnaire de package](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console) ou de l' [interface utilisateur du gestionnaire de package](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console).

::: moniker-end

::: moniker range="vs-2017"

1. [Déterminez la version du package de l’analyseur](#fxcopanalyzers-package-versions) à installer, en fonction de votre version de Visual Studio.

2. Installez le package dans Visual Studio à l’aide de la [console du gestionnaire de package](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console) ou de l' [interface utilisateur du gestionnaire de package](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console).

   > [!NOTE]
   > La page nuget.org pour chaque package de l’analyseur vous indique la commande à coller dans la **console du gestionnaire de package**. Il y a même un bouton pratique pour copier le texte dans le presse-papiers.
   >
   > ![Page NuGet.org qui indique la commande de la console du gestionnaire de package](media/nuget-package-manager-command.png)

   Les assemblys de l’analyseur sont installés et apparaissent dans **Explorateur de solutions** sous **références** > des **analyseurs**.

::: moniker-end

### <a name="custom-installation"></a>Installation personnalisée

Pour une installation personnalisée, par exemple pour spécifier une version différente du package, cliquez sur le bouton de sélection (...) sur la page des propriétés de l’analyse du code du projet. Ce bouton ouvre le gestionnaire de package NuGet avec « Microsoft. CodeAnalysis. FxCopAnalyzers » comme chaîne de recherche.

![Installer le package des analyseurs FxCop personnalisés à partir de la page Propriétés dans Visual Studio](media/install-fxcop-properties-page-ellipsis.png)

> [!TIP]
> Déterminez [la version du package de l’analyseur](#fxcopanalyzers-package-versions) à installer, en fonction de votre version de Visual Studio. Vous pouvez également installer le package à partir de l' [interface utilisateur du gestionnaire de package](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console).

### <a name="fxcopanalyzers-package-versions"></a>Versions du package FxCopAnalyzers

Utilisez les instructions suivantes pour déterminer la version du package des analyseurs FxCop à installer pour votre version de Visual Studio :

| Version de Visual Studio | Version du package de l’analyseur FxCop |
| - | - |
| Visual Studio 2019 (toutes les versions)<br />Visual Studio 2017 version 15,8 et versions ultérieures | [le plus récent](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/) |
| Visual Studio 2017 version 15,5 à 15,7 | [2.6.3](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.6.3) |
| Visual Studio 2017 version 15,3 à 15,4 | [2.3.0-beta1](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.3.0-beta1) |
| Visual Studio 2017 version 15,0 à 15,2 | [2.0.0-bêta2](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.0.0-beta2) |
| Visual Studio 2015 Update 2 et 3 | [1.2.0-bêta2](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.2.0-beta2) |
| Visual Studio 2015 Update 1 | [1.1.0](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.1.0) |
| Visual Studio 2015 RTW | [1.0.1](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.0.1) |

## <a name="vsix"></a>VSIX

::: moniker range="vs-2017"

Dans Visual Studio 2017 version 15,5 et versions ultérieures, vous pouvez installer l’extension [Microsoft Code analysis 2017](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2017) qui contient tous les analyseurs FxCop pour les projets managés.

1. Dans Visual Studio, sélectionnez **outils** > **extensions et mises à jour**.

   La boîte de dialogue **Extensions et mises à jour** s’ouvre.

   > [!NOTE]
   > Vous pouvez également télécharger l’extension directement à partir de [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2017).

2. Développez **en ligne** dans le volet gauche, puis sélectionnez **Visual Studio Marketplace**.

3. Dans la zone de recherche, tapez « analyse du code » et recherchez l’extension **Microsoft Code analysis 2017** .

   ![Extension Microsoft Code Analysis 2017](media/extensions-and-updates-code-analysis.png)

::: moniker-end

::: moniker range=">=vs-2019"

L’extension [Microsoft Code analysis 2019](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2019) contient tous les analyseurs FxCop pour les projets managés. Pour installer cette extension :

1. Dans Visual Studio, sélectionnez **extensions** > **gérer les extensions**.

   La boîte de dialogue **gérer les extensions** s’ouvre.

   > [!NOTE]
   > Vous pouvez également télécharger l’extension directement à partir de [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2019).

2. Développez **en ligne** dans le volet gauche, puis sélectionnez **Visual Studio Marketplace**.

3. Dans la zone de recherche, tapez « analyse du code » et recherchez l’extension **Microsoft Code analysis 2019** .

   ![Extension Microsoft Code Analysis 2019](media/manage-extensions-code-analysis.png)

::: moniker-end

4. Sélectionnez **Télécharger**.

   L’extension est téléchargée.

5. Sélectionnez **OK** pour fermer la boîte de dialogue, puis fermez toutes les instances de Visual Studio pour lancer le **programme d’installation VSIX**.

   La boîte de dialogue du **programme d’installation VSIX** s’ouvre.

   ::: moniker range="vs-2017"

   ![Programme d’installation VSIX pour l’analyse du code Microsoft](media/vsix-installer-code-analysis.png)

   ::: moniker-end

6. Sélectionnez **modifier** pour démarrer l’installation.

   Après une minute ou deux, l’installation est terminée.

7. Sélectionnez **Fermer**, puis rouvrez Visual Studio.

::: moniker range="vs-2017"

Si vous souhaitez vérifier si l’extension est installée, sélectionnez **outils** > **extensions et mises à jour**. Dans la boîte de dialogue **extensions et mises à jour** , sélectionnez la catégorie **installé** sur la gauche, puis recherchez l’extension par nom.

::: moniker-end

::: moniker range=">=vs-2019"

Si vous souhaitez vérifier si l’extension est installée, sélectionnez **extensions** > **gérer les extensions**. Dans la boîte de dialogue **gérer les extensions** , sélectionnez la catégorie **installé** sur la gauche, puis recherchez l’extension par nom.

::: moniker-end

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des analyseurs de code dans Visual Studio](../code-quality/roslyn-analyzers-overview.md)
- [Utiliser des analyseurs de code dans Visual Studio](../code-quality/use-roslyn-analyzers.md)
- [Migrer de l’analyse héritée vers les analyseurs de code](../code-quality/migrate-from-legacy-analysis-to-fxcop-analyzers.md)
