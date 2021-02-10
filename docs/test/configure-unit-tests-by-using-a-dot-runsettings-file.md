---
title: Configurer des tests unitaires avec un fichier .runsettings
description: Découvrez comment utiliser le fichier. RunSettings dans Visual Studio pour configurer des tests unitaires qui sont exécutés à partir de la ligne de commande, de l’IDE ou d’un flux de travail de génération.
ms.custom: SEO-VS-2020
ms.date: 07/15/2020
ms.topic: conceptual
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 10bfed2a9a2a0ce466e1b3276a487695d40fb580
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99964561"
---
# <a name="configure-unit-tests-by-using-a-runsettings-file"></a>Configurer des tests unitaires à l’aide d’un fichier *. RunSettings*

Les tests unitaires dans Visual Studio peuvent être configurés à l’aide d’un fichier *. RunSettings* . Par exemple, vous pouvez changer la version de .NET sur laquelle les tests sont exécutés, le répertoire des résultats des tests ou les données collectées pendant une série de tests. Une utilisation courante d’un fichier *.runsettings* est de personnaliser [l’analyse de la couverture du code](../test/customizing-code-coverage-analysis.md).

Les fichiers de paramètres d’exécution peuvent être utilisés pour configurer des tests exécutés à partir de la [ligne de commande](vstest-console-options.md), de l’IDE ou dans un [flux de travail de génération](/azure/devops/pipelines/test/getting-started-with-continuous-testing?view=vsts&preserve-view=true) à l’aide de Azure test plans ou Team Foundation Server (TFS).

Les fichiers de paramètres d’exécution sont facultatifs. Si vous n’avez pas besoin d’une configuration spéciale, vous n’avez pas besoin d’un fichier *. RunSettings* .

## <a name="create-a-run-settings-file-and-customize-it"></a>Créer un fichier de paramètres d’exécution et le personnaliser

1. Ajoutez un fichier de paramètres d’exécution à votre solution. Dans **Explorateur de solutions**, dans le menu contextuel de votre solution, choisissez **Ajouter**  >  **un nouvel élément**, puis sélectionnez **fichier XML**. Enregistrez le fichier sous un nom tel que *test. RunSettings*.

   > [!TIP]
   > Le nom du fichier n’a pas d’importance, à condition d’utiliser l’extension *.runsettings*.

2. Ajoutez le contenu à partir de l' [exemple de fichier *. RunSettings](#example-runsettings-file), puis personnalisez-le selon vos besoins, comme décrit dans les sections qui suivent.

3. Spécifiez le fichier *. RunSettings à l’aide de l’une des méthodes suivantes :

   - [IDE Visual Studio](#specify-a-run-settings-file-in-the-ide)
   - [Ligne de commande](#specify-a-run-settings-file-from-the-command-line)
   - [Générez un flux de travail](/azure/devops/pipelines/test/getting-started-with-continuous-testing?view=vsts&preserve-view=true) à l’aide de Azure Test Plans ou Team Foundation Server (TFS).

4. Exécutez les tests unitaires pour utiliser les paramètres d’exécution personnalisés.

::: moniker range="vs-2017"

Si vous souhaitez désactiver et activer les paramètres personnalisés dans l’IDE, désélectionnez ou sélectionnez le fichier dans le menu **tester** les > **paramètres de test** .

![Menu Paramètres de test avec le fichier de paramètres de test dans Visual Studio 2017](../test/media/codecoverage-settingsfile.png)

::: moniker-end

::: moniker range=">=vs-2019"

Si vous souhaitez désactiver et activer les paramètres personnalisés dans l’IDE, désélectionnez ou sélectionnez le fichier dans le menu **test** .

::: moniker-end

> [!TIP]
> Vous pouvez créer plusieurs fichiers *.runsettings* dans votre solution et en sélectionner un en tant que fichier de paramètres de test actif en fonction des besoins.

## <a name="specify-a-run-settings-file-in-the-ide"></a>Spécifier un fichier de paramètres d’exécution dans l’IDE

Les méthodes disponibles dépendent de votre version de Visual Studio.

::: moniker range="vs-2017"
Pour spécifier un fichier de paramètres d'exécution dans l’IDE, sélectionnez **Test** > **Paramètres de test** > **Sélectionner le fichier de paramètres des tests**, puis sélectionnez le fichier *.runsettings*.

![Option de menu Sélectionner le fichier de paramètres des tests dans Visual Studio 2017](media/select-test-settings-file.png)

Le fichier apparaît dans le menu Paramètres de test. Vous pouvez le sélectionner ou le désélectionner. Quand il est sélectionné, le fichier de paramètres d’exécution s’applique quand vous sélectionnez **Analyser la couverture du code**.
::: moniker-end

::: moniker range=">=vs-2019"

### <a name="visual-studio-2019-version-164-and-later"></a>Visual Studio 2019 version 16,4 et versions ultérieures

Il existe trois façons de spécifier un fichier de paramètres d’exécution dans Visual Studio 2019 version 16,4 et versions ultérieures.

- [Détection automatique des paramètres d’exécution](#autodetect-the-run-settings-file)
- [Définir manuellement les paramètres d’exécution](#manually-select-the-run-settings-file)
- [Définir une propriété de build](#set-a-build-property)

#### <a name="autodetect-the-run-settings-file"></a>Détection automatique du fichier de paramètres d’exécution

Pour détecter automatiquement le fichier de paramètres d’exécution, placez-le à la racine de votre solution.

Si la détection automatique des fichiers de paramètres d’exécution est activée, les paramètres de ce fichier sont appliqués dans l’ensemble des tests exécutés. Vous pouvez activer la détection automatique des fichiers RunSettings à l’aide de deux méthodes :

- Sélectionner les options des **Outils** >  > **tester** les > **fichiers de détection automatique RunSettings**

   ![Option de détection automatique de fichier RunSettings dans Visual Studio 2019](media/vs-2019/auto-detect-runsettings-tools-window.png)

- Sélectionnez **tester** > **configurer les paramètres d’exécution** > **détecter automatiquement les fichiers RunSettings**

   ![Menu détection automatique du fichier RunSettings dans Visual Studio 2019](media/vs-2019/auto-detect-runsettings-menu.png)

#### <a name="manually-select-the-run-settings-file"></a>Sélectionner manuellement le fichier de paramètres d’exécution

Dans l’IDE, sélectionnez **tester** > **configurer les paramètres d’exécution** > **Sélectionner la solution RunSettings fichier**, puis sélectionnez le fichier *. RunSettings* .

   - Ce fichier remplace le fichier *. RunSettings* à la racine de la solution, le cas échéant, et s’applique à tous les tests exécutés.
   - Cette sélection de fichier est conservée uniquement localement.

![Sélectionnez tester la solution RunSettings menu fichier dans Visual Studio 2019](media/vs-2019/select-solution-settings-file.png)

#### <a name="set-a-build-property"></a>Définir une propriété de build

Ajoutez une propriété de build à un projet par le biais du fichier projet ou d’un fichier Directory. Build. props. Le fichier de paramètres d’exécution d’un projet est spécifié par la propriété **RunSettingsFilePath**.

- Les paramètres d’exécution au niveau du projet sont actuellement pris en charge dans les projets C#, VB, C++ et F #.
- Un fichier spécifié pour un projet remplace tout autre fichier de paramètres d’exécution spécifié dans la solution.
- [Ces propriétés MSBuild](../msbuild/msbuild-reserved-and-well-known-properties.md) peuvent être utilisées pour spécifier le chemin d’accès au fichier RunSettings.

Exemple de spécification d’un fichier *. RunSettings* pour un projet :

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <RunSettingsFilePath>$(MSBuildProjectDirectory)\example.runsettings</RunSettingsFilePath>
  </PropertyGroup>
  ...
</Project>
```

### <a name="visual-studio-2019-version-163-and-earlier"></a>Visual Studio 2019 version 16,3 et versions antérieures

Pour spécifier un fichier de paramètres d’exécution dans l’IDE, sélectionnez **tester** le  >  **fichier de paramètres de sélection**. Accédez au fichier *.runsettings* et sélectionnez-le.

![Option de menu Sélectionner le fichier de paramètres des tests dans Visual Studio 2019](media/vs-2019/select-settings-file.png)

Le fichier apparaît dans le menu test, et vous pouvez le sélectionner ou le désélectionner. Quand il est sélectionné, le fichier de paramètres d’exécution s’applique quand vous sélectionnez **Analyser la couverture du code**.
::: moniker-end

## <a name="specify-a-run-settings-file-from-the-command-line"></a>Spécifier un fichier de paramètres d’exécution à partir de la ligne de commande

Pour exécuter des tests depuis la ligne de commande, utilisez *vstest.console.exe* et spécifiez le fichier de paramètres à l’aide du paramètre **/Settings**.

1. Ouvrez une [invite de commandes développeur](/dotnet/framework/tools/developer-command-prompt-for-vs) pour Visual Studio.

2. Entrez une commande semblable à la suivante :

   ```cmd
   vstest.console.exe MyTestAssembly.dll /EnableCodeCoverage /Settings:CodeCoverage.runsettings
   ```

   or

   ```cmd
   vstest.console.exe --settings:test.runsettings test.dll
   ```

Pour plus d’informations, consultez [Options de ligne de commande VSTest.Console.exe](vstest-console-options.md).

## <a name="the-runsettings-file"></a>Le fichier *. RunSettings

Le fichier *. RunSettings est un fichier XML qui contient des éléments de configuration différents au sein de l’élément **RunSettings** . Les sections qui suivent détaillent les différents éléments. Pour obtenir un exemple complet, consultez [exemple de fichier *. RunSettings](#example-runsettings-file).

```xml
<?xml version="1.0" encoding="utf-8"?>
<RunSettings>
  <!-- configuration elements -->
</RunSettings>
```

Chacun des éléments de configuration est facultatif, car il a une valeur par défaut.

## <a name="runconfiguration-element"></a>Élément RunConfiguration

```xml
<RunConfiguration>
    <MaxCpuCount>1</MaxCpuCount>
    <ResultsDirectory>.\TestResults</ResultsDirectory>
    <TargetPlatform>x86</TargetPlatform>
    <TargetFrameworkVersion>Framework40</TargetFrameworkVersion>
    <TestAdaptersPaths>%SystemDrive%\Temp\foo;%SystemDrive%\Temp\bar</TestAdaptersPaths>
    <TestSessionTimeout>10000</TestSessionTimeout>
    <TreatNoTestsAsError>true</TreatNoTestsAsError>
</RunConfiguration>
```

L’élément **RunConfiguration** peut inclure les éléments suivants :

|Nœud|Default|Valeurs|
|-|-|-|
|**MaxCpuCount**|1|Ce paramètre permet de contrôler le degré d’exécution des tests parallèles lors des tests unitaires, en utilisant les cœurs disponibles sur la machine. Le moteur d’exécution des tests démarre en tant que processus distinct sur chaque cœur disponible et donne à chaque cœur un conteneur de tests à exécuter. Un conteneur peut être un assembly, une DLL ou un artefact approprié. Le conteneur de test est l’unité de planification. Dans chaque conteneur, les tests sont exécutés en fonction du framework de test configuré. S’il y a beaucoup de conteneurs, chaque processus reçoit le conteneur disponible suivant dès qu’il a terminé l’exécution des tests d’un conteneur.<br /><br />Valeur possible pour MaxCpuCount :<br /><br />n, où 1 < = n < = nombre de cœurs : jusqu’à n processus peuvent être lancés.<br /><br />n, où n = toute autre valeur : le nombre de processus lancés peut atteindre le nombre de cœurs disponibles. Par exemple, définissez n = 0 pour permettre à la plateforme de déterminer automatiquement le nombre optimal de processus à lancer en fonction de l’environnement.|
|**ResultsDirectory**||Répertoire où les résultats des tests sont placés. Le chemin d’accès est relatif au répertoire qui contient le fichier. RunSettings.|
|**TargetFrameworkVersion**|Framework40|`FrameworkCore10` pour les sources .NET Core, `FrameworkUap10` pour les sources UWP, `Framework45` pour .NET Framework 4.5 et versions ultérieures, `Framework40` pour .NET Framework 4.0 et `Framework35` pour .NET Framework 3.5.<br /><br />Ce paramètre spécifie la version du framework de tests unitaires qui est utilisée pour découvrir et exécuter les tests. Elle peut être différente de la version de la plateforme .NET. que vous spécifiez dans les propriétés de génération du projet de test unitaire.<br /><br />Si vous omettez l’élément `TargetFrameworkVersion` dans le fichier *.runsettings*, la plateforme détermine automatiquement la version du framework sur la base des fichiers binaires générés.|
|**TargetPlatform**|x86|x86, x64|
|**TreatTestAdapterErrorsAsWarnings**|false|false, true|
|**TestAdaptersPaths**||Un ou plusieurs chemins du répertoire où se trouvent les TestAdapters|
|**TestSessionTimeout**||Permet aux utilisateurs de mettre fin à une session de test lorsque celle-ci dépasse le délai spécifié. La définition d’un délai d’expiration garantit que les ressources sont consommées et que les sessions de test sont limitées à une durée spécifique. Le paramètre est disponible dans **Visual Studio 2017 versions 15.5** et ultérieures.|
|**DotnetHostPath**||Spécifiez un chemin d’accès personnalisé à l’hôte dotnet qui est utilisé pour exécuter le testhost. Cela est utile lorsque vous créez votre propre DotNet, par exemple lors de la création du référentiel dotnet/Runtime. La spécification de cette option ignore la recherche de testhost.exe et utilise toujours le testhost.dll.|
|**TreatNoTestsAsError**|false| True ou False <br>Spécifiez une valeur booléenne qui définit le code de sortie quand aucun test n’est découvert. Si la valeur est `true` et qu’aucun test n’est découvert, un code de sortie différent de zéro est retourné. Sinon, la valeur zéro est renvoyée.|

## <a name="datacollectors-element-diagnostic-data-adapters"></a>Élément DataCollectors (adaptateurs de données de diagnostic)

L’élément **DataCollectors** spécifie les paramètres des adaptateurs de données de diagnostic. Les adaptateurs de données de diagnostic rassemblent des informations supplémentaires sur l’environnement et sur l’application testée. Chaque adaptateur a des paramètres par défaut. Il vous suffit de fournir des paramètres si vous ne souhaitez pas utiliser les valeurs par défaut.

```xml
<DataCollectionRunSettings>
  <DataCollectors>
    <!-- data collectors -->
  </DataCollectors>
</DataCollectionRunSettings>
```

### <a name="codecoverage-data-collector"></a>Collecteur de données CodeCoverage

Le collecteur de données de couverture du code crée un journal des parties du code d’application qui ont été testées. Pour plus d’informations sur la personnalisation des paramètres pour la couverture du code, consultez personnaliser l’analyse de la [couverture du code](../test/customizing-code-coverage-analysis.md).

```xml
<DataCollector friendlyName="Code Coverage" uri="datacollector://Microsoft/CodeCoverage/2.0" assemblyQualifiedName="Microsoft.VisualStudio.Coverage.DynamicCoverageDataCollector, Microsoft.VisualStudio.TraceCollector, Version=11.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a">
  <Configuration>
    <CodeCoverage>
      <ModulePaths>
        <Exclude>
          <ModulePath>.*CPPUnitTestFramework.*</ModulePath>
        </Exclude>
      </ModulePaths>

      <UseVerifiableInstrumentation>True</UseVerifiableInstrumentation>
      <AllowLowIntegrityProcesses>True</AllowLowIntegrityProcesses>
      <CollectFromChildProcesses>True</CollectFromChildProcesses>
      <CollectAspDotNet>False</CollectAspDotNet>
    </CodeCoverage>
  </Configuration>
</DataCollector>
```

### <a name="videorecorder-data-collector"></a>Collecteur de données VideoRecorder

Le collecteur de données vidéo capture un enregistrement de l’écran quand des tests sont exécutés. Cet enregistrement est utile pour résoudre les problèmes des tests d’interface utilisateur. Le collecteur de données vidéo est disponible dans **Visual Studio 2017 versions 15.5** et ultérieures. Pour obtenir un exemple de configuration de ce collecteur de données, consultez l' [exemple de fichier *. RunSettings](#example-runsettings-file).

Pour personnaliser un autre type d’adaptateur de données de diagnostic, utilisez un [fichier de paramètres de test](../test/collect-diagnostic-information-using-test-settings.md).

### <a name="blame-data-collector"></a>Collecteur de données de responsabilité

Cette option peut vous aider à isoler un test problématique qui provoque un blocage de l’hôte de test. L’exécution du collecteur crée un fichier de sortie (*Sequence.xml*) dans *TestResults*, qui capture l’ordre d’exécution du test avant l’incident.

```xml
<DataCollector friendlyName="blame" enabled="True">
</DataCollector>
```

## <a name="testrunparameters"></a>TestRunParameters

```xml
<TestRunParameters>
    <Parameter name="webAppUrl" value="http://localhost" />
    <Parameter name="docsUrl" value="https://docs.microsoft.com" />
</TestRunParameters>
```

Les paramètres de série de tests offrent un moyen de définir des variables et des valeurs qui sont disponibles pour les tests au moment de l’exécution. Accédez aux paramètres à l’aide de la <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext.Properties%2A?displayProperty=nameWithType> propriété MSTest (ou de nunit [TestContext](https://docs.nunit.org/articles/nunit/writing-tests/TestContext.html)) :

```csharp
private string _appUrl;
public TestContext TestContext { get; set; }

[TestMethod] // [Test] for NUnit
public void HomePageTest()
{
    string _appURL = TestContext.Properties["webAppUrl"];
}
```

Pour utiliser les paramètres de série de tests, ajoutez une <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext> propriété publique à votre classe de test.

## <a name="loggerrunsettings-element"></a>Élément LoggerRunSettings

La `LoggerRunSettings` section définit un ou plusieurs enregistreurs d’événements à utiliser pour la série de tests. Les journaux les plus courants sont console, fichier de Résultats des tests Visual Studio (TRX) et html.

```xml
<LoggerRunSettings>
    <Loggers>
      <Logger friendlyName="console" enabled="True">
        <Configuration>
            <Verbosity>quiet</Verbosity>
        </Configuration>
      </Logger>
      <Logger friendlyName="trx" enabled="True">
        <Configuration>
          <LogFileName>foo.trx</LogFileName>
        </Configuration>
      </Logger>
      <Logger friendlyName="html" enabled="True">
        <Configuration>
          <LogFileName>foo.html</LogFileName>
        </Configuration>
      </Logger>
    </Loggers>
  </LoggerRunSettings>
```

## <a name="mstest-element"></a>Élément MSTest

Ces paramètres sont spécifiques à l’adaptateur de test qui exécute les méthodes de test disposant de l’attribut <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> .

```xml
<MSTest>
    <MapInconclusiveToFailed>True</MapInconclusiveToFailed>
    <CaptureTraceOutput>false</CaptureTraceOutput>
    <DeleteDeploymentDirectoryAfterTestRunIsComplete>False</DeleteDeploymentDirectoryAfterTestRunIsComplete>
    <DeploymentEnabled>False</DeploymentEnabled>
    <AssemblyResolution>
      <Directory Path="D:\myfolder\bin\" includeSubDirectories="false"/>
    </AssemblyResolution>
</MSTest>
```

|Configuration|Default|Valeurs|
|-|-|-|
|**ForcedLegacyMode**|false|Dans Visual Studio 2012, l’adaptateur MSTest a été optimisé afin d’être plus rapide et plus scalable. Un comportement, tel que l’ordre dans lequel les tests sont exécutés, peut ne pas être exactement identique à celui d’éditions précédentes de Visual Studio. Définissez cette valeur sur **true** pour utiliser l’adaptateur de test le plus ancien.<br /><br />Par exemple, vous pouvez utiliser ce paramètre si un fichier *app.config* est spécifié pour un test unitaire.<br /><br />Il est recommandé d’envisager de refactoriser vos tests pour vous permettre d’utiliser le nouvel adaptateur.|
|**IgnoreTestImpact**|false|La fonctionnalité d’impact de test hiérarchise les tests affectés par les modifications récentes, lorsqu’elles sont exécutées dans MSTest ou à partir de Microsoft Test Manager (déconseillé dans Visual Studio 2017). Ce paramètre désactive la fonctionnalité. Pour plus d’informations, consultez [Quels tests doivent être exécutés depuis une version antérieure ?](/previous-versions/dd286589(v=vs.140)).|
|**SettingsFile**||Vous pouvez spécifier un fichier de paramètres de test à utiliser avec l’adaptateur MSTest ici. Vous pouvez également spécifier un fichier de paramètres de test à partir du [menu de paramètres](#specify-a-run-settings-file-in-the-ide).<br /><br />Si vous spécifiez cette valeur, vous devez également affecter à **ForcedlegacyMode** la valeur **true**.<br /><br />`<ForcedLegacyMode>true</ForcedLegacyMode>`|
|**KeepExecutorAliveAfterLegacyRun**|false|Une fois qu’une série de tests est terminée, MSTest est arrêté. Tout processus qui est lancé dans le cadre du test est également terminé. Si vous souhaitez conserver l’exécuteur de test actif, définissez la valeur sur **true**. Par exemple, vous pouvez utiliser ce paramètre pour que le navigateur continue à s’exécuter entre des tests codés de l’interface utilisateur.|
|**DeploymentEnabled**|true|Si vous définissez cette valeur sur **false**, les éléments de déploiement que vous avez spécifiés dans votre méthode de test ne sont pas copiés dans le répertoire de déploiement.|
|**CaptureTraceOutput**|true|Vous pouvez écrire dans la trace du débogage à partir de votre méthode de test en utilisant <xref:System.Diagnostics.Trace.WriteLine%2A?displayProperty=nameWithType>.|
|**DeleteDeploymentDirectoryAfterTestRunIsComplete**|true|Pour conserver le répertoire de déploiement après une série de tests, définissez cette valeur sur **false**.|
|**MapInconclusiveToFailed**|false|Si un test se termine avec un état Non concluant, il est mappé à l’état Ignoré dans **l’Explorateur de tests**. Si vous voulez que les tests non concluants s’affichent comme ayant échoué, définissez la valeur sur **true**.|
|**InProcMode**|false|Si vous souhaitez que vos tests soient exécutés dans le même processus que l’adaptateur de test Microsoft, définissez cette valeur sur **true**. Ce paramètre offre un gain de performances mineur. Mais si un test s’arrête à cause d’une exception, les tests restants ne s’exécutent pas.|
|**AssemblyResolution**|false|Vous pouvez spécifier des chemins d’assemblys supplémentaires pour la recherche et l’exécution des tests unitaires. Par exemple, utilisez ces chemins pour les assemblys de dépendance qui ne se trouvent pas dans le même répertoire que l’assembly de test. Pour spécifier un chemin, utilisez un élément **Directory Path**. Les chemins peuvent inclure des variables d’environnement.<br /><br />`<AssemblyResolution>  <Directory Path="D:\myfolder\bin\" includeSubDirectories="false"/> </AssemblyResolution>`|

## <a name="example-runsettings-file"></a>Exemple de fichier *. RunSettings*

Le code XML suivant illustre le contenu d’un fichier *.runsettings* type. Copiez ce code et modifiez-le selon vos besoins.

Chaque élément du fichier est facultatif, car il a une valeur par défaut.

```xml
<?xml version="1.0" encoding="utf-8"?>
<RunSettings>
  <!-- Configurations that affect the Test Framework -->
  <RunConfiguration>
    <MaxCpuCount>1</MaxCpuCount>
    <!-- Path relative to directory that contains .runsettings file-->
    <ResultsDirectory>.\TestResults</ResultsDirectory>

    <!-- x86 or x64 -->
    <!-- You can also change it from the Test menu; choose "Processor Architecture for AnyCPU Projects" -->
    <TargetPlatform>x86</TargetPlatform>

    <!-- Framework35 | [Framework40] | Framework45 -->
    <TargetFrameworkVersion>Framework40</TargetFrameworkVersion>

    <!-- Path to Test Adapters -->
    <TestAdaptersPaths>%SystemDrive%\Temp\foo;%SystemDrive%\Temp\bar</TestAdaptersPaths>

    <!-- TestSessionTimeout was introduced in Visual Studio 2017 version 15.5 -->
    <!-- Specify timeout in milliseconds. A valid value should be greater than 0 -->
    <TestSessionTimeout>10000</TestSessionTimeout>

    <!-- true or false -->
    <!-- Value that specifies the exit code when no tests are discovered -->
    <TreatNoTestsAsError>true</TreatNoTestsAsError>
  </RunConfiguration>

  <!-- Configurations for data collectors -->
  <DataCollectionRunSettings>
    <DataCollectors>
      <DataCollector friendlyName="Code Coverage" uri="datacollector://Microsoft/CodeCoverage/2.0" assemblyQualifiedName="Microsoft.VisualStudio.Coverage.DynamicCoverageDataCollector, Microsoft.VisualStudio.TraceCollector, Version=11.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a">
        <Configuration>
          <CodeCoverage>
            <ModulePaths>
              <Exclude>
                <ModulePath>.*CPPUnitTestFramework.*</ModulePath>
              </Exclude>
            </ModulePaths>

            <!-- We recommend you do not change the following values: -->
            <UseVerifiableInstrumentation>True</UseVerifiableInstrumentation>
            <AllowLowIntegrityProcesses>True</AllowLowIntegrityProcesses>
            <CollectFromChildProcesses>True</CollectFromChildProcesses>
            <CollectAspDotNet>False</CollectAspDotNet>

          </CodeCoverage>
        </Configuration>
      </DataCollector>

      <DataCollector uri="datacollector://microsoft/VideoRecorder/1.0" assemblyQualifiedName="Microsoft.VisualStudio.TestTools.DataCollection.VideoRecorder.VideoRecorderDataCollector, Microsoft.VisualStudio.TestTools.DataCollection.VideoRecorder, Version=15.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a" friendlyName="Screen and Voice Recorder">
        <!--Video data collector was introduced in Visual Studio 2017 version 15.5 -->
        <Configuration>
          <!-- Set "sendRecordedMediaForPassedTestCase" to "false" to add video attachments to failed tests only -->
          <MediaRecorder sendRecordedMediaForPassedTestCase="true"  xmlns="">           
            <ScreenCaptureVideo bitRate="512" frameRate="2" quality="20" />
          </MediaRecorder>
        </Configuration>
      </DataCollector>

      <!-- Configuration for blame data collector -->
      <DataCollector friendlyName="blame" enabled="True">
      </DataCollector>

    </DataCollectors>
  </DataCollectionRunSettings>

  <!-- Parameters used by tests at run time -->
  <TestRunParameters>
    <Parameter name="webAppUrl" value="http://localhost" />
    <Parameter name="webAppUserName" value="Admin" />
    <Parameter name="webAppPassword" value="Password" />
  </TestRunParameters>

  <!-- Configuration for loggers -->
  <LoggerRunSettings>
    <Loggers>
      <Logger friendlyName="console" enabled="True">
        <Configuration>
            <Verbosity>quiet</Verbosity>
        </Configuration>
      </Logger>
      <Logger friendlyName="trx" enabled="True">
        <Configuration>
          <LogFileName>foo.trx</LogFileName>
        </Configuration>
      </Logger>
      <Logger friendlyName="html" enabled="True">
        <Configuration>
          <LogFileName>foo.html</LogFileName>
        </Configuration>
      </Logger>
      <Logger friendlyName="blame" enabled="True" />
    </Loggers>
  </LoggerRunSettings>

  <!-- Adapter Specific sections -->

  <!-- MSTest adapter -->
  <MSTest>
    <MapInconclusiveToFailed>True</MapInconclusiveToFailed>
    <CaptureTraceOutput>false</CaptureTraceOutput>
    <DeleteDeploymentDirectoryAfterTestRunIsComplete>False</DeleteDeploymentDirectoryAfterTestRunIsComplete>
    <DeploymentEnabled>False</DeploymentEnabled>
    <AssemblyResolution>
      <Directory path="D:\myfolder\bin\" includeSubDirectories="false"/>
    </AssemblyResolution>
  </MSTest>

</RunSettings>
```

## <a name="specify-environment-variables-in-the-runsettings-file"></a>Spécifier des variables d’environnement dans le fichier *. RunSettings*

Les variables d’environnement peuvent être définies dans le fichier *. RunSettings* , qui peut interagir directement avec l’hôte de test. La spécification de variables d’environnement dans le fichier *. RunSettings* est nécessaire pour prendre en charge des projets non triviales qui requièrent la définition de variables d’environnement comme *DOTNET_ROOT*. Ces variables sont définies lors de la génération dynamique du processus hôte de test et sont disponibles dans l’hôte.

### <a name="example"></a>Exemple

Le code suivant est un fichier Sample *. RunSettings* qui transmet les variables d’environnement :

```xml
<?xml version="1.0" encoding="utf-8"?>
<!-- File name extension must be .runsettings -->
<RunSettings>
  <RunConfiguration>
    <EnvironmentVariables>
      <!-- List of environment variables we want to set-->
      <DOTNET_ROOT>C:\ProgramFiles\dotnet</DOTNET_ROOT>
      <SDK_PATH>C:\Codebase\Sdk</SDK_PATH>
    </EnvironmentVariables>
  </RunConfiguration>
</RunSettings>
```

Le nœud **RunConfiguration** doit contenir un nœud **EnvironmentVariables** . Une variable d’environnement peut être spécifiée sous la forme d’un nom d’élément et de sa valeur.

> [!NOTE]
> Étant donné que ces variables d’environnement doivent toujours être définies lorsque l’hôte de test est démarré, les tests doivent toujours s’exécuter dans un processus séparé. Pour ce faire, l’indicateur */InIsolation* est défini lorsqu’il existe des variables d’environnement afin que l’hôte de test soit toujours appelé.

## <a name="see-also"></a>Voir aussi

- [Configurer une série de tests](https://github.com/microsoft/vstest-docs/blob/master/docs/configure.md)
- [Personnaliser l’analyse de la couverture du code](../test/customizing-code-coverage-analysis.md)
- [Tâche de test Visual Studio (Azure Test Plans)](/azure/devops/pipelines/tasks/test/vstest?view=vsts&preserve-view=true)
