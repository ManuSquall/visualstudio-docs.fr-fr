---
title: Générer des métriques de code à partir de l’IDE ou de la ligne de commande
ms.date: 11/02/2018
ms.topic: how-to
helpviewer_keywords:
- code metrics data
- code metrics results
- code metrics [Visual Studio]
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1b254cb2077b748f34958e33dbc456f17df530ce
ms.sourcegitcommit: ed4372bb6f4ae64f1fd712b2b253bf91d9ff96bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/09/2020
ms.locfileid: "89600226"
---
# <a name="how-to-generate-code-metrics-data"></a>Comment : générer des données de métriques du code

Vous pouvez générer des données de métriques du code de trois façons :

- En activant les [analyseurs de qualité du code .net](#net-code-quality-analyzers-code-metrics-rules) et en activant les quatre règles de mesure du code (maintenabilité) qu’il contient.

- En choisissant la commande de menu [ **analyser**les  >  **métriques du code** ](#calculate-code-metrics-menu-command) dans Visual Studio.

- À partir de la [ligne de commande](#command-line-code-metrics) pour les projets C# et Visual Basic.

## <a name="net-code-quality-analyzers-code-metrics-rules"></a>Règles de mesure du code des analyseurs de qualité du code .NET

Les analyseurs de qualité du code .NET incluent plusieurs règles de l' [analyseur](roslyn-analyzers-overview.md) de métrique du code :

- [CA1501](./ca1501.md)
- [CA1502](ca1502.md)
- [CA1505](ca1505.md)
- [CA1506](ca1506.md)

Ces règles sont désactivées par défaut, mais vous pouvez les activer à partir de [**Explorateur de solutions**](use-roslyn-analyzers.md#set-rule-severity-from-solution-explorer) ou dans un fichier d' [ensemble de règles](using-rule-sets-to-group-code-analysis-rules.md) . Par exemple, pour activer la règle CA1502 comme un avertissement, votre fichier. RuleSet doit contenir l’entrée suivante :

```xml
<?xml version="1.0" encoding="utf-8"?>
<RuleSet Name="Rules" Description="Rules" ToolsVersion="16.0">
  <Rules AnalyzerId="Microsoft.CodeQuality.Analyzers" RuleNamespace="Microsoft.CodeQuality.Analyzers">
    <Rule Id="CA1502" Action="Warning" />
  </Rules>
</RuleSet>
```

### <a name="configuration"></a>Configuration

Vous pouvez configurer les seuils auxquels les règles de métriques du code se déclenchent.

1. Créer un fichier texte. Par exemple, vous pouvez le nommer *CodeMetricsConfig.txt*.

2. Ajoutez les seuils souhaités au fichier texte au format suivant :

   ```txt
   CA1502: 10
   ```

   Dans cet exemple, la règle [CA1502](ca1502.md) est configurée pour se déclencher lorsque la complexité cyclomatic d’une méthode est supérieure à 10.

3. Dans la fenêtre **Propriétés** de Visual Studio, ou dans le fichier projet, marquez l’action de génération du fichier de configuration en tant que [**AdditionalFiles**](../ide/build-actions.md#build-action-values). Par exemple :

   ```xml
   <ItemGroup>
     <AdditionalFiles Include="CodeMetricsConfig.txt" />
   </ItemGroup>
   ```

## <a name="calculate-code-metrics-menu-command"></a>Commande de menu calculer la métrique du code

Générez des métriques de code pour un ou tous vos projets ouverts dans l’IDE à l’aide du menu **analyser**les  >  **métriques du code** .

### <a name="generate-code-metrics-results-for-an-entire-solution"></a>Générer les résultats de la métrique du code pour une solution entière

Vous pouvez générer des résultats de métriques du code pour une solution complète de l’une des manières suivantes :

- Dans la barre de menus, sélectionnez **analyser**  >  **calculer la métrique du code**  >  **pour la solution**.

- Dans **Explorateur de solutions**, cliquez avec le bouton droit sur la solution, puis sélectionnez **calculer la métrique du code**.

- Dans la fenêtre résultats de la **métrique du code** , sélectionnez le bouton calculer la métrique du **code pour la solution** .

Les résultats sont générés et la fenêtre résultats de la **métrique du code** s’affiche. Pour afficher les détails des résultats, développez l’arborescence dans la colonne **hiérarchie** .

### <a name="generate-code-metrics-results-for-one-or-more-projects"></a>Générer les résultats de la métrique du code pour un ou plusieurs projets

1. Dans **Explorateur de solutions**, sélectionnez un ou plusieurs projets.

1. Dans la barre de menus, sélectionnez **analyser**  >  **calculer la métrique du code**  >  **pour le ou les projets sélectionnés**.

Les résultats sont générés et la fenêtre résultats de la **métrique du code** s’affiche. Pour afficher les détails des résultats, développez l’arborescence dans la **hiérarchie**.

::: moniker range="vs-2017"

> [!NOTE]
> La commande **calculer la métrique du code** ne fonctionne pas pour les projets .net Core et .NET standard. Pour calculer la métrique du code pour un projet .NET Core ou .NET Standard, vous pouvez :
>
> - Calculez à la place la métrique du code à partir de la [ligne de commande](#command-line-code-metrics)
>
> - Mettre à niveau vers [Visual Studio 2019](https://visualstudio.microsoft.com/downloads)

::: moniker-end

## <a name="command-line-code-metrics"></a>Métriques du code de ligne de commande

Vous pouvez générer des données de métriques du code à partir de la ligne de commande pour les projets C# et Visual Basic pour les applications .NET Framework, .NET Core et .NET Standard. Pour exécuter les métriques du code à partir de la ligne de commande, installez le [package NuGet Microsoft. CodeAnalysis. Metrics](#microsoftcodeanalysismetrics-nuget-package) ou créez le [Metrics.exe](#metricsexe) exécutable vous-même.

### <a name="microsoftcodeanalysismetrics-nuget-package"></a>Package NuGet Microsoft. CodeAnalysis. Metrics

Le moyen le plus simple de générer des données de métriques du code à partir de la ligne de commande consiste à installer le package NuGet [Microsoft. CodeAnalysis. Metrics](https://www.nuget.org/packages/Microsoft.CodeAnalysis.Metrics/) . Une fois le package installé, exécutez `msbuild /t:Metrics` à partir du répertoire qui contient votre fichier projet. Par exemple :

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

Vous pouvez remplacer le nom du fichier de sortie en spécifiant `/p:MetricsOutputFile=<filename>` . Vous pouvez également recevoir des données de métriques du code [hérité](#previous-versions) en spécifiant `/p:LEGACY_CODE_METRICS_MODE=true` . Par exemple :

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

### <a name="code-metrics-output"></a>Sortie de la métrique du code

La sortie XML générée prend le format suivant :

::: moniker range=">=vs-2019"

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
          <Metric Name="SourceLines" Value="11" />
          <Metric Name="ExecutableLines" Value="1" />
        </Metrics>
        <Namespaces>
          <Namespace Name="ConsoleApp20">
            <Metrics>
              <Metric Name="MaintainabilityIndex" Value="100" />
              <Metric Name="CyclomaticComplexity" Value="1" />
              <Metric Name="ClassCoupling" Value="1" />
              <Metric Name="DepthOfInheritance" Value="1" />
              <Metric Name="SourceLines" Value="11" />
              <Metric Name="ExecutableLines" Value="1" />
            </Metrics>
            <Types>
              <NamedType Name="Program">
                <Metrics>
                  <Metric Name="MaintainabilityIndex" Value="100" />
                  <Metric Name="CyclomaticComplexity" Value="1" />
                  <Metric Name="ClassCoupling" Value="1" />
                  <Metric Name="DepthOfInheritance" Value="1" />
                  <Metric Name="SourceLines" Value="7" />
                  <Metric Name="ExecutableLines" Value="1" />
                </Metrics>
                <Members>
                  <Method Name="void Program.Main(string[] args)" File="C:\source\repos\ConsoleApp20\ConsoleApp20\Program.cs" Line="7">
                    <Metrics>
                      <Metric Name="MaintainabilityIndex" Value="100" />
                      <Metric Name="CyclomaticComplexity" Value="1" />
                      <Metric Name="ClassCoupling" Value="1" />
                      <Metric Name="SourceLines" Value="4" />
                      <Metric Name="ExecutableLines" Value="1" />
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

::: moniker-end
::: moniker range="vs-2017"

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

::: moniker-end

### <a name="metricsexe"></a>Metrics.exe

Si vous ne souhaitez pas installer le package NuGet, vous pouvez générer et utiliser directement le *Metrics.exe* exécutable. Pour générer le fichier exécutable *Metrics.exe* :

1. Clonez les [analyseurs dotnet/Roslyn](https://github.com/dotnet/roslyn-analyzers) référentiel.
2. Ouvrez Invite de commandes développeur pour Visual Studio en tant qu’administrateur.
3. À partir de la racine de **Roslyn-Analysis** référentiel, exécutez la commande suivante : `Restore.cmd`
4. Accédez au répertoire *src\Tools*.
5. Exécutez la commande suivante pour générer le projet **Metrics. csproj** :

   ```shell
   msbuild /m /v:m /p:Configuration=Release Metrics.csproj
   ```

   Un fichier exécutable nommé *Metrics.exe* est généré dans le répertoire *artifacts\bin* sous la racine référentiel.

#### <a name="metricsexe-usage"></a>Utilisation de Metrics.exe

Pour exécuter *Metrics.exe*, fournissez un projet ou une solution et un fichier XML de sortie comme arguments. Par exemple :

```shell
C:\>Metrics.exe /project:ConsoleApp20.csproj /out:report.xml
Loading ConsoleApp20.csproj...
Computing code metrics for ConsoleApp20.csproj...
Writing output to 'report.xml'...
Completed Successfully.
```

#### <a name="legacy-mode"></a>Mode hérité

Vous pouvez choisir de générer *Metrics.exe* en *mode hérité*. La version en mode hérité de l’outil génère des valeurs de métriques qui sont plus proches de celles [générées par les anciennes versions de l’outil](#previous-versions). En outre, en mode hérité, *Metrics.exe* génère des métriques de code pour le même jeu de types de méthode que les versions précédentes de l’outil pour lequel des métriques de code ont été générées. Par exemple, il ne génère pas de données de métriques du code pour les initialiseurs de champ et de propriété. Le mode hérité est utile à des fins de compatibilité descendante ou si vous avez des portails d’archivage de code basés sur des numéros de métriques du code. La commande pour générer *Metrics.exe* en mode hérité est :

```shell
msbuild /m /v:m /t:rebuild /p:LEGACY_CODE_METRICS_MODE=true Metrics.csproj
```

Pour plus d’informations, consultez [activer la génération de métriques de code en mode hérité](https://github.com/dotnet/roslyn-analyzers/pull/1841).

### <a name="previous-versions"></a>Versions précédentes

::: moniker range=">=vs-2019"
Visual Studio 2015 inclut un outil de mesure du code de ligne de commande, également appelé *Metrics.exe*. Cette version précédente de l’outil a effectué une analyse binaire, c’est-à-dire une analyse basée sur un assembly. La version la plus récente de l’outil *Metrics.exe* analyse le code source à la place. Étant donné que le plus récent outil de *Metrics.exe* est basé sur le code source, les résultats de la métrique du code de ligne de commande peuvent être différents de ceux générés par l’IDE de Visual Studio et par les versions précédentes de *Metrics.exe*. À compter de Visual Studio 2019, l’IDE de Visual Studio analyse le code source comme l’outil en ligne de commande et les résultats doivent être identiques.

::: moniker-end
::: moniker range="vs-2017"
Visual Studio 2015 inclut un outil de mesure du code de ligne de commande, également appelé *Metrics.exe*. Cette version précédente de l’outil a effectué une analyse binaire, c’est-à-dire une analyse basée sur un assembly. Le nouvel outil de *Metrics.exe* analyse le code source à la place. Étant donné que le nouvel outil de *Metrics.exe* est basé sur le code source, les résultats de la métrique du code de ligne de commande sont différents de ceux générés par l’IDE de Visual Studio et par les versions précédentes de *Metrics.exe*.
::: moniker-end

Le nouvel outil de métriques de code de ligne de commande calcule les métriques même en présence d’erreurs de code source, à condition que la solution et le projet puissent être chargés.

#### <a name="metric-value-differences"></a>Différences de valeur de métrique

::: moniker range=">=vs-2019"
À partir de Visual Studio 2019 version 16,4 et Microsoft. CodeAnalysis. mesures (2.9.5) `SourceLines` , `ExecutableLines` Remplacez la `LinesOfCode` mesure précédente. Pour obtenir une description des nouvelles métriques, consultez valeurs de la [métrique du code](../code-quality/code-metrics-values.md). La `LinesOfCode` métrique est disponible en mode hérité.
::: moniker-end
::: moniker range="vs-2017"
La `LinesOfCode` métrique est plus précise et fiable dans le nouvel outil de métriques de code de ligne de commande. Elle est indépendante des différences de CodeGen et ne change pas lorsque l’ensemble d’outils ou le runtime change. Le nouvel outil compte les lignes de code réelles, y compris les lignes vides et les commentaires.
::: moniker-end

D’autres métriques telles que `CyclomaticComplexity` et `MaintainabilityIndex` utilisent les mêmes formules que les versions précédentes de *Metrics.exe*, mais le nouvel outil compte le nombre d' `IOperations` instructions (source logique) à la place des instructions de langage intermédiaire (il). Les nombres sont légèrement différents de ceux générés par l’IDE de Visual Studio et par les versions précédentes de *Metrics.exe*.

## <a name="see-also"></a>Voir aussi

- [Utiliser la fenêtre résultats de la métrique du code](../code-quality/working-with-code-metrics-data.md)
- [Valeurs de la métrique du code](../code-quality/code-metrics-values.md)