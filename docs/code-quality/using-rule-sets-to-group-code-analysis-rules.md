---
title: Ensembles de règles d'analyse du code
ms.date: 04/02/2018
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.rulesets.learnmore
helpviewer_keywords:
- code analysis, rule sets
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 13a49f208fe3c60dfb8b9e20c83675cc43f1efb1
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75587171"
---
# <a name="use-rule-sets-to-group-code-analysis-rules"></a>Utiliser des ensembles de règles pour regrouper des règles d’analyse du code

Quand vous configurez l’analyse du code dans Visual Studio, vous pouvez choisir dans une liste d' *ensembles de règles*intégrés. Un ensemble de règles est un regroupement de règles d’analyse du code qui identifient des problèmes ciblés et des conditions spécifiques pour ce projet. Par exemple, vous pouvez appliquer un ensemble de règles conçu pour analyser le code des API disponibles publiquement. Vous pouvez également appliquer un ensemble de règles qui comprend toutes les règles disponibles.

Vous pouvez personnaliser un ensemble de règles en ajoutant ou en supprimant des règles ou en modifiant les gravités de la règle pour qu’elles apparaissent sous la forme d’avertissements ou d’erreurs dans le **liste d’erreurs**. Les ensembles de règles personnalisés peuvent satisfaire un besoin pour votre environnement de développement particulier. Lorsque vous personnalisez un ensemble de règles, l’éditeur d’ensembles de règles fournit des outils de recherche et de filtrage pour vous aider dans le processus.

Les ensembles de règles sont disponibles pour l’analyse du [code managé](analyzer-rule-sets.md), l' [analyse héritée du code managé](how-to-configure-code-analysis-for-a-managed-code-project.md)et [ C++ l’analyse du code](using-rule-sets-to-specify-the-cpp-rules-to-run.md).

## <a name="rule-set-format"></a>Format de l’ensemble de règles

Un ensemble de règles est spécifié au format XML dans un fichier *. RuleSet* . Les règles, qui consistent en un ID et une *action*, sont regroupées par ID et espace de noms de l’analyseur dans le fichier.

Le contenu d’un fichier *. RuleSet* ressemble à ce code XML :

```xml
<RuleSet Name="Rules for Hello World project" Description="These rules focus on critical issues for the Hello World app." ToolsVersion="10.0">
  <Localization ResourceAssembly="Microsoft.VisualStudio.CodeAnalysis.RuleSets.Strings.dll" ResourceBaseName="Microsoft.VisualStudio.CodeAnalysis.RuleSets.Strings.Localized">
    <Name Resource="HelloWorldRules_Name" />
    <Description Resource="HelloWorldRules_Description" />
  </Localization>
  <Rules AnalyzerId="Microsoft.Analyzers.ManagedCodeAnalysis" RuleNamespace="Microsoft.Rules.Managed">
    <Rule Id="CA1001" Action="Warning" />
    <Rule Id="CA1009" Action="Warning" />
    <Rule Id="CA1016" Action="Warning" />
    <Rule Id="CA1033" Action="Warning" />
  </Rules>
  <Rules AnalyzerId="Microsoft.CodeQuality.Analyzers" RuleNamespace="Microsoft.CodeQuality.Analyzers">
    <Rule Id="CA1802" Action="Error" />
    <Rule Id="CA1814" Action="Info" />
    <Rule Id="CA1823" Action="None" />
    <Rule Id="CA2217" Action="Warning" />
  </Rules>
</RuleSet>
```

> [!TIP]
> Il est plus facile de [modifier un ensemble de règles](../code-quality/working-in-the-code-analysis-rule-set-editor.md) dans l' **éditeur d’ensembles de règles** graphique que manuellement.

## <a name="specify-a-rule-set-for-a-project"></a>Spécifier un ensemble de règles pour un projet

L’ensemble de règles d’un projet est spécifié par la propriété **CodeAnalysisRuleSet** dans le fichier projet Visual Studio. Par exemple :

```xml
<PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">
  ...
  <CodeAnalysisRuleSet>HelloWorld.ruleset</CodeAnalysisRuleSet>
</PropertyGroup>
```

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur l’ensemble de règles d’analyse du code](../code-quality/rule-set-reference.md)
