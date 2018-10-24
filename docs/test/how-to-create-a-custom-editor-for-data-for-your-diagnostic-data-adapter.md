---
title: Créer un éditeur de données personnalisé pour un adaptateur de données de diagnostic dans Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Diagnostic Data Adapter, creating custom editor
ms.assetid: 24970227-d1ea-4f6d-9839-e911478848ba
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 41008d1c2808a5a6e6428670a3e7dbbf1041caee
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49819337"
---
# <a name="how-to-create-a-custom-editor-for-data-for-your-diagnostic-data-adapter"></a>Guide pratique pour créer un éditeur personnalisé pour les données de votre adaptateur de données de diagnostic

Durant la création d’un adaptateur de données de diagnostic, vous souhaiterez peut-être que l’utilisateur final puisse configurer des données spécifiques si votre adaptateur de données de diagnostic personnalisé est sélectionné pour ses paramètres de test. Par exemple, vous pouvez sélectionner les données de configuration qui spécifient les clés de Registre à extraire, le niveau de charge réseau à simuler ou le répertoire dans lequel doivent se trouver les fichiers temporaires ou les fichiers de travail à joindre.

Vous devez utiliser un fichier de configuration pour configurer les valeurs initiales de votre adaptateur de données de diagnostic. Vous pouvez fournir un éditeur personnalisé pour permettre à l'utilisateur de modifier les données de configuration.

Pour créer votre propre éditeur, vous devez définir un contrôle utilisateur qui implémente <xref:Microsoft.VisualStudio.TestTools.Execution.IDataCollectorConfigurationEditor>.

Votre adaptateur de données de diagnostic peut utiliser <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationEditorAttribute> pour spécifier la classe d'éditeur à employer pour la modification des paramètres de configuration des données de diagnostic.

Vous pouvez également spécifier les données de configuration par défaut que vous voulez utiliser.  Pour obtenir un exemple de configuration par défaut, consultez [Exemple de projet pour la création d’un adaptateur de données de diagnostic](../test/sample-project-for-creating-a-diagnostic-data-adapter.md).

Utilisez la procédure suivante pour créer un éditeur personnalisé permettant de mettre à jour les données relatives à vos paramètres de test lorsque vous employez votre adaptateur de données de diagnostic personnalisé.

> [!NOTE]
> Pour créer un éditeur personnalisé, vous devez d'abord créer votre adaptateur de données de diagnostic en appliquant <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationEditorAttribute> à la classe. Vous pouvez utiliser la propriété <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationEditorAttribute.HelpUri*> facultative dans cet attribut pour spécifier la source de contenu d'aide de votre éditeur. Pour plus d’informations sur la création de votre adaptateur de données de diagnostic, consultez [Guide pratique pour créer un adaptateur de données de diagnostic](../test/how-to-create-a-diagnostic-data-adapter.md).

Pour obtenir un exemple complet de projet d’adaptateur de données de diagnostic, notamment un éditeur de configuration personnalisé, consultez [Exemple de projet pour la création d’un adaptateur de données de diagnostic](../test/sample-project-for-creating-a-diagnostic-data-adapter.md).

## <a name="to-create-a-custom-editor-for-your-diagnostic-data-adapter"></a>Pour créer un éditeur personnalisé pour votre adaptateur de données de diagnostic

1. Créez un contrôle utilisateur dans le projet pour votre adaptateur de données de diagnostic :

   1.  Cliquez avec le bouton droit sur le projet de code qui contient votre classe d’adaptateur de données de diagnostic, puis pointez sur **Ajouter** et sur **Contrôle utilisateur**.

   2.  Pour cet exemple, ajoutez une étiquette au formulaire avec le texte **Nom du fichier de données :** et une zone de texte nommée **ZoneTexteFichier** qui permet à l’utilisateur d’entrer les données nécessaires.

   > [!NOTE]
   > Seuls les contrôles utilisateur Windows Forms sont actuellement pris en charge.

2. Ajoutez ces lignes à la section de déclaration :

   ```csharp
   using System.Xml;
   using Microsoft.VisualStudio.TestTools.Common;
   using Microsoft.VisualStudio.TestTools.Execution;
   ```

3. Définissez ce contrôle utilisateur en tant qu'éditeur personnalisé.

   1.  Cliquez avec le bouton droit sur le contrôle utilisateur dans votre projet de code et pointez sur **Afficher le code**.

   2.  Définissez la classe permettant d'implémenter l'interface de l'éditeur <xref:Microsoft.VisualStudio.TestTools.Execution.IDataCollectorConfigurationEditor> comme suit :

   ```csharp
   public partial class MyDataConfigEditor :
        UserControl, IDataCollectorConfigurationEditor
   ```

   1.  Cliquez avec le bouton droit sur <xref:Microsoft.VisualStudio.TestTools.Execution.IDataCollectorConfigurationEditor> dans le code, puis sélectionnez la commande **Implémenter l’interface**. Les méthodes que vous devez implémenter pour cette interface sont ajoutées à votre classe.

   2.  Ajoutez la classe <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationEditorAttribute> au contrôle utilisateur de votre éditeur afin d’identifier ce dernier comme un éditeur d’adaptateurs de données de diagnostic. Pour ce faire, remplacez **Company**, **Product** et **Version** par les informations appropriées pour votre adaptateur de données de diagnostic :

       ```csharp
       [DataCollectorConfigurationEditorTypeUri(
           "configurationeditor://MyCompany/MyConfigEditor/1.0")]
       ```

4. Ajoutez deux variables privées comme suit :

   ```csharp
   private DataCollectorSettings collectorSettings;
   private IServiceProvider ServiceProvider { get; set; }
   ```

5. Ajoutez du code pour initialiser votre éditeur pour votre adaptateur de données de diagnostic. Vous pouvez ajouter des valeurs par défaut aux champs de votre contrôle utilisateur à l'aide des données de la variable de paramètre. Il s'agit des données figurant dans l'élément `<DefaultConfiguration>` du fichier de configuration XML de votre adaptateur.

   ```csharp
   public void Initialize(
       IServiceProvider svcProvider,
       DataCollectorSettings settings)
   {
       ServiceProvider = svcProvider;
       collectorSettings = settings;

       // Display the default file name as listed in the settings file.
       this.SuspendLayout();
       this.FileTextBox.Text = getText(collectorSettings.Configuration);
       this.ResumeLayout();
   }
   ```

6. Ajoutez du code pour réenregistrer les données de vos contrôles dans votre éditeur au format XML requis par l'API d'adaptateur de données de diagnostic comme suit :

   ```csharp
   public DataCollectorSettings SaveData()
   {
       collectorSettings.Configuration.InnerXml =
           String.Format(
   @"<MyCollectorName
       xmlns=""http://MyCompany/schemas/MyDiagnosticDataCollector/1.0"">
     <File FullPath=""{0}"" />
   </MyCollectorName>",
       FileTextBox.Text);
       return collectorSettings;
   }
   ```

7. Si cela est important, ajoutez du code pour vérifier que les données sont correctes dans la méthode `VerifyData` ; la méthode peut aussi simplement retourner la valeur `true`.

   ```csharp
   public bool VerifyData()
   {
       // Not currently verifying data
       return true;
   }
   ```

8. (Facultatif) Vous pouvez ajouter du code à la méthode `ResetToAgentDefaults()`, qui utilise la méthode `getText()` privée, pour réinitialiser les données aux paramètres initiaux fournis dans le fichier de configuration XML.

   ```csharp
   // Reset to default value from XML configuration
   // using a custom getText() method
   public void ResetToAgentDefaults()
   {
       this.FileTextBox.Text = getText(collectorSettings.DefaultConfiguration);
   }

   // Local method to read the configuration settings
   private string getText(XmlElement element)
   {
       // Setup namespace manager with our namespace
       XmlNamespaceManager nsmgr =
           new XmlNamespaceManager(
               element.OwnerDocument.NameTable);

       // Find all the "File" elements under our configuration
       XmlNodeList files = element.SelectNodes("//ns:MyCollectorName/ns:File", nsmgr);

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
   ```

9. Générez votre solution. Copiez l’assembly d’adaptateur de données de diagnostic et le fichier de configuration XML (`<diagnostic data adapter name>.dll.config`) à l’emplacement suivant, en fonction de votre répertoire d’installation : *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\PrivateAssemblies\DataCollectors*.

    > [!NOTE]
    > Bien que l'éditeur de configuration et l'adaptateur de données de diagnostic puissent se trouver dans un projet et un assembly différents, ils peuvent également se trouver dans le même assembly.

10. Pour utiliser votre adaptateur de données de diagnostic lors de tests, vous devez effectuer une sélection dans la liste des paramètres de test existants, ou bien créer une liste à partir de Microsoft Test Manager ou de Visual Studio, puis sélectionner dans celle-ci votre adaptateur de données de diagnostic.

     L’adaptateur s’affiche sous l’onglet **Données et diagnostics** de vos paramètres de test avec le nom convivial que vous avez assigné à la classe.

11. Pour configurer votre adaptateur de données de diagnostic pour vos paramètres de test, choisissez **Configurer** en regard du nom de l’adaptateur.

     Votre éditeur personnalisé s'affiche.

12. Apportez les modifications requises aux champs de votre éditeur personnalisé, puis choisissez **Enregistrer**.

13. Si vous exécutez vos tests à partir de Microsoft Test Manager, vous pouvez affecter ces paramètres de test à votre plan de test avant d’exécuter vos tests, ou utiliser la commande **Exécuter avec des options** pour affecter et remplacer des paramètres de test. Pour plus d’informations sur les paramètres de test, consultez [Collecter des informations de diagnostic à l’aide des paramètres de test](../test/collect-diagnostic-information-using-test-settings.md).

14. Avant de pouvoir utiliser votre nouvel éditeur de configuration avec un adaptateur de données de diagnostic, vous devez appliquer <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationEditorAttribute> à chaque classe d'adaptateur de données de diagnostic à employer dans l'éditeur, puis les recompiler et les réinstaller sur l'ordinateur client. Pour plus d’informations sur l’installation d’adaptateurs de données de diagnostic et d’éditeurs de configuration, consultez [Guide pratique pour installer un adaptateur de données de diagnostic personnalisé](../test/how-to-install-a-custom-diagnostic-data-adapter.md).

15. Exécutez vos tests à l'aide des paramètres de test, en sélectionnant votre adaptateur de données de diagnostic.

     Le fichier de données que vous avez spécifié dans votre éditeur est joint à vos résultats de tests.

    Pour plus d’informations sur la configuration de vos paramètres de test pour l’utilisation d’un environnement lors de l’exécution de vos tests, consultez [Collecter des données de diagnostic durant les tests (Azure Test Plans)](/azure/devops/test/collect-diagnostic-data?view=vsts) ou [Collecter des données de diagnostic dans les tests manuels (Azure Test Plans)](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts).

## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualStudio.TestTools.Execution.IDataCollectorConfigurationEditor>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationEditorAttribute>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationEditorAttribute>
- [Créer un adaptateur de données de diagnostic pour collecter des données personnalisées ou affecter une machine de test](../test/create-a-diagnostic-data-adapter-to-collect-custom-data-or-affect-a-test-machine.md)
- [Collecter des informations de diagnostic à l’aide des paramètres de test](../test/collect-diagnostic-information-using-test-settings.md)
- [Exemple de projet pour la création d’un adaptateur de données de diagnostic](../test/sample-project-for-creating-a-diagnostic-data-adapter.md)