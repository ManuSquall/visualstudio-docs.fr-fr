---
title: Définit des règles d’analyse du code dans Visual Studio
ms.date: 04/02/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.rulesets.learnmore
helpviewer_keywords:
- code analysis, rule sets
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 20e727fd331ebd98a74acbb63738e6921e5ad1a0
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31923053"
---
# <a name="use-rule-sets-to-group-code-analysis-rules"></a>Utiliser la règle définit aux règles d’analyse de code de groupe

Lorsque vous configurez l’analyse du code dans Visual Studio, vous pouvez choisir parmi une liste d’intégré *ensembles de règles*. Un ensemble de règles s’applique à un projet et est un regroupement de code des règles d’analyse qui identifient les problèmes ciblés et des conditions spécifiques pour ce projet. Par exemple, vous pouvez appliquer un ensemble de règles est conçu pour analyser le code des API publiques disponibles, ou simplement la valeur minimale des règles recommandées. Vous pouvez également appliquer un ensemble de règles qui inclut toutes les règles.

Vous pouvez personnaliser un ensemble de règles en ajoutant ou supprimant des règles, ou en modifiant les niveaux de gravité de règle apparaissent comme des avertissements ou erreurs dans le **liste d’erreurs**. Ensembles de règles personnalisés peuvent répondre à un besoin pour votre environnement de développement particulier. Lorsque vous personnalisez un ensemble de règles, l’éditeur d’ensemble de règles fournit des outils pour vous aider dans le processus de filtrage et de recherche.

## <a name="rule-set-format"></a>Format d’ensemble de règles

Un ensemble de règles est spécifié au format XML dans un *.ruleset* fichier. Règles, qui se composent d’un ID et un *action*, sont regroupés par ID de l’analyseur et l’espace de noms dans le fichier.

Le contenu XML d’un *.ruleset* fichier ressemble à ceci :

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
> Il est plus facile de [modifier un ensemble de règles](../code-quality/working-in-the-code-analysis-rule-set-editor.md) dans l’affichage graphique **Éditeur d’ensemble de règles** que manuellement.

La règle définie pour un projet est défini par le `CodeAnalysisRuleSet` propriété dans le fichier de projet Visual Studio. Par exemple :

```xml
<CodeAnalysisRuleSet>HelloWorld.ruleset</CodeAnalysisRuleSet>
```

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur l’ensemble de règles d’analyse du code](../code-quality/rule-set-reference.md)
