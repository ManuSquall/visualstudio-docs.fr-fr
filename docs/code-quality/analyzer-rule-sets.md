---
title: Ensembles de règles d’analyseur
ms.date: 04/22/2019
ms.topic: conceptual
helpviewer_keywords:
- analyzers, rule sets
- rule sets for analyzers
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 696e6bd46c17054494be2ea0e0f2a1af4fd703d7
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65675484"
---
# <a name="rule-sets-for-roslyn-analyzers"></a>Ensembles de règles pour les analyseurs Roslyn

Ensembles de règles prédéfinis sont inclus avec certains packages d’analyseur de NuGet. Par exemple, les ensembles de règles qui sont inclus dans le [Microsoft.CodeAnalysis.FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/) package NuGet de l’analyseur (depuis la version 2.6.2) activer ou désactiver les règles selon leur catégorie, telles que la sécurité, d’affectation de noms, ou performances. À l’aide des ensembles de règles rend plus facile pour rapidement afficher uniquement ces violations des règles qui se rapportent à une catégorie particulière de règle.

Si vous migrez à partir de l’analyse statique du code « FxCop » héritée vers des analyseurs de Roslyn, ces ensembles de règles permettent de continuer à utiliser les mêmes configurations de règle que vous avez utilisé précédemment.

## <a name="use-analyzer-rule-sets"></a>Utiliser des ensembles de règles d’analyseur

Après avoir [installer un package NuGet de l’analyseur](install-roslyn-analyzers.md), recherchez la règle prédéfinie définie ses *rulesets* directory. Par exemple, si vous avez référencé la `Microsoft.CodeAnalysis.FxCopAnalyzers` package de l’analyseur, puis vous pouvez trouver son *rulesets* répertoire à *% USERPROFILE%\\.nuget\packages\microsoft.codeanalysis.fxcopanalyzers\\ \<version\>\rulesets*. À partir de là, copier un ou plusieurs groupes de règles et les coller dans le répertoire qui contient votre projet Visual Studio ou directement dans **l’Explorateur de solutions**.

Vous pouvez également [personnaliser un ensemble de règles prédéfinies](how-to-create-a-custom-rule-set.md) selon vos préférences. Par exemple, vous pouvez modifier le niveau de gravité d’une ou plusieurs règles afin que les violations s’affichent comme des erreurs ou avertissements dans le **liste d’erreurs**.

## <a name="set-the-active-rule-set"></a>Définir l’ensemble de règles actif

Le processus de configuration de l’ensemble de règles actif est un peu différent selon que vous avez un projet .NET Core/.NET Standard ou un projet .NET Framework.

### <a name="net-core"></a>.NET Core

Pour faire une règle de la règle active définie pour l’analyse dans les projets .NET Core ou .NET Standard, ajouter manuellement le **CodeAnalysisRuleSet** propriété à votre fichier projet. Par exemple, le code suivant extrait de code jeux `HelloWorld.ruleset` que la règle active définie.

```xml
<PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">
  ...
  <CodeAnalysisRuleSet>HelloWorld.ruleset</CodeAnalysisRuleSet>
</PropertyGroup>
```

### <a name="net-framework"></a>.NET Framework

Pour faire une règle de la règle active définie pour l’analyse dans les projets .NET Framework, cliquez sur le projet dans **l’Explorateur de solutions** et choisissez **propriétés**. Dans les pages de propriétés de projet, sélectionnez le **analyse du Code** onglet. Sous **exécuter cet ensemble de règles**, sélectionnez **Parcourir**, puis sélectionnez l’ensemble de règles souhaité que vous avez copié dans le répertoire de projet. Maintenant, vous voyez uniquement les violations de règle pour que ces règles sont activées dans l’ensemble de règles sélectionné.

## <a name="available-rule-sets"></a>Ensembles de règles disponibles

Les ensembles de règles analyseur prédéfini incluent trois ensembles de règles qui affectent toutes les règles dans le package&mdash;un qui permet à tous les, désactive tous les accès à celui-ci et un qui respecte les paramètres de gravité et l’activation de chaque règle par défaut :

- AllRulesEnabled.ruleset
- AllRulesDisabled.ruleset
- AllRulesDefault.ruleset

En outre, il existe deux ensembles de règles pour chaque catégorie de règles dans le package, telles que les performances ou la sécurité. Un ensemble de règles Active toutes les règles pour la catégorie et un ensemble de règles respecte les paramètres de gravité et d’activation par défaut pour chaque règle dans la catégorie.

Le [Microsoft.CodeAnalysis.FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/) package NuGet de l’analyseur inclut les ensembles de règles pour les catégories suivantes, qui correspondent aux ensembles de règles disponibles pour l’analyse du code statique FxCop « hérités » :

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
- [Utiliser la règle définit pour les règles d’analyse de code de groupe](using-rule-sets-to-group-code-analysis-rules.md)
