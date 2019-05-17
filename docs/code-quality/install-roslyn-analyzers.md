---
title: Installer des analyseurs Roslyn
ms.date: 08/03/2018
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 1afeb6f75648ce2ab1687fa9262ab28b658b0d70
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62820818"
---
# <a name="install-net-compiler-platform-analyzers"></a>Installer les analyseurs .NET Compiler Platform

Visual Studio inclut un ensemble principal de .NET Compiler Platform (*Roslyn*) analyseurs. Ces analyseurs sont toujours activées. Vous pouvez installer des analyseurs supplémentaires comme packages NuGet, soit en tant qu’extensions Visual Studio dans *VSIX* fichiers.

## <a name="to-install-nuget-analyzer-packages"></a>Pour installer les packages NuGet analyzer

1. Recherchez le package à installer sur www.nuget.org de l’analyseur.

   Par exemple, vous souhaiterez [installer les analyseurs Microsoft FxCop](install-fxcop-analyzers.md#to-install-fxcop-analyzers-as-a-nuget-package) pour vérifier votre code pour les problèmes de sécurité et de performances, entre autres. Ou bien, installez [StyleCopAnalyzers](https://www.nuget.org/packages/stylecop.analyzers/) pour rechercher des problèmes de style dans votre code base.

2. Installez le package dans Visual Studio, à l’aide la [Console du Gestionnaire de Package](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console) ou [Package Manager UI](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console).

   > [!NOTE]
   > La page www.nuget.org pour chaque package de l’analyseur vous montre la commande Coller dans le **Console du Gestionnaire de Package**. Il existe même un bouton pratique pour copier le texte dans le Presse-papiers.

   Les assemblys de l’analyseur sont installés et s’affichent dans **l’Explorateur de solutions** sous **références** > **analyseurs**.

## <a name="to-install-vsix-analyzers"></a>Pour installer les analyseurs VSIX

::: moniker range="vs-2017"

1. Dans Visual Studio, sélectionnez **outils** > **Extensions et mises à jour**.

   La boîte de dialogue **Extensions et mises à jour** s’ouvre.

   > [!NOTE]
   > Ou bien, vous pouvez rechercher et télécharger l’extension analyseur directement à partir de [Visual Studio Marketplace](https://marketplace.visualstudio.com).

::: moniker-end

::: moniker range=">=vs-2019"

1. Dans Visual Studio, sélectionnez **Extensions** > **gérer les Extensions**.

   Le **gérer les Extensions** boîte de dialogue s’ouvre.

   > [!NOTE]
   > Ou bien, vous pouvez rechercher et télécharger l’extension analyseur directement à partir de [Visual Studio Marketplace](https://marketplace.visualstudio.com).

::: moniker-end

2. Développez **Online** dans le volet gauche, puis sélectionnez **Visual Studio Marketplace**.

3. Dans la zone de recherche, tapez le nom de l’extension analyseur que vous souhaitez installer. Par exemple, vous souhaiterez [installer les analyseurs Microsoft FxCop](install-fxcop-analyzers.md#to-install-fxcop-analyzers-as-a-vsix) pour vérifier votre code pour les problèmes de sécurité et de performances, entre autres.

4. Sélectionnez **télécharger**.

   L’extension est téléchargée.

5. Sélectionnez **OK** pour fermer la boîte de dialogue, puis fermez toutes les instances de Visual Studio pour lancer le **programme d’installation VSIX**.

   Le **programme d’installation VSIX** boîte de dialogue s’ouvre.

   ![Programme d’installation VSIX pour l’analyse de Code Microsoft](media/vsix-installer-code-analysis.png)

6. Sélectionnez **modifier** pour démarrer l’installation.

7. Après une minute ou deux, l’installation est terminée. Sélectionnez **Fermer**.

8. Ouvrez à nouveau Visual Studio.

::: moniker range="vs-2017"

Si vous souhaitez vérifier si l’extension est installée, sélectionnez **outils** > **Extensions et mises à jour**. Dans le **Extensions et mises à jour** boîte de dialogue, sélectionnez le **installé** catégorie sur la gauche, puis recherchez l’extension par nom.

::: moniker-end

::: moniker range=">=vs-2019"

Si vous souhaitez vérifier si l’extension est installée, sélectionnez **Extensions** > **gérer les Extensions**. Dans le **gérer les Extensions** boîte de dialogue, sélectionnez le **installé** catégorie sur la gauche, puis recherchez l’extension par nom.

::: moniker-end

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Utiliser des analyseurs Roslyn dans Visual Studio](../code-quality/use-roslyn-analyzers.md)

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des analyseurs de Roslyn dans Visual Studio](../code-quality/roslyn-analyzers-overview.md)
- [Installer des analyseurs FxCop](../code-quality/install-fxcop-analyzers.md)