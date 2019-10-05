---
title: Désactiver l’analyse du code
ms.date: 10/03/2019
ms.topic: conceptual
helpviewer_keywords:
- code analysis, disable
- disable code analysis
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: d769accce87b789b207d9cf337d5b9adc46e413e
ms.sourcegitcommit: dc12a7cb66124596089f01d3e939027ae562ede9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2019
ms.locfileid: "71963325"
---
# <a name="how-to-disable-code-analysis-in-visual-studio"></a>Comment désactiver l’analyse du code dans Visual Studio

::: moniker range=">=vs-2019"

Cette page vous aide à désactiver l’analyse du code dans Visual Studio. Il existe des limitations quant à ce que vous pouvez désactiver, et la procédure de désactivation de l’analyse du code diffère selon plusieurs facteurs :

- Type de projet (.NET Core/standard et .NET Framework)

  Les projets .NET Core et .NET Standard ont des options sur la page des propriétés de l’analyse du code qui vous permettent de désactiver l’analyse du code des analyseurs installés en tant que package NuGet. Pour plus d’informations, consultez [.net Core et les projets .NET standard](#net-core-and-net-standard-projects). Pour désactiver l’analyse du code source pour les projets .NET Framework, consultez [.NET Framework projets](#net-framework-projects).

- Package de l’analyseur NuGet et des analyseurs VSIX ou intégrés

  Actuellement, vous ne pouvez pas désactiver l’analyse du code en temps réel pour les analyseurs intégrés, par exemple, l’ID de règle IDE0067. De même, vous ne pouvez pas désactiver l’analyse du code en temps réel pour les analyseurs qui ont été installés dans le cadre d’une extension Visual Studio (VSIX). Pour supprimer les erreurs et les avertissements des analyseurs intégrés et VSIX, choisissez **analyser** > **générer et supprimer les problèmes actifs** dans la barre de menus. Vous *pouvez* désactiver l’analyse en temps réel et intégrée des analyseurs installés dans le cadre d’un package NuGet.

- Analyse de la source et analyse héritée

  Cette rubrique s’applique à l’analyse du code source et non à l’analyse héritée (binaire). Pour plus d’informations sur la désactivation de l’analyse héritée, voir [How à : Activer et désactiver l’analyse du code hérité @ no__t-0.

## <a name="net-core-and-net-standard-projects"></a>Projets .NET Core et .NET Standard

À compter de Visual Studio 2019 version 16,3, deux cases à cocher sont disponibles dans la page des propriétés de l’analyse du code, qui vous permettent de contrôler si les analyseurs NuGet s’exécutent au moment de la génération et au moment de la conception. Ces options sont spécifiques au projet.

![Activer ou désactiver l’analyse du code en direct ou la génération dans Visual Studio](media/run-on-build-run-live-analysis.png)

Pour ouvrir cette page, cliquez avec le bouton droit sur le nœud du projet dans **Explorateur de solutions** , puis sélectionnez **Propriétés**. Sélectionnez l’onglet **analyse du code** .

- Pour désactiver l’analyse de la source au moment de la génération, décochez l’option **exécuter sur la build** .
- Pour désactiver l’analyse de la source dynamique, décochez l’option **exécuter sur l’analyse en direct** .

> [!NOTE]
> Les analyseurs intégrés et VSIX continuent à fournir une analyse en temps réel de votre code, même si l’option **exécuter sur l’analyse en direct** est désactivée. Si vous souhaitez supprimer les erreurs et les avertissements de ces analyseurs, choisissez **analyser** > **générer et supprimer les problèmes actifs** dans la barre de menus.

## <a name="net-framework-projects"></a>Projets .NET Framework

Pour désactiver l’analyse du code source pour les analyseurs installés dans le cadre d’un package NuGet, ajoutez une ou plusieurs des propriétés MSBuild suivantes au [fichier projet](../ide/solutions-and-projects-in-visual-studio.md#project-file).

| MSBuild, propriété | Description | Par défaut |
| - | - | - |
| `RunAnalyzersDuringBuild` | Contrôle si les analyseurs NuGet s’exécutent au moment de la génération. | `true` |
| `RunAnalyzersDuringLiveAnalysis` | Contrôle si les analyseurs NuGet analysent le code en temps réel au moment du Design. | `true` |
| `RunAnalyzers` | Désactive les analyseurs NuGet à la fois au moment de la génération et de la conception. Cette propriété est prioritaire sur `RunAnalyzersDuringBuild` et `RunAnalyzersDuringLiveAnalysis`. | `true` |

Exemples :

```xml
<RunAnalyzersDuringBuild>false</RunAnalyzersDuringBuild>
<RunAnalyzersDuringLiveAnalysis>false</RunAnalyzersDuringLiveAnalysis>
<RunAnalyzers>false</RunAnalyzers>
```

::: moniker-end

::: moniker range="vs-2017"

## <a name="source-analysis"></a>Analyse du code source

Vous ne pouvez pas désactiver l’analyse de la [source](roslyn-analyzers-overview.md) dans Visual Studio 2017. Si vous souhaitez effacer les erreurs de l’analyseur de la Liste d’erreurs, vous pouvez supprimer toutes les violations en cours en choisissant **analyser** > **exécuter l’analyse du code et supprimer les problèmes actifs** dans la barre de menus. Pour plus d’informations, consultez [Supprimer les violations](use-roslyn-analyzers.md#suppress-violations).

À compter de Visual Studio 2019 version 16,3, vous pouvez désactiver l’analyse du code source NuGet. Envisagez une mise à niveau vers Visual Studio 2019.

## <a name="legacy-analysis"></a>Analyse héritée

Vous pouvez désactiver l’analyse héritée au moment de la génération dans la page des propriétés de l' **analyse du code** . Pour plus d'informations, voir [Procédure : Activer et désactiver l’analyse du code hérité @ no__t-0.

::: moniker-end

## <a name="see-also"></a>Voir aussi

- [Supprimer les violations](use-roslyn-analyzers.md#suppress-violations)
- [Guide pratique pour Activer et désactiver l’analyse du code hérité @ no__t-0
