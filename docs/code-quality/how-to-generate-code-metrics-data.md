---
title: Générer la métrique du code à partir de l’IDE ou de la ligne de commande
ms.date: 11/02/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- code metrics data
- code metrics results
- code metrics [Visual Studio]
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 96b74421d638a99823399a0049b712bc6c54c8a9
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53849056"
---
# <a name="how-to-generate-code-metrics-data"></a>Procédure : Générer des données de métrique du code

Vous pouvez générer des résultats de métriques de code pour un ou plusieurs projets ou d’une solution entière. Métrique du code est disponible dans l’environnement de développement interactif Visual Studio (IDE) et, pour C# et les projets Visual Basic, à la ligne de commande.

En outre, vous pouvez installer un [package NuGet](https://dotnet.myget.org/feed/roslyn-analyzers/package/nuget/Microsoft.CodeAnalysis.FxCopAnalyzers/2.6.2-beta2-63202-01) qui inclut quatre métrique du code [analyseur](roslyn-analyzers-overview.md) règles : CA1501 CA1502, CA1505 et CA1506. Ces règles sont désactivées par défaut, mais vous pouvez les activer à partir de **l’Explorateur de solutions** ou dans un [ensemble de règles](using-rule-sets-to-group-code-analysis-rules.md) fichier.

## <a name="visual-studio-ide-code-metrics"></a>Métrique du code Visual Studio IDE

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

## <a name="command-line-code-metrics"></a>Métrique du code en ligne de commande

Vous pouvez générer des données de métrique du code à partir de la ligne de commande pour C# et projets Visual Basic pour applications .NET Framework, .NET Core et .NET Standard. Les outils de métriques de code de ligne de commande est appelée *Metrics.exe*.

Pour obtenir le *Metrics.exe* exécutable, vous devez [générer vous-même](#generate-the-executable). Dans un avenir proche, un [version publiée de *Metrics.exe* sera disponible](https://github.com/dotnet/roslyn-analyzers/issues/1756) afin que vous n’êtes pas obligé de créer vous-même.

### <a name="generate-the-executable"></a>Générer le fichier exécutable

Pour générer le fichier exécutable *Metrics.exe*, procédez comme suit :

1. Clone le [dotnet/roslyn-analyzers](https://github.com/dotnet/roslyn-analyzers) dépôt.
2. Ouvrez l’invite de commandes développeur pour Visual Studio en tant qu’administrateur.
3. À partir de la racine de la **roslyn-analyzers** référentiel, exécutez la commande suivante : `Restore.cmd`
4. Accédez au répertoire *src\Tools*.
5. Exécutez la commande suivante pour générer le **Metrics.csproj** projet :

   ```shell
   msbuild /m /v:m /p:Configuration=Release Metrics.csproj
   ```

   Un fichier exécutable nommé *Metrics.exe* est généré dans le *artifacts\bin* répertoire sous la racine de référentiel.

   > [!TIP]
   > Pour générer *Metrics.exe* dans [mode hérité](#legacy-mode), exécutez la commande suivante :
   >
   > ```shell
   > msbuild /m /v:m /t:rebuild /p:LEGACY_CODE_METRICS_MODE=true Metrics.csproj
   > ```

### <a name="usage"></a>Utilisation

Pour exécuter *Metrics.exe*, fournir un projet ou solution et une sortie XML de fichier en tant qu’arguments. Exemple :

```shell
C:\>Metrics.exe /project:ConsoleApp20.csproj /out:report.xml
Loading ConsoleApp20.csproj...
Computing code metrics for ConsoleApp20.csproj...
Writing output to 'report.xml'...
Completed Successfully.
```

### <a name="output"></a>Sortie

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
                  <Method Name="void Program.Main(string[] args)" File="C:\Users\mavasani\source\repos\ConsoleApp20\ConsoleApp20\Program.cs" Line="7">
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

### <a name="tool-differences"></a>Différences d’outil

Les versions précédentes de Visual Studio, notamment Visual Studio 2015, incluaient un outil de métriques de code en ligne de commande appelé *Metrics.exe*. Cette version précédente de l’outil a fait une analyse binaire, autrement dit, une analyse basée sur l’assembly. Le nouvel outil d’analyse de code source à la place. Étant donné que la nouvelle *Metrics.exe* est source de code, les résultats sont différents de ce qui est généré par les versions précédentes de *Metrics.exe* et l’IDE de Visual Studio 2017.

La nouvelle *Metrics.exe* outil peut calculer les métriques même en présence d’erreurs de code source, tant que la solution et le projet peuvent être chargés.

#### <a name="metric-value-differences"></a>Différences de valeur de métrique

Le `LinesOfCode` métrique est plus précis et fiables dans le nouveau *Metrics.exe*. Il est indépendant des différences codegen et ne change pas lorsque le runtime ou un ensemble d’outils est modifiée. La nouvelle *Metrics.exe* le nombre réel de lignes de code, y compris les lignes vides et les commentaires.

Autres métriques telles que `CyclomaticComplexity` et `MaintainabilityIndex` utiliser les formules de mêmes que les versions précédentes de *Metrics.exe*, mais le nouveau *Metrics.exe* compte le nombre de `IOperations` (logique instructions de la source) au lieu des instructions de langage intermédiaire (IL). Les numéros sera légèrement différentes des versions précédentes de *Metrics.exe* et dans les résultats de métriques de code IDE de Visual Studio 2017.

### <a name="legacy-mode"></a>Mode hérité

Vous pouvez également choisir de générer *Metrics.exe* dans *mode hérité*. La version en mode hérité de l’outil génère des valeurs de mesures qui sont plus proches pour les versions antérieures de l’outil généré. En outre, en mode hérité, *Metrics.exe* génère la métrique du code pour le même ensemble de la méthode que les versions précédentes de la métrique du code générés par un outil pour les types. Par exemple, il ne génère des données de métrique du code pour les initialiseurs de champ et propriété. Mode hérité est utile pour descendante compatibilité ou si vous avez le code de vérification de portes en fonction de la métrique du code numéros. La commande pour générer *Metrics.exe* en mode hérité est :

```shell
msbuild /m /v:m /t:rebuild /p:LEGACY_CODE_METRICS_MODE=true Metrics.csproj
```

Pour plus d’informations, consultez [activer la génération de métrique du code en mode hérité](https://github.com/dotnet/roslyn-analyzers/pull/1841).

## <a name="see-also"></a>Voir aussi

- [Utiliser la fenêtre Résultats des métriques de Code](../code-quality/working-with-code-metrics-data.md)
- [Valeurs de métriques de code](../code-quality/code-metrics-values.md)
