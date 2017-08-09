---
title: "FAQ sur Live Unit Testing | Microsoft Docs"
ms.date: 2017-03-13
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio ALM
- Live Unit Testing FAQ
ms.assetid: 61baf3bb-646f-4c5a-b7c0-a6bdff68f21c
author: rpetrusha
ms.author: ronpet
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 359e1eb5df8f19774d352ace631802367b6dd8c9
ms.openlocfilehash: 2a58b84403189d824494af85bc732a1b8cf3d0b6
ms.contentlocale: fr-fr
ms.lasthandoff: 07/11/2017

---
# <a name="live-unit-testing-frequently-asked-questions"></a>Questions fréquentes concernant Live Unit Testing

## <a name="does-live-unit-testing-work-with-net-core"></a>Live Unit Testing fonctionne-il avec .NET Core ?  

**Réponse :**

Oui. Live Unit Testing fonctionne avec.NET Core et .NET Framework. La prise en charge de .NET Core a été ajoutée récemment dans la version Visual Studio 2017 Preview 15.3. 

## <a name="why-doesnt-live-unit-testing-work-when-i-turn-it-on"></a>Pourquoi Live Unit Testing ne fonctionne-t-il pas quand je l’active ? 

**Réponse :** 

La **Fenêtre Sortie** (lorsque vous sélectionnez la liste déroulante Live Unit Testing) doit indiquer les raisons de ce dysfonctionnement. Live Unit Testing Test peut ne pas fonctionner pour les raisons suivantes : 

- Si les packages NuGet référencés par les projets de la solution n’ont pas été restaurés, Live Unit Testing ne peut pas fonctionner. Pour résoudre ce problème, vous pouvez effectuer une génération explicite de la solution ou restaurer les packages NuGet dans la solution avant d’activer Live Unit Testing. 

- Si vous utilisez des tests basés sur MSTest dans vos projets, veillez à supprimer la référence à `Microsoft.VisualStudio.QualityTools.UnitTestFramework` et à ajouter des références aux derniers packages NuGet MSTest, `MSTest.TestAdapter` (version 1.1.11 au minimum requise) et `MSTest.TestFramework` (version 1.1.11 au minimum requise). Pour plus d’informations, reportez-vous à la section « Frameworks de test pris en charge » dans la rubrique [Utilisation de Live Unit Testing dans Visual Studio 2017 Enterprise Edition](live-unit-testing.md#supported-test-frameworks).
 
- Au moins un projet de votre solution doit contenir une référence NuGet ou une référence directe au framework de test xUnit, NUnit ou MSTest. Ce projet doit également faire référence au package NuGet des adaptateurs de test Visual Studio correspondants. L’adaptateur de test Visual Studio peut également être référencé via un fichier `.runsettings`. Le fichier `.runsettings` doit comporter une entrée similaire à celle-ci : 

   ```xml
    <RunSettings> 
       <RunConfiguration>
          <TestAdaptersPaths>path-to-your-test-adapter</TestAdaptersPaths>
       </RunConfiguration> 
    </RunSettings> 
   ``` 

## <a name="why-does-live-unit-testing-show-incorrect-coverage-after-you-upgrade-the-test-adapter-referenced-in-your-visual-studio-projects-to-the-supported-version"></a>Pourquoi est-ce que Live Unit Testing indique une couverture incorrecte après la mise à niveau de l’adaptateur de test référencé dans vos projets Visual Studio vers la version prise en charge ?

**Réponse :**

- Si plusieurs projets de la solution font référence au package de l’adaptateur de test NuGet, chacun d’eux doit être mis à niveau vers la version prise en charge.

- Vérifiez que le fichier .props MSBuild importé à partir du package de l’adaptateur de test est également mis à jour correctement. Vérifiez la version/le chemin du package NuGet de l’importation, qui figure généralement vers le haut du fichier projet, comme suit :

   ```xml
    <Import Project="..\packages\xunit.runner.visualstudio.2.2.0\build\net20\xunit.runner.visualstudio.props" Condition="Exists('..\packages\xunit.runner.visualstudio.2.2.0\build\net20\xunit.runner.visualstudio.props')" />
   ```

## <a name="can-i-customize-my-live-unit-testing-builds"></a>Est-il possible de personnaliser les générations Live Unit Testing ? 

**Réponse :**

Si votre solution nécessite des étapes personnalisées de génération pour l’instrumentation (Live Unit Testing) qui ne sont pas nécessaires pour la génération non instrumentée « standard », vous pouvez ajouter du code à vos fichiers projet ou .targets pour vérifier la propriété `BuildingForLiveUnitTesting` et effectuer les étapes personnalisées avant et après la génération. Vous pouvez également choisir de supprimer certaines étapes de génération (telles que la publication ou la génération de packages) ou d’ajouter des étapes de génération (par exemple, la copie des composants requis) pour une build Live Unit Testing basée sur cette propriété de projet. Cela ne modifiera en rien votre build standard et affectera uniquement les builds Live Unit Testing. 

Par exemple, vous pouvez avoir une cible qui génère des packages NuGet dans le cadre d’une build standard. Vous préférerez sans doute éviter que des packages NuGet soient générés après chaque modification que vous effectuez. Ainsi, vous pouvez désactiver cette cible dans la build Live Unit Testing en procédant comme suit :   

```xml
<Target Name="GenerateNuGetPackages" BeforeTargets="AfterBuild" Condition="'$(BuildingForLiveUnitTesting)' != 'true'"> 
    <Exec Command='"$(MSBuildThisFileDirectory)..\tools\GenPac" '/> 
</Target> 
```

## <a name="error-messages-with-ltoutputpathgt-or-ltoutdirgt"></a>Messages d’erreur avec &lt;OutputPath&gt; ou &lt;OutDir&gt;

**Pourquoi l’erreur suivante s’affiche-t-elle quand Live Unit Testing tente de générer ma solution : « ... appears to unconditionally set `<OutputPath>` or `<OutDir>`. Live Unit Testing will not execute tests from the output assembly » ?**

**Réponse :**

Cette erreur peut se produire si le processus de génération de votre solution remplace sans condition `<OutputPath>` ou `<OutDir>` afin qu’il ne soit pas un sous-répertoire de `<BaseOutputPath>`. Dans ce cas, Live Unit Testing ne fonctionnera pas car il les remplace également pour s’assurer que les artéfacts de build sont placés dans un dossier sous `<BaseOutputPath>`. Si vous devez remplacer l’emplacement où vous souhaitez déplacer vos artéfacts de build dans le cadre d’une build standard, remplacez `<OutputPath>` sous condition en fonction de `<BaseOutputPath>`. 

Par exemple, si votre build remplace le `<OutputPath>` comme indiqué ci-dessous : 

```xml 
<Project> 
  <PropertyGroup> 
    <OutputPath>$(SolutionDir)Artifacts\$(Configuration)\bin\$(MSBuildProjectName)</OutputPath> 
  </PropertyGroup> 
</Project> 
```

vous pouvez le remplacer par ce qui suit : 

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
  
## <a name="setting-the-location-of-live-unit-testing-build-artifacts"></a>Définition de l’emplacement des artéfacts de build Live Unit Testing

**J’aimerais que les artéfacts d’une build Live Unit Testing soient placés à un emplacement spécifique au lieu de l’emplacement par défaut sous le dossier `.vs`. Comment modifier cet emplacement ?**
 
**Réponse :**

Définissez la variable d’environnement de niveau utilisateur `LiveUnitTesting_BuildRoot` sur le chemin d’accès où vous souhaitez déposer les artéfacts de build Live Unit Testing.  

## <a name="how-is-running-tests-from-test-explorer-window-different-from-running-tests-in-live-unit-testing"></a>En quoi les tests exécutés dans la fenêtre de l’Explorateur de tests sont-ils différents de ceux exécutés dans Live Unit Testing ? 

**Réponse :**

Il existe plusieurs différences : 

- L’exécution ou le débogage des tests depuis la fenêtre de l’Explorateur de tests exécute des fichiers binaires standards tandis que Live Unit Testing exécute des fichiers binaires instrumentés. Si vous souhaitez déboguer des fichiers binaires instrumentés, l’ajout d’un appel de méthode [Debugger.Launch](xref:System.Diagnostics.Debugger.Launch) dans votre méthode de test a pour effet de lancer le débogueur à chaque exécution de la méthode (y compris lorsqu’elle est exécutée par Live Unit Testing), après quoi vous pouvez attacher et déboguer le fichier binaire instrumenté. Nous espérons cependant que l’instrumentation soit pour vous parfaitement transparente dans la plupart des scénarios utilisateur, et que vous n’ayez pas besoin de déboguer de fichiers binaires instrumentés. 

- Live Unit Testing ne crée pas de nouveau domaine d’application pour exécuter des tests, contrairement aux tests exécutés à partir de la fenêtre Explorateur de tests. 

- Live Unit Testing exécute des tests dans chaque assembly de test de façon séquentielle ; à l’inverse, si vous exécutez plusieurs tests à partir de la fenêtre Explorateur de tests et que vous avez sélectionné le bouton **Exécuter les tests en parallèle**, ces tests s’exécuteront en parallèle. 

- La détection et l’exécution de tests dans Live Unit Testing utilisent la version 2 de `TestPlatform`, tandis que la fenêtre Explorateur de tests utilise la version 1. Vous ne devriez cependant remarquer aucune différence dans la plupart des cas.  

- L’Explorateur de tests exécute actuellement des tests dans un seul thread cloisonné (STA) par défaut, tandis que Live Unit Testing exécute les tests dans plusieurs threads cloisonnés (MTA). Pour exécuter les tests MSTest dans un STA dans Live Unit Testing, complétez la méthode de test ou la classe de conteneur avec l’attribut `<STATestMethod>` ou `<STATestClass>` qui se trouve dans le package NuGet `MSTest.STAExtensions 1.0.3-beta`. Pour NUnit, complétez la méthode de test avec l’attribut `<RequiresThread(ApartmentState.STA)>`, et pour xUnit, avec l’attribut `<STAFact>`.
 
## <a name="how-do-i-exclude-tests-from-participating-in-live-unit-testing"></a>Comment exclure des tests de Live Unit Testing ?

**Réponse :**

Consultez la section « Including and excluding test projects and test methods » (Inclusion et exclusion de projets de test et de méthodes de test) de la rubrique [Use Live Unit Testing in Visual Studio 2017 Enterprise Edition](live-unit-testing.md#including-and-excluding-test-projects-and-test-methods) (Utilisation de Live Unit Testing dans Visual Studio 2017 Édition Entreprise) pour connaître les paramètres spécifiques à l’utilisateur. Cela est particulièrement utile lorsque vous souhaitez exécuter un ensemble spécifique de tests pour une session de modification particulière ou pour conserver vos préférences personnelles.
  
Pour les paramètres spécifiques à la solution, vous pouvez, à l’aide d’un programme, appliquer l’attribut <xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute?displayProperty=fullName> pour empêcher que des méthodes, des propriétés, des classes ou des structures soient instrumentées par Live Unit Testing. En outre, vous pouvez également définir la propriété `<ExcludeFromCodeCoverage>` sur `true` dans votre fichier projet pour exclure de l’instrumentation l’ensemble du projet. Live Unit Testing continue d’exécuter les tests qui n’ont pas été instrumentés, mais leur couverture n’est pas affichée.

Vous pouvez également vérifier si `Microsoft.CodeAnalysis.LiveUnitTesting.Runtime` est chargé dans le domaine d’application actuel et désactiver les tests sur cette base. Par exemple, vous pouvez procéder de cette manière avec xUnit :

```cs
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

## <a name="why-are-win32-pe-headers-different-in-instrumented-assemblies-built-by-live-unit-testing"></a>Pourquoi les en-têtes PE Win32 sont-ils différents dans les assemblys instrumentés générés par Live Unit Testing ? 

**Réponse :**

Il existe un problème connu qui peut empêcher les builds Live Unit Testing d’incorporer les données de l’en-tête PE Win32 suivantes : 

- Version de fichier (spécifiée par @System.Reflection.AssemblyFileVersionAttribute dans le code). 

- Icône Win32 (spécifiée par `/win32icon:` sur la ligne de commande). 

- Manifeste Win32 (spécifié par `/win32manifest:` sur la ligne de commande). 

Les tests qui reposent sur ces valeurs peuvent échouer lorsqu’ils sont exécutés par Live Unit Testing.

## <a name="why-does-live-unit-testing-keep-building-my-solution-all-the-time-even-if-i-am-not-making-any-edits"></a>Pourquoi Live Unit Testing ne cesse-t-il de générer ma solution, même si je n’y apporte aucune modification ? 

**Réponse :**

Cela peut se produire si le processus de génération de votre solution génère un code source qui fait partie de la solution elle-même, et si les fichiers cibles de la build ne possèdent ni les entrées appropriées ni les sorties spécifiées. Les cibles doivent disposer d’une liste d’entrées et de sorties afin que MSBuild puisse effectuer les contrôles à jour appropriés et déterminer si une nouvelle build est requise. 

Live Unit Testing démarre une build chaque fois qu’il détecte une modification des fichiers sources. Étant donné que la génération de votre solution génère des fichiers sources, Live Unit Testing obtient une boucle de génération infinie. Si, toutefois, les entrées et sorties de la cible sont vérifiées lorsque Live Unit Testing démarre la deuxième génération (après la détection des fichiers sources qui viennent d’être générés à partir de la build précédente), il quittera la boucle puisque les vérifications des entrées et des sorties indiquent que tout est à jour.   

## <a name="how-does-live-unit-testing-work-with-the-lightweight-solution-load-feature"></a>Comment fonctionne Live Unit Testing avec la fonctionnalité Lightweight Solution Load ? 

**Réponse :**

Live Unit Testing ne prend pas très bien en charge la fonctionnalité Chargement de solution allégé si tous les projets de la solution ne sont pas encore chargés. Vous risquez d’obtenir des informations de couverture incorrectes dans de tels scénarios.
 
## <a name="why-does-live-unit-testing-does-not-capture-coverage-from-a-new-process-created-by-a-test"></a>Pourquoi Live Unit Testing ne capture-t-il pas la couverture à partir d’un nouveau processus créé par un test ?
 
**Réponse :**

Il s’agit d’un problème connu que nous ne sommes pas parvenus à résoudre dans la version Visual Studio 2017. Il devrait être corrigé dans une prochaine mise à jour de Visual Studio 2017. 

## <a name="why-does-nothing-happen-after-i-include-or-exclude-tests-from-the-live-test-set"></a>Pourquoi rien ne se produit lorsque j’inclus ou exclus des tests à partir du jeu Live Test ? 

**Réponse :**

Il s'agit d'un problème connu. Pour contourner ce problème, vous devez apporter une modification à un fichier après avoir inclus ou exclu des tests.  

## <a name="live-unit-testing-and-editor-icons"></a>Icônes de Live Unit Testing et de l’éditeur 

**Pourquoi les icônes ne sont-elles pas visibles dans l’éditeur même si Live Unit Testing semble exécuter les tests à partir des messages de la fenêtre Sortie ?** 

**Réponse :**

Cela se produit si les assemblys sur lesquels agit Live Unit Testing ne sont pas instrumentés pour une raison quelconque. Par exemple, Live Unit Testing n’est pas compatible avec les projets qui définissent `<UseHostCompilerIfAvailable>false</UseHostCompilerIfAvailable>`. Dans ce cas, votre processus de génération devra être mis à jour pour supprimer ce paramètre ou le modifier en `true` afin de permettre à Live Unit Testing de fonctionner.  

## <a name="how-do-i-collect-more-detailed-logs-to-file-bug-reports"></a>Comment collecter des journaux plus détaillés pour les rapports de bogues de fichiers ? 

**Réponse :**

Vous pouvez collecter des journaux plus détaillés de plusieurs manières : 

- Accédez à **Outils**, **Options**, **Live Unit Testing** et définissez l’option de journalisation sur **Détaillé**. Des journaux plus détaillés s’afficheront alors dans la fenêtre Sortie. 

- Définissez la variable d’environnement utilisateur `LiveUnitTesting_BuildLog` sur le nom du fichier que vous souhaitez utiliser pour capturer le journal MSBuild. Vous pourrez ensuite récupérer à partir de ce fichier les messages détaillés du journal MSBuild compilé à partir des builds Live Unit Testing.

- Affectez à la variable d’environnement utilisateur `LiveUnitTesting_TestPlatformLog` la valeur `1` pour capturer le journal de la plateforme de test. Vous pourrez ensuite récupérer à partir de `[Solution Root]\.vs\[Solution Name]\log\[VisualStudio Process ID]` les messages détaillés de la plateforme de test issus des séries de tests Live Unit Testing.

- Créez une variable d’environnement de niveau utilisateur nommée `VS_UTE_DIAGNOSTICS` et affectez-lui la valeur 1 (ou n’importe quelle valeur), puis redémarrez Visual Studio. L’onglet **Sortie - Tests** de Visual Studio devrait maintenant contenir un nombre important de consignations. 
 
## <a name="see-also"></a>Voir aussi

[Tests unitaires en direct](live-unit-testing.md)
 

