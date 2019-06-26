---
title: FAQ Live Unit Testing
ms.date: 10/03/2017
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio ALM
- Live Unit Testing FAQ
author: rpetrusha
ms.author: ronpet
ms.workload:
- dotnet
ms.openlocfilehash: 1ed80454f6a87047de9e338d26c749d3c27a98ea
ms.sourcegitcommit: b468d71052a1b8a697f477ab23a3644de139f1e9
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2019
ms.locfileid: "67258135"
---
# <a name="live-unit-testing-frequently-asked-questions"></a>Questions fréquentes (FAQ) sur Live Unit Testing

## <a name="latest-features"></a>Fonctionnalités les plus récentes

**Live Unit Testing est régulièrement amélioré. Comment puis-je trouver des informations sur les dernières fonctionnalités et améliorations ?**

Pour en savoir plus sur les nouvelles fonctionnalités et les améliorations apportées à Live Unit Testing, consultez [Nouveautés de Live Unit Testing](live-unit-testing-whats-new.md).

## <a name="supported-frameworks-and-versions"></a>Les frameworks et versions pris en charge sont les suivants

**Quels sont les frameworks de tests pris en charge par Live Unit Testing et quelles sont les versions minimales prises en charge ?**

Live Unit Testing fonctionne avec les trois frameworks de tests unitaires populaires listés dans le tableau suivant. La version minimale prise en charge des adaptateurs et des frameworks est également listée dans le tableau. Les frameworks de tests unitaires sont tous disponibles dans NuGet.org.

|Framework de test  |Version minimale de l’adaptateur Visual Studio  |Version minimale du framework  |
|---------|---------|---------|
|xUnit.net |xunit.runner.visualstudio version 2.2.0-beta3-build1187 |xunit 1.9.2 |
|NUnit |NUnit3TestAdapter version 3.7.0 |NUnit version 3.5.0 |
|MSTest |MSTest.TestAdapter 1.1.4-preview |MSTest.TestFramework 1.0.5-preview |

Si vous avez des projets de test basés sur MSTest plus anciens qui référencent `Microsoft.VisualStudio.QualityTools.UnitTestFramework` et que vous ne souhaitez pas passer aux packages NuGet de MSTest plus récents, faites une mise à niveau vers Visual Studio 2017 version 15.4 ou ultérieure.

Dans certains cas, vous devez peut-être restaurer explicitement les packages NuGet référencés par les projets dans la solution pour que Live Unit Testing fonctionne. Vous pouvez restaurer les packages en exécutant une build explicite de la solution (sélectionnez **Générer**, **Regénérer la solution** à partir du menu Visual Studio de niveau supérieur) ou en cliquant avec le bouton droit sur la solution, puis en sélectionnant **Restaurer des packages NuGet** avant d’activer Live Unit Testing.

## <a name="net-core-support"></a>Support de .NET Core

**Live Unit Testing fonctionne-il avec .NET Core ?**

Oui. Live Unit Testing fonctionne avec.NET Core et .NET Framework. La prise en charge de .NET Core a été ajoutée dans Visual Studio 2017 version 15.3. Effectuez une mise à niveau vers cette version de Visual Studio ou une version ultérieure si vous souhaitez que .NET Core prenne en charge Live Unit Testing.

## <a name="configuration"></a>Configuration

**Pourquoi Live Unit Testing ne fonctionne-t-il pas quand je l’active ?**

La fenêtre **Sortie** (quand vous sélectionnez la liste déroulante Live Unit Testing) doit indiquer les raisons de ce dysfonctionnement. Live Unit Testing Test peut ne pas fonctionner pour les raisons suivantes :

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

- Vérifiez que le fichier *.props* MSBuild importé à partir du package de l’adaptateur de test est mis à jour correctement. Vérifiez la version/le chemin du package NuGet de l’importation, qui figure généralement vers le haut du fichier projet, comme suit :

   ```xml
    <Import Project="..\packages\xunit.runner.visualstudio.2.2.0\build\net20\xunit.runner.visualstudio.props" Condition="Exists('..\packages\xunit.runner.visualstudio.2.2.0\build\net20\xunit.runner.visualstudio.props')" />
   ```

## <a name="customize-builds"></a>Personnaliser des builds

**Est-il possible de personnaliser les builds Live Unit Testing ?**

Si votre solution nécessite des étapes personnalisées de génération pour l’instrumentation (Live Unit Testing) qui ne sont pas nécessaires pour la génération non instrumentée « standard », vous pouvez ajouter du code à vos fichiers projet ou *.targets* pour vérifier la propriété `BuildingForLiveUnitTesting` et effectuer les étapes personnalisées avant et après la génération. Vous pouvez également choisir de supprimer certaines étapes de génération (telles que la publication ou la génération de packages) ou d’ajouter des étapes de génération (par exemple, la copie des composants requis) pour une build Live Unit Testing basée sur cette propriété de projet. Le fait de personnaliser votre build avec cette propriété ne modifie pas votre build et impacte uniquement les builds Live Unit Testing.

Par exemple, vous pouvez avoir une cible qui génère des packages NuGet dans le cadre d’une build standard. Vous préférerez sans doute éviter que des packages NuGet soient générés après chaque modification que vous effectuez. Ainsi, vous pouvez désactiver cette cible dans la build Live Unit Testing en procédant comme suit :  

```xml
<Target Name="GenerateNuGetPackages" BeforeTargets="AfterBuild" Condition="'$(BuildingForLiveUnitTesting)' != 'true'">
    <Exec Command='"$(MSBuildThisFileDirectory)..\tools\GenPac" '/>
</Target>
```

## <a name="error-messages-with-ltoutputpathgt-or-ltoutdirgt"></a>Messages d’erreur avec &lt;OutputPath&gt; ou &lt;OutDir&gt;

**Pourquoi l’erreur suivante s’affiche-t-elle quand Live Unit Testing tente de générer ma solution : « ... appears to unconditionally set `<OutputPath>` or `<OutDir>`. Live Unit Testing will not execute tests from the output assembly » ?**

Cette erreur peut se produire si le processus de génération de votre solution remplace sans condition `<OutputPath>` ou `<OutDir>` afin qu’il ne soit pas un sous-répertoire de `<BaseOutputPath>`. Dans ce cas, Live Unit Testing ne fonctionnera pas, car il remplace également ces valeurs pour garantir que les artefacts de build soient placés dans un dossier sous `<BaseOutputPath>`. Si vous devez remplacer l’emplacement où vous souhaitez déplacer vos artéfacts de build dans le cadre d’une build standard, remplacez `<OutputPath>` sous condition en fonction de `<BaseOutputPath>`.

Par exemple, si votre build remplace le `<OutputPath>` comme indiqué ci-dessous :

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

## <a name="set-the-location-of-build-artifacts"></a>Définir l’emplacement des artefacts de build

**J’aimerais que les artefacts d’une build Live Unit Testing soient placés à un emplacement spécifique au lieu de l’emplacement par défaut, sous le dossier *.vs*. Comment modifier cet emplacement ?**

Définissez la variable d’environnement de niveau utilisateur `LiveUnitTesting_BuildRoot` sur le chemin d’accès où vous souhaitez déposer les artéfacts de build Live Unit Testing. 

## <a name="test-explorer-vs-live-unit-testing-test-runs"></a>Explorateur de tests et séries de tests Live Unit Testing

**En quoi les tests exécutés dans la fenêtre de l’Explorateur de tests sont-ils différents de ceux exécutés dans Live Unit Testing ?**

Il existe plusieurs différences :

- L’exécution ou le débogage des tests depuis la fenêtre de **l’Explorateur de tests** exécute des fichiers binaires réguliers, tandis que Live Unit Testing exécute des fichiers binaires instrumentés. Si vous souhaitez déboguer des fichiers binaires instrumentés, l’ajout d’un appel de méthode [Debugger.Launch](xref:System.Diagnostics.Debugger.Launch)  dans votre méthode de test a pour effet de lancer le débogueur à chaque exécution de la méthode (y compris quand elle est exécutée par Live Unit Testing), après quoi vous pouvez attacher et déboguer le fichier binaire instrumenté. Nous espérons cependant que l’instrumentation soit pour vous parfaitement transparente dans la plupart des scénarios utilisateur, et que vous n’ayez pas besoin de déboguer de fichiers binaires instrumentés.

- Live Unit Testing ne crée pas de nouveau domaine d’application pour exécuter des tests, contrairement aux tests exécutés à partir de la fenêtre **Explorateur de tests**.

- Live Unit Testing exécute des tests dans chaque assembly de test de façon séquentielle. Si vous exécutez plusieurs tests à partir de la fenêtre **Explorateur de tests** et que vous avez sélectionné le bouton **Exécuter les tests en parallèle**, ces tests s’exécuteront en parallèle.

- La découverte et l’exécution de tests dans Live Unit Testing utilisent la version 2 de `TestPlatform`, tandis que la fenêtre **Explorateur de tests** utilise la version 1. Toutefois, dans la plupart des cas, vous ne devriez remarquer aucune différence.

- **L’Explorateur de tests** exécute des tests dans un seul thread cloisonné (STA) par défaut, tandis que Live Unit Testing exécute les tests dans plusieurs threads cloisonnés (MTA). Pour exécuter les tests MSTest dans un STA dans Live Unit Testing, complétez la méthode de test ou la classe de conteneur avec l’attribut `<STATestMethod>` ou `<STATestClass>` qui se trouve dans le package NuGet `MSTest.STAExtensions 1.0.3-beta`. Pour NUnit, complétez la méthode de test avec l’attribut `<RequiresThread(ApartmentState.STA)>`, et pour xUnit, avec l’attribut `<STAFact>`.

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

## <a name="win32-pe-headers"></a>En-têtes PE Win32

**Pourquoi les en-têtes PE Win32 sont-ils différents dans les assemblys instrumentés générés par Live Unit Testing ?**

Ce problème est résolu et n’existe pas dans Visual Studio 2017 versions 15.3 et ultérieures.

Pour les précédentes versions de Visual Studio 2017, il existe un bogue connu qui peut empêcher les builds Live Unit Testing d’incorporer les données de l’en-tête PE Win32 suivantes :

- Version de fichier (spécifiée par @System.Reflection.AssemblyFileVersionAttribute dans le code).

- Icône Win32 (spécifiée par `/win32icon:` sur la ligne de commande).

- Manifeste Win32 (spécifié par `/win32manifest:` sur la ligne de commande).

Les tests qui reposent sur ces valeurs peuvent échouer lorsqu’ils sont exécutés par Live Unit Testing.

## <a name="continuous-builds"></a>Builds en continu

**Pourquoi Live Unit Testing ne cesse-t-il de générer ma solution, même si je n’y apporte aucune modification ?**

Votre solution peut être générée même si vous n’apportez pas de modifications, si le processus de génération de votre solution génère un code source qui fait partie de la solution elle-même, et si les fichiers cibles de la build n’ont ni les entrées appropriées ni les sorties spécifiées. Les cibles doivent disposer d’une liste d’entrées et de sorties afin que MSBuild puisse effectuer les contrôles à jour appropriés et déterminer si une nouvelle build est requise.

Live Unit Testing démarre une build chaque fois qu’il détecte une modification des fichiers sources. Étant donné que la génération de votre solution génère des fichiers sources, Live Unit Testing obtient une boucle de génération infinie. Si, toutefois, les entrées et sorties de la cible sont vérifiées lorsque Live Unit Testing démarre la deuxième génération (après la détection des fichiers sources qui viennent d’être générés à partir de la build précédente), il quittera la boucle de génération puisque les vérifications des entrées et des sorties indiquent que tout est à jour.  

## <a name="new-process-coverage"></a>Nouvelle couverture de processus

**Pourquoi Live Unit Testing ne capture-t-il pas la couverture à partir d’un nouveau processus créé par un test ?**

Il s’agit d’un problème connu qui devrait être corrigé dans une prochaine version.

## <a name="including-or-excluding-tests-doesnt-work"></a>L’inclusion ou l’exclusion de tests ne fonctionne pas

**Pourquoi rien ne se produit lorsque j’inclus ou exclus des tests à partir du jeu Live Test ?**

Ce problème est résolu et n’existe pas dans Visual Studio 2017 versions 15.3 et ultérieures.

Il s’agit d’un problème connu dans les versions antérieures de Visual Studio 2017. Pour contourner ce problème, vous devez apporter une modification à un fichier après avoir inclus ou exclu des tests.

## <a name="editor-icons"></a>Icônes de l’éditeur

**Pourquoi les icônes ne sont-elles pas visibles dans l’éditeur, alors que Live Unit Testing semble exécuter les tests à partir des messages de la fenêtre Sortie ?**

Les icônes ne sont pas visibles dans l’éditeur si les assemblys sur lesquels agit Live Unit Testing ne sont pas instrumentés pour une raison quelconque. Par exemple, Live Unit Testing n’est pas compatible avec les projets qui définissent `<UseHostCompilerIfAvailable>false</UseHostCompilerIfAvailable>`. Dans ce cas, votre processus de build doit être mis à jour pour supprimer ce paramètre ou le modifier en `true` afin de permettre à Live Unit Testing de fonctionner. 

## <a name="capture-logs"></a>Capturer les journaux

**Comment collecter des journaux plus détaillés pour les rapports de bogues de fichiers ?**

Vous pouvez collecter des journaux plus détaillés de plusieurs manières :

- Accédez à **Outils** > **Options** > **Live Unit Testing** et définissez l’option de journalisation sur **Détaillé**. La journalisation détaillée fournit des journaux plus détaillés dans la fenêtre **Sortie**.

- Définissez la variable d’environnement utilisateur `LiveUnitTesting_BuildLog` sur le nom du fichier que vous souhaitez utiliser pour capturer le journal MSBuild. Vous pourrez ensuite récupérer à partir de ce fichier les messages détaillés du journal MSBuild compilé à partir des builds Live Unit Testing.

- Affectez à la variable d’environnement utilisateur `LiveUnitTesting_TestPlatformLog` la valeur `1` pour capturer le journal de la plateforme de test. Vous pourrez ensuite récupérer à partir de `[Solution Root]\.vs\[Solution Name]\log\[VisualStudio Process ID]` les messages détaillés de la plateforme de test issus des séries de tests Live Unit Testing.

- Créez une variable d’environnement de niveau utilisateur nommée `VS_UTE_DIAGNOSTICS` et affectez-lui la valeur 1 (ou n’importe quelle valeur), puis redémarrez Visual Studio. L’onglet **Sortie - Tests** de Visual Studio devrait maintenant contenir un nombre important de consignations.

## <a name="see-also"></a>Voir aussi

- [Tests unitaires en direct](live-unit-testing.md)
