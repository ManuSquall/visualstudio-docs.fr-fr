---
title: Désactiver l’analyse de code
ms.date: 10/03/2019
ms.topic: conceptual
helpviewer_keywords:
- code analysis, disable
- disable code analysis
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8db6ad7bed4b1526d87112f33d3586728728d7f5
ms.sourcegitcommit: 92361aac3665a934faa081e1d1ea89a067b01c5b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79431395"
---
# <a name="how-to-disable-source-code-analysis-for-managed-code"></a>Comment désactiver l’analyse du code source pour le code géré

::: moniker range=">=vs-2019"

Cette page vous aide à désactiver l’analyse de code dans Visual Studio. Il y a des limites à ce que vous pouvez désactiver, et la procédure pour désactiver l’analyse de code diffère selon quelques facteurs :

- Type de projet (.NET Core/Standard versus .NET Framework)

  .NET Core et .NET Standard projets ont des options sur leur page de propriétés d’analyse de code qui vous permettent d’éteindre l’analyse de code à partir d’analyseurs installés comme un paquet NuGet. Pour plus d’informations, voir [.NET Core et .NET Standard projects](#net-core-and-net-standard-projects). Pour désactiver l’analyse du code source pour les projets cadre .NET, voir [.NET Framework projects](#net-framework-projects).

- Analyse des sources par rapport à l’analyse héritée

  Ce sujet s’applique à l’analyse du code source et non à l’analyse héritée (binaire). Pour plus d’informations sur la désactivation de l’analyse de l’héritage, voir [Comment : Activer et désactiver l’analyse du code hérité.](how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)

## <a name="net-core-and-net-standard-projects"></a>.NET Core et .NET Standard projects

À partir de Visual Studio 2019 version 16.3, il ya deux case box disponibles dans la page des propriétés d’analyse de code qui vous permettent de contrôler si les analyseurs fonctionnent au moment de la construction et le temps de conception. Ces options sont spécifiques au projet.

![Activez ou désactivez l’analyse de code en direct ou sur la construction dans Visual Studio](media/run-on-build-run-live-analysis.png)

Pour ouvrir cette page, cliquez à droite sur le nœud de projet dans **Solution Explorer** et sélectionnez **Propriétés**. Sélectionnez l’onglet **Analyse du Code.**

- Pour désactiver l’analyse de source au moment de la construction, décochez l’option **Run on build.**
- Pour désactiver l’analyse de source en direct, décochez la **course sur l’option d’analyse en direct.**

> [!NOTE]
> À partir de Visual Studio 2019 version 16.5, si vous préférez le flux d’exécution d’exécution d’analyse de code à la demande, vous pouvez désactiver l’exécution de l’analyseur pendant l’analyse en direct et/ou construire et déclencher manuellement l’analyse de code une fois sur un projet ou une solution à la demande. Pour plus d’informations sur l’exécution manuelle de l’analyse de code, voir [Comment : Exécuter l’analyse du code manuellement pour le code géré](how-to-run-code-analysis-manually-for-managed-code.md).  

## <a name="net-framework-projects"></a>.NET Projets-cadres

Pour désactiver l’analyse du code source pour les analyseurs, ajoutez une ou plusieurs des propriétés MSBuild suivantes au fichier du [projet.](../ide/solutions-and-projects-in-visual-studio.md#project-file)

| Propriété MSBuild | Description | Default |
| - | - | - |
| `RunAnalyzersDuringBuild` | Contrôle si les analyseurs fonctionnent au moment de la construction. | `true` |
| `RunAnalyzersDuringLiveAnalysis` | Contrôle si les analyseurs analysent le code en direct au moment de la conception. | `true` |
| `RunAnalyzers` | Désactivez les analyseurs à la fois au moment de la construction et de la conception. Cette propriété a `RunAnalyzersDuringBuild` préséance sur et `RunAnalyzersDuringLiveAnalysis`. | `true` |

Exemples :

```xml
<RunAnalyzersDuringBuild>false</RunAnalyzersDuringBuild>
<RunAnalyzersDuringLiveAnalysis>false</RunAnalyzersDuringLiveAnalysis>
<RunAnalyzers>false</RunAnalyzers>
```

::: moniker-end

::: moniker range="vs-2017"

## <a name="source-analysis"></a>Analyse du code source

Vous ne pouvez pas désactiver [l’analyse source](roslyn-analyzers-overview.md) dans Visual Studio 2017. Si vous souhaitez effacer les erreurs d’analyseur de la liste d’erreurs, vous pouvez supprimer toutes les violations actuelles en choisissant **Analyse** > **de code d’exécution et supprimer les problèmes actifs** sur la barre du menu. Pour plus d’informations, voir [Suppress violations](use-roslyn-analyzers.md#suppress-violations).

En commençant par Visual Studio 2019 version 16.3, vous pouvez désactiver l’analyse de code source ou l’exécuter à la demande. Envisagez de passer à Visual Studio 2019.

## <a name="legacy-analysis"></a>Analyse héritée

Vous pouvez désactiver l’analyse héritée et le temps de construction sur la page des propriétés **d’analyse de code.** Pour plus d’informations, voir [Comment : Activer et désactiver l’analyse de code héritée](how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).

::: moniker-end

## <a name="see-also"></a>Voir aussi

- [Supprimer les violations](use-roslyn-analyzers.md#suppress-violations)
- [Comment : Activer et désactiver l’analyse de code héritée](how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)
