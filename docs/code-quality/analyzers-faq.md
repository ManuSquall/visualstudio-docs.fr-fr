---
title: EditorConfig et analyseurs
ms.date: 03/11/2019
description: En savoir plus sur l’analyse du code basé sur .NET Compiler Platform dans Visual Studio. Consultez les réponses aux questions sur les fichiers EditorConfig, les ensembles de règles et d’autres rubriques.
ms.custom: SEO-VS-2020
ms.topic: conceptual
helpviewer_keywords:
- analyzers, faq
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6d67471027f36d0e22c055f4306ce2137d972463
ms.sourcegitcommit: dd2fc6e03a789c044f8438096b8f112e4dba5557
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2021
ms.locfileid: "108800509"
---
# <a name="code-analysis-faq"></a>FAQ sur l’analyse du code

Cette page contient des réponses à certaines questions fréquemment posées sur l’analyse du code basé sur .NET Compiler Platform dans Visual Studio.

## <a name="code-analysis-versus-editorconfig"></a>Analyse du code et EditorConfig

**Q**: dois-je utiliser l’analyse du code ou EditorConfig pour vérifier le style du code ?

**R**: l’analyse du code et les fichiers EditorConfig fonctionnent à la main. Quand vous définissez des styles [de code dans un fichier EditorConfig](/dotnet/fundamentals/code-analysis/code-style-rule-options) ou dans la page d’options de l' [éditeur de texte](../ide/code-styles-and-code-cleanup.md) , vous configurez en fait les analyseurs de code intégrés à Visual Studio. Les fichiers EditorConfig peuvent être utilisés pour activer ou désactiver les règles de l’analyseur, ainsi que pour configurer les packages de l’analyseur NuGet.

## <a name="editorconfig-versus-rule-sets"></a>EditorConfig et ensembles de règles

**Q**: dois-je configurer mes analyseurs à l’aide d’un ensemble de règles ou d’un fichier EditorConfig ?

**R**: les ensembles de règles et les fichiers EditorConfig peuvent coexister et peuvent tous deux être utilisés pour configurer des analyseurs. Les fichiers EditorConfig et les ensembles de règles vous permettent d’activer et de désactiver des règles et de définir leur gravité.

Toutefois, les fichiers EditorConfig offrent d’autres moyens de configurer les règles :

- Pour les analyseurs de qualité du code .NET, les fichiers EditorConfig vous permettent de [définir les types de code à analyser](/dotnet/fundamentals/code-analysis/code-quality-rule-options).
- Pour les analyseurs de style de code .NET intégrés à Visual Studio, les fichiers EditorConfig vous permettent de [définir les styles de code préférés](/dotnet/fundamentals/code-analysis/code-style-rule-options) pour un code base.

Outre les ensembles de règles et les fichiers EditorConfig, certains analyseurs sont configurés à l’aide de fichiers texte marqués comme [fichiers supplémentaires](../ide/build-actions.md#build-action-values) pour les compilateurs C# et VB.

> [!NOTE]
> - Les fichiers EditorConfig peuvent uniquement être utilisés pour activer des règles et définir leur gravité dans Visual Studio 2019 version 16,3 et versions ultérieures.
> - Les fichiers EditorConfig ne peuvent pas être utilisés pour configurer l’analyse héritée, contrairement aux ensembles de règles.

## <a name="code-analysis-in-ci-builds"></a>Analyse du code dans les builds d’intégration continue

**Q**: l’analyse du code basé sur .NET Compiler Platform fonctionne-t-elle dans les builds d’intégration continue ?

**R** : Oui. Pour les analyseurs installés à partir d’un package NuGet, ces règles sont [appliquées au moment](roslyn-analyzers-overview.md#build-errors)de la génération, y compris pendant une build ci. Les analyseurs utilisés dans les builds d’intégration continue respectent la configuration des règles des ensembles de règles et des fichiers EditorConfig. Actuellement, les analyseurs de code intégrés à Visual Studio ne sont pas disponibles en tant que package NuGet. par conséquent, ces règles ne sont pas applicables dans une build CI.

## <a name="ide-analyzers-versus-stylecop"></a>Analyseurs IDE et StyleCop

**Q**: quelle est la différence entre les analyseurs de code de l’IDE de Visual Studio et les analyseurs StyleCop ?

**R**: l’IDE de Visual Studio comprend des analyseurs intégrés qui recherchent à la fois les problèmes de style de code et de qualité. Ces règles vous aident à utiliser les nouvelles fonctionnalités de langage telles qu’elles sont introduites et à améliorer la maintenabilité de votre code. Les analyseurs IDE sont continuellement mis à jour avec chaque version de Visual Studio.

Les [analyseurs StyleCop](https://github.com/DotNetAnalyzers/StyleCopAnalyzers) sont des analyseurs tiers installés en tant que package NuGet qui vérifient la cohérence du style dans votre code. En général, les règles StyleCop vous permettent de définir des préférences personnelles pour une base de code sans recommander un style sur un autre.

## <a name="code-analyzers-versus-legacy-analysis"></a>Analyseurs de code et analyse héritée

**Q**: quelle est la différence entre l’analyse héritée et l’analyse du code basé sur .NET Compiler Platform ?

**R**: l’analyse du code basé sur le .NET Compiler Platform analyse le code source en temps réel et Pendant la compilation, tandis que l’analyse héritée analyse les fichiers binaires une fois la génération terminée. Pour plus d’informations, consultez [analyse basée sur les .NET Compiler Platform et analyse héritée](../code-quality/net-analyzers-faq.md#whats-the-difference-between-legacy-fxcop-and-net-analyzers).

## <a name="fxcop-analyzers-versus-net-analyzers"></a>Analyseurs FxCop et analyseurs .NET

**Q**: quelle est la différence entre les analyseurs FxCop et les analyseurs .net ?

**R**: les analyseurs FxCop et les analyseurs .net font référence aux implémentations de l’analyseur de .NET Compiler Platform (« Roslyn ») des règles d’autorité de certification FxCop. Avant Visual Studio 2019 16,8 et .NET 5,0, ces analyseurs étaient fournis sous forme de `Microsoft.CodeAnalysis.FxCopAnalyzers` [package NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers). À compter de Visual Studio 2019 16,8 et .NET 5,0, ces analyseurs sont [inclus dans le kit de développement logiciel (SDK) .net](/dotnet/fundamentals/code-analysis/overview). Ils sont également disponibles en tant que `Microsoft.CodeAnalysis.NetAnalyzers` [package NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers). Envisagez [de migrer des analyseurs FxCop vers des analyseurs .net](migrate-from-fxcop-analyzers-to-net-analyzers.md).

## <a name="treat-warnings-as-errors"></a>Considérer les avertissements comme des erreurs

**Q**: mon projet utilise l’option de build pour traiter les avertissements comme des erreurs. Après la migration de l’analyse héritée vers l’analyse du code source, tous les avertissements de l’analyse du code s’affichent désormais comme des erreurs. Comment puis-je l’éviter ?

**R**: pour empêcher les avertissements d’analyse du code d’être traités comme des erreurs, procédez comme suit :

  1. Créez un fichier. props avec le contenu suivant :

     ```xml
     <Project>
        <PropertyGroup>
           <CodeAnalysisTreatWarningsAsErrors>false</CodeAnalysisTreatWarningsAsErrors>
        </PropertyGroup>
     </Project>
     ```

  2. Ajoutez une ligne à votre fichier projet. csproj ou. vbproj pour importer le fichier. props que vous avez créé à l’étape précédente. Cette ligne doit être placée avant toutes les lignes qui importent les fichiers Analyzer. props. Par exemple, si votre fichier. props est nommé CodeAnalysis. props :

     ```xml
     ...
     <Import Project="..\..\codeanalysis.props" Condition="Exists('..\..\codeanalysis.props')" />
     <Import Project="..\packages\Microsoft.CodeAnalysis.NetAnalyzers.5.0.0\build\Microsoft.CodeAnalysis.NetAnalyzers.props" Condition="Exists('..\packages\Microsoft.CodeAnalysis.NetAnalyzers.5.0.0\build\Microsoft.CodeAnalysis.NetAnalyzers.props')" />
     ...
     ```

## <a name="code-analysis-solution-property-page"></a>Page de propriétés de la solution d’analyse du code

**Q**: où se trouve la page de propriétés analyse du code pour la solution ?

**R**: la page de propriétés analyse du code au niveau de la solution a été supprimée au profit du groupe de propriétés partagées plus fiable. Pour la gestion de l’analyse du code au niveau du projet, la page de propriétés analyse du code est toujours disponible. (Pour les projets managés, nous vous recommandons également de migrer des ensembles de règles vers EditorConfig pour la configuration des règles.)  Pour partager des groupes de règles sur plusieurs projets dans une solution ou un référentiel, nous vous recommandons de définir un groupe de propriétés avec la propriété [CodeAnalysisRuleSet](../code-quality/using-rule-sets-to-group-code-analysis-rules.md#specify-a-rule-set-for-a-project) dans un fichier Shared/Targets ou *Directory. props/Directory. targets* . Si vous n’avez pas de propriétés ou de cibles courantes que tous vos projets importent, vous devez envisager d’ajouter ce type de groupe de propriétés à un [fichier Directory. props ou Directory. targets](../msbuild/customize-your-build.md) dans un répertoire de solution de niveau supérieur, qui est importé automatiquement dans tous les fichiers projet définis dans le répertoire ou dans ses sous-répertoires.

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des analyseurs](roslyn-analyzers-overview.md)
- [Paramètres de Convention de codage .NET pour EditorConfig](/dotnet/fundamentals/code-analysis/code-style-rule-options)