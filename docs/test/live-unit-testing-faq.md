---
title: FAQ Live Unit Testing
description: Passez en revue ces Live Unit Testing Forum aux questions, y compris les frameworks, la configuration et la personnalisation pris en charge.
ms.custom: SEO-VS-2020
ms.date: 10/03/2017
ms.topic: conceptual
helpviewer_keywords:
- Live Unit Testing FAQ
author: mikejo5000
ms.author: mikejo
ms.workload:
- dotnet
ms.openlocfilehash: bb2c9a4cae25b388d5817b04ff54f6e6443b2f44
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96329287"
---
# <a name="live-unit-testing-frequently-asked-questions"></a>Questions fréquentes (FAQ) sur Live Unit Testing

## <a name="supported-frameworks"></a>Frameworks pris en charge

**Quels sont les frameworks de tests pris en charge par Live Unit Testing et quelles sont les versions minimales prises en charge ?**

Live Unit Testing fonctionne avec les trois frameworks de tests unitaires populaires listés dans le tableau suivant. La version minimale prise en charge des adaptateurs et des frameworks est également listée dans le tableau. Les frameworks de tests unitaires sont tous disponibles dans NuGet.org.

|Framework de test  |Version minimale de l’adaptateur Visual Studio  |Version minimale du framework  |
|---------|---------|---------|
|xUnit.net |xunit.runner.visualstudio version 2.2.0-beta3-build1187 |xunit 1.9.2 |
|NUnit |NUnit3TestAdapter version 3.7.0 |NUnit version 3.5.0 |
|MSTest |MSTest.TestAdapter 1.1.4-preview |MSTest.TestFramework 1.0.5-preview |

Si vous avez des projets de test basés sur MSTest plus anciens qui référencent `Microsoft.VisualStudio.QualityTools.UnitTestFramework` et que vous ne souhaitez pas passer à la version plus récente des packages NuGet MSTest, effectuez une mise à niveau vers Visual studio 2019 ou Visual studio 2017.

Dans certains cas, vous devez peut-être restaurer explicitement les packages NuGet référencés par les projets dans la solution pour que Live Unit Testing fonctionne. Vous pouvez restaurer les packages en procédant à une génération explicite de la solution (sélectionnez **générer**  >  **reconstruire la solution** dans le menu Visual Studio de niveau supérieur) ou en cliquant avec le bouton droit sur la solution et en sélectionnant **restaurer les packages NuGet** avant d’activer les tests d’unités vivantes.

## <a name="net-core-support"></a>Support de .NET Core

**Live Unit Testing fonctionne-il avec .NET Core ?**

Oui. Live Unit Testing fonctionne avec.NET Core et .NET Framework.

## <a name="configuration"></a>Configuration

**Pourquoi Live Unit Testing ne fonctionne-t-il pas quand je l’active ?**

La fenêtre sortie (lorsque la liste déroulante Live Unit Testing est sélectionnée) doit vous indiquer la raison pour laquelle Live Unit Testing ne fonctionne pas. Live Unit Testing Test peut ne pas fonctionner pour les raisons suivantes :

- Si les packages NuGet référencés par les projets de la solution n’ont pas été restaurés, Live Unit Testing ne peut pas fonctionner. Pour résoudre ce problème, effectuez une build explicite de la solution ou restaurez les packages NuGet de la solution avant d’activer Live Unit Testing.

- Si vous utilisez des tests basés sur MSTest dans vos projets, veillez à supprimer la référence à `Microsoft.VisualStudio.QualityTools.UnitTestFramework` et à ajouter des références aux derniers packages NuGet MSTest, `MSTest.TestAdapter` (version 1.1.11 au minimum requise) et `MSTest.TestFramework` (version 1.1.11 au minimum requise). Pour plus d’informations, consultez la section « Frameworks de test pris en charge » de l’article [Utiliser Live Unit Testing dans Visual Studio](live-unit-testing.md#supported-test-frameworks).

- Au moins un projet de votre solution doit contenir une référence NuGet ou une référence directe au framework de tests xUnit, NUnit ou MSTest. Ce projet doit également faire référence au package NuGet des adaptateurs de test Visual Studio correspondants. L’adaptateur de test Visual Studio peut également être référencé via un fichier *.runsettings*. Le fichier *.runsettings* doit avoir une entrée semblable à ce qui est contenu dans l’exemple suivant :

```xml
<RunSettings>
    <RunConfiguration>
          <TestAdaptersPaths>path-to-your-test-adapter</TestAdaptersPaths>
     </RunConfiguration>
</RunSettings>
```

## <a name="incorrect-coverage-after-upgrade"></a>Couverture incorrecte après la mise à niveau

**Pourquoi est-ce que Live Unit Testing indique une couverture incorrecte après la mise à niveau de l’adaptateur de test référencé dans vos projets Visual Studio vers la version prise en charge ?**

- Si plusieurs projets de la solution font référence au package de l’adaptateur de test NuGet, chacun d’eux doit être mis à niveau vers la version prise en charge.

- Assurez-vous que le fichier MSBuild *. props* importé à partir du package de l’adaptateur de test est également correctement mis à jour. Vérifiez la version/le chemin du package NuGet de l’importation, qui figure généralement vers le haut du fichier projet, comme suit :

   ```xml
    <Import Project="..\packages\xunit.runner.visualstudio.2.2.0\build\net20\xunit.runner.visualstudio.props" Condition="Exists('..\packages\xunit.runner.visualstudio.2.2.0\build\net20\xunit.runner.visualstudio.props')" />
   ```

## <a name="customize-builds"></a>Personnaliser des builds

**Est-il possible de personnaliser les builds Live Unit Testing ?**

Si votre solution nécessite des étapes personnalisées pour la génération de l’instrumentation (Live Unit Testing) qui ne sont pas requises pour la build « normale » non instrumentée, vous pouvez ajouter du code à vos fichiers projet ou *. targets* qui vérifient la `BuildingForLiveUnitTesting` propriété et exécute des étapes de génération/publication personnalisées. Vous pouvez également choisir de supprimer certaines étapes de génération (telles que la publication ou la génération de packages) ou d’ajouter des étapes de génération (par exemple, la copie des composants requis) pour une build Live Unit Testing basée sur cette propriété de projet. Le fait de personnaliser votre build avec cette propriété ne modifie pas votre build et impacte uniquement les builds Live Unit Testing.

Par exemple, vous pouvez avoir une cible qui génère des packages NuGet dans le cadre d’une build standard. Vous préférerez sans doute éviter que des packages NuGet soient générés après chaque modification que vous effectuez. Ainsi, vous pouvez désactiver cette cible dans la build Live Unit Testing en procédant comme suit :  

```xml
<Target Name="GenerateNuGetPackages" BeforeTargets="AfterBuild" Condition="'$(BuildingForLiveUnitTesting)' != 'true'">
    <Exec Command='"$(MSBuildThisFileDirectory)..\tools\GenPac" '/>
</Target>
```

## <a name="error-messages-with-outputpath-outdir-or-intermediateoutputpath"></a>Messages d’erreur \<OutputPath> avec \<OutDir> ou \<IntermediateOutputPath>

**Pourquoi reçois-je l’erreur suivante quand Live Unit Testing tente de générer ma solution : «... semble être défini de manière inconditionnelle `<OutputPath>` ou `<OutDir>` . Live Unit Testing n’exécutera pas de tests à partir de l’assembly de sortie» ?**

Vous pouvez obtenir cette erreur si le processus de génération de votre solution a une logique personnalisée qui spécifie où les binaires doivent être générés. Par défaut, l’emplacement de vos fichiers binaires dépend de `<OutputPath>` , ou, ainsi que de `<OutDir>` ou de `<IntermediateOutputPath>` `<BaseOutputPath>` `<BaseIntermediateOutputPath>` .

Live Unit Testing Substitue ces variables pour s’assurer que les artefacts de build sont déposés dans un dossier d’artefacts Live Unit Testing et échouent si votre processus de génération remplace également ces variables.

Il existe deux approches principales pour effectuer la génération de Live Unit Testing. Pour faciliter la configuration des builds, vous pouvez baser vos chemins de sortie sur `<BaseIntermediateOutputPath>` . Pour les configurations plus complexes, vous pouvez baser vos chemins de sortie sur `<LiveUnitTestingBuildRootPath>` .

### <a name="overriding-outputpathintermediateoutputpath-conditionally-based-on-baseoutputpath-baseintermediateoutputpath"></a>Remplacement `<OutputPath>` / `<IntermediateOutputPath>` conditionnel basé sur `<BaseOutputPath>` / `<BaseIntermediateOutputPath>` .

> [!NOTE]
> Pour utiliser cette approche, chaque projet doit pouvoir être généré indépendamment l’un de l’autre. Il n’existe pas d’artefacts de référence de projet à partir d’un autre projet pendant la génération. Aucun projet ne charge dynamiquement les assemblys à partir d’un autre projet pendant l’exécution (par exemple `Assembly.Loadfile("..\..\Project2\Release\Project2.dll")` , appel).

Pendant la génération, Live Unit testing remplace automatiquement les `<BaseOutputPath>` / `<BaseIntermediateOutputPath>` variables pour cibler le dossier artefacts Live Unit testing.

Par exemple, si votre build remplace le <OutputPath> comme indiqué ci-dessous :

```xml
<Project>
  <PropertyGroup>
    <OutputPath>$(SolutionDir)Artifacts\$(Configuration)\bin\$(MSBuildProjectName)</OutputPath>
  </PropertyGroup>
</Project>
```

Ensuite, vous pouvez le remplacer par le code XML suivant :

```xml
<Project>
  <PropertyGroup>
    <BaseOutputPath Condition="'$(BaseOutputPath)' == ''">$(SolutionDir)Artifacts\$(Configuration)\bin\$(MSBuildProjectName)\</BaseOutputPath>
    <OutputPath Condition="'$(OutputPath)' == ''">$(BaseOutputPath)</OutputPath>
  </PropertyGroup>
</Project>
```

Vous avez ainsi la garantie que `<OutputPath>` se trouvera dans le dossier `<BaseOutputPath>`.

Ne remplacez pas `<OutDir>` directement dans votre processus de génération ; remplacez plutôt `<OutputPath>` pour placer les artéfacts de build à un emplacement spécifique.

### <a name="overriding-your-properties-based-on-the-liveunittestingbuildrootpath-property"></a>Substitution de vos propriétés en fonction de la `<LiveUnitTestingBuildRootPath>` propriété.

> [!NOTE]
> Dans cette approche, vous devez faire attention aux fichiers ajoutés dans le dossier artefacts qui ne sont pas générés pendant la génération. L’exemple ci-dessous montre comment placer le dossier Packages sous artefacts. Étant donné que le contenu de ce dossier n’est pas généré au cours de la génération, la propriété MSBuild ne **doit pas être modifiée**.

Pendant une génération de Live Unit Testing, la `<LiveUnitTestingBuildRootPath>` propriété est définie sur l’emplacement de Live Unit testing dossier artefacts.

Supposons, par exemple, que la structure de votre projet soit indiquée ici.

```
.vs\...\lut\0\b
artifacts\{binlog,obj,bin,nupkg,testresults,packages}
src\{proj1,proj2,proj3}
tests\{testproj1,testproj2}
Solution.sln
```
Pendant la génération de Live Unit Testing, la `<LiveUnitTestingBuildRootPath>` propriété est définie sur le chemin d’accès complet de `.vs\...\lut\0\b` . Si le projet définit la `<ArtifactsRoot>` propriété qui est mappée au répertoire de la solution, vous pouvez mettre à jour le projet MSBuild comme suit :

```xml
<Project>
    <PropertyGroup Condition="'$(LiveUnitTestingBuildRootPath)' == ''">
        <SolutionDir>$([MSBuild]::GetDirectoryNameOfFileAbove(`$(MSBuildProjectDirectory)`, `YOUR_SOLUTION_NAME.sln`))\</SolutionDir>

        <ArtifactsRoot>Artifacts\</ArtifactsRoot>
        <ArtifactsRoot Condition="'$(LiveUnitTestingBuildRootPath)' != ''">$(LiveUnitTestingBuildRootPath)</ArtifactsRoot>
    </PropertyGroup>

    <PropertyGroup>
        <BinLogPath>$(ArtifactsRoot)\BinLog</BinLogPath>
        <ObjPath>$(ArtifactsRoot)\Obj</ObjPath>
        <BinPath>$(ArtifactsRoot)\Bin</BinPath>
        <NupkgPath>$(ArtifactsRoot)\Nupkg</NupkgPath>
        <TestResultsPath>$(ArtifactsRoot)\TestResults</TestResultsPath>

        <!-- Note: Given that a build doesn't generate packages, the path should be relative to the solution dir, rather than artifacts root, which will change during a Live Unit Testing build. -->
        <PackagesPath>$(SolutionDir)\artifacts\packages</PackagesPath>
    </PropertyGroup>
</Project>
```

## <a name="build-artifact-location"></a>Créer l’emplacement de l’artefact

**Je souhaite que les artefacts d’un Live Unit Testing Build s’affichent à un emplacement spécifique au lieu de l’emplacement par défaut sous le dossier *. vs* . Comment puis-je modifier cela ?**

Définissez la variable d’environnement de niveau utilisateur `LiveUnitTesting_BuildRoot` sur le chemin d’accès où vous souhaitez déposer les artéfacts de build Live Unit Testing. 

## <a name="test-explorer-versus-live-unit-testing"></a>Explorateur de tests et Live Unit Testing

**En quoi les tests exécutés dans la fenêtre de l’Explorateur de tests sont-ils différents de ceux exécutés dans Live Unit Testing ?**

Il existe plusieurs différences :

- L’exécution ou le débogage des tests à partir de la fenêtre de l' **Explorateur de tests** exécute des binaires standard, tandis que Live Unit testing exécute des fichiers binaires instrumentés. Si vous souhaitez déboguer des fichiers binaires instrumentés, l’ajout d’un appel de méthode [Debugger.Launch](xref:System.Diagnostics.Debugger.Launch) dans votre méthode de test a pour effet de lancer le débogueur à chaque exécution de la méthode (y compris lorsqu’elle est exécutée par Live Unit Testing), après quoi vous pouvez attacher et déboguer le fichier binaire instrumenté. Nous espérons cependant que l’instrumentation soit pour vous parfaitement transparente dans la plupart des scénarios utilisateur, et que vous n’ayez pas besoin de déboguer de fichiers binaires instrumentés.

- Live Unit Testing ne crée pas de domaine d’application pour exécuter des tests, mais les tests exécutés à partir de la fenêtre de l' **Explorateur de tests** créent un nouveau domaine d’application.

- Live Unit Testing exécute des tests dans chaque assembly de test de manière séquentielle. Dans l' **Explorateur de tests**, vous pouvez choisir d’exécuter plusieurs tests en parallèle.

- L' **Explorateur de tests** exécute les tests dans un thread cloisonné (STA) par défaut, tandis que Live Unit testing exécute les tests dans un cloisonnement MULTITHREAD (MTA). Pour exécuter les tests MSTest dans un STA dans Live Unit Testing, complétez la méthode de test ou la classe de conteneur avec l’attribut `<STATestMethod>` ou `<STATestClass>` qui se trouve dans le package NuGet `MSTest.STAExtensions 1.0.3-beta`. Pour NUnit, complétez la méthode de test avec l’attribut `<RequiresThread(ApartmentState.STA)>`, et pour xUnit, avec l’attribut `<STAFact>`.

## <a name="exclude-tests"></a>Exclure des tests

**Comment exclure des tests de Live Unit Testing ?**

Consultez la section « Inclure et exclure des projets de test et des méthodes de test » de l’article [Utiliser Live Unit Testing dans Visual Studio Enterprise Edition](live-unit-testing.md#include-and-exclude-test-projects-and-test-methods) pour connaître les paramètres spécifiques à l’utilisateur. L’inclusion et l’exclusion de tests s’avèrent utiles quand vous souhaitez exécuter un ensemble spécifique de tests pour une session de modification particulière ou pour conserver vos préférences personnelles.

Pour les paramètres spécifiques à la solution, vous pouvez, à l’aide d’un programme, appliquer l’attribut <xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute?displayProperty=fullName> pour empêcher que des méthodes, des propriétés, des classes ou des structures soient instrumentées par Live Unit Testing. En outre, vous pouvez également définir la propriété `<ExcludeFromCodeCoverage>` sur `true` dans votre fichier projet pour exclure de l’instrumentation l’ensemble du projet. Live Unit Testing continue d’exécuter les tests qui n’ont pas été instrumentés, mais leur couverture n’est pas affichée.

Vous pouvez également vérifier si `Microsoft.CodeAnalysis.LiveUnitTesting.Runtime` est chargé dans le domaine d’application actuel et désactiver les tests selon le résultat. Par exemple, vous pouvez procéder de cette manière avec xUnit :

```csharp
[ExcludeFromCodeCoverage]
public class SkipLiveFactAttribute : FactAttribute
{
   private static bool s_lutRuntimeLoaded = AppDomain.CurrentDomain.GetAssemblies().Any(a => a.GetName().Name ==
                                            "Microsoft.CodeAnalysis.LiveUnitTesting.Runtime");
   public override string Skip => s_lutRuntimeLoaded ? "Test excluded from Live Unit Testing" : "";
}

public class Class1
{
   [SkipLiveFact]
   public void F()
   {
      Assert.True(true);
   }
}
```

::: moniker range="vs-2017"

## <a name="win32-pe-headers"></a>En-têtes PE Win32

**Pourquoi les en-têtes PE Win32 sont-ils différents dans les assemblys instrumentés générés par Live Unit Testing ?**

Ce problème est résolu et n’existe pas dans Visual Studio 2017 versions 15.3 et ultérieures.

Pour les précédentes versions de Visual Studio 2017, il existe un bogue connu qui peut empêcher les builds Live Unit Testing d’incorporer les données de l’en-tête PE Win32 suivantes :

- Version de fichier (spécifiée par @System.Reflection.AssemblyFileVersionAttribute dans le code).

- Icône Win32 (spécifiée par `/win32icon:` sur la ligne de commande).

- Manifeste Win32 (spécifié par `/win32manifest:` sur la ligne de commande).

Les tests qui reposent sur ces valeurs peuvent échouer lorsqu’ils sont exécutés par Live Unit Testing.

::: moniker-end

## <a name="continuous-builds"></a>Builds en continu

**Pourquoi Live Unit Testing ne cesse-t-il de générer ma solution, même si je n’y apporte aucune modification ?**

Votre solution peut être générée même si vous n’apportez pas de modifications si le processus de génération génère du code source qui fait partie de la solution elle-même, et si les entrées et sorties appropriées ne sont pas spécifiées pour vos fichiers cibles de génération. Les cibles doivent disposer d’une liste d’entrées et de sorties afin que MSBuild puisse effectuer les contrôles à jour appropriés et déterminer si une nouvelle build est requise.

Live Unit Testing démarre une build chaque fois qu’il détecte une modification des fichiers sources. Étant donné que la génération de votre solution génère des fichiers sources, Live Unit Testing est dans une boucle de génération infinie. Si, toutefois, les entrées et les sorties de la cible sont vérifiées lorsque Live Unit Testing démarre la deuxième génération (après avoir détecté les fichiers sources nouvellement générés à partir de la build précédente), elle s’arrête hors de la boucle de génération, car les contrôles des entrées et des sorties indiquent que tout est à jour.

## <a name="editor-icons"></a>Icônes de l’éditeur

**Pourquoi les icônes ne s’affichent-elles pas dans l’éditeur même si Live Unit Testing semble exécuter les tests en fonction des messages de la fenêtre sortie ?**

Les icônes ne sont pas visibles dans l’éditeur si les assemblys sur lesquels agit Live Unit Testing ne sont pas instrumentés pour une raison quelconque. Par exemple, Live Unit Testing n’est pas compatible avec les projets qui définissent `<UseHostCompilerIfAvailable>false</UseHostCompilerIfAvailable>`. Dans ce cas, votre processus de build doit être mis à jour pour supprimer ce paramètre ou le modifier en `true` afin de permettre à Live Unit Testing de fonctionner. 

## <a name="capture-logs"></a>Capturer les journaux

**Comment collecter des journaux plus détaillés pour les rapports de bogues de fichiers ?**

Vous pouvez collecter des journaux plus détaillés de plusieurs manières :

- Accédez à **Outils**  >  **options**  >  **Live Unit testing** et modifiez l’option de journalisation en mode **détaillé**. La journalisation détaillée fournit des journaux plus détaillés dans la fenêtre **Sortie**.

- Définissez la variable d’environnement utilisateur `LiveUnitTesting_BuildLog` sur le nom du fichier que vous souhaitez utiliser pour capturer le journal MSBuild. Vous pourrez ensuite récupérer à partir de ce fichier les messages détaillés du journal MSBuild compilé à partir des builds Live Unit Testing.

- Affectez à la variable d’environnement utilisateur `LiveUnitTesting_TestPlatformLog` la valeur `1` pour capturer le journal de la plateforme de test. Vous pourrez ensuite récupérer à partir de `[Solution Root]\.vs\[Solution Name]\log\[VisualStudio Process ID]` les messages détaillés de la plateforme de test issus des séries de tests Live Unit Testing.

- Créez une variable d’environnement de niveau utilisateur nommée `VS_UTE_DIAGNOSTICS` et affectez-lui la valeur 1 (ou n’importe quelle valeur), puis redémarrez Visual Studio. Vous devez maintenant voir un grand nombre de journaux dans l’onglet **résultats-tests** dans Visual Studio.

## <a name="see-also"></a>Voir aussi

- [Live Unit Testing](live-unit-testing.md)
