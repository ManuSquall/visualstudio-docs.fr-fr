---
title: Générer la métrique du code à partir de l’IDE ou de la ligne de commande
ms.date: 11/02/2018
ms.topic: conceptual
helpviewer_keywords:
- code metrics data
- code metrics results
- code metrics [Visual Studio]
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4275e92b21289c5cf1e3243b2bc782a9e0821fde
ms.sourcegitcommit: 36f5ffd6ae3215fe31837f4366158bf0d871f7a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59232747"
---
# <a name="how-to-generate-code-metrics-data"></a>Procédure : Générer des données de métrique du code

Vous pouvez générer des données de métrique du code de trois façons :

- En installant [analyseurs FxCop](#fxcop-analyzers-code-metrics-rules) et d’activer les règles de métriques (la facilité de gestion) de quatre code qu’il contient.

- En choisissant le [ **analyser** > **calculer la métrique du Code** ](#calculate-code-metrics-menu-command) commande de menu dans Visual Studio.

- À partir de la [ligne de commande](#command-line-code-metrics) pour C# et projets Visual Basic.

## <a name="fxcop-analyzers-code-metrics-rules"></a>Règles de métriques du code analyseurs FxCop

Le [package NuGet de FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) inclut plusieurs métriques de code [analyseur](roslyn-analyzers-overview.md) règles :

- [CA1501](ca1501-avoid-excessive-inheritance.md)
- [CA1502](ca1502-avoid-excessive-complexity.md)
- [CA1505](ca1505-avoid-unmaintainable-code.md)
- [CA1506](ca1506-avoid-excessive-class-coupling.md)

Ces règles sont désactivées par défaut, mais vous pouvez les activer à partir de [ **l’Explorateur de solutions** ](use-roslyn-analyzers.md#set-rule-severity-from-solution-explorer) ou dans un [ensemble de règles](using-rule-sets-to-group-code-analysis-rules.md) fichier. Par exemple, pour activer la règle CA1502 comme un avertissement, votre fichier .ruleset contiendrait l’entrée suivante :

```xml
<?xml version="1.0" encoding="utf-8"?>
<RuleSet Name="Rules" Description="Rules" ToolsVersion="16.0">
  <Rules AnalyzerId="Microsoft.CodeQuality.Analyzers" RuleNamespace="Microsoft.CodeQuality.Analyzers">
    <Rule Id="CA1502" Action="Warning" />
  </Rules>
</RuleSet>
```

### <a name="configuration"></a>Configuration

Vous pouvez configurer les seuils à laquelle les règles de métriques de code dans les analyseurs FxCop package incendie.

1. Créer un fichier texte. Par exemple, vous pouvez la nommer *CodeMetricsConfig.txt*.

2. Ajoutez les seuils souhaités dans le fichier texte au format suivant :

   ```txt
   CA1502: 10
   ```

   Dans cet exemple, la règle [CA1502](ca1502-avoid-excessive-complexity.md) est configuré pour se déclencher lors de la complexité de cyclomatique d’une méthode est supérieure à 10.

3. Dans le **propriétés** fenêtre de Visual Studio ou dans le fichier projet, sélectionnez l’action de génération du fichier de configuration en tant que [ **AdditionalFiles**](../ide/build-actions.md#build-action-values). Exemple :

   ```xml
   <ItemGroup>
     <AdditionalFiles Include="CodeMetricsConfig.txt" />
   </ItemGroup>
   ```

## <a name="calculate-code-metrics-menu-command"></a>Calculer la commande de menu de métrique du Code

Générer des mesures de code pour une ou plusieurs de vos projets ouverts dans l’IDE à l’aide de la **analyser** > **calculer la métrique du Code** menu.

### <a name="generate-code-metrics-results-for-an-entire-solution"></a>Générer des résultats de métriques de code pour une solution entière

Vous pouvez générer des résultats de métriques de code pour une solution entière dans une des manières suivantes :

- Dans la barre de menus, choisissez **analyser** > **calculer la métrique du Code** > **pour la Solution**.

- Dans **l’Explorateur de solutions**, avec le bouton droit de la solution, puis choisissez **calculer la métrique du Code**.

- Dans le **résultats de la métrique Code** fenêtre, choisissez le **calculer la métrique du Code pour la Solution** bouton.

Les résultats sont générés et la **résultats de la métrique Code** fenêtre s’affiche. Pour afficher les détails des résultats, développez l’arborescence dans le **hiérarchie** colonne.

### <a name="generate-code-metrics-results-for-one-or-more-projects"></a>Générer des résultats de métriques de code pour un ou plusieurs projets

1. Dans **l’Explorateur de solutions**, sélectionnez un ou plusieurs projets.

1. Dans la barre de menus, choisissez **analyser** > **calculer la métrique du Code** > **pour sélectionné ou les projets**.

Les résultats sont générés et la **résultats de la métrique Code** fenêtre s’affiche. Pour afficher les détails des résultats, développez l’arborescence dans le **hiérarchie**.

::: moniker range="vs-2017"

> [!NOTE]
> Le **calculer la métrique du Code** commande ne fonctionne pas pour les projets .NET Core et .NET Standard. Pour calculer la métrique du code pour un projet .NET Core ou .NET Standard, vous pouvez :
>
> - calculer la métrique du code à partir de la [ligne de commande](#command-line-code-metrics) à la place
>
> - Mise à niveau vers [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)

::: moniker-end

## <a name="command-line-code-metrics"></a>Métrique du code en ligne de commande

Vous pouvez générer des données de métrique du code à partir de la ligne de commande pour C# et projets Visual Basic pour applications .NET Framework, .NET Core et .NET Standard. Pour exécuter la métrique du code à partir de la ligne de commande, vous devez installer le [package NuGet de Microsoft.CodeAnalysis.Metrics](#microsoftcodeanalysismetrics-nuget-package) ou générer le [Metrics.exe](#metricsexe) exécutable vous-même.

### <a name="microsoftcodeanalysismetrics-nuget-package"></a>Package NuGet de Microsoft.CodeAnalysis.Metrics

Le moyen le plus simple pour générer des données de métrique du code à partir de la ligne de commande consiste à installer le [Microsoft.CodeAnalysis.Metrics](https://www.nuget.org/packages/Microsoft.CodeAnalysis.Metrics/) package NuGet. Une fois que vous avez installé le package, exécutez `msbuild /t:Metrics` à partir du répertoire qui contient votre fichier projet. Exemple :

```shell
C:\source\repos\ClassLibrary3\ClassLibrary3>msbuild /t:Metrics
Microsoft (R) Build Engine version 16.0.360-preview+g9781d96883 for .NET Framework
Copyright (C) Microsoft Corporation. All rights reserved.

Build started 1/22/2019 4:29:57 PM.
Project "C:\source\repos\ClassLibrary3\ClassLibrary3\ClassLibrary3.csproj" on node 1 (Metrics target(s))
.
Metrics:
  C:\source\repos\ClassLibrary3\packages\Microsoft.CodeMetrics.2.6.4-ci\build\\..\Metrics\Metrics.exe /project:C:\source\repos\ClassLibrary3\ClassLibrary3\ClassLibrary3.csproj /out:ClassLibrary3.Metrics.xml
  Loading ClassLibrary3.csproj...
  Computing code metrics for ClassLibrary3.csproj...
  Writing output to 'ClassLibrary3.Metrics.xml'...
  Completed Successfully.
Done Building Project "C:\source\repos\ClassLibrary3\ClassLibrary3\ClassLibrary3.csproj" (Metrics target(s)).

Build succeeded.
    0 Warning(s)
    0 Error(s)
```

Vous pouvez remplacer le nom de fichier de sortie en spécifiant `/p:MetricsOutputFile=<filename>`. Vous pouvez également obtenir [héritée](#previous-versions) des données de métriques de code en spécifiant `/p:LEGACY_CODE_METRICS_MODE=true`. Exemple :

```shell
C:\source\repos\ClassLibrary3\ClassLibrary3>msbuild /t:Metrics /p:LEGACY_CODE_METRICS_MODE=true /p:MetricsOutputFile="Legacy.xml"
Microsoft (R) Build Engine version 16.0.360-preview+g9781d96883 for .NET Framework
Copyright (C) Microsoft Corporation. All rights reserved.

Build started 1/22/2019 4:31:00 PM.
The "MetricsOutputFile" property is a global property, and cannot be modified.
Project "C:\source\repos\ClassLibrary3\ClassLibrary3\ClassLibrary3.csproj" on node 1 (Metrics target(s))
.
Metrics:
  C:\source\repos\ClassLibrary3\packages\Microsoft.CodeMetrics.2.6.4-ci\build\\..\Metrics.Legacy\Metrics.Legacy.exe /project:C:\source\repos\ClassLibrary3\ClassLibrary3\ClassLibrary3.csproj /out:Legacy.xml
  Loading ClassLibrary3.csproj...
  Computing code metrics for ClassLibrary3.csproj...
  Writing output to 'Legacy.xml'...
  Completed Successfully.
Done Building Project "C:\source\repos\ClassLibrary3\ClassLibrary3\ClassLibrary3.csproj" (Metrics target(s)).

Build succeeded.
    0 Warning(s)
    0 Error(s)
```

### <a name="code-metrics-output"></a>Sortie des métriques de code

La sortie XML générée prend le format suivant :

```xml
<?xml version="1.0" encoding="utf-8"?>
<CodeMetricsReport Version="1.0">
  <Targets>
    <Target Name="ConsoleApp20.csproj">
      <Assembly Name="ConsoleApp20, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null">
        <Metrics>
          <Metric Name="MaintainabilityIndex" Value="100" />
          <Metric Name="CyclomaticComplexity" Value="1" />
          <Metric Name="ClassCoupling" Value="1" />
          <Metric Name="DepthOfInheritance" Value="1" />
          <Metric Name="LinesOfCode" Value="11" />
        </Metrics>
        <Namespaces>
          <Namespace Name="ConsoleApp20">
            <Metrics>
              <Metric Name="MaintainabilityIndex" Value="100" />
              <Metric Name="CyclomaticComplexity" Value="1" />
              <Metric Name="ClassCoupling" Value="1" />
              <Metric Name="DepthOfInheritance" Value="1" />
              <Metric Name="LinesOfCode" Value="11" />
            </Metrics>
            <Types>
              <NamedType Name="Program">
                <Metrics>
                  <Metric Name="MaintainabilityIndex" Value="100" />
                  <Metric Name="CyclomaticComplexity" Value="1" />
                  <Metric Name="ClassCoupling" Value="1" />
                  <Metric Name="DepthOfInheritance" Value="1" />
                  <Metric Name="LinesOfCode" Value="7" />
                </Metrics>
                <Members>
                  <Method Name="void Program.Main(string[] args)" File="C:\source\repos\ConsoleApp20\ConsoleApp20\Program.cs" Line="7">
                    <Metrics>
                      <Metric Name="MaintainabilityIndex" Value="100" />
                      <Metric Name="CyclomaticComplexity" Value="1" />
                      <Metric Name="ClassCoupling" Value="1" />
                      <Metric Name="LinesOfCode" Value="4" />
                    </Metrics>
                  </Method>
                </Members>
              </NamedType>
            </Types>
          </Namespace>
        </Namespaces>
      </Assembly>
    </Target>
  </Targets>
</CodeMetricsReport>
```

### <a name="metricsexe"></a>Metrics.exe

Si vous ne souhaitez pas installer le package NuGet, vous pouvez générer et utiliser le *Metrics.exe* exécutable directement. Pour générer le *Metrics.exe* exécutable :

1. Clone le [dotnet/roslyn-analyzers](https://github.com/dotnet/roslyn-analyzers) dépôt.
2. Ouvrez l’invite de commandes développeur pour Visual Studio en tant qu’administrateur.
3. À partir de la racine de la **roslyn-analyzers** référentiel, exécutez la commande suivante : `Restore.cmd`
4. Accédez au répertoire *src\Tools*.
5. Exécutez la commande suivante pour générer le **Metrics.csproj** projet :

   ```shell
   msbuild /m /v:m /p:Configuration=Release Metrics.csproj
   ```

   Un fichier exécutable nommé *Metrics.exe* est généré dans le *artifacts\bin* répertoire sous la racine de référentiel.

#### <a name="metricsexe-usage"></a>Utilisation de Metrics.exe

Pour exécuter *Metrics.exe*, fournir un projet ou solution et une sortie XML de fichier en tant qu’arguments. Exemple :

```shell
C:\>Metrics.exe /project:ConsoleApp20.csproj /out:report.xml
Loading ConsoleApp20.csproj...
Computing code metrics for ConsoleApp20.csproj...
Writing output to 'report.xml'...
Completed Successfully.
```

#### <a name="legacy-mode"></a>Mode hérité

Vous pouvez choisir de créer *Metrics.exe* dans *mode hérité*. La version en mode hérité de l’outil génère des valeurs de mesures qui sont plus proches à quoi [des versions antérieures de l’outil généré](#previous-versions). En outre, en mode hérité, *Metrics.exe* génère la métrique du code pour le même ensemble de la méthode que les versions précédentes de la métrique du code générés par un outil pour les types. Par exemple, il ne génère des données de métrique du code pour les initialiseurs de champ et propriété. Mode hérité est utile pour descendante compatibilité ou si vous avez le code de vérification de portes en fonction de la métrique du code numéros. La commande pour générer *Metrics.exe* en mode hérité est :

```shell
msbuild /m /v:m /t:rebuild /p:LEGACY_CODE_METRICS_MODE=true Metrics.csproj
```

Pour plus d’informations, consultez [activer la génération de métrique du code en mode hérité](https://github.com/dotnet/roslyn-analyzers/pull/1841).

### <a name="previous-versions"></a>Versions antérieures

Visual Studio 2015 inclut un outil de métriques de code en ligne de commande qui a été appelé également *Metrics.exe*. Cette version précédente de l’outil a fait une analyse binaire, autrement dit, une analyse basée sur l’assembly. La nouvelle *Metrics.exe* outil analyse le code source à la place. Étant donné que la nouvelle *Metrics.exe* outil est les résultats sont différents de ceux générés par l’IDE Visual Studio et par les versions précédentes de la métrique du code en ligne de commande, basée sur le code source *Metrics.exe*.

Le nouvel outil de métriques de code en ligne de commande calcule les mesures même en présence d’erreurs de code source, tant que la solution et le projet peuvent être chargés.

#### <a name="metric-value-differences"></a>Différences de valeur de métrique

Le `LinesOfCode` métrique est plus précis et fiables dans le nouvel outil de métriques de code en ligne de commande. Il est indépendant des différences codegen et ne change pas lorsque le runtime ou un ensemble d’outils est modifiée. Le nouvel outil compte réel de lignes de code, y compris les commentaires et les lignes vides.

Autres métriques telles que `CyclomaticComplexity` et `MaintainabilityIndex` utiliser les formules de mêmes que les versions précédentes de *Metrics.exe*, mais le nouvel outil compte le nombre de `IOperations` (instructions source logique) au lieu d’intermédiaire instructions en langage (il Intermediate). Les numéros sont légèrement différents de ceux générés par l’IDE Visual Studio et par les versions précédentes de *Metrics.exe*.

## <a name="see-also"></a>Voir aussi

- [Utiliser la fenêtre Résultats des métriques de Code](../code-quality/working-with-code-metrics-data.md)
- [Valeurs de métriques de code](../code-quality/code-metrics-values.md)
