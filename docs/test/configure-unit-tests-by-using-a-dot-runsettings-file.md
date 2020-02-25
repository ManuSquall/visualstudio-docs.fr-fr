---
title: Configurer des tests unitaires avec un fichier .runsettings
ms.date: 10/03/2019
ms.topic: conceptual
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 4f7d44482937eb80540314db37bc9c664eaab689
ms.sourcegitcommit: bf2e9d4ff38bf5b62b8af3da1e6a183beb899809
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2020
ms.locfileid: "77557948"
---
# <a name="configure-unit-tests-by-using-a-runsettings-file"></a>Configurer des tests unitaires à l’aide d’un fichier *.runsettings*

Les tests unitaires dans Visual Studio peuvent être configurés à l’aide d’un fichier *.runsettings*. Par exemple, vous pouvez changer la version de .NET sur laquelle les tests sont exécutés, le répertoire des résultats des tests ou les données collectées pendant une série de tests.

Les fichiers de paramètres d’exécution sont facultatifs. Si vous n’avez pas besoin d’une configuration spéciale, un fichier *.runsettings* n’est pas nécessaire. Une utilisation courante d’un fichier *.runsettings* est de personnaliser [l’analyse de la couverture du code](../test/customizing-code-coverage-analysis.md).

## <a name="specify-a-run-settings-file"></a>Spécifier un fichier de paramètres d’exécution

Les fichiers de paramètres d’exécution permettent de configurer des tests qui sont exécutés depuis la [ligne de commande](vstest-console-options.md), dans l’IDE ou dans un [flux de travail de build](/azure/devops/pipelines/test/getting-started-with-continuous-testing?view=vsts) avec Azure Test Plans ou Team Foundation Server (TFS).

### <a name="ide"></a>IDE

::: moniker range="vs-2017"

Pour spécifier un fichier de paramètres d’exécution dans l’IDE, sélectionnez **tester** les **paramètres de test** > > **Sélectionnez fichier de paramètres de test**, puis sélectionnez le fichier *. RunSettings* .

![Option de menu Sélectionner le fichier de paramètres des tests dans Visual Studio 2017](media/select-test-settings-file.png)

Le fichier apparaît dans le menu Paramètres de test. Vous pouvez le sélectionner ou le désélectionner. Quand il est sélectionné, le fichier de paramètres d’exécution s’applique quand vous sélectionnez **Analyser la couverture du code**.

::: moniker-end

::: moniker range=">=vs-2019"

#### <a name="visual-studio-2019-version-163-and-earlier"></a>Visual Studio 2019 version 16,3 et versions antérieures

Pour spécifier un fichier de paramètres d’exécution dans l’IDE, sélectionnez **tester** > **Sélectionner le fichier de paramètres**. Accédez au fichier *.runsettings* et sélectionnez-le.

![Option de menu Sélectionner le fichier de paramètres des tests dans Visual Studio 2019](media/vs-2019/select-settings-file.png)

Le fichier apparaît dans le menu test, et vous pouvez le sélectionner ou le désélectionner. Quand il est sélectionné, le fichier de paramètres d’exécution s’applique quand vous sélectionnez **Analyser la couverture du code**.

#### <a name="visual-studio-2019-version-164-and-later"></a>Visual Studio 2019 version 16,4 et versions ultérieures

Il existe trois façons de spécifier un fichier de paramètres d’exécution dans Visual Studio 2019 version 16,4 et versions ultérieures :

- Ajoutez une propriété de build à un projet par le biais du fichier projet ou d’un fichier Directory. Build. props. Le fichier de paramètres d’exécution d’un projet est spécifié par la propriété **RunSettingsFilePath**. 

    - Les paramètres d’exécution au niveau du projet sont C#actuellement pris en C++charge dans F# les projets, VB, et.
    - Un fichier spécifié pour un projet remplace tout autre fichier de paramètres d’exécution spécifié dans la solution.

    Exemple de spécification d’un fichier *. RunSettings* pour un projet :
    
    ```xml
    <Project Sdk="Microsoft.NET.Sdk">
      <PropertyGroup>
        <RunSettingsFilePath>$(SolutionDir)\example.runsettings</RunSettingsFilePath>
      </PropertyGroup>
      ...
    </Project>
    ```

- Placez un fichier de paramètres d’exécution nommé « . RunSettings » à la racine de votre solution.

  Si la détection automatique des fichiers de paramètres d’exécution est activée, les paramètres de ce fichier sont appliqués dans l’ensemble des tests exécutés. Vous pouvez activer la détection automatique des fichiers RunSettings à partir de deux emplacements :
  
    - **Outils** > **Options** > **Tester** > **détecter automatiquement les fichiers RunSettings**

      ![Option de détection automatique de fichier RunSettings dans Visual Studio 2019](media/vs-2019/auto-detect-runsettings-tools-window.png)
      
    - **Test** > **configurer les paramètres d’exécution** > **détecter automatiquement les fichiers RunSettings**
    
      ![Menu détection automatique du fichier RunSettings dans Visual Studio 2019](media/vs-2019/auto-detect-runsettings-menu.png)

- Dans l’IDE, sélectionnez **Test** > **configurer les paramètres d’exécution** > **sélectionnez le fichier solution RunSettings**, puis sélectionnez le fichier *. RunSettings* .

   ![Menu fichier RunSettings de la solution de test dans Visual Studio 2019](media/vs-2019/select-solution-settings-file.png)
      
   - Ce fichier remplace le fichier « . RunSettings » à la racine de la solution, s’il existe, et s’applique à toutes les exécutions de tests.  
   - Cette sélection de fichier est conservée uniquement localement. 

::: moniker-end

### <a name="command-line"></a>Ligne de commande

Pour exécuter des tests depuis la ligne de commande, utilisez *vstest.console.exe* et spécifiez le fichier de paramètres à l’aide du paramètre **/Settings**.

1. Lancez l'invite de commandes développeur Visual Studio :

   ::: moniker range="vs-2017"

   Dans le menu **Démarrer** de Windows, choisissez **Visual Studio 2017** > **invite de commandes développeur pour vs 2017**.

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   Dans le menu **Démarrer** de Windows, choisissez **Visual Studio 2019** > **invite de commandes développeur pour vs 2019**.

   ::: moniker-end

2. Entrez une commande semblable à la suivante :

   ```cmd
   vstest.console.exe MyTestAssembly.dll /EnableCodeCoverage /Settings:CodeCoverage.runsettings
   ```

   or

   ```cmd
   vstest.console.exe --settings:test.runsettings test.dll
   ```

Pour plus d’informations, consultez [Options de ligne de commande VSTest.Console.exe](vstest-console-options.md).

## <a name="customize-tests"></a>Personnaliser des tests

Pour personnaliser vos tests en utilisant un fichier *.runsettings*, effectuez les étapes suivantes :

1. Ajoutez un fichier XML à votre solution Visual Studio et enregistrez-le sous le nom *test.runsettings*.

   > [!TIP]
   > Le nom du fichier n’a pas d’importance, à condition d’utiliser l’extension *.runsettings*.

2. Remplacez le contenu du fichier par le code XML de l’exemple qui suit, puis personnalisez-le selon vos besoins.

::: moniker range="vs-2017"

3. Dans le menu **Test**, choisissez **Paramètres de test** > **Sélectionner le fichier de paramètres des tests**. Accédez au fichier *.runsettings* que vous avez créé, puis sélectionnez **OK**.

::: moniker-end

::: moniker range=">=vs-2019"

3. Pour sélectionner le fichier de paramètres d’exécution, choisissez **Test** > **Sélectionner le fichier de paramètres**. Accédez au fichier *.runsettings* que vous avez créé, puis sélectionnez **OK**.

::: moniker-end

   > [!TIP]
   > Vous pouvez créer plusieurs fichiers *.runsettings* dans votre solution et en sélectionner un en tant que fichier de paramètres de test actif en fonction des besoins.

## <a name="example-runsettings-file"></a>Exemple de fichier *.runsettings*

Le code XML suivant illustre le contenu d’un fichier *.runsettings* type. Chaque élément du fichier est facultatif, car il a une valeur par défaut.

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
    </DataCollectors>
  </DataCollectionRunSettings>

  <!-- Parameters used by tests at run time -->
  <TestRunParameters>
    <Parameter name="webAppUrl" value="http://localhost" />
    <Parameter name="webAppUserName" value="Admin" />
    <Parameter name="webAppPassword" value="Password" />
  </TestRunParameters>

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

## <a name="elements-of-a-runsettings-file"></a>Éléments d’un fichier *.runsettings*

Les sections qui suivent détaillent les éléments d’un fichier *.runsettings*.

### <a name="run-configuration"></a>Configuration de série de tests

```xml
<RunConfiguration>
    <MaxCpuCount>1</MaxCpuCount>
    <ResultsDirectory>.\TestResults</ResultsDirectory>
    <TargetPlatform>x86</TargetPlatform>
    <TargetFrameworkVersion>Framework40</TargetFrameworkVersion>
    <TestAdaptersPaths>%SystemDrive%\Temp\foo;%SystemDrive%\Temp\bar</TestAdaptersPaths>
    <TestSessionTimeout>10000</TestSessionTimeout>
</RunConfiguration>
```

L’élément **RunConfiguration** peut inclure les éléments suivants :

|Nœud|Default|Valeurs|
|-|-|-|
|**ResultsDirectory**||Répertoire où les résultats des tests sont placés.|
|**TargetFrameworkVersion**|Framework40|`FrameworkCore10` pour les sources .NET Core, `FrameworkUap10` pour les sources UWP, `Framework45` pour .NET Framework 4.5 et versions ultérieures, `Framework40` pour .NET Framework 4.0 et `Framework35` pour .NET Framework 3.5.<br /><br />Ce paramètre spécifie la version du framework de tests unitaires qui est utilisée pour découvrir et exécuter les tests. Elle peut être différente de la version de la plateforme .NET. que vous spécifiez dans les propriétés de génération du projet de test unitaire.<br /><br />Si vous omettez l’élément `TargetFrameworkVersion` dans le fichier *.runsettings*, la plateforme détermine automatiquement la version du framework sur la base des fichiers binaires générés.|
|**TargetPlatform**|x86|x86, x64|
|**TreatTestAdapterErrorsAsWarnings**|false|false, true|
|**TestAdaptersPaths**||Un ou plusieurs chemins du répertoire où se trouvent les TestAdapters|
|**MaxCpuCount**|1|Ce paramètre permet de contrôler le degré d’exécution des tests parallèles lors des tests unitaires, en utilisant les cœurs disponibles sur la machine. Le moteur d’exécution des tests démarre en tant que processus distinct sur chaque cœur disponible et donne à chaque cœur un conteneur de tests à exécuter. Un conteneur peut être un assembly, une DLL ou un artefact approprié. Le conteneur de test est l’unité de planification. Dans chaque conteneur, les tests sont exécutés en fonction de l’infrastructure de tests configurée. S’il y a beaucoup de conteneurs, chaque processus reçoit le conteneur disponible suivant dès qu’il a terminé l’exécution des tests d’un conteneur.<br /><br />Valeur possible pour MaxCpuCount :<br /><br />n, où 1 < = n < = nombre de cœurs : jusqu’à n processus peuvent être lancés.<br /><br />n, où n = toute autre valeur : le nombre de processus lancés peut atteindre le nombre de cœurs disponibles. Par exemple, définissez n = 0 pour permettre à la plateforme de déterminer automatiquement le nombre optimal de processus à lancer en fonction de l’environnement.|
|**TestSessionTimeout**||Permet aux utilisateurs de mettre fin à une session de test lorsque celle-ci dépasse le délai spécifié. La définition d’un délai d’expiration garantit que les ressources sont consommées et que les sessions de test sont limitées à une durée spécifique. Le paramètre est disponible dans **Visual Studio 2017 versions 15.5** et ultérieures.|

### <a name="diagnostic-data-adapters-data-collectors"></a>Diagnostic des adaptateurs de données (collecteurs de données)

L’élément **DataCollectors** spécifie les paramètres des adaptateurs de données de diagnostic. Les adaptateurs de données de diagnostic rassemblent des informations supplémentaires sur l’environnement et sur l’application testée. Chaque adaptateur a des paramètres par défaut. Il vous suffit de fournir des paramètres si vous ne souhaitez pas utiliser les valeurs par défaut.

#### <a name="code-coverage-adapter"></a>Adaptateur de couverture du code

```xml
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
```

Le collecteur de données de couverture du code crée un journal des parties du code d’application qui ont été testées. Pour plus d’informations sur la personnalisation des paramètres pour la couverture du code, consultez [Personnaliser l’analyse de la couverture du code](../test/customizing-code-coverage-analysis.md).

#### <a name="video-data-collector"></a>Collecteur de données vidéo

Le collecteur de données vidéo capture un enregistrement de l’écran quand des tests sont exécutés. Cet enregistrement est utile pour résoudre les problèmes des tests d’interface utilisateur. Le collecteur de données vidéo est disponible dans **Visual Studio 2017 versions 15.5** et ultérieures.

Pour personnaliser un autre type d’adaptateur de données de diagnostic, utilisez un [fichier de paramètres de test](../test/collect-diagnostic-information-using-test-settings.md).

### <a name="testrunparameters"></a>TestRunParameters

```xml
<TestRunParameters>
    <Parameter name="webAppUrl" value="http://localhost" />
    <Parameter name="docsUrl" value="https://docs.microsoft.com" />
</TestRunParameters>
```

Les paramètres de série de tests offrent un moyen de définir des variables et des valeurs qui sont disponibles pour les tests au moment de l’exécution. Accédez aux paramètres à l’aide de la propriété <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext.Properties%2A?displayProperty=nameWithType> :

```csharp
[TestMethod]
public void HomePageTest()
{
    string appURL = TestContext.Properties["webAppUrl"];
}
```

Pour utiliser les paramètres de série de tests, ajoutez un champ <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext> privé et une propriété <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext> publique à votre classe de test.

### <a name="mstest-run-settings"></a>Paramètres d’exécution MSTest

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

Ces paramètres sont spécifiques à l’adaptateur de test qui exécute les méthodes de test disposant de l’attribut <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> .

|Configuration|Default|Valeurs|
|-|-|-|
|**ForcedLegacyMode**|false|Dans Visual Studio 2012, l’adaptateur MSTest a été optimisé afin d’être plus rapide et plus scalable. Un comportement, tel que l’ordre dans lequel les tests sont exécutés, peut ne pas être exactement identique à celui d’éditions précédentes de Visual Studio. Définissez cette valeur sur **true** pour utiliser l’adaptateur de test le plus ancien.<br /><br />Par exemple, vous pouvez utiliser ce paramètre si un fichier *app.config* est spécifié pour un test unitaire.<br /><br />Il est recommandé d’envisager de refactoriser vos tests pour vous permettre d’utiliser le nouvel adaptateur.|
|**IgnoreTestImpact**|false|La fonctionnalité d’impact de test classe par priorité les tests affectés par des modifications récentes, lorsqu’ils sont exécutés dans MSTest ou à partir de Microsoft Test Manager. Ce paramètre désactive la fonctionnalité. Pour plus d’informations, consultez [Quels tests doivent être exécutés depuis une version antérieure ?](https://msdn.microsoft.com/library/dd286589).|
|**SettingsFile**||Vous pouvez spécifier un fichier de paramètres de test à utiliser avec l’adaptateur MSTest ici. Vous pouvez également spécifier un fichier de paramètres de test à partir du [menu de paramètres](#ide).<br /><br />Si vous spécifiez cette valeur, vous devez également affecter à **ForcedlegacyMode** la valeur **true**.<br /><br />`<ForcedLegacyMode>true</ForcedLegacyMode>`|
|**KeepExecutorAliveAfterLegacyRun**|false|Une fois qu’une série de tests est terminée, MSTest est arrêté. Tout processus qui est lancé dans le cadre du test est également terminé. Si vous souhaitez conserver l’exécuteur de test actif, définissez la valeur sur **true**. Par exemple, vous pouvez utiliser ce paramètre pour que le navigateur continue à s’exécuter entre des tests codés de l’interface utilisateur.|
|**DeploymentEnabled**|true|Si vous définissez cette valeur sur **false**, les éléments de déploiement que vous avez spécifiés dans votre méthode de test ne sont pas copiés dans le répertoire de déploiement.|
|**CaptureTraceOutput**|true|Vous pouvez écrire dans la trace du débogage à partir de votre méthode de test en utilisant <xref:System.Diagnostics.Trace.WriteLine%2A?displayProperty=nameWithType>.|
|**DeleteDeploymentDirectoryAfterTestRunIsComplete**|true|Pour conserver le répertoire de déploiement après une série de tests, définissez cette valeur sur **false**.|
|**MapInconclusiveToFailed**|false|Si un test se termine avec un état Non concluant, il est mappé à l’état Ignoré dans **l’Explorateur de tests**. Si vous voulez que les tests non concluants s’affichent comme ayant échoué, définissez la valeur sur **true**.|
|**InProcMode**|false|Si vous souhaitez que vos tests soient exécutés dans le même processus que l’adaptateur de test Microsoft, définissez cette valeur sur **true**. Ce paramètre offre un gain de performances mineur. Mais si un test s’arrête à cause d’une exception, les tests restants ne s’exécutent pas.|
|**AssemblyResolution**|false|Vous pouvez spécifier des chemins d’assemblys supplémentaires pour la recherche et l’exécution des tests unitaires. Par exemple, utilisez ces chemins pour les assemblys de dépendance qui ne se trouvent pas dans le même répertoire que l’assembly de test. Pour spécifier un chemin, utilisez un élément **Directory Path**. Les chemins peuvent inclure des variables d’environnement.<br /><br />`<AssemblyResolution>  <Directory Path="D:\myfolder\bin\" includeSubDirectories="false"/> </AssemblyResolution>`|

## <a name="see-also"></a>Voir aussi

- [Configurer une série de tests](https://github.com/microsoft/vstest-docs/blob/master/docs/configure.md)
- [Personnaliser l’analyse de la couverture du code](../test/customizing-code-coverage-analysis.md)
- [Tâche de test Visual Studio (Azure Test Plans)](/azure/devops/pipelines/tasks/test/vstest?view=vsts)
