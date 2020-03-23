---
title: EditorConfig contre analyseurs
ms.date: 03/11/2019
ms.topic: conceptual
helpviewer_keywords:
- analyzers, faq
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 680d52ff04553d399b6abeb53919d8aafd4fa792
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301691"
---
# <a name="code-analysis-faq"></a>Analyse de code FAQ

Cette page contient des réponses à certaines questions fréquemment posées sur l’analyse de code basée sur la plate-forme .NET dans Visual Studio.

## <a name="code-analysis-versus-editorconfig"></a>Analyse du code par rapport à EditorConfig

**Q**: Dois-je utiliser l’analyse de code ou EditorConfig pour vérifier le style de code ?

**R**: Analyse de code et fichiers EditorConfig fonctionnent main dans la main. Lorsque vous définissez les styles de code [dans un fichier EditorConfig](../ide/editorconfig-code-style-settings-reference.md) ou sur la page Options de l’éditeur [de texte,](../ide/code-styles-and-code-cleanup.md) vous configurez en fait les analyseurs de code intégrés dans Visual Studio. EditorConfig fichiers peuvent être utilisés pour activer ou désactiver les règles d’analyseur, et aussi pour configurer certains paquets d’analyseur NuGet, tels que [les analyseurs FxCop](configure-fxcop-analyzers.md).

## <a name="editorconfig-versus-rule-sets"></a>EditorConfig contre les ensembles de règles

**Q**: Dois-je configurer mes analyseurs à l’aide d’un ensemble de règles ou d’un fichier EditorConfig ?

**R**: Les ensembles de règles et les fichiers EditorConfig peuvent coexister et peuvent tous deux être utilisés pour configurer des analyseurs. Les fichiers EditorConfig et les ensembles de règles vous permettent d’activer et de désactiver les règles et de définir leur sévérité.

Toutefois, les fichiers EditorConfig offrent également des moyens supplémentaires de configurer les règles :

- Pour les analyseurs FxCop, les fichiers EditorConfig vous permettent [de définir quels types de code analyser](fxcop-analyzer-options.md).
- Pour les analyseurs de code intégrés dans Visual Studio, les fichiers EditorConfig vous permettent de [définir les styles de code préférés](../ide/editorconfig-code-style-settings-reference.md) pour une base de code.

En plus des ensembles de règles et des fichiers EditorConfig, certains analyseurs sont configurés grâce à l’utilisation de fichiers texte [marqués](../ide/build-actions.md#build-action-values) comme fichiers supplémentaires pour les compilateurs C et VB.

> [!NOTE]
> - EditorConfig fichiers ne peuvent être utilisés que pour activer les règles et définir leur gravité dans Visual Studio 2019 version 16.3 et plus tard.
> - EditorConfig fichiers ne peuvent pas être utilisés pour configurer l’analyse de l’héritage, tandis que les ensembles de règles peuvent.

## <a name="code-analysis-in-ci-builds"></a>L’analyse de code dans CI construit

**Q**: Est-ce que l’analyse de code basée sur la plate-forme .NET Compiler fonctionne dans l’intégration continue (CI) ?

**R**: Oui. Pour les analyseurs qui sont installés à partir d’un paquet NuGet, ces règles sont [appliquées au moment de la construction,](roslyn-analyzers-overview.md#build-errors)y compris lors d’une build CI. Les analyseurs utilisés dans CI construisent la configuration des règles de respect à partir des ensembles de règles et des fichiers EditorConfig. Actuellement, les analyseurs de code qui sont intégrés dans Visual Studio ne sont pas disponibles sous forme de paquet NuGet, et donc ces règles ne sont pas exécutoires dans une build CI.

## <a name="ide-analyzers-versus-stylecop"></a>Analyseurs IDE contre StyleCop

**Q**: Quelle est la différence entre les analyseurs de code IDE Visual Studio et les analyseurs StyleCop ?

**R**: L’IDE Visual Studio comprend des analyseurs intégrés qui recherchent à la fois le style de code et les problèmes de qualité. Ces règles vous aident à utiliser de nouvelles fonctionnalités linguistiques au fur et à mesure qu’elles sont introduites et à améliorer la maintenance de votre code. Les analyseurs IDE sont continuellement mis à jour avec chaque version Visual Studio.

[Les analyseurs StyleCop](https://github.com/DotNetAnalyzers/StyleCopAnalyzers) sont des analyseurs tiers installés sous forme de paquet NuGet qui vérifient la cohérence du style dans votre code. En général, les règles StyleCop vous permettent de définir des préférences personnelles pour une base de code sans recommander un style plutôt qu’un autre.

## <a name="code-analyzers-versus-legacy-analysis"></a>Analyseurs de code par rapport à l’analyse héritée

**Q**: Quelle est la différence entre l’analyse héritée et l’analyse de code basée sur la plate-forme .NET Compiler ?

**A**: .NET Compiler Platform-based code analysiss source code in real time and during compilation, whereas legacy analysis analyzes binary files after build has completed. Pour plus d’informations, voir [.NET Compiler Analyse basée sur la plate-forme par rapport à l’analyse de l’héritage](roslyn-analyzers-overview.md#source-code-analysis-versus-legacy-analysis) et [analyseurs FxCop FAQ](fxcop-analyzers-faq.md).

## <a name="treat-warnings-as-errors"></a>Considérer les avertissements comme des erreurs

**Q**: Mon projet utilise l’option de construction pour traiter les avertissements comme des erreurs. Après avoir migré de l’analyse héritée à l’analyse de code source, tous les avertissements d’analyse de code apparaissent maintenant comme des erreurs. Comment puis-je empêcher cela?

**R**: Pour éviter que les avertissements d’analyse de code ne soient traités comme des erreurs, suivez ces étapes :

  1. Créez un fichier .props avec le contenu suivant :

     ```xml
     <Project>
        <PropertyGroup>
           <CodeAnalysisTreatWarningsAsErrors>false</CodeAnalysisTreatWarningsAsErrors>
        </PropertyGroup>
     </Project>
     ```

  2. Ajoutez une ligne à votre fichier de projet .csproj ou .vbproj pour importer le fichier .props que vous avez créé dans l’étape précédente. Cette ligne doit être placée avant toutes les lignes qui importent les fichiers .props de l’analyseur FxCop. Par exemple, si votre fichier .props est nommé codeanalysis.props:

     ```xml
     ...
     <Import Project="..\..\codeanalysis.props" Condition="Exists('..\..\codeanalysis.props')" />
     <Import Project="..\packages\Microsoft.CodeAnalysis.FxCopAnalyzers.2.6.5\build\Microsoft.CodeAnalysis.FxCopAnalyzers.props" Condition="Exists('..\packages\Microsoft.CodeAnalysis.FxCopAnalyzers.2.6.5\build\Microsoft.CodeAnalysis.FxCopAnalyzers.props')" />
     ...
     ```

## <a name="see-also"></a>Voir aussi

- [Aperçu des analyseurs](roslyn-analyzers-overview.md)
- [Paramètres de convention de codage .NET pour EditorConfig](../ide/editorconfig-code-style-settings-reference.md)
