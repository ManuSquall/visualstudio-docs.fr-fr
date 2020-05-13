---
title: Générer des mesures de code à partir de l’IDE ou de la ligne de commande
ms.date: 11/02/2018
ms.topic: conceptual
helpviewer_keywords:
- code metrics data
- code metrics results
- code metrics [Visual Studio]
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1abae26ed8a5e5db74f7b0d04db66d9d99930d5c
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649321"
---
# <a name="how-to-generate-code-metrics-data"></a>Comment : Générer des données de métriques de code

Vous pouvez générer des données de métriques de code de trois façons :

- En installant [des analyseurs FxCop](#fxcop-analyzers-code-metrics-rules) et en permettant les quatre règles de code (maintenabilité) qu’il contient.

- En choisissant la commande de menu [ **Analyze** > Calculate Code Metrics](#calculate-code-metrics-menu-command) au sein de Visual Studio.

- De la [ligne de commande](#command-line-code-metrics) pour les projets C et Visual Basic.

## <a name="fxcop-analyzers-code-metrics-rules"></a>FxCop analyseurs code règles de métriques

Le [paquet FxCopAnalyzers NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) comprend plusieurs règles [d’analyse de](roslyn-analyzers-overview.md) mesures de code :

- [CA1501](ca1501-avoid-excessive-inheritance.md)
- [CA1502](ca1502.md)
- [CA1505](ca1505.md)
- [CA1506](ca1506.md)

Ces règles sont désactivées par défaut, mais vous pouvez les activer à partir de [**Solution Explorer**](use-roslyn-analyzers.md#set-rule-severity-from-solution-explorer) ou dans un fichier [défini par les règles.](using-rule-sets-to-group-code-analysis-rules.md) Par exemple, pour activer la règle CA1502 comme avertissement, votre fichier .ruleset contiendrait l’entrée suivante :

```xml
<?xml version="1.0" encoding="utf-8"?>
<RuleSet Name="Rules" Description="Rules" ToolsVersion="16.0">
  <Rules AnalyzerId="Microsoft.CodeQuality.Analyzers" RuleNamespace="Microsoft.CodeQuality.Analyzers">
    <Rule Id="CA1502" Action="Warning" />
  </Rules>
</RuleSet>
```

### <a name="configuration"></a>Configuration

Vous pouvez configurer les seuils auxquels le code mesure les règles dans le feu de l’analyseur FxCop.

1. Créer un fichier texte. À titre d’exemple, vous pouvez l’appeler *CodeMetricsConfig.txt*.

2. Ajoutez les seuils souhaités au fichier texte dans le format suivant :

   ```txt
   CA1502: 10
   ```

   Dans cet exemple, la règle [CA1502](ca1502.md) est configurée pour tirer lorsque la complexité cyclomatique d’une méthode est supérieure à 10.

3. Dans la fenêtre **Propriétés** de Visual Studio, ou dans le fichier de projet, marquer l’action de construction du fichier de configuration comme [**AdditionalFiles**](../ide/build-actions.md#build-action-values). Par exemple :

   ```xml
   <ItemGroup>
     <AdditionalFiles Include="CodeMetricsConfig.txt" />
   </ItemGroup>
   ```

## <a name="calculate-code-metrics-menu-command"></a>Calculer la commande du menu Code Metrics

Générez des mesures de code pour un ou la totalité de vos projets ouverts dans l’IDE en utilisant le menu **Analyze** > **Calculate Code Metrics.**

### <a name="generate-code-metrics-results-for-an-entire-solution"></a>Générer des résultats de mesures de code pour toute une solution

Vous pouvez générer des résultats de mesures de code pour une solution entière de toutes les manières suivantes :

- De la barre de menu, choisissez **Analysez les** > **mesures** > de code de calcul**pour la solution**.

- Dans **Solution Explorer**, cliquez à droite sur la solution, puis choisissez **Calculatez les paramètres de code**.

- Dans la fenêtre **de résultats de code Metrics,** choisissez les mesures de code de calcul pour le bouton **Solution.**

Les résultats sont générés et la fenêtre **de résultats de mesures de code** est affichée. Pour afficher les détails des résultats, étendre l’arbre dans la colonne **Hiérarchie.**

### <a name="generate-code-metrics-results-for-one-or-more-projects"></a>Générer des résultats de mesures de code pour un ou plusieurs projets

1. Dans **Solution Explorer**, sélectionnez un ou plusieurs projets.

1. À partir de la barre de menu, choisissez **Analysez les** > **mesures** > de code de calcul**pour le projet sélectionné.**

Les résultats sont générés et la fenêtre **de résultats de mesures de code** est affichée. Pour voir les détails des résultats, étendre l’arbre dans la **Hiérarchie**.

::: moniker range="vs-2017"

> [!NOTE]
> La commande **Calculate Code Metrics** ne fonctionne pas pour les projets .NET Core et .NET Standard. Pour calculer les paramètres de code pour un projet .NET Core ou .NET Standard, vous pouvez :
>
> - Calculer les mesures de code de la ligne de [commande](#command-line-code-metrics) à la place
>
> - Mise à niveau vers [Visual Studio 2019](https://visualstudio.microsoft.com/downloads)

::: moniker-end

## <a name="command-line-code-metrics"></a>Mesures de code de commande-ligne

Vous pouvez générer des données de métriques de code à partir de la ligne de commande pour les projets C et Visual Basic pour les applications .NET Framework, .NET Core et .NET Standard. Pour exécuter les mesures de code à partir de la ligne de commande, installez le [paquet Microsoft.CodeAnalysis.Metrics NuGet](#microsoftcodeanalysismetrics-nuget-package) ou créez le [Metrics.exe exe exe exe exe exe exe exe](#metricsexe) exécutant vous-même.

### <a name="microsoftcodeanalysismetrics-nuget-package"></a>Microsoft.CodeAnalysis.Metrics NuGet package

La façon la plus simple de générer des données de mesures de code à partir de la ligne de commande est d’installer le paquet [Microsoft.CodeAnalysis.Metrics](https://www.nuget.org/packages/Microsoft.CodeAnalysis.Metrics/) NuGet. Après avoir installé le paquet, exécutez `msbuild /t:Metrics` à partir de l’annuaire qui contient votre fichier de projet. Par exemple :

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

Vous pouvez remplacer le nom du `/p:MetricsOutputFile=<filename>`fichier de sortie en spécifiant . Vous pouvez également obtenir des données de `/p:LEGACY_CODE_METRICS_MODE=true`métriques de code de type [héritage](#previous-versions) en spécifiant . Par exemple :

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

### <a name="code-metrics-output"></a>Sortie de mesures du code

La sortie XML générée prend le format suivant :

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

### <a name="metricsexe"></a>Metrics.exe (en)

Si vous ne souhaitez pas installer le paquet NuGet, vous pouvez générer et utiliser le *Metrics.exe exe exécutable* directement. Pour générer le *Metrics.exe exe exe exe exe exe exécutable:*

1. Clonez le [repo dotnet/roslyn-analyseurs.](https://github.com/dotnet/roslyn-analyzers)
2. Open Developer Command Prompt for Visual Studio en tant qu’administrateur.
3. De la racine de la **répo roslyn-analyseurs,** exécutez la commande suivante :`Restore.cmd`
4. Changez d’annuaire pour *src-Tools*.
5. Exécutez la commande suivante pour construire le projet **Metrics.csproj** :

   ```shell
   msbuild /m /v:m /p:Configuration=Release Metrics.csproj
   ```

   Un exécutable nommé *Metrics.exe* est généré dans le répertoire *des artefacts-bin* sous la racine de pension.

#### <a name="metricsexe-usage"></a>Metrics.exe utilisation

Pour exécuter *Metrics.exe*, fournir un projet ou une solution et un fichier de sortie XML comme arguments. Par exemple :

```shell
C:\>Metrics.exe /project:ConsoleApp20.csproj /out:report.xml
Loading ConsoleApp20.csproj...
Computing code metrics for ConsoleApp20.csproj...
Writing output to 'report.xml'...
Completed Successfully.
```

#### <a name="legacy-mode"></a>Mode héritage

Vous pouvez choisir de construire *Metrics.exe* en *mode héritage*. La version mode héritée de l’outil génère des valeurs métriques qui sont plus proches de ce que [les anciennes versions de l’outil généré .](#previous-versions) En outre, en mode héritage, *Metrics.exe* génère des mesures de code pour le même ensemble de types de méthode que les versions précédentes de l’outil généré des mesures de code pour. Par exemple, il ne génère pas de données de mesures de code pour les initialisateurs de champ et de propriété. Le mode Héritage est utile pour la compatibilité vers l’arrière ou si vous avez des portes d’enregistrement de code basées sur les numéros de mesures de code. La commande pour construire *Metrics.exe* en mode héritage est :

```shell
msbuild /m /v:m /t:rebuild /p:LEGACY_CODE_METRICS_MODE=true Metrics.csproj
```

Pour plus d’informations, voir [Active générer des mesures de code en mode héritage](https://github.com/dotnet/roslyn-analyzers/pull/1841).

### <a name="previous-versions"></a>Versions précédentes

::: moniker range=">=vs-2019"
Visual Studio 2015 comprenait un outil de métriques de code de commande qui a également été appelé *Metrics.exe*. Cette version précédente de l’outil a fait une analyse binaire, c’est-à-dire une analyse basée sur l’assemblage. La nouvelle version de l’outil *Metrics.exe* analyse plutôt le code source. Parce que le nouvel outil *Metrics.exe* est basé sur le code source, les résultats de mesures de code de commande peuvent être différents de ceux générés par l’IDE Visual Studio et par les versions précédentes de *Metrics.exe*. À partir de Visual Studio 2019, le Visual Studio IDE analyse le code source comme l’outil de ligne de commande et les résultats devraient être les mêmes.

::: moniker-end
::: moniker range="vs-2017"
Visual Studio 2015 comprenait un outil de métriques de code de commande qui a également été appelé *Metrics.exe*. Cette version précédente de l’outil a fait une analyse binaire, c’est-à-dire une analyse basée sur l’assemblage. Le nouvel outil *Metrics.exe* analyse plutôt le code source. Parce que le nouvel outil *Metrics.exe* est basé sur le code source, les résultats de mesures de code de commande sont différents de ceux générés par l’IDE Visual Studio et par les versions précédentes de *Metrics.exe*.
::: moniker-end

Le nouvel outil de métriques de code de commande calcule des mesures même en présence d’erreurs de code source, tant que la solution et le projet peuvent être chargés.

#### <a name="metric-value-differences"></a>Différences de valeur métriques

::: moniker range=">=vs-2019"
A partir de Visual Studio 2019 version 16.4 et Microsoft.CodeAnalysis.Metics `SourceLines` `ExecutableLines` (2.9.5), et remplacer la mesure précédente. `LinesOfCode` Pour les descriptions des nouvelles mesures, voir les [valeurs de mesures du Code](../code-quality/code-metrics-values.md). La `LinesOfCode` mesure est disponible en mode héritage.
::: moniker-end
::: moniker range="vs-2017"
La `LinesOfCode` mesure est plus précise et plus fiable dans le nouvel outil de métriques de code de commande. Il est indépendant de toute différence de codegen et ne change pas lorsque la salle d’outils ou le temps d’exécution change. Le nouvel outil compte les lignes de code réelles, y compris les lignes et commentaires vierges.
::: moniker-end

D’autres mesures `CyclomaticComplexity` `MaintainabilityIndex` telles que et utiliser les mêmes formules que les versions précédentes `IOperations` de *Metrics.exe*, mais le nouvel outil compte le nombre d’instructions (source logique) au lieu de la langue intermédiaire (IL) instructions. Les chiffres seront légèrement différents de ceux générés par le Visual Studio IDE et par les versions précédentes de *Metrics.exe*.

## <a name="see-also"></a>Voir aussi

- [Utilisez la fenêtre de résultats de métriques de code](../code-quality/working-with-code-metrics-data.md)
- [Valeurs de métriques de code](../code-quality/code-metrics-values.md)
