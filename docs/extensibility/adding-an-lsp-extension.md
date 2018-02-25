---
title: "Ajout d’une extension du protocole du serveur langue | Documents Microsoft"
ms.custom: 
ms.date: 11/14/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 52f12785-1c51-4c2c-8228-c8e10316cd83
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: ea93ddee9c47f80322db2403aeecc0fb7dddb209
ms.sourcegitcommit: c0a2385a16cc4f47d2e1ff23d35c4da40f5605e0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/23/2018
---
# <a name="adding-a-language-server-protocol-extension"></a>Ajout d’une extension du protocole de serveur de langage

Le protocole de serveur de langage (LSP) est un protocole commun, sous la forme de JSON RPC v2.0, utilisée pour fournir des fonctionnalités de service à différents éditeurs de code de langue. À l’aide du protocole, les développeurs peuvent écrire un serveur unilingue fournissent des fonctionnalités telles qu’IntelliSense, les diagnostics d’erreur du service de langage, rechercher toutes les références, etc. pour différents éditeurs de code qui prennent en charge le LSP. En règle générale, les services de langage dans Visual Studio peuvent être ajoutés par une à l’aide de fichiers de grammaire TextMate pour fournir des fonctionnalités de base telles que la mise en surbrillance de syntaxe, ou en écrivant des services de langage personnalisé à l’aide de l’ensemble des API d’extensibilité de Visual Studio pour fournir des données plus riches. À présent, prise en charge le LSP offre une troisième option.

![service de protocole de serveur de langage dans Visual Studio](media/lsp-service-in-VS.png)

## <a name="language-server-protocol"></a>Protocole de serveur de langage

Pour plus d’informations sur le protocole lui-même, consultez la documentation [ici](https://github.com/Microsoft/language-server-protocol). Implémentation de Visual Studio du protocole de serveur de langage est en version préliminaire et prise en charge doit être considérée comme expérimentale. La version préliminaire est sous la forme d’une extension ([Language Server protocole Client Preview](https://marketplace.visualstudio.com/items?itemName=vsext.LanguageServerClientPreview)), **, mais cette extension ne peut être installée sur le canal de version préliminaire de Visual Studio**. Une version ultérieure de Visual Studio inclut la prise en charge intégrée pour le protocole de serveur langue, moment auquel l’indicateur de version préliminaire est supprimées. **Vous ne devez pas utiliser la version d’évaluation à des fins de production.**

Pour plus d’informations sur la création d’un exemple de serveur de langue ou de l’intégration d’un serveur de langue existant dans Visual Studio Code, consultez la documentation [ici](https://code.visualstudio.com/docs/extensions/example-language-server).

![implémentation de protocole de serveur de langage](media/lsp-implementation.png)

Cet article décrit comment créer une extension de Visual Studio qui utilise un serveur de langage LSP. Il part du principe que vous avez déjà créé un serveur de langage LSP et que vous souhaitez intégrer à Visual Studio.

Pour la prise en charge dans Visual Studio, les serveurs de langage peuvent communiquer avec le client (Visual Studio) via les mécanismes suivants :

* Flux d’entrée/sortie standard
* Canaux nommés
* sockets

Le but des LSP et sa prise en charge dans Visual Studio est aux services de langage intégré qui ne font pas partie du produit Visual Studio. Il n’est pas destinée à étendre existantes des services de langage (tels que c#) dans Visual Studio. Pour étendre les langages existants, reportez-vous au guide d’extensibilité du service de langage (par exemple, le [plateforme des compilateurs .NET « Roslyn »](../extensibility/dotnet-compiler-platform-roslyn-extensibility.md)).

## <a name="language-server-protocol-features-supported"></a>Fonctionnalités de protocole serveur langage pris en charge

Les fonctionnalités LSP suivantes sont prises en charge dans Visual Studio jusqu'à présent :

Message | Prend en charge dans Visual Studio
--- | ---
initialiser | oui
initialisé | oui
arrêt | oui
quitter | oui
$/ cancelRequest | oui
window/showMessage | oui
window/showMessageRequest | oui
window/logMessage | oui
événement de télémétrie / |
client/registerCapability |
client/unregisterCapability |
workspace/didChangeConfiguration | oui
workspace/didChangeWatchedFiles | oui
espace de travail/symboles | oui
workspace/executeCommand | oui
espace de travail/applyEdit | oui
textDocument/publishDiagnostics | oui
textDocument/didOpen | oui
textDocument/didChange | oui
textDocument/willSave |
textDocument/willSaveWaitUntil |
textDocument/didSave | oui
textDocument/didClose | oui
textDocument/completion | oui
Saisie semi-automatique/résolution | oui
textDocument/hover | oui
textDocument/signatureHelp | oui
textDocument/references | oui
textDocument/documentHighlight |
textDocument/documentSymbol | oui
textDocument/la mise en forme | oui
textDocument/rangeFormatting | oui
textDocument/onTypeFormatting |
textDocument/definition | oui
textDocument/codeAction | oui
textDocument/codeLens |
codeLens/resolve |
textDocument/documentLink |
documentLink/resolve |
textDocument/rename | oui

## <a name="getting-started"></a>Prise en main

### <a name="create-a-vsix-project"></a>Créez un projet VSIX

Pour créer une extension de service de langage à l’aide d’un serveur de langage LSP, commencez par vérifier que vous avez le **le développement d’extensions Visual Studio** la charge de travail installé pour votre instance de Visual Studio.

Ensuite créer un nouveau VSIXProject vide en accédant à **fichier** > **nouveau projet** > **Visual C#**  >   **Extensibilité** > **projet VSIX**:

![créer le projet vsix](media/lsp-vsix-project.png)

Pour la version préliminaire, prise en charge de Visual Studio pour le LSP sera sous la forme d’une extension VSIX ([Microsoft.VisualStudio.LanguageServer.Client.Preview](https://marketplace.visualstudio.com/items?itemName=vsext.LanguageServerClientPreview)). Les développeurs d’extensions qui souhaitent créer une extension à l’aide de serveurs de langue LSP doivent prendre une dépendance sur ce VSIX. Par conséquent, les clients qui souhaitent installer une extension du langage **doit tout d’abord installer la langue serveur protocole Client Preview extension VSIX.**

Pour définir la dépendance VSIX, ouvrez le Concepteur de manifeste VSIX pour votre extension VSIX (en double-cliquant sur le fichier source.extension.vsixmanifest dans votre projet) et accédez à **dépendances**:

![Ajouter une référence à un client de protocole de serveur de langage](media/lsp-reference-lsp-dependency.png)

Créer une nouvelle dépendance comme suit :

![définir la dépendance de client de protocole de serveur language](media/lsp-define-lsp-dependency.png)

* **Source**: définis manuellement
* **Nom**: aperçu du langage serveur protocole Client
* **Identifier**: Microsoft.VisualStudio.LanguageServer.Client.Preview
* **Plage de versions**: [1.0,2.0)
* **Comment la dépendance est résolue**: installée par utilisateur
* **Download URL**: [https://marketplace.visualstudio.com/items?itemName=vsext.LanguageServerClientPreview](https://marketplace.visualstudio.com/items?itemName=vsext.LanguageServerClientPreview)

> [!NOTE]
> Le **URL de téléchargement** doit être renseigné afin que les utilisateurs de l’installation de votre extension sachent comment installer la dépendance requise.

### <a name="language-server-and-runtime-installation"></a>Installation de serveur et d’exécution de langage

Par défaut, les extensions créées pour prendre en charge des serveurs de langage LSP dans Visual Studio ne contiendra pas les serveurs de la langue ou les runtimes nécessaires à leur exécution. Les développeurs d’extensions sont responsables de distribution les serveurs de langage et les runtimes si nécessaires. Il existe plusieurs façons de le faire :

* Serveurs de langue peuvent être incorporées dans le projet VSIX en tant que fichiers de contenu.
* Créer un fichier MSI pour installer le serveur de langage et/ou nécessaire runtimes.
* Fournissent des instructions sur les utilisateurs information Marketplace comment obtenir les runtimes et langage de serveurs.

### <a name="textmate-grammar-files"></a>Fichiers de grammaire TextMate

LSP n’inclut pas de spécification sur la façon de fournir la colorisation de texte pour les langues. Pour fournir la colorisation personnalisée pour les langues dans Visual Studio, les développeurs d’extensions peuvent utiliser un fichier de grammaire TextMate. Pour ajouter des fichiers thème ou de grammaire TextMate personnalisés, procédez comme suit :

1. Créez un dossier nommé « Grammaires » à l’intérieur de votre extension (ou il peut être le nom de votre choix).

2. Dans le dossier « Grammaires », inclure des *.tmlanguage, *.plist, *.tmtheme ou les fichiers *.json que vous aimeriez qui fournit la colorisation personnalisée.

3. Avec le bouton droit sur les fichiers et sélectionnez **propriétés**. Modifier l’action de génération pour **contenu** et **inclure dans VSIX** true à la propriété.

4. Créer un fichier .pkgdef et ajoutez une ligne semblable à celle-ci :

  ```xml
  [$RootKey$\TextMate\Repositories]
  "MyLang"="$PackageFolder$\Grammars"
  ```

5. Avec le bouton droit sur les fichiers et sélectionnez **propriétés**. Modifier l’action de génération pour **contenu** et **inclure dans VSIX** true à la propriété.

Après avoir effectué les étapes précédentes, un dossier « Grammaires » est ajouté pour l’installation du package active en tant que référentiel source nommé 'MyLang' ('MyLang' est simplement un nom de lever l’ambiguïté et peut être toute chaîne unique). Toutes les grammaires (fichiers .tmlanguage) et le thème (fichiers .tmtheme) dans ce répertoire sont prélevés comme potentiels et remplacent les grammaires intégrés fournis avec TextMate. Si les extensions du fichier de grammaire déclaré correspond à l’extension du fichier en cours d’ouverture, TextMate pas.

## <a name="creating-a-simple-language-client"></a>Création d’un client de langage simple

### <a name="main-interface---ilanguageclientdotnetapimicrosoftvisualstudiolanguageserverclientilanguageclientviewvisualstudiosdk-2017"></a>Interface principale - [ILanguageClient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017)

Après avoir créé votre projet VSIX, ajoutez les packages NuGet suivants à votre projet :

* [Microsoft.VisualStudio.LanguageServer.Client](https://www.nuget.org/packages/Microsoft.VisualStudio.LanguageServer.Client)

> [!NOTE]
> Lorsque vous prenez une dépendance sur le package NuGet après avoir effectué les étapes précédentes, les packages Newtonsoft.Json et StreamJsonRpc sont ajoutés à votre projet. **Ne mettez pas à jour ces packages, sauf si vous êtes certain que les nouvelles versions seront installées sur la version de Visual Studio qui les cibles de l’extension**. Les assemblys ne sera pas inclus dans votre projet VSIX--au lieu de cela, ils sont récupérés à partir du répertoire d’installation de Visual Studio. Si vous référencez une version plus récente des assemblys que celle qui est installée sur l’ordinateur d’un utilisateur, votre extension *ne fonctionne pas*.

Vous pouvez créer ensuite une nouvelle classe qui implémente le [ILanguageClient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017) interface, l’interface principale nécessaire pour les clients de langue qui se connectent à un serveur de langage LSP.

Voici un exemple :

```csharp
namespace MockLanguageExtension
{
    [ContentType("bar")]
    [Export(typeof(ILanguageClient))]
    public class BarLanguageClient : ILanguageClient
    {
        public string Name => "Bar Language Extension";

        public IEnumerable<string> ConfigurationSections => null;

        public object InitializationOptions => null;

        public IEnumerable<string> FilesToWatch => null;

        public event AsyncEventHandler<EventArgs> StartAsync;
        public event AsyncEventHandler<EventArgs> StopAsync;

        public async Task<Connection> ActivateAsync(CancellationToken token)
        {
            await Task.Yield();

            ProcessStartInfo info = new ProcessStartInfo();
            info.FileName = Path.Combine(Path.GetDirectoryName(Assembly.GetExecutingAssembly().Location), "Server", @"MockLanguageServer.exe");
            info.Arguments = "bar";
            info.RedirectStandardInput = true;
            info.RedirectStandardOutput = true;
            info.UseShellExecute = false;
            info.CreateNoWindow = true;

            Process process = new Process();
            process.StartInfo = info;

            if (process.Start())
            {
                return new Connection(process.StandardOutput.BaseStream, process.StandardInput.BaseStream);
            }

            return null;
        }

        public async Task OnLoadedAsync()
        {
            await StartAsync?.InvokeAsync(this, EventArgs.Empty);
        }

        public async Task OnServerInitializeFailedAsync(Exception e)
        {
            return Task.CompletedTask;
        }

        public async Task OnServerInitializedAsync()
        {
            return Task.CompletedTask;
        }
    }
}
```

Les principales méthodes qui doivent être implémentés sont [OnLoadedAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.onloadedasync?view=visualstudiosdk-2017) et [ActivateAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.activateasync?view=visualstudiosdk-2017). [OnLoadedAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.onloadedasync?view=visualstudiosdk-2017) est appelée lors du chargement de votre extension de Visual Studio et votre serveur est prêt à démarrer. Dans cette méthode, vous pouvez appeler la [StartAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017) délégué immédiatement pour signaler que le serveur doit être démarré, ou vous pouvez effectuer une logique supplémentaire et appeler [StartAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017) plus tard. **Pour activer votre serveur de langue, vous devez appeler StartAsync à un moment donné.**

[ActivateAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.activateasync?view=visualstudiosdk-2017) est la méthode appelée par la suite en appelant le [StartAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017) délégué ; il contient la logique permettant de démarrer le serveur de langage et d’établir la connexion à celui-ci. Un objet de connexion qui contient le flux de données pour l’écriture sur le serveur et la lecture à partir du serveur doit être retourné. Toutes les exceptions levées ici sont interceptées et affichées à l’utilisateur via un message de la barre d’informations dans Visual Studio.

### <a name="activation"></a>Activation

Une fois que votre classe de client de langage est implémenté, vous devez définir deux attributs pour pouvoir définir la façon dont il sera chargé dans Visual Studio et activé :

```csharp
  [Export(typeof(ILanguageClient))]
  [ContentType("bar")]
```

### <a name="mef"></a>MEF

Visual Studio utilise [MEF](https://github.com/Microsoft/vs-mef/blob/master/doc/index.md) (Managed Extensibility Framework) pour gérer ses points d’extensibilité. Le [exporter](https://msdn.microsoft.com/library/system.componentmodel.composition.exportattribute(v=vs.110).aspx) attribut indique à Visual Studio que cette classe doit être récupérée en tant qu’un point d’extension et chargée au moment opportun.

Pour utiliser MEF, vous devez également définir MEF comme un élément multimédia dans le manifeste VSIX.

Ouvrez le Concepteur de manifeste VSIX et accédez à la **actifs** onglet :

![ajouter des ressources MEF](media/lsp-add-asset.png)

Cliquez sur Nouveau pour créer un nouvel élément multimédia :

![définir l’élément multimédia MEF](media/lsp-define-asset.png)

* **Type**: Microsoft.VisualStudio.MefComponent
* **Source**: un projet dans la solution actuelle
* **Projet**: [nom de votre projet]

### <a name="content-type-definition"></a>Définition de Type de contenu

Actuellement, la seule façon de charger votre extension de serveur de langage LSP est par type de contenu de fichier. Autrement dit, lorsque vous définissez votre classe de client de langage (qui implémente [ILanguageClient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017)), vous devez définir les types de fichiers qui, quand elle est ouverte, entraîne votre extension à charger. Si aucun fichier ne correspond à votre type de contenu défini n’est ouverte, puis votre extension ne sera pas chargée.

Cela est effectué à partir de la définition d’une ou plusieurs classes ContentTypeDefinition :

```csharp
namespace MockLanguageExtension
{
    public class BarContentDefinition
    {
        [Export]
        [Name("bar")]
        [BaseDefinition(CodeRemoteContentDefinition.CodeRemoteContentTypeName)]
        internal static ContentTypeDefinition BarContentTypeDefinition;


        [Export]
        [FileExtension(".bar")]
        [ContentType("bar")]
        internal static FileExtensionToContentTypeDefinition BarFileExtensionDefinition;
    }
}
```

Dans l’exemple précédent, une définition de type de contenu est créée pour les fichiers qui se terminent par `.bar` extension de fichier. La définition de type de contenu est fonction de la barre « nom » et **doit** dérivent [CodeRemoteContentTypeName](/dotnet/api/microsoft.visualstudio.languageserver.client.coderemotecontentdefinition.coderemotecontenttypename?view=visualstudiosdk-2017).

Après avoir ajouté une définition de type de contenu, vous pouvez définir votre extension de client de langage dans la classe de client de langage de chargement :

```csharp
    [ContentType("bar")]
    [Export(typeof(ILanguageClient))]
    public class BarLanguageClient : ILanguageClient
    {
    }
```

Ajout de la prise en charge pour les serveurs de langage LSP ne nécessite pas d’implémenter votre propre système de projet dans Visual Studio. Les clients peuvent ouvrir un seul fichier ou un dossier dans Visual Studio pour démarrer à l’aide de votre service de langage. En fait, prise en charge des serveurs de langue LSP est conçu pour fonctionner uniquement dans les scénarios de dossier/fichier ouvert. Si un système de projet personnalisé est implémenté, certaines fonctionnalités (telles que les paramètres) ne fonctionneront pas.

## <a name="advanced-features"></a>Fonctionnalités avancées

### <a name="settings"></a>Paramètres

Prise en charge des paramètres de serveur-spécifiques au langage personnalisés ne sont pas disponibles pour la version préliminaire de la prise en charge LSP dans Visual Studio, mais il est toujours en cours d’améliorées. Paramètres sont spécifiques à ce que le serveur prend en charge et généralement contrôler comment le serveur émet des données. Par exemple, un serveur de langue peut avoir un paramètre pour le nombre maximal d’erreurs signalées. Auteurs d’extensions définissez une valeur par défaut, qui peut être modifiée par les utilisateurs pour des projets spécifiques.

Suivez ces étapes ci-dessous pour ajouter la prise en charge des paramètres pour votre extension de service de langage LSP :

1. Ajouter un fichier JSON (par exemple, « MockLanguageExtensionSettings.json ») dans votre projet qui contient les paramètres et leurs valeurs par défaut. Exemple :

  ```json
  {
    "foo.maxNumberOfProblems": -1
  }
  ```
2. Cliquez avec le bouton droit sur le fichier JSON et sélectionnez **propriétés**. Modifier la **générer** action pour « Contenu » et le « inclure dans VSIX' true à la propriété.

3. Implémenter ConfigurationSections et retourner la liste des préfixes pour les paramètres définis dans le fichier JSON (dans Visual Studio Code, il serait correspondre au nom de la section de configuration dans package.json) :

  ```csharp
  public IEnumerable<string> ConfigurationSections
  {
      get
      {
          yield return "foo";
      }
  }
  ```
4. Ajoutez un fichier .pkgdef au projet (ajouter le nouveau fichier texte et remplacez l’extension de fichier .pkgdef). Le fichier pkgdef doit contenir ces informations :

  ```xml
    [$RootKey$\OpenFolder\Settings\VSWorkspaceSettings\[settings-name]]
    @="$PackageFolder$\[settings-file-name].json"
  ```

5. Cliquez avec le bouton droit sur le fichier .pkgdef et sélectionnez **propriétés**. Modifier la **générer** l’action « Contenu » et la valeur true à la propriété « Inclure dans VSIX ».

6. Ouvrez le `source.extension.vsixmanifest` et ajoutez un élément multimédia dans le **Asset** onglet :

  ![modifier le vspackage actif](media/lsp-add-vspackage-asset.png)

  * **Type**: Microsoft.VisualStudio.VsPackage
  * **Source**: fichier sur le système de fichiers
  * **Chemin d’accès**: [chemin d’accès à votre fichier pkgdef]

### <a name="user-editing-of-settings-for-a-workspace"></a>Modification des paramètres pour un espace de travail d’utilisateur

1. Utilisateur ouvre un espace de travail contenant le propriétaire de votre serveur de fichiers.
2. Utilisateur ajoute un fichier dans le dossier « .vs » appelé « VSWorkspaceSettings.json ».
3. Utilisateur ajoute une ligne dans le fichier VSWorkspaceSettings.json pour un paramètre que fournit par le serveur. Exemple :

  ```json
  {
    "foo.maxNumberOfProblems": 10
  }
  ```
### <a name="enabling-diagnostics-tracing"></a>L’activation du traçage de diagnostic
Traçage de diagnostic peut être activé pour tous les messages entre le client et le serveur, ce qui peut être utile lors du débogage des problèmes de sortie.  Pour activer le suivi de diagnostic, procédez comme suit :

1. Ouvrez ou créez le fichier de paramètres d’espace de travail « VSWorkspaceSettings.json » (voir « Utilisateur modification des paramètres pour un espace de travail »).
2. Ajoutez la ligne suivante dans le fichier json de paramètres :

```json
{
    "foo.server.trace": "Off"
}
```

Il existe trois valeurs possibles pour les commentaires de trace :
* « Désactivé » : le suivi complètement mise hors tension
* « Messages » : le traçage activé mais l’ID de nom et de réponse seule méthode est suivi.
* « Commentaires » : le suivi activé ; le message rpc entière est suivi.

Quand le traçage est activé sur le contenu est écrit dans un fichier dans le répertoire « temp%\VisualStudio\LSP % ».  Le journal suit le format d’affectation de noms `[LanguageClientName]-[Datetime Stamp].log`.  Actuellement, le suivi ne peut être activé que pour les scénarios d’ouvrir le dossier.  Ouverture d’un fichier unique pour activer un serveur de langue n’est pas prise en charge de suivi de diagnostic.

### <a name="custom-messages"></a>Messages personnalisés

Il existe des API en place afin de faciliter le passage des messages à et réception de messages à partir du serveur de langage qui ne font pas partie du protocole du serveur de langage standard. Pour gérer des messages personnalisés, vous devez implémenter [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017) interface dans votre classe de client de langage. [VS-StreamJsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/doc/index.md) bibliothèque est utilisée pour transmettre des messages personnalisés entre votre client de langage et le serveur. Étant donné que votre extension de client de langage LSP est identique à une autre extension de Visual Studio, vous pouvez décider d’ajouter des fonctionnalités supplémentaires (qui ne sont pas pris en charge par le LSP) pour Visual Studio (à l’aide d’autres API de Studio Visual) dans votre extension par le biais des messages personnalisés.

#### <a name="receiving-custom-messages"></a>Réception de messages personnalisés

Pour recevoir des messages personnalisés à partir du serveur de la langue, vous devez implémenter la [CustomMessageTarget](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.custommessagetarget?view=visualstudiosdk-2017) propriété sur [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017) et retourner un objet qui sait comment gérer vos messages personnalisés . Exemple ci-dessous :

```csharp
internal class MockCustomLanguageClient : MockLanguageClient, ILanguageClientCustomMessage
{
    private JsonRpc customMessageRpc;

    public MockCustomLanguageClient() : base()
    {
        CustomMessageTarget = new CustomTarget();
    }

    public object CustomMessageTarget
    {
        get;
        set;
    }

    public class CustomTarget
    {
        public void OnCustomNotification(JToken arg)
        {
            // Provide logic on what happens OnCustomNotification is called from the language server
        }

        public string OnCustomRequest(string test)
        {
            // Provide logic on what happens OnCustomRequest is called from the language server
        }
    }
}
```

#### <a name="sending-custom-messages"></a>Envoi de messages personnalisés

Pour envoyer des messages personnalisés sur le serveur de la langue, vous devez implémenter la [AttachForCustomMessageAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.attachforcustommessageasync?view=visualstudiosdk-2017) méthode sur [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017). Cette méthode est appelée lorsque votre serveur est démarré et prêt à recevoir des messages. A [JsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/src/StreamJsonRpc/JsonRpc.cs) objet est passé en tant que paramètre, que vous pouvez ensuite mettre à envoyer des messages vers le serveur de langue à l’aide de [VS-StreamJsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/doc/index.md) API. Exemple ci-dessous :

```csharp
internal class MockCustomLanguageClient : MockLanguageClient, ILanguageClientCustomMessage
{
    private JsonRpc customMessageRpc;

    public MockCustomLanguageClient() : base()
    {
        CustomMessageTarget = new CustomTarget();
    }

    public async Task AttachForCustomMessageAsync(JsonRpc rpc)
    {
        await Task.Yield();

        this.customMessageRpc = rpc;
    }

    public async Task SendServerCustomNotification(object arg)
    {
        await this.customMessageRpc.NotifyWithParameterObjectAsync("OnCustomNotification", arg);
    }

    public async Task<string> SendServerCustomMessage(string test)
    {
        return await this.customMessageRpc.InvokeAsync<string>("OnCustomRequest", test);
    }
}
```

### <a name="middle-layer"></a>Couche intermédiaire

Un développeur d’extension peut souhaiter intercepter des messages LSP envoyées à / reçues à partir du serveur de langue. Par exemple, un développeur d’extension peut à modifier le paramètre de message envoyé d’un message LSP particulier, ou modifier les résultats retournés à partir du serveur de langue pour une fonctionnalité LSP (par exemple les achèvements). Lorsque cela est nécessaire, développeurs d’extensions peuvent utiliser l’API MiddleLayer pour intercepter les messages LSP.

Chaque message LSP possède sa propre interface de couche intermédiaire pour l’interception. Pour intercepter un message particulier, créez une classe qui implémente l’interface de couche intermédiaire pour le message. Ensuite, implémentez la [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017) interface dans votre classe de client de langue et de retourner une instance de l’objet dans le [MiddleLayer](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.middlelayer?view=visualstudiosdk-2017) propriété. Exemple ci-dessous :

```csharp
public class MockLanguageClient: ILanguageClient, ILanguageClientCustomMessage
{
    public object MiddleLayer => MiddleLayerProvider.Instance;

    private class MiddleLayerProvider : ILanguageClientWorkspaceSymbolProvider
    {
        internal readonly static MiddleLayerProvider Instance = new MiddleLayerProvider();

        private MiddleLayerProvider()
        {
        }

        public async Task<SymbolInformation[]> RequestWorkspaceSymbols(WorkspaceSymbolParams param, Func<WorkspaceSymbolParams, Task<SymbolInformation[]>> sendRequest)
        {
            // Send along the request as given
            SymbolInformation[] symbols = await sendRequest(param);

            // Only return symbols that are "files"
            return symbols.Where(sym => string.Equals(new Uri(sym.Location.Uri).Scheme, "file", StringComparison.OrdinalIgnoreCase)).ToArray();
        }
    }
}
```

La fonctionnalité de couche intermédiaire est en cours de développement et pas encore complète.

## <a name="sample-lsp-language-server-extension"></a>Exemple d’extension de serveur LSP language

Pour afficher le code source d’un exemple d’extension à l’aide de l’API du client LSP dans Visual Studio, consultez les exemples d’extensibilité d’extensibilité Visual Studio [exemple LSP](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/LanguageServerProtocol).

## <a name="faq"></a>FAQ

**Je souhaite créer un système de projet personnalisés pour compléter l’action mon serveur LSP pour fournir la prise en charge des fonctionnalités plus riche dans Visual Studio, comment faire pour y parvenir ?**

Prise en charge pour les serveurs de langage LSP dans Visual Studio s’appuie sur le [fonctionnalité Ouvrir le dossier](https://blogs.msdn.microsoft.com/visualstudio/2016/04/12/open-any-folder-with-visual-studio-15-preview/) et est spécifiquement conçu pour ne pas exiger un système de projet personnalisé. Vous pouvez créer votre propre système de projet personnalisé suivant instructions [ici](https://github.com/Microsoft/VSProjectSystem), mais certaines fonctionnalités, telles que les paramètres peuvent ne pas fonctionnent. La logique d’initialisation par défaut pour les serveurs de langage LSP consiste à passer dans l’emplacement du dossier racine du dossier actuellement ouvert, donc si vous utilisez un système de projet personnalisé, vous devrez peut-être fournir une logique personnalisée lors de l’initialisation pour vous assurer de votre serveur de langage peut démarrer correctement.

**Comment ajouter la prise en charge du débogueur ?**

Nous vous fournirons prise en charge pour le [courants de débogage de protocole](https://code.visualstudio.com/docs/extensionAPI/api-debugging) dans une version ultérieure.

**S’il existe déjà un service de langage pris en charge Visual Studio installé (par exemple, JavaScript), puis-je toujours installer une extension de serveur de langage LSP qui offre des fonctionnalités supplémentaires (telles que pelucheux) ?**

Oui, mais certaines fonctionnalités ne fonctionneront correctement. Le but ultime pour les extensions serveur LSP language est pour activer les services de langage natif pris en charge par Visual Studio. Vous pouvez créer des extensions qui offrent la prise en charge supplémentaire à l’aide de serveurs de langue LSP, mais certaines fonctionnalités (telles qu’IntelliSense) ne sera pas une meilleure expérience. En règle générale, il est recommandé que les extensions serveur LSP langage être utilisé pour fournir de nouvelles expériences de langage, ne pas étendre les objets existants.

**Où publier mon serveur de langage LSP VSIX terminé ?**

Consultez les instructions de Marketplace [ici](walkthrough-publishing-a-visual-studio-extension.md).
