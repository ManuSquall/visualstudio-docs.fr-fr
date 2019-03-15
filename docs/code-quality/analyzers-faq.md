---
title: EditorConfig par rapport à des analyseurs
ms.date: 03/11/2019
ms.topic: conceptual
helpviewer_keywords:
- analyzers, faq
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bec9296f15c48cf3b327c78cd0ce7d57adafa002
ms.sourcegitcommit: f7c401a376ce410336846835332a693e6159c551
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57874668"
---
# <a name="analyzers-faq"></a>FAQ sur les Analyseurs

Cette page contient des réponses à certaines questions fréquemment posées sur les analyseurs de Roslyn dans Visual Studio.

## <a name="roslyn-analyzers-versus-editorconfig"></a>Analyseurs de Roslyn par rapport à .editorconfig

**Q**: Dois-je utiliser des analyseurs de Roslyn ou .editorconfig pour le style de code ?

**R** : Analyseurs de Roslyn et les fichiers .editorconfig fonctionnent de pair. Lorsque vous définissez des styles de code [dans un fichier .editorconfig](../ide/editorconfig-code-style-settings-reference.md) ou sur le [éditeur de texte Options](../ide/code-styles-and-quick-actions.md) page, que vous configurez en fait les analyseurs de Roslyn qui sont intégrés à Visual Studio. Les fichiers EditorConfig peuvent également être utilisés pour configurer des packages tiers analyzer, tel que [analyseurs FxCop](configure-fxcop-analyzers.md).

## <a name="editorconfig-versus-rule-sets"></a>EditorConfig par rapport à des ensembles de règles

**Q**: Dois-je configurer mon analyseurs à l’aide d’un ensemble de règles ou un fichier .editorconfig ?

**R** : Ensembles de règles et les fichiers .editorconfig manières mutuellement exclusives pour configurer les analyseurs. Ils peuvent coexister. [Ensembles de règles](analyzer-rule-sets.md) vous permettent d’activer et désactiver des règles et définir leur niveau de gravité. Les fichiers EditorConfig offrent les autres façons de configurer des règles. Pour les analyseurs FxCop, fichiers .editorconfig vous permettent de [définir les types de code pour analyser](fxcop-analyzer-options.md). Pour les analyseurs qui sont intégrés à Visual Studio, les fichiers .editorconfig vous permettent de [définir les styles de code par défaut](../ide/editorconfig-code-style-settings-reference.md) pour une base de code.

En plus des ensembles de règles et les fichiers .editorconfig, certains analyseurs par des tiers sont configurés via l’utilisation de fichiers texte marqués comme [des fichiers supplémentaires](../ide/build-actions.md#build-action-values) pour le C# et les compilateurs Visual Basic.

> [!NOTE]
> Les fichiers EditorConfig ne peut pas être utilisés pour configurer des règles d’analyse statique du code, tandis que les ensembles de règles peuvent.

## <a name="analyzers-in-ci-builds"></a>Analyseurs dans les builds d’intégration continue

**Q**: Analyseurs fonctionnent dans les builds d’intégration continue (CI) ?

**R** : Oui. Pour les analyseurs qui sont installés à partir d’un package NuGet, ces règles sont [appliquées au moment de la génération](roslyn-analyzers-overview.md#build-errors), y compris lors d’une génération CI. Analyseurs utilisés dans la configuration de règles de respect de builds CI à partir des deux [ensembles de règles](analyzer-rule-sets.md) et [fichiers .editorconfig](configure-fxcop-analyzers.md). Actuellement, les analyseurs de code qui sont intégrés à Visual Studio ne sont pas disponibles sous forme de package NuGet, et par conséquent, ces règles ne sont pas applicables dans une build CI.

## <a name="ide-analyzers-versus-stylecop"></a>Analyseurs d’IDE et StyleCop

**Q**: Quelle est la différence entre les analyseurs de code Visual Studio IDE et les analyseurs de StyleCop ?

**R** : L’IDE Visual Studio inclut des analyseurs intégrés qui les recherchent ces deux problèmes de style et la qualité du code. Ces règles vous aider à utiliser les nouvelles fonctionnalités de langage lorsqu’ils sont introduites et améliorent la gestion de votre code. Les analyseurs IDE continuellement mise à jour avec chaque version de Visual Studio.

[Analyseurs de StyleCop](https://github.com/DotNetAnalyzers/StyleCopAnalyzers) sont des analyseurs de fournisseurs tiers installés sous forme de package NuGet vérifier la cohérence du style dans votre code. En règle générale, les règles StyleCop vous permettent de définir des préférences personnelles pour un code base sans recommander un style à un autre.

## <a name="analyzers-versus-static-code-analysis"></a>Analyseurs par rapport à l’analyse statique du code

**Q**: Quelle est la différence entre les analyseurs et d’analyse statique du code ?

**R** : Analyseurs analyser du code source en temps réel et pendant la compilation, tandis que l’analyse statique du code analyse les fichiers binaires après que la génération terminée. Pour plus d’informations, consultez [et l’analyse statique du code, les analyseurs de Roslyn](roslyn-analyzers-overview.md#roslyn-analyzers-vs-static-code-analysis) et [Forum aux questions sur les analyseurs FxCop](fxcop-analyzers-faq.md).

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des analyseurs](roslyn-analyzers-overview.md)
- [Paramètres des conventions de codage .NET pour EditorConfig](../ide/editorconfig-code-style-settings-reference.md)