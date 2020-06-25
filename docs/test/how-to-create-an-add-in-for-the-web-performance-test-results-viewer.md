---
title: Créer un complément pour l’Afficheur de résultats de test de performances Web
ms.date: 10/20/2016
ms.topic: how-to
helpviewer_keywords:
- Web performance tests, Visual Studio Add-in
- Visual Studio Add-in, Web performance tests
ms.assetid: 1118c604-4b1b-4b21-a04e-45995b676fa8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 736c43a83a956c02b760b4909a427a82c6fa9e4c
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85287829"
---
# <a name="how-to-create-an-add-in-for-the-web-performance-test-results-viewer"></a>Comment : créer un complément pour la visionneuse de Résultats des tests performances de site Web

Pour étendre l’interface utilisateur de **l’Afficheur de résultats de test de performances web**, utilisez les espaces de noms suivants :

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting>

- <xref:Microsoft.VisualStudio.TestTools.WebTesting>

En outre, vous devez ajouter une référence à la DLL LoadTestPackage, qui se trouve dans le dossier *% ProgramFiles (x86)% \ Microsoft Visual Studio \\ \<version> \Enterprise\Common7\IDE\PrivateAssemblies* .

Pour étendre l’interface utilisateur de **l’Afficheur de résultats de test de performances web**, vous devez créer un complément Visual Studio et un contrôle utilisateur. Les procédures suivantes expliquent comment les créer et comment implémenter les classes nécessaires pour étendre l’interface utilisateur de **l’Afficheur de résultats de test de performances web**.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="create-or-open-a-solution-that-contains-an-aspnet-web-application-and-a-web-performance-and-load-test-project"></a>Créer ou ouvrir une solution contenant une application web ASP.NET et un projet de test de performances de site web et de charge

### <a name="to-prepare-for-extending-the-web-performance-test-results-viewer"></a>Pour préparer l'extension de l'Afficheur de résultats de test de performances Web

Créez ou ouvrez une solution qui ne soit pas en production et dans laquelle vous puissiez effectuer des tests. Elle doit contenir une application web ASP.NET et un projet de test de performances web et de charge comportant un ou plusieurs tests de performances web pour l’application web ASP.NET.

> [!NOTE]
> Vous pouvez créer une application Web ASP.NET et un projet de test de performances Web et de charge qui contient des tests de performances de site Web en suivant les procédures décrites dans [Comment : créer un test de service Web](../test/how-to-create-a-web-service-test.md) et [générer et exécuter un test de performances Web codé](../test/generate-and-run-a-coded-web-performance-test.md).

## <a name="create-a-visual-studio-add-in"></a>Créer un complément Visual Studio

Un complément est une DLL compilée qui s’exécute dans l’environnement de développement intégré (IDE) de Visual Studio. Sa compilation contribue à protéger votre propriété intellectuelle et améliore les performances. Même si vous pouvez créer des compléments manuellement, il est toutefois plus facile d’utiliser**l’Assistant Complément**. L'Assistant crée un complément fonctionnel de base que vous pouvez exécuter immédiatement après sa création. Une fois que **l’Assistant Complément** a généré le programme de base, vous pouvez y ajouter du code et le personnaliser.

**l’Assistant Complément** vous permet de fournir un nom complet et une description pour votre complément. Ils s’afficheront dans le **Gestionnaire de compléments**. Vous pouvez indiquer à l’Assistant de générer un code qui ajoute au menu **Outils** une commande permettant d’ouvrir le complément. Vous pouvez également choisir d’afficher une boîte de dialogue **À propos de** personnalisée pour votre complément. Une fois l'Assistant terminé, votre nouveau projet n'a qu'une classe, qui implémente le complément. Cette classe est appelée Connect.

Vous utiliserez le **Gestionnaire de compléments** à la fin de cet article.

### <a name="to-create-an-add-in-by-using-the-add-in-wizard"></a>Pour créer un complément en utilisant l'Assistant Complément

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur la solution, choisissez **Ajouter**, puis sélectionnez **nouveau projet**.

2. Créez un projet **Complément Visual Studio**.

    **L’Assistant Complément** Visual Studio démarre.

3. Choisissez **Suivant**.

4. Dans la page **Sélectionner un langage de programmation**, sélectionnez le langage de programmation que vous souhaitez utiliser pour écrire le complément.

   > [!NOTE]
   > Pour l'exemple de code, cette rubrique utilise Visual C#.

5. Dans la page **Sélectionner une application hôte**, sélectionnez **Visual Studio** et désactivez **Visual Studio Macros**.

6. Choisissez **Suivant**.

7. Entrez le nom et la description de votre complément dans la page **Entrer un nom et une description**.

     Une fois le complément créé, ses nom et description s’affichent dans la liste **Compléments disponibles** dans le **Gestionnaire de compléments**. Indiquez suffisamment d'informations dans la description de votre complément afin que les utilisateurs puissent connaître l'utilité de votre complément, son fonctionnement, etc.

8. Choisissez **Suivant**.

9. Dans la page **Choisir les options du complément**, sélectionnez **Je souhaite que mon complément soit chargé en même temps que l’application hôte**.

10. Désactivez les autres cases à cocher.

11. Dans la page **Choisir les informations contenues dans « À propos de »**, vous pouvez indiquer si vous voulez que les informations relatives à votre complément apparaissent dans une boîte de dialogue **À propos de**. Si vous souhaitez que les informations soient affichées, cochez la case **Oui, je souhaite que mon complément propose une boîte de dialogue « À propos de »**.

     Les informations que vous pouvez ajouter dans la boîte de dialogue **À propos de** de Visual Studio incluent notamment le numéro de version, des informations relatives à la prise en charge, des données relatives à la licence, etc.

12. Choisissez **Suivant**.

13. Vous pouvez vérifier les options sélectionnées dans la page **Résumé**. Si vous êtes satisfait, choisissez **Terminer** pour créer le complément. Pour effectuer une modification, choisissez le bouton **Précédent**.

     La nouvelle solution et le nouveau projet sont créés. Le fichier *Connect.cs* du nouveau complément s’affiche dans **l’éditeur de code**.

     Vous ajouterez le code au fichier *Connect.cs* après la procédure suivante, qui crée un contrôle utilisateur référencé par ce projet WebPerfTestResultsViewerAddin.

    Après avoir créé un complément, vous devez l’inscrire auprès de Visual Studio avant de l’activer dans le **Gestionnaire de compléments**. Pour cela, vous devez utiliser un fichier XML avec l’extension de fichier *.addin*.

    Le fichier *. AddIn* décrit les informations requises par Visual Studio pour afficher le complément dans le **Gestionnaire de compléments**. Au démarrage de Visual Studio, il recherche les fichiers *. AddIn* disponibles dans l’emplacement du fichier. *AddIn* . Si des fichiers sont trouvés, Visual Studio lit le fichier XML et transmet au **Gestionnaire de compléments** les informations dont il a besoin pour démarrer le complément quand un utilisateur clique dessus.

    Le fichier *.addin* est créé automatiquement lors de la création d’un complément à l’aide de **l’Assistant Complément**.

### <a name="add-in-file-locations"></a>Emplacements du fichier .addin

Deux copies du fichier *.addin* sont créées automatiquement par **l’Assistant Complément** :

|**Emplacement du fichier .addin**|**Description**|
|-|----------------------------|-|
|Dossier de projet racine|Utilisé pour le déploiement du projet de complément. Incluse dans le projet pour des modifications facilitées. Chemin d’accès local pour un déploiement de style XCopy.|
|Dossier des compléments|Utilisé pour exécuter le complément dans l'environnement de débogage. Doit toujours pointer sur le chemin de sortie de la configuration de build actuelle.|

## <a name="create-a-windows-form-control-library-project"></a>Créer un projet de bibliothèque de contrôles Windows Forms

Le complément Visual Studio créé dans les procédures précédentes référence un projet de bibliothèque de contrôles Windows Forms pour créer une instance d’une classe <xref:System.Windows.Forms.UserControl>.

### <a name="to-create-a-control-to-be-used-in-the-web-test-results-viewer"></a>Pour créer un contrôle à utiliser dans l'Afficheur des résultats de test Web

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur la solution, choisissez **Ajouter**, puis sélectionnez **nouveau projet**.

2. Créez un projet **Bibliothèque de contrôles Windows Forms**.

3. Dans la **Boîte à outils**, faites glisser un <xref:System.Windows.Forms.DataGridView> sur la surface de userControl1.

4. Cliquez sur le glyphe d’étiquette d’action (![Glyphe d’étiquette active](../test/media/vs_winformsmttagglyph.gif)) dans le coin supérieur droit de <xref:System.Windows.Forms.DataGridView> et suivez ces étapes :

    1. Choisissez **Ancrer dans le conteneur parent**.

    2. Décochez les cases **Activer l’ajout**, **Activer la modification**, **Activer la suppression** et **Activer la réorganisation des colonnes**.

    3. Choisissez **Ajouter une colonne**.

         La boîte de dialogue **Ajouter une colonne** s’affiche.

    4. Dans la liste déroulante **Type**, sélectionnez **DataGridViewTextBoxColumn**.

    5. Effacez le texte « Column1 » dans **Texte d’en-tête**.

    6. Choisissez **Ajouter**.

    7. Choisissez **Fermer**.

5. Dans la fenêtre **Propriétés** , affectez à la propriété **(Name)** de la <xref:System.Windows.Forms.DataGridView> valeur **par resultControlDataGridView**.

6. Cliquez avec le bouton droit sur l’aire de conception et sélectionnez **Afficher le code**.

     Le fichier *UserControl1.cs* s’affiche dans **l’Éditeur de code**.

7. Remplacez le nom UserContro1 de la classe instanciée <xref:System.Windows.Forms.UserControl> par resultControl :

    ```csharp
    namespace WebPerfTestResultsViewerControl
    {
        public partial class resultControl : UserControl
        {
            public resultControl()
            {
                InitializeComponent();
            }
    ```

     Dans la procédure suivante, vous allez ajouter le code au fichier *Connect.cs* du projet WebPerfTestResultsViewerAddin. Il va référencer la classe resultControl.

     Vous ajouterez ultérieurement du code supplémentaire au fichier *Connect.cs*.

## <a name="add-code-to-the-webperftestresultsvieweraddin"></a>Ajouter du code au projet WebPerfTestResultsViewerAddin

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le nœud **références** dans le projet WebPerfTestResultsViewerAddin, puis sélectionnez **Ajouter une référence**.

2. Dans la boîte de dialogue **Ajouter une référence**, choisissez l’onglet **.NET**.

3. Faites défiler vers le bas et sélectionnez **Microsoft.VisualStudio.QualityTools.WebTestFramework** et **System.Windows.Forms**.

4. Choisissez **OK**.

5. Cliquez à nouveau avec le bouton droit sur le nœud **Références** et sélectionnez **Ajouter une référence**.

6. Dans la boîte de dialogue **Ajouter une référence**, choisissez l’onglet **Parcourir**.

7. Choisissez la liste déroulante pour **regarder dans** et accédez à *% ProgramFiles (x86)% \ Microsoft Visual Studio\2017\Enterprise\Common7\IDE\PrivateAssemblies* et sélectionnez le fichier *Microsoft.VisualStudio.QualityTools.LoadTestPackage.dll* .

8. Choisissez **OK**.

9. Cliquez avec le bouton droit sur le nœud du projet WebPerfTestResultsViewerAddin et sélectionnez **Ajouter une référence**.

10. Dans la boîte de dialogue **Ajouter une référence**, choisissez l’onglet **Projets**.

11. Sous **Nom du projet**, sélectionnez le projet **WebPerfTestResultsViewerControl**, puis choisissez **OK**.

12. Si le fichier *Connect.cs* n’est pas encore ouvert, dans **Explorateur de solutions**, cliquez avec le bouton droit sur le fichier **Connect.cs** dans le projet WebPerfTestResultsViewerAddin, puis sélectionnez **afficher le code**.

13. Dans le fichier *Connect.cs*, ajoutez les instructions Using suivantes :

    ```csharp
    using System.IO;
    using System.Windows.Forms;
    using System.Collections.Generic;
    using Microsoft.VisualStudio.TestTools.LoadTesting;
    using Microsoft.VisualStudio.TestTools.WebTesting;
    using WebPerfTestResultsViewerControl;
    ```

14. Faites défiler le fichier *Connect.cs* jusqu’en bas. Ajoutez une liste de GUID pour <xref:System.Windows.Forms.UserControl> au cas où plusieurs instances de **l’Afficheur de résultats de test de performances web** seraient ouvertes. Vous ajouterez ultérieurement du code pour utiliser cette liste.

     Une deuxième liste de chaînes est utilisée dans la méthode OnDiscconection que vous coderez ultérieurement.

    ```csharp
    private DTE2 _applicationObject;
    private AddIn _addInInstance;

    private Dictionary<Guid, List<UserControl>> m_controls = new Dictionary<Guid, List<UserControl>>();        private List<string> temporaryFilePaths = new List<string>();
    ```

15. Le fichier *Connect.cs* instancie une classe nommée Connect à partir de la <xref:Extensibility.IDTExtensibility2> classe et propose également des méthodes pour implémenter le complément Visual Studio. La méthode OnConnection est l'une de ces méthodes. Elle reçoit une notification lorsque le complément est chargé. Dans la méthode OnConnection, vous utiliserez la classe LoadTestPackageExt pour créer votre package d’extensibilité pour **l’Afficheur de résultats de test de performances web**. Ajoutez le code suivant à la méthode OnConnection :

    ```csharp
    public void OnConnection(object application, ext_ConnectMode connectMode, object addInInst, ref Array custom)
                {
                _applicationObject = (DTE2)application;
                _addInInstance = (AddIn)addInInst;

                // Create a load test packge extensibility class.            LoadTestPackageExt loadTestPackageExt = _applicationObject.GetObject("Microsoft.VisualStudio.TestTools.LoadTesting.LoadTestPackageExt") as LoadTestPackageExt;            // Process open windows.            foreach (WebTestResultViewer webTestResultViewer in loadTestPackageExt.WebTestResultViewerExt.ResultWindows)            {                WindowCreated(webTestResultViewer);            }            // Create event handlers.            loadTestPackageExt.WebTestResultViewerExt.WindowCreated += new EventHandler<WebTestResultViewerExt.WindowCreatedEventArgs>(WebTestResultViewerExt_WindowCreated);            loadTestPackageExt.WebTestResultViewerExt.WindowClosed += new EventHandler<WebTestResultViewerExt.WindowClosedEventArgs>(WebTesResultViewer_WindowClosed);            loadTestPackageExt.WebTestResultViewerExt.SelectionChanged += new EventHandler<WebTestResultViewerExt.SelectionChangedEventArgs>(WebTestResultViewer_SelectedChanged);
            }
    ```

16. Ajoutez le code suivant à la classe Connect pour créer la méthode WebTestResultViewerExt_WindowCreated pour le gestionnaire d'événements loadTestPackageExt.WebTestResultViewerExt.WindowCreated que vous avez ajouté dans la méthode OnConnection et pour la méthode WindowCreated appelée par la méthode WebTestResultViewerExt_WindowCreated.

    ```csharp
            void WebTestResultViewerExt_WindowCreated(object sender, WebTestResultViewerExt.WindowCreatedEventArgs e)
            {
                // New control added to new result viewer window.
                WindowCreated(e.WebTestResultViewer);
            }

    private void WindowCreated(WebTestResultViewer viewer)        {            // Instantiate an instance of the resultControl referenced in the WebPerfTestResultsViewerControl project.
                resultControl resultControl = new resultControl();            // Add to the dictionary of open playback windows.            System.Diagnostics.Debug.Assert(!m_controls.ContainsKey(viewer.TestResultId));            List<UserControl> userControls = new List<UserControl>();            userControls.Add(resultControl);            // Add Guid to the m_control List to manage Result viewers and controls.            m_controls.Add(viewer.TestResultId, userControls);            // Add tabs to the playback control.            resultControl.Dock = DockStyle.Fill;            viewer.AddResultPage(new Guid(), "Sample", resultControl);        }
    ```

17. Ajoutez le code suivant à la classe Connect pour créer la méthode WebTestResultViewer_SelectedChanged pour le gestionnaire d'événements loadTestPackageExt.WebTestResultViewerExt.SelectionChanged que vous avez ajouté dans la méthode OnConnection :

    ```csharp
    void WebTestResultViewer_SelectedChanged(object sender, WebTestResultViewerExt.SelectionChangedEventArgs e)
    {
        foreach (UserControl userControl in m_controls[e.TestResultId])            {                // Update the userControl in each result viewer.                resultControl resultControl = userControl as resultControl;                if (resultControl != null)                    // Call the resultControl's Update method (This will be added in the next procedure).                    resultControl.Update(e.WebTestRequestResult);            }
    }
    ```

18. Ajoutez le code suivant à la classe Connect pour créer la méthode WebTesResultViewer_WindowClosed pour le gestionnaire d'événements pour le loadTestPackageExt.WebTestResultViewerExt.WindowClosed que vous avez ajouté dans la méthode OnConnection :

    ```csharp
    void WebTesResultViewer_WindowClosed(object sender, WebTestResultViewerExt.WindowClosedEventArgs e)
    {
        if (m_controls.ContainsKey(e.WebTestResultViewer.TestResultId))
        {
            m_controls.Remove(e.WebTestResultViewer.TestResultId);
        }
    }
    ```

     Après la complétion du code du complément Visual Studio, vous devez ajouter la méthode Update au resultControl dans le projet WebPerfTestResultsViewerControl.

## <a name="add-code-to-the-webperftestresultsviewercontrol"></a>Ajouter du code au WebPerfTestResultsViewerControl

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le nœud de projet WebPerfTestResultsViewerControl et sélectionnez **Propriétés**.

2. Sélectionnez l’onglet **Application**, choisissez la liste déroulante **Framework cible**, puis sélectionnez **.NET Framework 4** (ou ultérieur). Fermez la fenêtre **Propriétés** .

   Cette opération est nécessaire pour prendre en charge les références DLL requises afin d’étendre **l’Afficheur de résultats de test de performances web**.

3. Dans **Explorateur de solutions**, dans le projet WebPerfTestResultsViewerControl, cliquez avec le bouton droit sur le nœud **références** et sélectionnez **Ajouter une référence**.

4. Dans la boîte de dialogue **Ajouter une référence**, cliquez sur l’onglet **.NET**.

5. Faites défiler la page et sélectionnez **Microsoft.VisualStudio.QualityTools.WebTestFramework**.

6. Choisissez **OK**.

7. Dans le fichier *UserControl1.cs*, ajoutez les instructions Using suivantes :

    ```csharp
    using Microsoft.VisualStudio.TestTools.WebTesting;
    using Microsoft.VisualStudio.TestTools.WebTesting.Rules;
    ```

8. Ajoutez la méthode Update qui est appelée et passée à WebTestRequestResult à partir de la méthode WebPerfTestResultsViewerAddin WebTestResultViewer_SelectedChanged du fichier *Connect.cs*. La méthode Update remplit le contrôle DataGridView avec différentes propriétés qui lui sont passées dans le WebTestRequestResult.

    ```csharp
    public void Update(WebTestRequestResult WebTestResults)
            {
                // Clear the DataGridView when a request is selected.
                resultControlDataGridView.Rows.Clear();
                // Populate the DataGridControl with properties from the WebTestResults.
                this.resultControlDataGridView.Rows.Add("Request: " + WebTestResults.Request.Url.ToString());
                this.resultControlDataGridView.Rows.Add("Response: " + WebTestResults.Response.ResponseUri.ToString());
                foreach (RuleResult ruleResult in WebTestResults.ExtractionRuleResults)
                {
                    this.resultControlDataGridView.Rows.Add("Extraction rule results: " + ruleResult.Message.ToString());
                }
                foreach (RuleResult ruleResult in WebTestResults.ValidationRuleResults)
                {
                    this.resultControlDataGridView.Rows.Add("Validation rule results: " + ruleResult.Message.ToString());
                }
                foreach (WebTestError webTestError in WebTestResults.Errors)
                {
                    this.resultControlDataGridView.Rows.Add("Error: " + webTestError.ErrorType.ToString() + " " + webTestError.ErrorSubtype.ToString() + " " + webTestError.ExceptionText.ToString());
                }
            }
    ```

## <a name="build-the-solution"></a>Générez la solution.

- Dans le menu **Générer**, sélectionnez **Générer la solution**.

## <a name="register-the-webperftestresultsvieweraddin-add-in"></a>Inscrire le complément WebPerfTestResultsViewerAddin

1. Dans le menu **Outils**, sélectionnez **Gestionnaire de compléments**.

2. La boîte de dialogue **Gestionnaire de compléments** s’affiche.

3. Cochez la case pour le complément WebPerfTestResultsViewerAddin dans la colonne **Compléments disponibles** et décochez les cases situées sous les colonnes **Démarrage** et **Ligne de commande**.

4. Choisissez **OK**.

## <a name="run-the-web-performance-test-using-the-web-test-results-viewer"></a>Exécutez le test de performances web avec l’Afficheur de résultats de test web

1. Exécutez votre test de performances web. Le nouvel onglet du complément WebPerfTestResultsViewerAddin, intitulé Exemple, apparaît dans **l’Afficheur de résultats de test de performances web**.

2. Cliquez sur l'onglet pour consulter les propriétés présentées dans le contrôle DataGridView.

## <a name="net-security"></a>Sécurité .NET

Pour améliorer la sécurité en empêchant les compléments nuisibles de s’activer automatiquement, Visual Studio fournit différents paramètres dans une page **Options Outils** nommée **Sécurité des compléments/macros**.

En outre, cette page d’options vous permet de spécifier les dossiers dans lesquels Visual Studio recherche *. *Fichiers d’enregistrement de complément. Cela améliore la sécurité en vous permettant de limiter les emplacements dans lesquels les fichiers d’inscription *.AddIn* peuvent être lus. Cela permet d’éviter que des fichiers *.AddIn* malveillants ne soient involontairement utilisés.

**Paramètres de sécurité des compléments**

Les paramètres de la page d’options pour la sécurité des compléments sont les suivants :

- **Autoriser le chargement des composants de compléments.** Option sélectionnée par défaut. Quand ce paramètre est activé, le chargement des compléments est autorisé dans Visual Studio. Quand il est désactivé, le chargement des compléments est interdit dans Visual Studio.

- **Autoriser le chargement des composants de compléments à partir d’une URL.** Cette option est désélectionnée par défaut. Lorsqu’elle est sélectionnée, le chargement des compléments à partir de sites web externes est autorisé. Quand il est désactivé, le chargement des compléments distants est interdit dans Visual Studio. Si, pour une raison ou une autre, un complément ne peut pas se charger, il ne peut pas l'être non plus depuis le Web. Ce paramètre contrôle uniquement le chargement de la DLL complémentaire. Les fichiers d’inscription *.Addin* doivent toujours se trouver sur le système local.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.UserControl>
- <xref:Microsoft.VisualStudio.TestTools.LoadTesting>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules>
- <xref:System.Windows.Forms.UserControl>
- <xref:System.Windows.Forms.DataGrid>
- [Créer un code et des plug-ins personnalisés pour les tests de charge](../test/create-custom-code-and-plug-ins-for-load-tests.md)
