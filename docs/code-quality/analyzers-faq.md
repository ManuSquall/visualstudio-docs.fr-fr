---
title: EditorConfig et analyseurs
ms.date: 03/11/2019
ms.topic: conceptual
helpviewer_keywords:
- analyzers, faq
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 53bd2139d5b81ed743cdfd92fe76cb575dcc6487
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/16/2019
ms.locfileid: "69547890"
---
# <a name="code-analysis-faq"></a>FAQ sur l’analyse du code

Cette page contient des réponses à certaines questions fréquemment posées sur l’analyse du code basé sur .NET Compiler Platform dans Visual Studio.

## <a name="code-analysis-versus-editorconfig"></a>Analyse du code et EditorConfig

**Q** : Dois-je utiliser l’analyse du code ou EditorConfig pour vérifier le style du code?

**R** : L’analyse du code et les fichiers. editorconfig fonctionnent à la main. Quand vous définissez des styles [de code dans un fichier. editorconfig](../ide/editorconfig-code-style-settings-reference.md) ou dans la page d’options de l' [éditeur de texte](../ide/code-styles-and-code-cleanup.md) , vous configurez en fait les analyseurs de code intégrés à Visual Studio. Les fichiers EditorConfig peuvent également être utilisés pour configurer des packages de l’analyseur tiers, tels que les [analyseurs FxCop](configure-fxcop-analyzers.md).

## <a name="editorconfig-versus-rule-sets"></a>EditorConfig et ensembles de règles

**Q** : Dois-je configurer mes analyseurs à l’aide d’un ensemble de règles ou d’un fichier. editorconfig?

**R** : Les ensembles de règles et les fichiers. editorconfig sont des méthodes mutuellement exclusives pour configurer des analyseurs. Ils peuvent coexister. Les [ensembles de règles](analyzer-rule-sets.md) vous permettent d’activer et de désactiver des règles et de définir leur gravité. Les fichiers EditorConfig offrent d’autres méthodes de configuration des règles. Pour les analyseurs FxCop, les fichiers. editorconfig vous permettent de [définir les types de code à analyser](fxcop-analyzer-options.md). Pour les analyseurs intégrés à Visual Studio, les fichiers. editorconfig vous permettent de [définir les styles de code préférés](../ide/editorconfig-code-style-settings-reference.md) pour un code base.

Outre les ensembles de règles et les fichiers. editorconfig, certains analyseurs tiers sont configurés via l’utilisation de fichiers texte marqués comme [fichiers supplémentaires](../ide/build-actions.md#build-action-values) pour les C# compilateurs vb et.

> [!NOTE]
> Les fichiers EditorConfig ne peuvent pas être utilisés pour configurer l’analyse héritée, contrairement aux ensembles de règles.

## <a name="code-analysis-in-ci-builds"></a>Analyse du code dans les builds d’intégration continue

**Q** : L’analyse du code basé sur .NET Compiler Platform fonctionne-t-elle dans les builds d’intégration continue?

**R** : Oui. Pour les analyseurs installés à partir d’un package NuGet, ces règles sont [appliquées au moment](roslyn-analyzers-overview.md#build-errors)de la génération, y compris pendant une build ci. Les analyseurs utilisés dans les builds d’intégration continue respectent la configuration des règles des [ensembles de règles](analyzer-rule-sets.md) et des [fichiers. editorconfig](configure-fxcop-analyzers.md). Actuellement, les analyseurs de code intégrés à Visual Studio ne sont pas disponibles en tant que package NuGet. par conséquent, ces règles ne sont pas applicables dans une build CI.

## <a name="ide-analyzers-versus-stylecop"></a>Analyseurs IDE et StyleCop

**Q** : Quelle est la différence entre les analyseurs de code de l’IDE de Visual Studio et les analyseurs StyleCop?

**R** : L’IDE de Visual Studio comprend des analyseurs intégrés qui recherchent à la fois les problèmes de style de code et de qualité. Ces règles vous aident à utiliser les nouvelles fonctionnalités de langage telles qu’elles sont introduites et à améliorer la maintenabilité de votre code. Les analyseurs IDE sont continuellement mis à jour avec chaque version de Visual Studio.

Les [analyseurs StyleCop](https://github.com/DotNetAnalyzers/StyleCopAnalyzers) sont des analyseurs tiers installés en tant que package NuGet qui vérifient la cohérence du style dans votre code. En général, les règles StyleCop vous permettent de définir des préférences personnelles pour une base de code sans recommander un style sur un autre.

## <a name="code-analyzers-versus-legacy-analysis"></a>Analyseurs de code et analyse héritée

**Q** : Quelle est la différence entre l’analyse héritée et l’analyse du code basé sur .NET Compiler Platform?

**R**: l’analyse du code basé sur le .NET Compiler Platform analyse le code source en temps réel et Pendant la compilation, tandis que l’analyse héritée analyse les fichiers binaires une fois la génération terminée. Pour plus d’informations, consultez [analyse basée sur les .NET Compiler Platform plutôt que analyse héritée](roslyn-analyzers-overview.md#net-compiler-platform-based-analysis-versus-legacy-analysis) et [FAQ sur les analyseurs FxCop](fxcop-analyzers-faq.md).

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des analyseurs](roslyn-analyzers-overview.md)
- [Paramètres des conventions de codage .NET pour EditorConfig](../ide/editorconfig-code-style-settings-reference.md)