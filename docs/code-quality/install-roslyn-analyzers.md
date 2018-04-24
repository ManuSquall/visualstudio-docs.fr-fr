---
title: Installer des analyseurs de Roslyn dans Visual Studio
ms.date: 03/26/2018
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 8a3b40b3b471e6bb57da561ac51f23086a0f01bd
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2018
---
# <a name="install-net-compiler-platform-analyzers"></a>Installer des analyseurs de plateforme des compilateurs .NET

Visual Studio 2017 inclut un ensemble de la plateforme des compilateurs .NET (*Roslyn*) des analyseurs. Ces analyseurs sont toujours activées. Vous pouvez installer des analyseurs supplémentaires comme packages NuGet, ou en tant qu’extensions de Visual Studio dans *VSIX* fichiers.

## <a name="to-install-nuget-package-analyzers"></a>Pour installer des analyseurs de package NuGet

1. [Déterminer la version de package analyseur](https://github.com/dotnet/roslyn-analyzers#recommended-version-of-analyzer-packages) à installer, selon votre version de Visual Studio.

1. Installer le package dans Visual Studio, soit à l’aide de la [Package Manager Console](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console) ou [Package Manager UI](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console).

   > [!NOTE]
   > La page nuget.org pour chaque package analyzer vous montre la commande Coller dans le **Package Manager Console**. Il existe même un bouton pratique de copier le texte dans le Presse-papiers.
   >
   > ![Page NuGet.org affichant la commande de Console du Gestionnaire de Package](media/nuget-package-manager-command.png)

   Les assemblys de l’analyseur sont installés et s’affichent dans **l’Explorateur de solutions** sous **références** > **analyseurs**.

   ![Nœud analyseurs dans l’Explorateur de solutions](media/solution-explorer-analyzers-node.png)

## <a name="to-install-vsix-analyzers"></a>Pour installer des analyseurs de VSIX

1. Dans Visual Studio, sélectionnez **outils** > **Extensions et mises à jour**.

   La boîte de dialogue **Extensions et mises à jour** s’ouvre.

   > [!NOTE]
   > Vous pouvez également télécharger l’extension directement à partir de [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2017).

1. Développez **Online** dans le volet gauche, puis sélectionnez **Visual Studio Marketplace**.

1. Dans la zone de recherche, tapez « analyse du code » et recherchez le **Microsoft Code Analysis 2017** extension.

   ![Extension de l’analyse du Code Microsoft](media/extensions-and-updates-code-analysis.png)

1. Sélectionnez **télécharger**.

   L’extension est téléchargée.

1. Sélectionnez **OK** pour fermer la boîte de dialogue, puis fermez toutes les instances de Visual Studio à lancer le **programme d’installation de VSIX**.

   Le **programme d’installation de VSIX** boîte de dialogue s’ouvre.

   ![Programme d’installation VSIX pour l’analyse de Code Microsoft](media/vsix-installer-code-analysis.png)

1. Sélectionnez **modifier** pour démarrer l’installation.

1. Après une ou deux minutes, l’installation est terminée. Sélectionnez **fermer**.

1. Rouvrez Visual Studio.

Si vous souhaitez vérifier si l’extension est installée, sélectionnez **outils** > **Extensions et mises à jour**. Dans le **Extensions et mises à jour** boîte de dialogue, sélectionnez le **installé** catégorie sur la gauche, puis recherchez l’extension de nom.

## <a name="next-steps"></a>Étapes suivantes

- [Utiliser les analyseurs de Roslyn de Visual Studio](../code-quality/use-roslyn-analyzers.md)

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des analyseurs de Roslyn dans Visual Studio](../code-quality/roslyn-analyzers-overview.md)