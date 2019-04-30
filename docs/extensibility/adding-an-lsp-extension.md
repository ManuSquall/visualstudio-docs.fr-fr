---
title: Ajout d’une extension du protocole de serveur de langage | Microsoft Docs
ms.date: 11/14/2017
ms.topic: conceptual
ms.assetid: 52f12785-1c51-4c2c-8228-c8e10316cd83
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 44b8e31fea497bff928ce19e5cb165c7809883cb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62892342"
---
# <a name="add-a-language-server-protocol-extension"></a>Ajouter une extension du protocole de serveur de langage

Le protocole de serveur de langage (LSP) est un protocole commun, sous la forme de JSON RPC v2.0, utilisé pour fournir des fonctionnalités de service à différents éditeurs de code de langue. En utilisant le protocole, les développeurs peuvent écrire un serveur unilingue fournissent des fonctionnalités comme IntelliSense, des diagnostics d’erreur du service de langage, de trouver toutes les références, etc., pour différents éditeurs de code qui prennent en charge le LSP. En règle générale, les services de langage dans Visual Studio peuvent être ajoutés à l’aide à l’aide de fichiers de grammaire TextMate pour fournir des fonctionnalités de base telles que la coloration syntaxique, ou en écrivant des services de langage personnalisés à l’aide de l’ensemble des API d’extensibilité de Visual Studio pour fournir des données plus riches. À présent, prend en charge pour le partenaire LSP offre une troisième option.

![service de protocole de serveur de langage dans Visual Studio](media/lsp-service-in-VS.png)

## <a name="language-server-protocol"></a>Protocole de serveur de langage

![implémentation de protocole de serveur de langage](media/lsp-implementation.png)

Cet article décrit comment créer une extension Visual Studio qui utilise un serveur de langage basé sur des LSP. Il suppose que vous avez déjà développé un serveur de langage basé sur des LSP et que vous voulez uniquement pour l’intégrer à Visual Studio.

Pour la prise en charge dans Visual Studio, langage peuvent communiquer avec le client (Visual Studio) via n’importe quel mécanisme de transmission de flux de données en fonction, par exemple :

* Flux d’entrée/sortie standard
* Canaux nommés
* Sockets (TCP uniquement)

L’objectif des LSP et prise en charge dans Visual Studio consiste à des services de langage intégrée qui ne font pas partie du produit Visual Studio. Il n’est pas destinée à étendre existante des services de langage (tels que c#) dans Visual Studio. Pour étendre les langages existants, reportez-vous au guide de d’extensibilité du service de langage (par exemple, le [plateforme des compilateurs .NET « Roslyn »](../extensibility/dotnet-compiler-platform-roslyn-extensibility.md)).

Pour plus d’informations sur le protocole lui-même, consultez la documentation [ici](https://github.com/Microsoft/language-server-protocol).

Pour plus d’informations sur la création d’un exemple de serveur de langage ou apprendre à intégrer un serveur de langue existant dans Visual Studio Code, consultez la documentation [ici](https://code.visualstudio.com/docs/extensions/example-language-server).

## <a name="language-server-protocol-features-supported"></a>Fonctionnalités de protocole de serveur de langage prises en charge

Les fonctionnalités LSP suivantes sont prises en charge dans Visual Studio jusqu'à présent :

Message | Prend en charge dans Visual Studio
--- | ---
initialize | oui
initialisé | oui
arrêt | oui
quitter | oui
$/cancelRequest | oui
window/showMessage | oui
window/showMessageRequest | oui
window/logMessage | oui
événement de télémétrie / |
client/registerCapability |
client/unregisterCapability |
workspace/didChangeConfiguration | oui
workspace/didChangeWatchedFiles | oui
espace de travail/symbole | oui
workspace/executeCommand | oui
workspace/applyEdit | oui
textDocument/publishDiagnostics | oui
textDocument/didOpen | oui
textDocument/didChange | oui
textDocument/willSave |
textDocument/willSaveWaitUntil |
textDocument/didSave | oui
textDocument/didClose | oui
textDocument/completion | oui
Saisie semi-automatique ou résoudre | oui
textDocument/hover | oui
textDocument/signatureHelp | oui
textDocument/references | oui
textDocument/documentHighlight | oui
textDocument/documentSymbol | oui
textDocument/formatting | oui
textDocument/rangeFormatting | oui
textDocument/onTypeFormatting |
textDocument/definition | oui
textDocument/codeAction | oui
textDocument/codeLens |
codeLens/resolve |
textDocument/documentLink |
documentLink/resolve |
textDocument/rename | oui

## <a name="getting-started"></a>Bien démarrer

> [!NOTE]
> En commençant par Visual Studio 15.8 Preview 3, la prise en charge pour le protocole de serveur de langage commun est intégrée à Visual Studio. Si vous avez créé à l’aide de notre version préliminaire des extensions de LSP [langage serveur Client VSIX](https://marketplace.visualstudio.com/items?itemName=vsext.LanguageServerClientPreview) version, il cesse de fonctionner pour vous avez mis à niveau vers 15,8 Preview 3 ou version ultérieure. Vous devez effectuer les opérations suivantes pour obtenir vos extensions LSP fonctionne à nouveau :
>
> 1. Désinstallez la préversion protocole de serveur dans Microsoft Visual Studio langage VSIX. À partir de 15,8 Preview 4, chaque fois que vous effectuez une mise à niveau dans Visual Studio, nous automatiquement détecter et supprimer l’aperçu VSIX pour vous pendant le processus de mise à niveau.
>
> 2. Mettre à jour vos références Nuget vers la dernière version non-preview pour [packages des LSP](https://www.nuget.org/packages/Microsoft.VisualStudio.LanguageServer.Client).
>
> 3. Supprimez la dépendance à Microsoft Visual Studio langage serveur protocole aperçu VSIX dans votre manifeste VSIX.
>
> 4. Assurez-vous que votre projet VSIX spécifie 15.8 Preview 3 de Visual Studio en tant que la limite inférieure pour la cible d’installation.
>
> 5. Régénérez et déployez de nouveau.

### <a name="create-a-vsix-project"></a>Créez un projet VSIX

Pour créer une extension de service de langage à l’aide d’un serveur de langage basé sur des LSP, commencez par vérifier que vous avez le **développement d’extensions Visual Studio** charge de travail installée pour votre instance de Visual Studio.

Créez ensuite un nouveau VSIXProject vide en accédant à **fichier** > **nouveau projet** > **Visual C#**  >   **Extensibilité** > **projet VSIX**:

![créer le projet vsix](media/lsp-vsix-project.png)

### <a name="language-server-and-runtime-installation"></a>Installation du serveur et de runtime de langage

Par défaut, les extensions créées pour prendre en charge des serveurs de langage basé sur des LSP dans Visual Studio ne contiendra pas les serveurs de langage eux-mêmes ou les runtimes nécessaires à leur exécution. Les développeurs d’extensions sont responsables de distribuer les serveurs de langage et les runtimes nécessités. Il existe plusieurs manières de procéder :

* Serveurs de langue peuvent être incorporés dans l’extension VSIX en tant que fichiers de contenu.
* Créer un fichier MSI pour installer le serveur de langage et/ou nécessaire runtimes.
* Fournissent des instructions sur les utilisateurs informe de la place de marché comment obtenir des runtimes et langage de serveurs.

### <a name="textmate-grammar-files"></a>Fichiers de grammaire TextMate

Le partenaire LSP n’inclut pas de spécification sur la façon de fournir la colorisation de texte pour les langues. Pour fournir une colorisation personnalisée pour les langues dans Visual Studio, les développeurs d’extensions peuvent utiliser un fichier de grammaire TextMate. Pour ajouter des fichiers de grammaire ou thème TextMate personnalisés, procédez comme suit :

1. Créez un dossier nommé « Grammaires » à l’intérieur de votre extension (ou il peut être le nom que vous choisissez).

2. À l’intérieur de la *grammaires* dossier, inclure les  *\*.tmlanguage*,  *\*.plist*,  *\*.tmtheme*, ou  *\*.json* vous souhaitez que les fichiers qui fournit la colorisation personnalisée.

3. Avec le bouton droit sur les fichiers, puis sélectionnez **propriétés**. Modifier le **générer** action à **contenu** et **inclure dans VSIX** true à la propriété.

4. Créer un *.pkgdef* fichier, puis ajoutez une ligne semblable à ceci :

    ```
    [$RootKey$\TextMate\Repositories]
    "MyLang"="$PackageFolder$\Grammars"
    ```

5. Avec le bouton droit sur les fichiers, puis sélectionnez **propriétés**. Modifier le **générer** action à **contenu** et **inclure dans VSIX** true à la propriété.

Après avoir effectué les étapes précédentes, un *grammaires* dossier est ajouté pour l’installation du package répertoire en tant que référentiel source nommé « MyLang » (« MyLang » est simplement un nom pour éviter les ambiguïtés et peut être n’importe quelle chaîne unique). Toutes les grammaires (*.tmlanguage* fichiers) et les fichiers de thème (*.tmtheme* fichiers) dans ce répertoire sont sélectionnés en tant que sources et remplacent les grammaires intégrés fournis avec TextMate. Si les extensions du fichier de grammaire déclaré correspond à l’extension du fichier en cours d’ouverture, TextMate pas.

## <a name="create-a-simple-language-client"></a>Créer un client de langage simple

### <a name="main-interface---ilanguageclientdotnetapimicrosoftvisualstudiolanguageserverclientilanguageclientviewvisualstudiosdk-2017"></a>Interface principale - [ILanguageClient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017)

Après avoir créé votre projet VSIX, ajoutez les packages NuGet suivants à votre projet :

* [Microsoft.VisualStudio.LanguageServer.Client](https://www.nuget.org/packages/Microsoft.VisualStudio.LanguageServer.Client)

> [!NOTE]
> Lorsque vous prenez une dépendance sur le package NuGet après avoir terminé les étapes précédentes, les packages Newtonsoft.Json et StreamJsonRpc sont ajoutés à votre projet. **Ne mettez pas à jour ces packages, sauf si vous êtes certain que ces nouvelles versions seront être installées sur la version de Visual Studio qui ciblée par votre extension**. Les assemblys ne sera pas inclus dans votre projet VSIX--au lieu de cela, ils ne seront récupérés à partir du répertoire d’installation de Visual Studio. Si vous faites référence à une version plus récente des assemblys que ce qui est installé sur un ordinateur d’utilisateur, votre extension *ne fonctionnera pas*.

Vous pouvez ensuite créer une nouvelle classe qui implémente le [ILanguageClient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017) interface, l’interface principale nécessaire pour les clients de langue qui se connectent à un serveur de langage basé sur des LSP.

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
            await StartAsync.InvokeAsync(this, EventArgs.Empty);
        }

        public Task OnServerInitializeFailedAsync(Exception e)
        {
            return Task.CompletedTask;
        }

        public Task OnServerInitializedAsync()
        {
            return Task.CompletedTask;
        }
    }
}
```

Les principales méthodes qui doivent être implémentées sont [OnLoadedAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.onloadedasync?view=visualstudiosdk-2017) et [ActivateAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.activateasync?view=visualstudiosdk-2017). [OnLoadedAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.onloadedasync?view=visualstudiosdk-2017) est appelée lorsque Visual Studio a chargé votre extension et votre serveur de langage est prêt à démarrer. Dans cette méthode, vous pouvez appeler la [StartAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017) délégué immédiatement à signaler que le serveur de langage doit être démarré, ou vous pouvez faire une logique supplémentaire et appeler [StartAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017) plus tard. **Pour activer votre serveur de langage, vous devez appeler StartAsync à un moment donné.**

[ActivateAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.activateasync?view=visualstudiosdk-2017) est la méthode appelée par la suite en appelant le [StartAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017) délégué ; il contient la logique pour démarrer le serveur de langage et d’établir la connexion à celui-ci. Un objet de connexion qui contient le flux pour écrire sur le serveur et lire à partir du serveur doit être retourné. Toutes les exceptions levées ici sont interceptées et affichées à l’utilisateur via un message de la barre d’informations dans Visual Studio.

### <a name="activation"></a>Activation

Une fois que votre classe de client de langage est implémentée, vous devez définir les deux attributs pour pouvoir définir la façon dont il est chargé dans Visual Studio et activé :

```csharp
  [Export(typeof(ILanguageClient))]
  [ContentType("bar")]
```

### <a name="mef"></a>MEF

Visual Studio utilise [MEF](https://github.com/Microsoft/vs-mef/blob/master/doc/index.md) (Managed Extensibility Framework) pour gérer ses points d’extensibilité. Le [exporter](/dotnet/api/system.componentmodel.composition.exportattribute) attribut indique à Visual Studio que cette classe doit être récupérée en tant qu’un point d’extension et chargée au moment opportun.

Pour utiliser MEF, vous devez également définir MEF en tant que ressource dans le manifeste VSIX.

Ouvrez votre Concepteur de manifeste VSIX et accédez à la **actifs** onglet :

![Ajouter un actif MEF](media/lsp-add-asset.png)

Cliquez sur Nouveau pour créer un nouvel élément multimédia :

![définir l’élément multimédia MEF](media/lsp-define-asset.png)

* **Type**: Microsoft.VisualStudio.MefComponent
* **Source**: Un projet dans la solution actuelle
* **Projet**: [nom de votre projet]

### <a name="content-type-definition"></a>Définition de type de contenu

Actuellement, la seule façon de charger votre extension de serveur de langage basé sur des LSP est par type de contenu de fichier. Autrement dit, lorsque vous définissez votre classe de client de langage (qui implémente [ILanguageClient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017)), vous devez définir les types de fichiers qui, lorsque ouvert, entraîneront votre extension à charger. Si aucun fichier qui correspondent à votre type de contenu défini n’est ouverts, votre extension ne sera pas chargée.

Cela s’effectue via la définition d’une ou plusieurs classes de ContentTypeDefinition :

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

Dans l’exemple précédent, une définition de type de contenu est créée pour les fichiers qui se terminent par *.bar* extension de fichier. La définition de type de contenu est fournie à la barre « nom » et **doit** dérivent [CodeRemoteContentTypeName](/dotnet/api/microsoft.visualstudio.languageserver.client.coderemotecontentdefinition.coderemotecontenttypename?view=visualstudiosdk-2017).

Après avoir ajouté une définition de type de contenu, vous pouvez définir votre extension de client de langage dans la classe de client de langage de chargement :

```csharp
    [ContentType("bar")]
    [Export(typeof(ILanguageClient))]
    public class BarLanguageClient : ILanguageClient
    {
    }
```

Ajout de prise en charge pour les serveurs de langage LSP ne nécessite pas d’implémenter votre propre système de projet dans Visual Studio. Les clients peuvent ouvrir un seul fichier ou un dossier dans Visual Studio pour commencer à utiliser votre service de langage. En fait, la prise en charge pour les serveurs de langue LSP est conçu pour fonctionner uniquement dans les scénarios de dossier/fichier ouvert. Si un système de projet personnalisé est implémenté, certaines fonctionnalités (telles que les paramètres) ne fonctionnera pas.

## <a name="advanced-features"></a>Fonctionnalités avancées

### <a name="settings"></a>Paramètres

Prise en charge pour les paramètres linguistiques server personnalisés est disponible, mais il est toujours en cours améliorés. Les paramètres sont spécifiques à ce que le serveur de langage prend en charge et généralement contrôler comment le serveur de langage émet des données. Par exemple, un serveur de langage peut avoir un paramètre pour le nombre maximal d’erreurs signalées. Auteurs de l’extension définirait une valeur par défaut, ce qui peut être modifiée par les utilisateurs pour des projets spécifiques.

Suivez ces étapes ci-dessous pour ajouter la prise en charge des paramètres à votre extension de service de langage LSP :

1. Ajoutez un fichier JSON (par exemple, *MockLanguageExtensionSettings.json*) dans votre projet qui contient les paramètres et leurs valeurs par défaut. Exemple :

    ```json
    {
        "foo.maxNumberOfProblems": -1
    }
    ```

2. Avec le bouton droit sur le fichier JSON et sélectionnez **propriétés**. Modification la **Build** action pour « Content » et le « inclure dans VSIX' true à la propriété.

3. Implémenter ConfigurationSections et retourner la liste des préfixes pour les paramètres définis dans le fichier JSON (dans Visual Studio Code, il serait correspondre au nom de la section de configuration dans le fichier package.json) :

    ```csharp
    public IEnumerable<string> ConfigurationSections
    {
        get
        {
            yield return "foo";
        }
    }
    ```

4. Ajoutez un fichier .pkgdef au projet (ajouter le nouveau fichier texte et attribuez l’extension au fichier .pkgdef). Le fichier pkgdef doit contenir ces informations :

    ```
    [$RootKey$\OpenFolder\Settings\VSWorkspaceSettings\[settings-name]]
    @="$PackageFolder$\[settings-file-name].json"
    ```

    Aperçu :

    ```
    [$RootKey$\OpenFolder\Settings\VSWorkspaceSettings\MockLanguageExtension]
    @="$PackageFolder$\MockLanguageExtensionSettings.json"
    ```

5. Cliquez avec le bouton droit sur le fichier .pkgdef et sélectionnez **propriétés**. Modifier le **générer** action à **contenu** et **inclure dans VSIX** true à la propriété.

6. Ouvrez le *source.extension.vsixmanifest* fichier, puis ajoutez un élément multimédia dans le **Asset** onglet :

   ![modifier la ressource de package Visual Studio](media/lsp-add-vspackage-asset.png)

   * **Type**: Microsoft.VisualStudio.VsPackage
   * **Source**: Des fichiers sur le système de fichiers
   * **Chemin d’accès**: [chemin d’accès à votre *.pkgdef* fichier]

### <a name="user-editing-of-settings-for-a-workspace"></a>Modification de l’utilisateur des paramètres pour un espace de travail

1. Utilisateur ouvre un espace de travail contenant le propriétaire de votre serveur de fichiers.
2. Utilisateur ajoute un fichier dans le *.vs* dossier appelé *VSWorkspaceSettings.json*.
3. Utilisateur ajoute une ligne à la *VSWorkspaceSettings.json* fichier pour un paramètre fournit le serveur. Exemple :

    ```json
    {
        "foo.maxNumberOfProblems": 10
    }
    ```

### <a name="enabling-diagnostics-tracing"></a>L’activation du suivi de diagnostic

Traçage de diagnostic peut être activé pour tous les messages entre le client et le serveur, qui peut être utile lors du débogage des problèmes de sortie. Pour activer le suivi de diagnostic, procédez comme suit :

4. Ouvrez ou créez le fichier de paramètres d’espace de travail *VSWorkspaceSettings.json* (voir « Utilisateur modification de paramètres pour un espace de travail »).
5. Ajoutez la ligne suivante du fichier de paramètres json :

```json
{
    "foo.trace.server": "Off"
}
```

Il existe trois valeurs possibles pour le niveau de détail de trace :
* « Off » : le suivi complètement mise hors tension
* « Messages » : le suivi activé mais ID de nom et de réponse seule méthode est suivi.
* « Commentaires » : le suivi activé ; le message rpc entière est suivi.

Lorsque le suivi est activé sur le contenu est écrit dans un fichier dans le *%temp%\VisualStudio\LSP* directory. Le journal suit le format d’affectation de noms *[LanguageClientName]-[horodateur] .log*. Actuellement, le suivi ne peut être activé que pour les scénarios d’ouvrir le dossier. Ouverture d’un fichier unique pour activer un serveur de langage n’a pas la prise en charge de diagnostics.

### <a name="custom-messages"></a>Messages personnalisés

Il existe des API en place pour faciliter le passage de messages à et recevoir des messages à partir du serveur de langage qui ne font pas partie du protocole du serveur de langage standard. Pour gérer des messages personnalisés, implémentez [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017) interface dans votre classe de client de langage. [VS-StreamJsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/doc/index.md) bibliothèque est utilisée pour transmettre des messages personnalisés entre votre client de langage et le serveur de langage. Étant donné que votre extension de client de langage LSP s’apparente à une autre extension Visual Studio, vous pouvez décider d’ajouter des fonctionnalités supplémentaires (qui ne sont pas pris en charge par le LSP) pour Visual Studio (à l’aide d’autres API Visual Studio) dans votre extension via des messages personnalisés.

#### <a name="receiving-custom-messages"></a>Réception de messages personnalisés

Pour recevoir des messages personnalisés à partir du serveur de langage, vous devez implémenter le [CustomMessageTarget](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.custommessagetarget?view=visualstudiosdk-2017) propriété sur [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017) et retourner un objet qui sait comment gérer vos messages personnalisés . Exemple ci-dessous :

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

Pour envoyer des messages personnalisés sur le serveur de langage, vous devez implémenter le [AttachForCustomMessageAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.attachforcustommessageasync?view=visualstudiosdk-2017) méthode sur [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017). Cette méthode est appelée lorsque votre serveur de langage est démarré et prêt à recevoir des messages. Un [JsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/src/StreamJsonRpc/JsonRpc.cs) objet est passé comme un paramètre, vous pouvez conserver ensuite pour envoyer des messages au serveur de langage avec [VS-StreamJsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/doc/index.md) API. Exemple ci-dessous :

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

Un développeur d’extension peut souhaiter intercepter des LSP messages envoyés et reçus à partir du serveur de langage. Par exemple, un développeur d’extension peut à modifier le paramètre de message envoyé pour un message LSP particulier, ou modifier les résultats retournés à partir du serveur de langage pour une fonctionnalité LSP (saisies par exemple). Lorsque cela est nécessaire, les développeurs d’extensions peuvent utiliser l’API MiddleLayer pour intercepter les messages LSP.

Chaque message LSP ayant sa propre interface de couche intermédiaire pour l’interception. Pour intercepter un message particulier, créez une classe qui implémente l’interface de couche intermédiaire pour ce message. Ensuite, implémentez la [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017) interface dans votre classe de client de langage et de retourner une instance de votre objet dans le [MiddleLayer](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.middlelayer?view=visualstudiosdk-2017) propriété. Exemple ci-dessous :

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

La fonctionnalité de couche intermédiaire est toujours en cours de développement et pas encore complète.

## <a name="sample-lsp-language-server-extension"></a>Exemple d’extension de serveur LSP langage

Pour afficher le code source d’un exemple d’extension à l’aide de l’API du client LSP dans Visual Studio, consultez les exemples d’extensibilité d’extensibilité Visual Studio [exemple des LSP](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/LanguageServerProtocol).

## <a name="faq"></a>FAQ

**Je souhaite créer un système de projet personnalisé en supplément de mon serveur de langage LSP pour fournir la prise en charge de fonctionnalités plus riches dans Visual Studio, comment faire pour effectuer cette opération ?**

Prise en charge pour les serveurs de langage basé sur des LSP dans Visual Studio s’appuie sur le [fonctionnalité Ouvrir le dossier](https://devblogs.microsoft.com/visualstudio/open-any-folder-with-visual-studio-15-preview/) et est conçu spécialement pour ne pas exiger un système de projet personnalisé. Vous pouvez créer votre propre système de projet personnalisé suivant instructions [ici](https://github.com/Microsoft/VSProjectSystem), mais certaines fonctionnalités, telles que les paramètres, peuvent ne pas fonctionnent. La logique d’initialisation par défaut pour les serveurs de langage LSP consiste à passer dans l’emplacement du dossier racine du dossier actuellement ouvert, donc si vous utilisez un système de projet personnalisé, vous devrez peut-être fournir une logique personnalisée pendant l’initialisation pour vous assurer de votre serveur de langage peut démarrer correctement.

**Comment ajouter la prise en charge du débogueur ?**

Nous vous fournirons une prise en charge pour le [courants de débogage de protocole](https://code.visualstudio.com/docs/extensionAPI/api-debugging) dans une version ultérieure.

**S’il existe déjà un service de langage pris en charge Visual Studio installé (par exemple, JavaScript), puis-je encore installer une extension de serveur de langage LSP qui offre des fonctionnalités supplémentaires (par exemple, linting) ?**

Oui, mais toutes les fonctionnalités ne fonctionneront correctement. L’objectif ultime pour les extensions de serveur de langage LSP consiste à activer les services de langage pas en mode natif pris en charge par Visual Studio. Vous pouvez créer des extensions qui offrent la prise en charge supplémentaire à l’aide de serveurs de langage LSP, mais certaines fonctionnalités (telles que IntelliSense) ne sera pas d’une expérience sans heurts. En règle générale, il est recommandé que les extensions de serveur de langage LSP être utilisées pour fournir de nouvelles expériences de langage, ne pas étendre les objets existants.

**Où publier mon serveur de langage LSP VSIX terminé ?**

Consultez les instructions de la place de marché [ici](walkthrough-publishing-a-visual-studio-extension.md).
