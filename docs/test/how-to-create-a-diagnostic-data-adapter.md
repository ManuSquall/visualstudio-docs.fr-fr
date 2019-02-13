---
title: 'Procédure : créer un adaptateur de données de diagnostic'
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Diagnostic Data Adapter, creating
ms.assetid: bd7ad36c-54cb-4d2a-9aea-9d10ad98d7ba
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 3f00ff0f794bec43a6d81bf4303488885d901bcb
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55914017"
---
# <a name="how-to-create-a-diagnostic-data-adapter"></a>Procédure : Créer un adaptateur de données de diagnostic

Pour créer un *adaptateur de données de diagnostic*, vous devez créer une bibliothèque de classes à l’aide de Visual Studio, puis ajouter à cette dernière les API d’adaptateur de données de diagnostic fournies par Visual Studio Enterprise. Envoyez toutes les informations que vous voulez sous forme de flux de données ou de fichier au <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionSink> fourni par l’infrastructure durant la gestion des événements déclenchés pendant la série de tests. Les flux de données ou les fichiers envoyés au <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionSink> sont stockés en tant que pièces jointes aux résultats des tests lorsque votre test est terminé. Si vous créez un bogue à partir de ces résultats de tests ou quand vous utilisez [!INCLUDE[mtrlong](../test/includes/mtrlong_md.md)], les fichiers sont également liés au bogue.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Vous pouvez créer un adaptateur de données de diagnostic qui affecte l'ordinateur où vos tests sont exécutés, ou un ordinateur qui fait partie de l'environnement que vous utilisez pour exécuter votre application testée. Il est par exemple possible de collecter des fichiers sur l’ordinateur de test où sont exécutés les tests ou sur l’ordinateur ayant le rôle de serveur web de l’application.

Vous pouvez attribuer à l’adaptateur de données de diagnostic un nom convivial qui s’affiche quand vous créez vos paramètres de test à l’aide de Microsoft Test Manager ou de Visual Studio. Les paramètres de test vous permettent de définir le rôle d'ordinateur qui exécutera des adaptateurs de données de diagnostic spécifiques dans votre environnement lors de l'exécution de vos tests. Vous pouvez également configurer vos adaptateurs de données de diagnostic lorsque vous créez vos paramètres de test. Il est par exemple possible de créer un adaptateur de données de diagnostic qui collecte des journaux personnalisés auprès de votre serveur web. Lorsque vous créez vos paramètres de test, vous pouvez choisir d’exécuter cet adaptateur de données de diagnostic sur le ou les ordinateurs qui prennent en charge ce rôle de serveur web et modifier la configuration de vos paramètres de test de façon à collecter uniquement les trois derniers journaux créés. Pour plus d’informations sur les paramètres de test, consultez [Collecter des informations de diagnostic à l’aide des paramètres de test](../test/collect-diagnostic-information-using-test-settings.md).

Les événements sont déclenchés lorsque vous exécutez vos tests afin que votre adaptateur de données de diagnostic puisse exécuter des tâches à ce stade du test.

> [!IMPORTANT]
> Ces événements peuvent être déclenchés sur différents threads, en particulier lorsque les tests s'exécutent sur plusieurs ordinateurs. Par conséquent, vous devez savoir que des problèmes de threads peuvent survenir et veiller à ne pas endommager accidentellement les données internes de l'adaptateur personnalisé. Vérifiez que votre adaptateur de données de diagnostic est thread-safe.

Voici une liste partielle des principaux événements que vous pouvez utiliser lorsque vous créez votre adaptateur de données de diagnostic. Pour obtenir une liste complète des événements d'adaptateur de données de diagnostic, consultez la classe <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents> abstraite.

|événement|Description|
|-|-----------------|
|<xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.SessionStart>|Début de votre série de tests|
|<xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.SessionEnd>|Fin de votre série de tests|
|<xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.TestCaseStart>|Début de chaque test dans la série de tests|
|<xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.TestCaseEnd>|Fin de chaque test dans la série de tests|
|<xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.TestStepStart>|Début de chaque étape de test dans un test|
|<xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.TestStepEnd>|Fin de chaque étape de test dans un test|

> [!NOTE]
> Lorsqu’un test manuel est terminé, plus aucun événement de collection de données n’est envoyé à l’adaptateur de données de diagnostic. Lorsqu'un test est réexécuté, un nouvel identificateur de cas de test lui est affecté. Si un utilisateur réinitialise un test pendant son exécution (ce qui déclenche l’événement <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.TestCaseReset> ) ou modifie le résultat d’une étape de test, aucun événement de collection de données n’est envoyé à l’adaptateur de données de diagnostic, mais l’identificateur de cas de test reste inchangé. Pour déterminer si un cas de test a été réinitialisé, vous devez effectuer le suivi de l'identificateur de cas de test de votre adaptateur de données de diagnostic.

Utilisez la procédure suivante pour créer un adaptateur de données de diagnostic qui collecte un fichier de données basé sur les informations configurées lors de la création de vos paramètres de test.

Pour obtenir un exemple complet de projet d’adaptateur de données de diagnostic, notamment un éditeur de configuration personnalisé, consultez [Exemple de projet pour la création d’un adaptateur de données de diagnostic](../test/quickstart-create-a-load-test-project.md).

##  <a name="create-and-install-a-diagnostic-data-adapter"></a>Créer et installer un adaptateur de données de diagnostic

### <a name="to-create-and-install-a-diagnostic-data-adapter"></a>Pour créer et installer un adaptateur de données de diagnostic

1. Créer un nouveau projet de bibliothèque de classes.

   1.  Dans le menu **Fichier**, sélectionnez **Nouveau**, puis pointez sur **Nouveau projet**.

   2.  Dans **Types de projets**, sélectionnez la langue à utiliser.

   3.  Dans **Modèles Visual Studio installés**, sélectionnez **Bibliothèque de classes**.

   4.  Tapez un nom pour votre Adaptateur de données de diagnostic.

   5.  Cliquez sur **OK**.

2. Ajoutez l’assembly **Microsoft.VisualStudio.QualityTools.ExecutionCommon**.

   1.  Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur **Références**, puis sélectionnez la commande **Ajouter une référence**.

   2.  Choisissez **.NET** et recherchez **Microsoft.VisualStudio.QualityTools.ExecutionCommon.dll**.

   3.  Cliquez sur **OK**.

3. Ajoutez l’assembly **Microsoft.VisualStudio.QualityTools.Common**.

   1.  Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur **Références**, puis sélectionnez la commande **Ajouter une référence**.

   2.  Choisissez **/.NET** et recherchez **Microsoft.VisualStudio.QualityTools.Common.dll**.

   3.  Cliquez sur **OK**.

4. Ajoutez les instructions `using` suivantes à votre fichier de classe :

   ```csharp
   using Microsoft.VisualStudio.TestTools.Common;
   using Microsoft.VisualStudio.TestTools.Execution;
   using System.Linq;
   using System.Text;
   using System.Xml;
   using System;
   ```

5. Ajoutez <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorTypeUriAttribute> à la classe de votre adaptateur de données de diagnostic pour l’identifier comme un adaptateur de données de diagnostic, en remplaçant **Company**, **Product** et **Version** par les informations appropriées pour votre adaptateur de données de diagnostic :

   ```csharp
   [DataCollectorTypeUri("datacollector://Company/Product/Version")]
   ```

6. Ajoutez l'attribut <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorFriendlyNameAttribute> à la classe, en remplaçant les paramètres par les informations appropriées pour votre Adaptateur de données de diagnostic :

   ```csharp
   [DataCollectorFriendlyName("Collect Log Files", false)]
   ```

    Ce nom convivial est affiché dans l'activité de paramètres test.

   > [!NOTE]
   > Vous pouvez également ajouter le <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationEditorAttribute> pour spécifier le `Type` de votre éditeur de configuration personnalisée pour cet adaptateur de données, et indiquer éventuellement le fichier d'aide à utiliser pour l'éditeur.
   >
   > Vous pouvez également appliquer le <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorEnabledByDefaultAttribute> pour indiquer qu'il doit toujours être activé.

7. La classe de l'adaptateur de données de diagnostic doit hériter de la classe <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollector> comme suit :

   ```csharp
   public class MyDiagnosticDataAdapter : DataCollector
   ```

8. Ajoutez les variables locales comme suit :

   ```csharp
   private DataCollectionEvents dataEvents;
   private DataCollectionLogger dataLogger;
   private DataCollectionSink dataSink;
   private XmlElement configurationSettings;
   ```

9. Ajoutez la méthode <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollector.Initialize*> et une méthode **Dispose**. Dans la méthode `Initialize`, vous pouvez initialiser le récepteur de données, ainsi que toutes les données de configuration des paramètres de test, et inscrire les gestionnaires d'événements à utiliser comme suit :

    ```csharp
    public override void Initialize(
        XmlElement configurationElement,
        DataCollectionEvents events,
        DataCollectionSink sink,
        DataCollectionLogger logger,
        DataCollectionEnvironmentContext environmentContext)
    {
           dataEvents = events;  // The test events
           dataLogger = logger;  // The error and warning log
           dataSink = sink;      // Saves collected data
           // Configuration from the test settings
           configurationSettings = configurationElement;

           // Register common events for the data collector
           // Not all of the events are used in this class
        dataEvents.SessionStart +=
            new EventHandler<SessionStartEventArgs>(OnSessionStart);
        dataEvents.SessionEnd +=
            new EventHandler<SessionEndEventArgs>(OnSessionEnd);
        dataEvents.TestCaseStart +=
            new EventHandler<TestCaseStartEventArgs>(OnTestCaseStart);
        dataEvents.TestCaseEnd +=
            new EventHandler<TestCaseEndEventArgs>(OnTestCaseEnd);
    }

    public override void Dispose(bool disposing)
    {
        if (disposing)
        {
            // Unregister the registered events
            dataEvents.SessionStart -=
                new EventHandler<SessionStartEventArgs>(OnSessionStart);
            dataEvents.SessionEnd -=
                new EventHandler<SessionEndEventArgs>(OnSessionEnd);
            dataEvents.TestCaseStart -=
                new EventHandler<TestCaseStartEventArgs>(OnTestCaseStart);
            dataEvents.TestCaseEnd -=
                new EventHandler<TestCaseEndEventArgs>(OnTestCaseEnd);
        }
    }
    ```

10. Utilisez le code de gestionnaire d'événements suivant et la méthode privée pour collecter le fichier journal générées pendant le test :

    ```csharp
    public void OnTestCaseEnd(sender, TestCaseEndEventArgs e)
    {
        // Get any files to be collected that are
        // configured in your test settings
        List<string> files = getFilesToCollect();

        // For each of the files, send the file to the data sink
        // which will attach it to the test results or to a bug
        foreach (string file in files)
        {
            dataSink.SendFileAsync(e.Context, file, false);
        }
    }

    // A private method that returns the file names
    private List<string> getFilesToCollect()
    {
        // Get a namespace manager with our namespace
        XmlNamespaceManager nsmgr =
            new XmlNamespaceManager(
                configurationSettings.OwnerDocument.NameTable);
        nsmgr.AddNamespace("ns",
            "http://MyCompany/schemas/MyDataCollector/1.0");

        // Find all of the "File" elements under our configuration
        XmlNodeList files =
            configurationSettings.SelectNodes(
                "//ns:MyDataCollector/ns:File");

        // Build the list of files to collect from the
        // "FullPath" attributes of the "File" nodes.
        List<string> result = new List<string>();
        foreach (XmlNode fileNode in files)
        {
            XmlAttribute pathAttribute =
                fileNode.Attributes["FullPath"];
            if (pathAttribute != null &&
                !String.IsNullOrEmpty(pathAttribute.Value))
            {
                result.Add(pathAttribute.Value);
            }
        }

        return result;
    }
    ```

     Ces fichiers sont joints aux résultats de test. Si vous créez un bogue à partir de ces résultats de tests ou lorsque vous utilisez [!INCLUDE[mtrlong](../test/includes/mtrlong_md.md)], les fichiers sont également joints au bogue.

     Si vous souhaitez utiliser votre propre éditeur pour collecter des données à utiliser dans vos paramètres de test, consultez [Guide pratique pour créer un éditeur personnalisé pour les données de votre adaptateur de données de diagnostic](../test/quickstart-create-a-load-test-project.md).

11. Pour collecter un fichier journal lorsqu’un test se termine en fonction des éléments configurés par l’utilisateur dans les paramètres de test, vous devez créer un fichier *App.config* et l’ajouter à votre solution. Ce fichier présente le format suivant et doit contenir l'URI de votre adaptateur de données de diagnostic pour l'identifier. Remplacez « Société/NomProduit/Version » par les vraies valeurs.

    > [!NOTE]
    > Si vous n'avez pas besoin de configurer les informations de votre adaptateur de données de diagnostic, vous n'avez pas besoin de créer un fichier de configuration.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <configuration>
      <configSections>
        <section name="DataCollectorConfiguration" type="Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationSection, Microsoft.VisualStudio.QualityTools.ExecutionCommon, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a "/>
      </configSections>
      <DataCollectorConfiguration xmlns="http://microsoft.com/schemas/VisualStudio/TeamTest/2010">
        <DataCollector typeUri="datacollector://MyCompany/MyProduct/1.0">
          <DefaultConfiguration>
            <!-- Your default config settings -->
            <Binaries>
              <Binary FullPath="C:\Example\Example.dll"/>
              <Binary FullPath="\\Server2\Example2.dll"/>
            </Binaries>
            <Symbols>
              <Symbol FullPath="\\ExampleServer\ExampleSymbol.pdb"/>
            </Symbols>
          </DefaultConfiguration>
        </DataCollector>
      </DataCollectorConfiguration>
    </configuration>
    ```

    > [!NOTE]
    > L'élément de configuration par défaut peut contenir les données dont vous avez besoin. Si l'utilisateur ne configure pas l'adaptateur de données de diagnostic dans les paramètres de test, les données par défaut seront transmises à votre adaptateur de données de diagnostic lorsqu'il est exécuté. Comme le code XML que vous ajoutez à la section `<DefaultConfigurations>` n'est pas susceptible de faire partie du schéma déclaré, vous pouvez ignorer les erreurs XML qu'il génère.
    >
    > Il existe d’autres exemples de fichiers config dans le chemin suivant en fonction de votre répertoire d’installation : *Program Files\Microsoft Visual Studio 10.0\Common7\IDE\PrivateAssemblies\DataCollectors*.

     Pour plus d’informations sur la configuration de vos paramètres de test pour l’utilisation d’un environnement durant l’exécution de vos tests, consultez [Collecter les données de diagnostic dans les tests manuels (Azure Test Plans)](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts).

     Pour plus d’informations sur l’installation du fichier config, consultez [Guide pratique pour installer un adaptateur de données de diagnostic personnalisé](../test/quickstart-create-a-load-test-project.md)

12. Générez votre solution pour créer votre assembly d'adaptateur de données de diagnostic.

13. Pour plus d’informations sur l’installation de votre éditeur personnalisé, consultez [Guide pratique pour installer un adaptateur de données de diagnostic personnalisé](../test/quickstart-create-a-load-test-project.md).

14. Pour plus d’informations sur la configuration de vos paramètres de test pour l’utilisation d’un environnement durant l’exécution de vos tests, consultez [Collecter les données de diagnostic dans les tests manuels (Azure Test Plans)](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts).

15. Pour sélectionner votre adaptateur de données de diagnostic, vous devez d’abord sélectionner des paramètres de test existants ou en créer dans Microsoft Test Manager ou Visual Studio. L’adaptateur s’affiche sous l’onglet **Données et diagnostics** de vos paramètres de test avec le nom convivial que vous avez assigné à la classe.

16. Définissez ces paramètres de test comme actifs. Pour plus d’informations sur les paramètres de test, consultez [Collecter des informations de diagnostic à l’aide des paramètres de test](../test/collect-diagnostic-information-using-test-settings.md).

17. Exécutez vos tests à l'aide des paramètres de test, en sélectionnant votre adaptateur de données de diagnostic.

    Le fichier de données que vous avez spécifié est joint à vos résultats de tests.

## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationEditorAttribute>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollector>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionSink>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorTypeUriAttribute>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorFriendlyNameAttribute>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorEnabledByDefaultAttribute>
- [Collecter des informations de diagnostic à l’aide des paramètres de test](../test/collect-diagnostic-information-using-test-settings.md)
- [Collecter les données de diagnostic dans des tests manuels (Azure Test Plans)](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts)
- [Collecter les données de diagnostic pendant les tests (Azure Test Plans)](/azure/devops/test/collect-diagnostic-data?view=vsts)
- [Guide pratique pour créer un éditeur personnalisé pour les données de votre adaptateur de données de diagnostic](../test/quickstart-create-a-load-test-project.md)