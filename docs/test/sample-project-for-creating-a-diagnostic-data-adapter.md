---
title: Exemple de projet pour la création d’un adaptateur de données de diagnostic dans Visual Studio | Microsoft Docs
ms.date: 10/19/2016
ms.topic: article
helpviewer_keywords:
- Diagnostic Data Adapter [Visual Studio ALM]
- samples. Diagnostic Data Adapter [Visual Studio ALM]
- Diagnostic Data Adapter, sample
ms.assetid: 548bdc5e-338f-4be7-a555-e6a2efb1df6b
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-test
ms.openlocfilehash: 0b37512405442b327bb4b9688a39bfc4c99ea594
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2018
---
# <a name="sample-project-for-creating-a-diagnostic-data-adapter"></a>Exemple de projet pour la création d'un adaptateur de données de diagnostic

"MyDiagnosticDataAdapter" est un adaptateur de données de diagnostic simple qui peut attacher un fichier journal aux résultats des tests lorsque vous exécutez vos tests.

 Vous devez disposer d'autorisations d'administration sur l'ordinateur où sont installés le collecteur de données de diagnostic ou l'éditeur de configuration.

## <a name="example-data-adapter"></a>Exemple d’adaptateur de données

Cet exemple montre comment effectuer les tâches suivantes :

-   Appliquer des attributs permettant de rendre une classe détectable par Microsoft Test Manager en tant qu’adaptateur de données de diagnostic.

-   Appliquer des attributs permettant de rendre une classe de contrôle utilisateur détectable par Microsoft Test Manager en tant qu’éditeur à utiliser pour modifier la configuration d’un adaptateur de données de diagnostic.

-   Accéder aux données de configuration par défaut.

-   S'inscrire pour des événements de collecte de données de diagnostic spécifiques.

-   Attacher le fichier journal en l'envoyant à <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionSink>.

```csharp
// My Data Collector Class
using Microsoft.VisualStudio.TestTools.Common;
using Microsoft.VisualStudio.TestTools.Execution;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Xml;
using System;

namespace MyCompany.MyDiagnosticDataAdapters
{
    // Provide a URI and friendly name for your diagnostic data adapter
    [DataCollectorTypeUri("datacollector://MyCompany/MyDataCollector/1.0")]
    [DataCollectorFriendlyName("Collect Log Files sample", false)]
    // Designate your chosen configuration editor
    [DataCollectorConfigurationEditor(
        "configurationeditor://MyCompany/MyDataConfigEditor/1.0")]
    public class MyDataCollector : DataCollector
    {
        private DataCollectionEvents dataEvents;
        private DataCollectionLogger dataLogger;
        private DataCollectionSink dataSink;
        private XmlElement configurationSettings;

        // Required method called by the testing framework
        public override void Initialize(
            XmlElement configurationElement,
            DataCollectionEvents events,
            DataCollectionSink sink,
            DataCollectionLogger logger,
            DataCollectionEnvironmentContext environmentContext)
        {
            dataEvents = events; // The test events
            dataLogger = logger; // The error and warning log
            dataSink = sink;     // Saves collected data
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
            dataEvents.DataRequest +=
                new EventHandler<DataRequestEventArgs>(OnDataRequest);
        }

        protected override void Dispose(bool disposing)
        {
            if (disposing)
            {
                dataEvents.SessionStart -=
                    new EventHandler<SessionStartEventArgs>(OnSessionStart);
                dataEvents.SessionEnd -=
                    new EventHandler<SessionEndEventArgs>(OnSessionEnd);
                dataEvents.TestCaseStart -=
                    new EventHandler<TestCaseStartEventArgs>(OnTestCaseStart);
                dataEvents.TestCaseEnd -=
                    new EventHandler<TestCaseEndEventArgs>(OnTestCaseEnd);
                dataEvents.DataRequest -=
                    new EventHandler<DataRequestEventArgs>(OnDataRequest);
            }
        }

        #region Event Handlers
        public void OnSessionStart(object sender, SessionStartEventArgs e)
        {
            // TODO: Provide implementation
        }

        public void OnSessionEnd(object sender, SessionEndEventArgs e)
        {
            // TODO: Provide implementation
        }

        public void OnTestCaseStart(object sender, TestCaseEventArgs e)
        {
            // TODO: Provide implementation
        }

        public void OnTestCaseEnd(object sender, TestCaseEndEventArgs e)
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

        public void OnDataRequest(object sender, DataRequestEventArgs e)
        {
            // TODO: Provide implementation
            // Most likely this occurs because a bug is being filed
        }
        #endregion

        // A private method to collect the configured file names
        private List<string> getFilesToCollect()
        {
            // Seetup namespace manager with our namespace
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
    }
}
```

## <a name="example-configuration-editor"></a>Exemple d’éditeur de configuration

Il s'agit d'un exemple d'éditeur de configuration pour votre adaptateur de données de diagnostic. Ajoutez un contrôle utilisateur à votre projet et créez un formulaire très simple avec une étiquette (« Nom du fichier journal : ») et une zone de texte nommée « FileTextBox ».

```csharp
using Microsoft.VisualStudio.TestTools.Common;
using Microsoft.VisualStudio.TestTools.Execution;
using System.Collections.Generic;
using System.ComponentModel;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Windows.Forms;
using System.Xml;
using System;

namespace MyCompany.DiagnosticDataAdapters.ConfigurationEditors
{
    [DataCollectorConfigurationEditorTypeUri(
        "configurationeditor://MyCompany/MyConfigEditor/1.0")]
    public partial class MyDataConfigEditor :
        UserControl, IDataCollectorConfigurationEditor
    {
        private DataCollectorSettings collectorSettings;

        // Create a private property for the service provider
        private IServiceProvider ServiceProvider { get; set; }

        // Constructor
        public MyConfigurationEditor()
        {
            InitializeComponent();
        }

        // Required method called by the testing framework
        public void Initialize(
            IServiceProvider svcProvider,
            DataCollectorSettings settings)
        {
            ServiceProvider = svcProvider;
            collectorSettings = settings;

            // Display the file name as listed in the settings file.
            // If the configuration has not been updated before, this
            // data will be provided by the default configuration
            // section from <nameofcollector>.dll.config:
            // <DefaultConfiguration>
            //   <MyCollectorName
            //       xmlns="http://MyCompany/schemas/ProductName/Version");
            //     <File FullPath="C:\temp\logfile1.txt" />
            //   </MyCollectorName>
            // </DefaultConfiguration>
            this.SuspendLayout();
            this.FileTextBox.Text = GetText(collectorSettings.Configuration);
            this.ResumeLayout();
        }

        // Can be used to verify data before saving it
        public bool VerifyData()
        {
            // Not currently verifying data
            return true;
        }

        // Reset to default value from XML configuration
        // using a custom method
        public void ResetToAgentDefaults()
        {
            this.FileTextBox.Text =
                getText(collectorSettings.DefaultConfiguration);
        }

        // Saves data changed in the editor to the test configuration
        // settings. Does not change the default value.
        public DataCollectorSettings SaveData()
        {
            collectorSettings.Configuration.InnerXml =
                String.Format(
                    @"<MyCollectorName
      xmlns=""http://MyCompany/schemas/MyDataCollector/1.0"">
  <File FullPath=""{0}"" />
</MyCollectorName>",
                    FileTextBox.Text);
            return collectorSettings;
        }

        // Reads the configuration settings
        private string getText(XmlElement element)
        {
            // Setup namespace manager with our namespace
            XmlNamespaceManager nsmgr =
                new XmlNamespaceManager(
                    element.OwnerDocument.NameTable);

            // Find all the "File" elements under our configuration
            XmlNodeList files = element.SelectNodes("//ns:MyDataCollector/ns:File", nsmgr);

            string result = String.Empty;
            if (files.Count > 0)
            {
                XmlAttribute pathAttribute = files[0].Attributes["FullPath"];
                if (pathAttribute != null &&
                    !String.IsNullOrEmpty(pathAttribute.Value))
                {
                    result = pathAttribute.Value;
                }
            }

            return result;
        }
    }
}
```

## <a name="example-configuration-file"></a>Exemple de fichier de configuration

Voici un exemple de fichier de configuration pour votre éditeur de configuration de collecteur de données de diagnostic.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <configSections>
    <section
      name="DataCollectorConfiguration"
      type="Microsoft.VisualStudio.QualityTools.Execution.DataCollectorConfigurationSection,
        Microsoft.visualStudio.QualityTools.ExecutionCommon,
        Version=4.0.0.0, Culture=neutral,
        PublicKeyToken=b03f5f7f11d50a3a" />
  </configSections>
  <DataCollectorConfiguration
      xmlns="http://microsoft.com/schemas/VisualStudio/TeamTest/11">
    <DataCollector
        typeUri="datacollector://MyCompany/MyDataCollector/1.0">
      <DefaultConfiguration>
        <!-- Your default config settings-->
        <File FullPath="c:\temp\logfile1.txt" />
      </DefaultConfiguration>
    </DataCollector>
  </DataCollectorConfiguration>
</configuration>

```

## <a name="compiling-the-code"></a>Compilation du code

### <a name="to-create-the-code-project-for-this-diagnostic-adapter"></a>Pour créer le projet de code pour cet adaptateur de diagnostic

1.  Créez un projet de bibliothèque de classes nommé "MyDataCollector".

2.  Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur le projet, puis choisissez **Propriétés**. Pour sélectionner un dossier à ajouter, choisissez **Chemins d’accès des références**, puis le bouton de sélection (**…**).

     La boîte de dialogue **Sélectionner le chemin d’accès de référence** s’affiche.

3.  Sélectionnez le chemin suivant, qui dépend de votre répertoire d’installation : *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\PrivateAssemblies*. Cliquez sur **OK**.

4.  Pour ajouter le dossier à votre chemin de référence, choisissez **Ajouter un dossier**.

     Le dossier s’affiche dans la liste des chemins d’accès de référence.

5.  Choisissez l’icône **Enregistrer tout** pour enregistrer les chemins de référence.

6.  Ajoutez l’assembly **Microsoft.VisualStudio.QualityTools.ExecutionCommon**.

    1.  Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur **Références**, puis choisissez **Ajouter une référence**.

    2.  Choisissez **Parcourir** et recherchez **Microsoft.VisualStudio.QualityTools.ExecutionCommon.dll**.

         Cet assembly se trouve dans *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\PrivateAssemblies*.

    3.  Cliquez sur **OK**.

7.  Ajoutez l’assembly **Microsoft.VisualStudio.QualityTools.Common**.

    1.  Dans l’Explorateur de solutions, cliquez avec le bouton droit sur **Références** et sélectionnez **Ajouter une référence**.

    2.  Choisissez **Parcourir** et recherchez **Microsoft.VisualStudio.QualityTools.Common.dll**.

         Cet assembly se trouve dans *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\PrivateAssemblies*.

    3.  Cliquez sur **OK**.

8.  Copiez la classe d'adaptateur de données de diagnostic indiquée précédemment dans ce document dans la classe de votre bibliothèque de classes. Enregistrez cette classe.

9. Pour ajouter un contrôle utilisateur au projet, cliquez avec le bouton droit sur le projet MyDataCollector dans l’Explorateur de solutions, pointez sur **Ajouter**, puis choisissez **Contrôle utilisateur**. Sélectionnez **Ajouter**.

10. À l’aide de la boîte à outils, ajoutez une étiquette au contrôle utilisateur et remplacez la valeur de la propriété Text par **Nom de fichier :**.

11. À l’aide de la boîte à outils, ajoutez une zone de texte au contrôle utilisateur et remplacez le nom par **textBoxFileName**.

12. Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur le contrôle utilisateur, puis choisissez **Afficher le code**. Remplacez cette classe de contrôle utilisateur par celle indiquée précédemment dans ce document. Enregistrez cette classe.

    > [!NOTE]
    > Par défaut, le contrôle utilisateur est nommé UserControl1. Assurez-vous que le code de classe du contrôle utilisateur utilise le nom de votre contrôle utilisateur.

13. Pour créer le fichier de configuration, dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur la solution, pointez sur **Ajouter**, puis choisissez **Nouvel élément**. Choisissez **Fichier de configuration de l’application**, puis **Ajouter**. Un fichier nommé **App.config** est alors ajouté à votre solution.

14. Copiez le code XML de l'exemple fourni précédent dans le fichier XML. Enregistrez le fichier.

15. Générez la solution, puis copiez l’assembly généré et le fichier `App.config` dans le répertoire *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\PrivateAssemblies\DataCollectors*.

16. Créez des paramètres de test qui utilisent cet adaptateur de données de diagnostic personnalisé. Configurez les paramètres de test pour collecter un fichier existant.

     Si vous exécutez vos tests à partir de Microsoft Test Manager, vous pouvez affecter ces paramètres de test à votre plan de test avant d’exécuter vos tests, ou utiliser la commande Exécuter avec des options pour affecter et remplacer des paramètres de test. Pour plus d’informations sur les paramètres de test, consultez [Collecter des informations de diagnostic avec des paramètres de test](../test/collect-diagnostic-information-using-test-settings.md).

17. Exécutez vos tests à l'aide des paramètres de test, en sélectionnant votre adaptateur de données de diagnostic.

     Le fichier de données que vous avez spécifié est attaché à vos résultats de tests lors de l'exécution du test.

## <a name="see-also"></a>Voir aussi

- [Guide pratique pour créer un adaptateur de données de diagnostic](../test/how-to-create-a-diagnostic-data-adapter.md)
- [Guide pratique pour créer un éditeur personnalisé pour les données de votre adaptateur de données de diagnostic](../test/how-to-create-a-custom-editor-for-data-for-your-diagnostic-data-adapter.md)
- [Guide pratique pour installer un adaptateur de données de diagnostic personnalisé](../test/how-to-install-a-custom-diagnostic-data-adapter.md)
- [Création d’un adaptateur de données de diagnostic pour collecter des données personnalisées ou affecter un ordinateur de test](../test/create-a-diagnostic-data-adapter-to-collect-custom-data-or-affect-a-test-machine.md)