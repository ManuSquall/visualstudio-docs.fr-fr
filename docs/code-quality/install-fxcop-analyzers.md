---
title: Installer des analyseurs FxCop
ms.date: 08/03/2018
ms.topic: conceptual
helpviewer_keywords:
- fxcop analyzers
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 0e3719201c561e013d33549584d00b397c89a832
ms.sourcegitcommit: f17e3afa5c324595afccf15a8a69df8c33b873d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2019
ms.locfileid: "58658851"
---
# <a name="install-fxcop-analyzers-in-visual-studio"></a>Installer les analyseurs FxCop dans Visual Studio

Microsoft a créé un ensemble d’analyseurs, appelé [Microsoft.CodeAnalysis.FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers), qui contient les règles de « FxCop » plus importantes à partir de l’analyse statique du code, converti en analyseurs de Roslyn. Ces analyseurs Vérifiez votre code de sécurité, les performances et les problèmes de conception, entre autres.

Vous pouvez installer ces analyseurs FxCop sous la forme d’un package NuGet ou une extension VSIX à Visual Studio. Pour en savoir plus sur les avantages et inconvénients de chacun d’eux, consultez [NuGet package vs. Extension VSIX](roslyn-analyzers-overview.md#nuget-package-versus-vsix-extension).

## <a name="to-install-fxcop-analyzers-as-a-nuget-package"></a>Pour installer les analyseurs FxCop comme package NuGet

1. [Déterminer la version du package analyseur](#fxcopanalyzers-package-versions) à installer, selon votre version de Visual Studio.

2. Installez le package dans Visual Studio, à l’aide la [Console du Gestionnaire de Package](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console) ou [Package Manager UI](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console).

   > [!NOTE]
   > La page de nuget.org pour chaque package de l’analyseur vous montre la commande Coller dans le **Console du Gestionnaire de Package**. Il existe même un bouton pratique pour copier le texte dans le Presse-papiers.
   >
   > ![Page NuGet.org affichant la commande de Console du Gestionnaire de Package](media/nuget-package-manager-command.png)

   Les assemblys de l’analyseur sont installés et qu’ils apparaissent dans **l’Explorateur de solutions** sous **références** > **analyseurs**.

   ![Nœud d’analyseurs dans l’Explorateur de solutions](media/solution-explorer-analyzers-node.png)

### <a name="fxcopanalyzers-package-versions"></a>Versions de package FxCopAnalyzers

Utilisez les instructions suivantes pour déterminer la version du package analyseurs FxCop à installer pour votre version de Visual Studio :

| Version de Visual Studio | Version du package analyseur FxCop |
| - | - |
| Visual Studio 2017 15,8 et versions ultérieures | [2.9.1](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.9.1) |
| Visual Studio 2017 version 15.5 pour 15.7 | [2.6.3](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.6.3) |
| Visual Studio 2017 version 15.3 à 15.4 | [2.3.0-beta1](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.3.0-beta1) |
| Visual Studio 2017 version 15.0 pour 15.2 | [2.0.0-beta2](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.0.0-beta2) |
| Visual Studio 2015 update 2 et 3 | [1.2.0-beta2](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.2.0-beta2) |
| Visual Studio 2015 Update 1 | [1.1.0](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.1.0) |
| Visual Studio 2015 RTW | [1.0.1](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.0.1) |

## <a name="to-install-fxcop-analyzers-as-a-vsix"></a>Pour installer les analyseurs FxCop en tant qu’une extension VSIX

Dans Visual Studio 2017 version 15.5 et versions ultérieure, vous pouvez installer le [Microsoft Code Analysis 2017](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2017) extension qui contient tous les analyseurs FxCop pour les projets managés.

::: moniker range="vs-2017"

1. Dans Visual Studio, sélectionnez **outils** > **Extensions et mises à jour**.

   La boîte de dialogue **Extensions et mises à jour** s’ouvre.

   > [!NOTE]
   > Vous pouvez également télécharger l’extension directement à partir de [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2017).

::: moniker-end

::: moniker range=">=vs-2019"

1. Dans Visual Studio, sélectionnez **Extensions** > **gérer les Extensions**.

   Le **gérer les Extensions** boîte de dialogue s’ouvre.

   > [!NOTE]
   > Vous pouvez également télécharger l’extension directement à partir de [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2017).

::: moniker-end

1. Développez **Online** dans le volet gauche, puis sélectionnez **Visual Studio Marketplace**.

1. Dans la zone de recherche, tapez « analyse du code », puis recherchez le **Microsoft Code Analysis 2017** extension.

   ![Extension d’analyse du Code Microsoft](media/extensions-and-updates-code-analysis.png)

1. Sélectionnez **télécharger**.

   L’extension est téléchargée.

1. Sélectionnez **OK** pour fermer la boîte de dialogue, puis fermez toutes les instances de Visual Studio pour lancer le **programme d’installation VSIX**.

   Le **programme d’installation VSIX** boîte de dialogue s’ouvre.

   ![Programme d’installation VSIX pour l’analyse de Code Microsoft](media/vsix-installer-code-analysis.png)

1. Sélectionnez **modifier** pour démarrer l’installation.

1. Après une minute ou deux, l’installation est terminée. Sélectionnez **Fermer**.

1. Ouvrez à nouveau Visual Studio.

::: moniker range="vs-2017"

Si vous souhaitez vérifier si l’extension est installée, sélectionnez **outils** > **Extensions et mises à jour**. Dans le **Extensions et mises à jour** boîte de dialogue, sélectionnez le **installé** catégorie sur la gauche, puis recherchez l’extension par nom.

::: moniker-end

::: moniker range=">=vs-2019"

Si vous souhaitez vérifier si l’extension est installée, sélectionnez **Extensions** > **gérer les Extensions**. Dans le **gérer les Extensions** boîte de dialogue, sélectionnez le **installé** catégorie sur la gauche, puis recherchez l’extension par nom.

::: moniker-end

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des analyseurs de Roslyn dans Visual Studio](../code-quality/roslyn-analyzers-overview.md)
- [Utiliser des analyseurs Roslyn dans Visual Studio](../code-quality/use-roslyn-analyzers.md)
- [Migrer à partir de FxCop pour les analyseurs Roslyn](../code-quality/fxcop-analyzers.yml)
