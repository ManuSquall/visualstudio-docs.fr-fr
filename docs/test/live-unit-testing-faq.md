---
title: FAQ Live Unit Testing
ms.date: 10/03/2017
ms.topic: conceptual
helpviewer_keywords:
- Live Unit Testing FAQ
author: mikejo5000
ms.author: mikejo
ms.workload:
- dotnet
ms.openlocfilehash: ba231e6c203197518b75a7a8c0592f01bba4ffe9
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591539"
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

Si vous avez d’anciens projets de test basés sur MSTest qui font référence `Microsoft.VisualStudio.QualityTools.UnitTestFramework` et que vous ne souhaitez pas passer aux nouveaux forfaits MSTest NuGet, passez à Visual Studio 2019 ou Visual Studio 2017.

Dans certains cas, vous devez peut-être restaurer explicitement les packages NuGet référencés par les projets dans la solution pour que Live Unit Testing fonctionne. Vous pouvez restaurer les paquets soit en faisant une version explicite de la solution (sélectionnez **Build** > **Rebuild Solution** à partir du menu Visual Studio de haut niveau), soit en cliquant à droite sur la solution et en sélectionnant des **paquets NuGet de restauration** avant d’activer les tests d’unité vivante.

## <a name="net-core-support"></a>Support de .NET Core

**Live Unit Testing fonctionne-il avec .NET Core ?**

Oui. Live Unit Testing fonctionne avec.NET Core et .NET Framework.

## <a name="configuration"></a>Configuration

**Pourquoi Live Unit Testing ne fonctionne-t-il pas quand je l’active ?**

La fenêtre de sortie (lorsque le drop-down d’unités en direct est sélectionné) devrait vous indiquer pourquoi les tests d’unité en direct ne fonctionnent pas. Live Unit Testing Test peut ne pas fonctionner pour les raisons suivantes :

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

- Assurez-vous que le fichier MSBuild *.props* importé du paquet d’adaptateur de test est correctement mis à jour ainsi. Vérifiez la version/le chemin du package NuGet de l’importation, qui figure généralement vers le haut du fichier projet, comme suit :

   ```xml
    <Import Project="..\packages\xunit.runner.visualstudio.2.2.0\build\net20\xunit.runner.visualstudio.props" Condition="Exists('..\packages\xunit.runner.visualstudio.2.2.0\build\net20\xunit.runner.visualstudio.props')" />
   ```

## <a name="customize-builds"></a>Personnaliser des builds

**Est-il possible de personnaliser les builds Live Unit Testing ?**

Si votre solution nécessite des étapes personnalisées à construire pour l’instrumentation (Live Unit Testing) qui ne sont pas nécessaires pour la `BuildingForLiveUnitTesting` construction « régulière » non instrumentée, alors vous pouvez ajouter du code à votre projet ou *.cibles* fichiers qui vérifie la propriété et effectue des étapes personnalisées de pré/post de construction. Vous pouvez également choisir de supprimer certaines étapes de génération (telles que la publication ou la génération de packages) ou d’ajouter des étapes de génération (par exemple, la copie des composants requis) pour une build Live Unit Testing basée sur cette propriété de projet. Le fait de personnaliser votre build avec cette propriété ne modifie pas votre build et impacte uniquement les builds Live Unit Testing.

Par exemple, vous pouvez avoir une cible qui génère des packages NuGet dans le cadre d’une build standard. Vous préférerez sans doute éviter que des packages NuGet soient générés après chaque modification que vous effectuez. Ainsi, vous pouvez désactiver cette cible dans la build Live Unit Testing en procédant comme suit :  

```xml
<Target Name="GenerateNuGetPackages" BeforeTargets="AfterBuild" Condition="'$(BuildingForLiveUnitTesting)' != 'true'">
    <Exec Command='"$(MSBuildThisFileDirectory)..\tools\GenPac" '/>
</Target>
```

## <a name="error-messages-with-outputpath-outdir-or-intermediateoutputpath"></a>Messages d’erreur avec \<OutputPath \<>, OutDir \<> ou IntermediateOutputPath>

**Pourquoi puis-je obtenir l’erreur suivante lorsque Live Unit Testing tente de construire ma solution: "... semble inconditionnellement fixé `<OutputPath>` ou `<OutDir>`. Live Unit Testing n’exécutera pas de tests à partir de l’assemblage de sortie ??**

Vous pouvez obtenir cette erreur si le processus de construction de votre solution a la logique personnalisée qui spécifie où les binaires doivent être générés. Par défaut, l’emplacement de `<OutputPath>` `<OutDir>` vos `<IntermediateOutputPath>` binaires `<BaseOutputPath>` `<BaseIntermediateOutputPath>`dépend, ou ainsi que ou .

Live Unit Testing remplace ces variables pour s’assurer que les artefacts de construction sont déposés à un dossier d’artefacts d’essai d’unité en direct et échouera si votre processus de construction l’emporte également sur ces variables.

Il existe deux approches principales pour faire vivre les tests d’unité en main avec succès. Pour des configurations de construction plus `<BaseIntermediateOutputPath>`faciles, vous pouvez baser vos chemins de sortie sur . Pour des configurations plus complexes, `<LiveUnitTestingBuildRootPath>`vous pouvez baser vos trajectoires de sortie sur .

### <a name="overriding-outputpathintermediateoutputpath-conditionally-based-on-baseoutputpath-baseintermediateoutputpath"></a>/ `<IntermediateOutputPath>` `<BaseOutputPath>` / `<BaseIntermediateOutputPath>`Dépassement conditionnellement basé sur `<OutputPath>` .

> [!NOTE]
> Pour utiliser cette approche, chaque projet doit être en mesure de construire indépendamment les uns des autres. N’ayez pas un seul projet d’artefacts de référence d’un autre projet pendant la construction. N’avez pas un projet de chargement dynamique des assemblages d’un autre projet pendant le temps d’exécution (par exemple l’appel `Assembly.Loadfile("..\..\Project2\Release\Project2.dll")`).

Pendant la construction, Live Unit `<BaseOutputPath>` / `<BaseIntermediateOutputPath>` Testing remplace automatiquement les variables pour cibler le dossier d’essai d’unité en direct.

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

### <a name="overriding-your-properties-based-on-the-liveunittestingbuildrootpath-property"></a>Dépassement de vos propriétés `<LiveUnitTestingBuildRootPath>` en fonction de la propriété.

> [!NOTE]
> Dans cette approche, vous devez être prudent sur les fichiers ajoutés sous le dossier d’artefacts qui ne sont pas générés pendant la construction. L’exemple ci-dessous montre ce qu’il faut faire lorsque vous placez le dossier de paquets sous des artefacts. Étant donné que le contenu de ce dossier n’est pas généré pendant la construction, la propriété MSBuild **ne doit pas être modifiée.**

Au cours d’une `<LiveUnitTestingBuildRootPath>` construction d’essai d’unité en direct, la propriété est réglée à l’emplacement du dossier d’essai d’unité vivante.

Supposons, par exemple, que votre projet a la structure montrée ici.

```
.vs\...\lut\0\b
artifacts\{binlog,obj,bin,nupkg,testresults,packages}
src\{proj1,proj2,proj3}
tests\{testproj1,testproj2}
Solution.sln
```
Pendant la construction d’essais d’unité en direct, la `<LiveUnitTestingBuildRootPath>` propriété est réglée sur le chemin complet de `.vs\...\lut\0\b`. Si le projet `<ArtifactsRoot>` définit la propriété qui cartographie le dir de solution, vous pouvez mettre à jour le projet MSBuild comme suit :

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

## <a name="build-artifact-location"></a>Construire l’emplacement de l’artefact

**Je veux que les artefacts d’une construction de test d’unité en direct pour aller à un endroit spécifique au lieu de l’emplacement par défaut sous le dossier *.vs.* Comment puis-je changer cela?**

Définissez la variable d’environnement de niveau utilisateur `LiveUnitTesting_BuildRoot` sur le chemin d’accès où vous souhaitez déposer les artéfacts de build Live Unit Testing. 

## <a name="test-explorer-versus-live-unit-testing"></a>Test Explorer versus Live Unit Testing

**En quoi les tests exécutés dans la fenêtre de l’Explorateur de tests sont-ils différents de ceux exécutés dans Live Unit Testing ?**

Il existe plusieurs différences :

- Les tests d’exécution ou de débogage de la fenêtre **Test Explorer** exécutent des binaires réguliers, tandis que les tests d’unité en direct exécutent des binaires instrumentés. Si vous voulez déboiller les binaires instrumentés, l’ajout d’un appel [méthode Debugger.Launch](xref:System.Diagnostics.Debugger.Launch) dans votre méthode de test provoque le débbugger de lancer chaque fois que cette méthode est exécutée (y compris quand il est exécuté par Live Unit Testing), et vous pouvez ensuite attacher et déboiller le binaire instrumenté. Nous espérons cependant que l’instrumentation soit pour vous parfaitement transparente dans la plupart des scénarios utilisateur, et que vous n’ayez pas besoin de déboguer de fichiers binaires instrumentés.

- Live Unit Testing ne crée pas un nouveau domaine d’application pour exécuter des tests, mais les tests exécutés à partir de la fenêtre **Test Explorer** créent un nouveau domaine d’application.

- Live Unit Testing exécute des tests dans chaque assembly de test de manière séquentielle. Dans **Test Explorer**, vous pouvez choisir d’exécuter plusieurs tests en parallèle.

- **Test Explorer** effectue des tests dans un appartement à un seul thread (STA) par défaut, tandis que Live Unit Testing effectue des tests dans un appartement à plusieurs threads (MTA). Pour exécuter les tests MSTest dans un STA dans Live Unit Testing, complétez la méthode de test ou la classe de conteneur avec l’attribut `<STATestMethod>` ou `<STATestClass>` qui se trouve dans le package NuGet `MSTest.STAExtensions 1.0.3-beta`. Pour NUnit, complétez la méthode de test avec l’attribut `<RequiresThread(ApartmentState.STA)>`, et pour xUnit, avec l’attribut `<STAFact>`.

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

Votre solution peut être construite même si vous ne modifiez pas si le processus de construction génère du code source qui fait partie de la solution elle-même, et vos fichiers cibles de construction n’ont pas d’entrées et de sorties appropriées spécifiées. Les cibles doivent disposer d’une liste d’entrées et de sorties afin que MSBuild puisse effectuer les contrôles à jour appropriés et déterminer si une nouvelle build est requise.

Live Unit Testing démarre une build chaque fois qu’il détecte une modification des fichiers sources. Parce que la construction de votre solution génère des fichiers source, Live Unit Testing entre dans une boucle de construction infinie. Toutefois, si les entrées et les extrants de la cible sont vérifiés lorsque le test d’unité en direct commence la deuxième version (après avoir détecté les fichiers source nouvellement générés de la version précédente), il sort de la boucle de construction parce que les entrées et les vérifications des sorties indiquent que tout est à jour.

## <a name="editor-icons"></a>Icônes de l’éditeur

**Pourquoi ne vois-je pas d’icônes dans l’éditeur, même si Live Unit Testing semble exécuter les tests basés sur les messages dans la fenêtre de sortie?**

Les icônes ne sont pas visibles dans l’éditeur si les assemblys sur lesquels agit Live Unit Testing ne sont pas instrumentés pour une raison quelconque. Par exemple, Live Unit Testing n’est pas compatible avec les projets qui définissent `<UseHostCompilerIfAvailable>false</UseHostCompilerIfAvailable>`. Dans ce cas, votre processus de build doit être mis à jour pour supprimer ce paramètre ou le modifier en `true` afin de permettre à Live Unit Testing de fonctionner. 

## <a name="capture-logs"></a>Capturer les journaux

**Comment collecter des journaux plus détaillés pour les rapports de bogues de fichiers ?**

Vous pouvez collecter des journaux plus détaillés de plusieurs manières :

- Aller à **Tools** > **Options** > **Live Unit Testing** et changer l’option d’enregistrement à **Verbose**. La journalisation détaillée fournit des journaux plus détaillés dans la fenêtre **Sortie**.

- Définissez la variable d’environnement utilisateur `LiveUnitTesting_BuildLog` sur le nom du fichier que vous souhaitez utiliser pour capturer le journal MSBuild. Vous pourrez ensuite récupérer à partir de ce fichier les messages détaillés du journal MSBuild compilé à partir des builds Live Unit Testing.

- Affectez à la variable d’environnement utilisateur `LiveUnitTesting_TestPlatformLog` la valeur `1` pour capturer le journal de la plateforme de test. Vous pourrez ensuite récupérer à partir de `[Solution Root]\.vs\[Solution Name]\log\[VisualStudio Process ID]` les messages détaillés de la plateforme de test issus des séries de tests Live Unit Testing.

- Créez une variable d’environnement de niveau utilisateur nommée `VS_UTE_DIAGNOSTICS` et affectez-lui la valeur 1 (ou n’importe quelle valeur), puis redémarrez Visual Studio. Maintenant, vous devriez voir beaucoup de connexion dans la **sortie - Test** onglet dans Visual Studio.

## <a name="see-also"></a>Voir aussi

- [Tests d’unité en direct](live-unit-testing.md)
