---
title: Ensembles de règles de l’analyseur
ms.date: 04/22/2019
ms.topic: conceptual
helpviewer_keywords:
- analyzer packages, rule sets
- rule sets for analyzers
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 68410fd43f182873c27e3d5fed742bed7ba8a4ed
ms.sourcegitcommit: b83fefa8177c5554cbe2c59c4d102cbc534f7cc6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69585136"
---
# <a name="rule-sets-for-analyzer-packages"></a>Ensembles de règles pour les packages de l’analyseur

Les ensembles de règles prédéfinis sont inclus dans certains packages de l’analyseur NuGet. Par exemple, les ensembles de règles inclus dans le package de l’analyseur NuGet [Microsoft. CodeAnalysis. FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/) (à partir de la version 2.6.2) activent ou désactivent les règles en fonction de leur catégorie, telles que la sécurité, l’attribution de noms ou les performances. Grâce à l’utilisation d’ensembles de règles, il est facile de voir rapidement les violations de règle qui se rapportent à une catégorie de règle particulière.

Si vous effectuez une migration à partir d’une analyse «FxCop» héritée vers une analyse de code basée sur .NET Compiler Platform, ces ensembles de règles vous permettent de continuer à utiliser des configurations de règles similaires à [celles que vous avez utilisées précédemment](rule-set-reference.md).

## <a name="use-analyzer-package-rule-sets"></a>Utiliser les ensembles de règles du package de l’analyseur

Après avoir [installé un package de l’analyseur NuGet](install-roslyn-analyzers.md), localisez l’ensemble de règles prédéfini dans son répertoire RuleSet. Par exemple, si vous avez référencé le `Microsoft.CodeAnalysis.FxCopAnalyzers` package de l’analyseur, vous pouvez trouver son répertoire RuleSet dans *% UserProfile\\%.\\\<nuget\packages\microsoft.CodeAnalysis.fxcopanalyzers version \rulesets\>* . À partir de là, copiez un ou plusieurs ensembles de règles et collez-les dans le répertoire qui contient votre projet Visual Studio ou directement dans **Explorateur de solutions**.

Vous pouvez également [personnaliser un ensemble de règles prédéfini](how-to-create-a-custom-rule-set.md) à votre convenance. Par exemple, vous pouvez modifier la gravité d’une ou plusieurs règles afin que les violations apparaissent en tant qu’erreurs ou avertissements dans le **liste d’erreurs**.

## <a name="set-the-active-rule-set"></a>Définir l’ensemble de règles actif

Le processus de définition de l’ensemble de règles actif est un peu différent selon que vous disposez d’un projet .NET Core/. NET standard ou d’un projet de .NET Framework.

### <a name="net-core"></a>.NET Core

Pour qu’une règle définisse l’ensemble de règles actif pour l’analyse dans les projets .NET Core ou .NET Standard, ajoutez manuellement la propriété **CodeAnalysisRuleSet** à votre fichier projet. Par exemple, l’extrait de code suivant `HelloWorld.ruleset` définit comme ensemble de règles actif.

```xml
<PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">
  ...
  <CodeAnalysisRuleSet>HelloWorld.ruleset</CodeAnalysisRuleSet>
</PropertyGroup>
```

### <a name="net-framework"></a>.NET Framework

Pour définir l’ensemble de règles actif pour l’analyse dans .NET Framework projets, cliquez avec le bouton droit sur le projet dans **Explorateur de solutions** et choisissez **Propriétés**. Dans les pages de propriétés du projet, sélectionnez l’onglet **analyse du code** . Sous **exécuter cet ensemble de règles**, sélectionnez **Parcourir**, puis sélectionnez l’ensemble de règles souhaité que vous avez copié dans le répertoire du projet. À présent, vous ne voyez que les violations de règle pour les règles qui sont activées dans l’ensemble de règles sélectionné.

## <a name="available-rule-sets"></a>Ensembles de règles disponibles

Les ensembles de règles de l’analyseur prédéfinis incluent trois groupes de règles qui affectent toutes&mdash;les règles du package qui les active, les désactive toutes et l’autre qui respecte les paramètres de gravité et d’activation par défaut de chaque règle:

- AllRulesEnabled.ruleset
- AllRulesDisabled.ruleset
- AllRulesDefault.ruleset

En outre, il existe deux ensembles de règles pour chaque catégorie de règles dans le package, telles que les performances ou la sécurité. Un ensemble de règles active toutes les règles de la catégorie, et un ensemble de règles honore les paramètres de gravité et d’activation par défaut pour chaque règle de la catégorie.

Le package de l’analyseur NuGet [Microsoft. CodeAnalysis. FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/) comprend des ensembles de règles pour les catégories suivantes:

- design
- documentation
- facilité de gestion
- affecter des noms
- performances
- fiabilité
- security
- utilisation

## <a name="see-also"></a>Voir aussi

- [FAQ sur les analyseurs](analyzers-faq.md)
- [Vue d’ensemble des analyseurs .NET Compiler Platform](roslyn-analyzers-overview.md)
- [Installer des analyseurs](install-roslyn-analyzers.md)
- [Utiliser des analyseurs](use-roslyn-analyzers.md)
- [Utiliser des ensembles de règles pour regrouper des règles d’analyse du code](using-rule-sets-to-group-code-analysis-rules.md)
