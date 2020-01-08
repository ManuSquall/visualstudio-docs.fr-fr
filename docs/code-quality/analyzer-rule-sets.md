---
title: Ensembles de règles et fichiers editorconfig de l’analyseur FxCop
ms.date: 10/08/2019
ms.topic: conceptual
helpviewer_keywords:
- analyzer packages, rule sets
- rule sets for analyzers
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0b3ed77a309448a854d733453c932fc007f7f591
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75573285"
---
# <a name="enable-a-category-of-rules"></a>Activer une catégorie de règles

Les packages de l’analyseur peuvent inclure des fichiers [EditorConfig](use-roslyn-analyzers.md#rule-severity) et des [ensembles de règles](using-rule-sets-to-group-code-analysis-rules.md) prédéfinis qui permettent d’activer rapidement et facilement une catégorie de règles, telles que des règles de sécurité ou de conception. Le package de l’analyseur NuGet [Microsoft. CodeAnalysis. FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/) comprend les deux ensembles de règles (à partir de la version 2.6.2) et les fichiers EditorConfig (à partir de la version 2.9.5). En activant une catégorie spécifique de règles, vous pouvez identifier des problèmes ciblés et des conditions spécifiques.

> [!NOTE]
> L’activation des règles de l’analyseur et la définition de leur gravité à l’aide d’un fichier EditorConfig sont prises en charge à partir de Visual Studio 2019 version 16,3.

Le package NuGet Analyzer de FxCop comprend des ensembles de règles prédéfinis et des fichiers EditorConfig pour les catégories de règles suivantes :

- Toutes les règles
- Flux de données
- Création
- Documentation
- Globalisation
- Interopérabilité
- Maintenabilité
- Attribution des noms
- Performances
- Porté depuis FxCop
- Fiabilité
- Sécurité
- Contrôle

Chacune de ces catégories de règles a un fichier de EditorConfig ou d’ensemble de règles pour :

- activer toutes les règles de la catégorie (et désactiver toutes les autres règles)
- Utilisez le paramètre de gravité et d’activation par défaut de chaque règle (et désactivez toutes les autres règles).

> [!TIP]
> La catégorie « toutes les règles » dispose d’un EditorConfig ou d’un fichier d’ensemble de règles supplémentaire pour désactiver toutes les règles. Utilisez ce fichier pour supprimer rapidement les avertissements ou erreurs de l’analyseur dans un projet.

> [!TIP]
> Si vous effectuez une migration à partir d’une analyse « FxCop » héritée vers une analyse de code basée sur .NET Compiler Platform, les fichiers EditorConfig et d’ensemble de règles vous permettent de continuer à utiliser des configurations de règles similaires à [celles que vous avez utilisées précédemment](rule-set-reference.md).

## <a name="predefined-editorconfig-files"></a>Fichiers EditorConfig prédéfinis

Les fichiers EditorConfig prédéfinis pour le package de l’analyseur Microsoft. CodeAnalysis. FxCopAnalyzers se trouvent dans le répertoire *% UserProfile%\\. nuget\packages\microsoft.codeanalysis.fxcopanalyzers\\\<version\>\editorconfig* . Par exemple, le fichier EditorConfig pour activer toutes les règles de sécurité se trouve dans *% UserProfile%\\. nuget\packages\microsoft.codeanalysis.fxcopanalyzers\\\<version\>\editorconfig\SecurityRulesEnabled\\. EditorConfig*.

Copiez le fichier. editorconfig choisi dans le répertoire racine de votre projet.

## <a name="predefined-rule-sets"></a>Ensembles de règles prédéfinis

Les fichiers d’ensemble de règles prédéfinis pour le package de l’analyseur Microsoft. CodeAnalysis. FxCopAnalyzers se trouvent dans le répertoire *% UserProfile%\\. nuget\packages\microsoft.codeanalysis.fxcopanalyzers\\\<version\>\rulesets* . Par exemple, le fichier d’ensemble de règles permettant d’activer toutes les règles de sécurité se trouve à l’emplacement *% UserProfile%\\. nuget\packages\microsoft.codeanalysis.fxcopanalyzers\\\<version\>\rulesets\SecurityRulesEnabled.RuleSet*.

Copiez un ou plusieurs ensembles de règles et collez-les dans le répertoire qui contient votre projet Visual Studio ou directement dans **Explorateur de solutions**.

Vous pouvez également [personnaliser un ensemble de règles prédéfini](how-to-create-a-custom-rule-set.md) à votre convenance. Par exemple, vous pouvez modifier la gravité d’une ou plusieurs règles afin que les violations apparaissent en tant qu’erreurs ou avertissements dans le **liste d’erreurs**.

### <a name="set-the-active-rule-set"></a>Définir l’ensemble de règles actif

Le processus de définition de l’ensemble de règles actif est un peu différent selon que vous disposez d’un projet .NET Core/. NET standard ou d’un projet de .NET Framework.

#### <a name="net-core"></a>.NET Core

Pour qu’une règle définisse l’ensemble de règles actif pour l’analyse dans les projets .NET Core ou .NET Standard, ajoutez manuellement la propriété **CodeAnalysisRuleSet** à votre fichier projet. Par exemple, l’extrait de code suivant définit `HelloWorld.ruleset` comme ensemble de règles actif.

```xml
<PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">
  ...
  <CodeAnalysisRuleSet>HelloWorld.ruleset</CodeAnalysisRuleSet>
</PropertyGroup>
```

#### <a name="net-framework"></a>.NET Framework

Pour définir l’ensemble de règles actif en vue d’une analyse dans des projets .NET Framework, procédez comme suit :

- Dans **Explorateur de solutions** , cliquez avec le bouton droit sur le projet et choisissez **Propriétés**.

- Dans les pages de propriétés du projet, sélectionnez l’onglet **analyse du code** .

::: moniker range="vs-2017"

- Sous **exécuter cet ensemble de règles**, sélectionnez **Parcourir**, puis sélectionnez l’ensemble de règles souhaité que vous avez copié dans le répertoire du projet.

::: moniker-end

::: moniker range=">=vs-2019"

- Sous **règles actives**, sélectionnez **Parcourir**, puis sélectionnez l’ensemble de règles souhaité que vous avez copié dans le répertoire du projet.

::: moniker-end

   À présent, vous ne voyez que les violations de règle pour les règles qui sont activées dans l’ensemble de règles sélectionné.

## <a name="see-also"></a>Voir aussi

- [FAQ sur les analyseurs](analyzers-faq.md)
- [Vue d’ensemble des analyseurs .NET Compiler Platform](roslyn-analyzers-overview.md)
- [Installer des analyseurs](install-roslyn-analyzers.md)
- [Configurer des analyseurs](use-roslyn-analyzers.md)
- [Utiliser des ensembles de règles pour regrouper des règles d’analyse du code](using-rule-sets-to-group-code-analysis-rules.md)
