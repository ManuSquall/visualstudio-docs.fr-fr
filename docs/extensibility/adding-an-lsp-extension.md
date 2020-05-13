---
title: Ajout d’une extension du protocole de serveur linguistique (fr) Microsoft Docs
ms.date: 11/14/2017
ms.topic: conceptual
ms.assetid: 52f12785-1c51-4c2c-8228-c8e10316cd83
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ef2093915538f09f425fc961420c4a3078043c91
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740234"
---
# <a name="add-a-language-server-protocol-extension"></a>Ajouter une extension du protocole de serveur de langage

Le protocole de serveur de langue (LSP) est un protocole commun, sous la forme de JSON RPC v2.0, utilisé pour fournir des fonctionnalités de service linguistique à divers éditeurs de code. En utilisant le protocole, les développeurs peuvent écrire un serveur de langue unique pour fournir des fonctionnalités de service linguistique comme IntelliSense, diagnostics d’erreurs, trouver toutes les références, et ainsi de suite, à divers éditeurs de code qui prennent en charge le LSP. Traditionnellement, les services linguistiques dans Visual Studio peuvent être ajoutés en utilisant des fichiers de grammaire TextMate pour fournir des fonctionnalités de base telles que la mise en évidence de la syntaxe ou en écrivant des services linguistiques personnalisés qui utilisent l’ensemble complet des API d’extabilité Visual Studio pour fournir des données plus riches. Avec le support Visual Studio pour LSP, il y a une troisième option.

![service de protocole de serveur de langue dans Visual Studio](media/lsp-service-in-VS.png)

## <a name="language-server-protocol"></a>Protocole de serveur de langage

![mise en œuvre du protocole du serveur de langue](media/lsp-implementation.png)

Cet article décrit comment créer une extension Visual Studio qui utilise un serveur de langue basé sur le LSP. Il suppose que vous avez déjà développé un serveur de langage basé sur le LSP et que vous souhaitez simplement l’intégrer dans Visual Studio.

Pour le support au sein de Visual Studio, les serveurs linguistiques peuvent communiquer avec le client (Visual Studio) via n’importe quel mécanisme de transmission basé sur le flux, par exemple :

* Flux d’entrée/sortie standard
* Canaux nommés
* Sockets (TCP seulement)

L’intention du LSP et son soutien dans Visual Studio est de prendre des services linguistiques qui ne font pas partie du produit Visual Studio. Il n’est pas destiné à étendre les services linguistiques existants (comme le C) dans Visual Studio. Pour étendre les langues existantes, consultez le guide d’extabilité du service linguistique (par exemple, la [plate-forme de compilateur "Roslyn" .NET)](../extensibility/dotnet-compiler-platform-roslyn-extensibility.md)ou voir [Extend the editor and language services](../extensibility/extending-the-editor-and-language-services.md).

Pour plus d’informations sur le protocole lui-même, voir la documentation [ici](https://github.com/Microsoft/language-server-protocol).

Pour plus d’informations sur la façon de créer un serveur de langue échantillon ou comment intégrer un serveur de langue existant dans Visual Studio Code, voir la documentation [ici](https://code.visualstudio.com/docs/extensions/example-language-server).

## <a name="language-server-protocol-supported-features"></a>Caractéristiques prises en charge par le protocole De serveur linguistique

Les tableaux suivants montrent quelles fonctionnalités LSP sont prises en charge dans Visual Studio:

Message | A un soutien dans Visual Studio
--- | ---
initialize | Oui
initialisé | Oui
shutdown | Oui
exit | Oui
$/cancelRequest | Oui
fenêtre/showMessage | Oui
fenêtre/showMessageRequest | Oui
fenêtre/logMessage | Oui
télémétrie/événement |
client/registerCapabilité |
client/non-enregistréCapabilité |
espace de travail/didChangeConfiguration | Oui
espace de travail/didChangeWatchedFiles | Oui
espace de travail/symbole | Oui
espace de travail/exécuterCommand | Oui
espace de travail/applicationEdit | Oui
textDocument/publishDiagnostics | Oui
textDocument/didOpen | Oui
textDocument/didChange | Oui
textDocument/willSave |
textDocument/willSaveWaitUntil |
textDocument/didSave | Oui
textDocument/didClose | Oui
textDocument/achèvement | Oui
achèvement/résolution | Oui
textDocument/hover | Oui
textDocument/signatureHelp | Oui
textDocument/références | Oui
textDocument/documentHighlight | Oui
textDocument/documentSymbol | Oui
textDocument/formatage | Oui
textDocument/rangeFormatting | Oui
textDocument/onTypeFormatting |
texteDocument/définition | Oui
textDocument/codeAction | Oui
textDocument/codeLens |
codeLens/résolution |
textDocument/documentLink |
documentLink/résolution |
textDocument/renomme | Oui

## <a name="get-started"></a>Bien démarrer

> [!NOTE]
> En commençant par Visual Studio 2017 version 15.8, le support pour le protocole commun de serveur de langue est intégré dans Visual Studio. Si vous avez construit des extensions LSP à l’aide de la version [VSIX de Language Server,](https://marketplace.visualstudio.com/items?itemName=vsext.LanguageServerClientPreview) elles cesseront de fonctionner une fois que vous passerez à la version 15.8 ou plus. Vous devrez faire ce qui suit pour que vos extensions de LSP fonctionnent à nouveau :
>
> 1. Désinstaller le Microsoft Visual Studio Language Server Protocol Preview VSIX.
>
>    En commençant par la version 15.8, chaque fois que vous effectuez une mise à niveau dans Visual Studio, l’aperçu VSIX est automatiquement détecté et supprimé.
>
> 2. Mettez à jour votre référence Nuget à la dernière version non-preview pour [les paquets LSP](https://www.nuget.org/packages/Microsoft.VisualStudio.LanguageServer.Client).
>
> 3. Supprimez la dépendance au Microsoft Visual Studio Language Server Protocol Preview VSIX dans votre manifeste VSIX.
>
> 4. Assurez-vous que votre VSIX spécifie Visual Studio 2017 version 15.8 Aperçu 3 comme la limite inférieure pour la cible d’installation.
>
> 5. Procédez maintenant à la régénération et au redéploiement.

### <a name="create-a-vsix-project"></a>Créer un projet VSIX

Pour créer une extension de service linguistique à l’aide d’un serveur de langue basé sur le LSP, assurez-vous d’abord que vous avez installé la charge de travail de **développement d’extension Visual Studio** pour votre exemple de VS.

Ensuite, créez un nouveau projet VSIX en naviguant pour **le projet De nouveau** > **projet** > **Visual CMD** > **Extensibility** > **VSIX Project**:

![créer un projet vsix](media/lsp-vsix-project.png)

### <a name="language-server-and-runtime-installation"></a>Serveur de langue et installation de temps d’exécution

Par défaut, les extensions créées pour prendre en charge les serveurs linguistiques basés sur le LSP dans Visual Studio ne contiennent pas les serveurs linguistiques eux-mêmes ou les temps d’exécution nécessaires pour les exécuter. Les développeurs d’extension sont responsables de la distribution des serveurs linguistiques et des temps d’exécution nécessaires. Il y a plusieurs façons de le faire :

* Les serveurs linguistiques peuvent être intégrés dans le VSIX sous forme de fichiers de contenu.
* Créez un MSI pour installer le serveur de langue et/ou les temps d’exécution nécessaires.
* Fournir des instructions sur Marketplace informant les utilisateurs comment obtenir des temps d’exécution et des serveurs linguistiques.

### <a name="textmate-grammar-files"></a>Fichiers de grammaire TextMate

Le LSP n’inclut pas de spécifications sur la façon de fournir la colorisation du texte pour les langues. Pour fournir une colorisation personnalisée pour les langues de Visual Studio, les développeurs d’extension peuvent utiliser un fichier de grammaire TextMate. Pour ajouter des fichiers de grammaire ou de thème TextMate personnalisés, suivez ces étapes :

1. Créez un dossier nommé "Grammars" à l’intérieur de votre extension (ou il peut être quel que soit le nom que vous choisissez).

2. À l’intérieur du dossier *Grammars,* inclure n’importe quel * \*.tmlanguage*, * \*.plist*, * \*.tmtheme*, ou * \*.json* fichiers que vous souhaitez qui fournissent la colorisation personnalisée.

   > [!TIP]
   > Un fichier *.tmtheme* définit la façon dont les portées sont cartographiques pour les classifications Visual Studio (appelées touches de couleur). Pour obtenir des conseils, vous pouvez faire référence au fichier global *.tmtheme* dans la *version %ProgramFiles(x86)% -Microsoft Visual\\\<Studio>\\ \<SKU>-Common7-IDE-CommonExtensions-Microsoft-TextMate-Starterkit-Themesg* directory.

3. Créez un fichier *.pkgdef* et ajoutez une ligne similaire à ceci :

    ```
    [$RootKey$\TextMate\Repositories]
    "MyLang"="$PackageFolder$\Grammars"
    ```

4. Cliquez à droite sur les fichiers et sélectionnez **les propriétés**. Modifier l’action **Construire** en **Contenu** et modifier **l’inclure dans la** propriété VSIX à **vrai**.

Après avoir terminé les étapes *précédentes,* un dossier Grammars est ajouté à l’annuaire d’installation du paquet comme une source de dépôt nommé «MyLang» («MyLang» est juste un nom pour la désambiguation et peut être n’importe quelle chaîne unique). Toutes les grammaires (fichiers *.tmlanguage)* et les fichiers thématiques (fichiers *.tmtheme)* dans ce répertoire sont ramassés comme des potentiels et ils remplacent les grammaires intégrées fournies avec TextMate. Si les extensions déclarées du fichier de grammaire correspondent à l’extension du fichier en cours d’ouverture, TextMate interdira.

## <a name="create-a-simple-language-client"></a>Créer un client de langue simple

### <a name="main-interface---ilanguageclient"></a>Interface principale - [ILanguageClient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017)

Après avoir créé votre projet VSIX, ajoutez le package NuGet suivant à votre projet :

* [Microsoft.VisualStudio.LanguageServer.Client](https://www.nuget.org/packages/Microsoft.VisualStudio.LanguageServer.Client)

> [!NOTE]
> Lorsque vous prenez une dépendance sur le paquet NuGet après avoir terminé les étapes précédentes, les paquets Newtonsoft.Json et StreamJsonRpc sont ajoutés à votre projet ainsi. **Ne mettez pas à jour ces paquets sauf si vous êtes certain que ces nouvelles versions seront installées sur la version de Visual Studio que vos objectifs d’extension**. Les assemblages ne seront pas inclus dans votre VSIX; au lieu de cela, ils seront ramassés à partir du répertoire d’installation Visual Studio. Si vous faites référence à une version plus récente des assemblages que ce qui est installé sur la machine d’un utilisateur, votre extension ne fonctionnera pas.

Vous pouvez ensuite créer une nouvelle classe qui implémente l’interface [ILanguageClient,](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017) qui est l’interface principale nécessaire pour les clients de langue se connectant à un serveur de langue basé sur le LSP.

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

Les principales méthodes qui doivent être mises en œuvre sont [OnLoadedAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.onloadedasync?view=visualstudiosdk-2017) et [ActivateAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.activateasync?view=visualstudiosdk-2017). [OnLoadedAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.onloadedasync?view=visualstudiosdk-2017) est appelé lorsque Visual Studio a chargé votre extension et votre serveur de langue est prêt à être lancé. Dans cette méthode, vous pouvez invoquer le délégué [StartAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017) immédiatement pour signaler que le serveur de langue doit être lancé, ou vous pouvez faire une logique supplémentaire et invoquer [StartAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017) plus tard. **Pour activer votre serveur de langue, vous devez appeler StartAsync à un moment donné.**

[ActivateAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.activateasync?view=visualstudiosdk-2017) est la méthode finalement invoquée en appelant le délégué [StartAsync.](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017) Il contient la logique pour démarrer le serveur de langue et d’établir la connexion à elle. Un objet de connexion qui contient des flux pour écrire au serveur et lire à partir du serveur doit être retourné. Toutes les exceptions lancées ici sont prises et affichées à l’utilisateur via un message InfoBar dans Visual Studio.

### <a name="activation"></a>Activation

Une fois que votre classe de client linguistique est implémentée, vous devrez définir deux attributs pour qu’il définisse comment il sera chargé dans Visual Studio et activé :

```csharp
  [Export(typeof(ILanguageClient))]
  [ContentType("bar")]
```

### <a name="mef"></a>MEF

Visual Studio utilise [MEF](https://github.com/Microsoft/vs-mef/blob/master/doc/index.md) (Managed Extensibility Framework) pour gérer ses points d’exténuabilité. [L’attribut Export](/dotnet/api/system.componentmodel.composition.exportattribute) indique à Visual Studio que cette classe doit être ramassée comme point d’extension et chargée au moment approprié.

Pour utiliser MEF, vous devez également définir meF comme un actif dans le manifeste VSIX.

Ouvrez votre concepteur manifeste VSIX et naviguez vers l’onglet **Actifs** :

![ajouter de l’actif MEF](media/lsp-add-asset.png)

Cliquez **sur Nouveau** pour créer un nouvel actif :

![définir l’actif MEF](media/lsp-define-asset.png)

* **Type**: Microsoft.VisualStudio.MefComponent
* **Source**: Un projet dans la solution actuelle
* **Projet**: [Votre projet]

### <a name="content-type-definition"></a>Définition de type de contenu

Actuellement, la seule façon de charger votre extension de serveur de langue basée sur le LSP est par type de contenu de fichier. Autrement dit, lors de la définition de votre classe de client de langue (qui implémente [ILanguageClient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017)), vous aurez besoin de définir les types de fichiers qui, une fois ouvert, causera votre extension à charger. Si aucun fichier correspondant à votre type de contenu défini n’est ouvert, votre extension ne sera pas chargée.

Ceci se fait en `ContentTypeDefinition` définissant une ou plusieurs classes :

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

Dans l’exemple précédent, une définition de type de contenu est créée pour les fichiers qui se terminent par une extension de fichiers *.bar.* La définition de type de contenu est donnée le nom "bar" et doit dériver de [CodeRemoteContentTypeName](/dotnet/api/microsoft.visualstudio.languageserver.client.coderemotecontentdefinition.coderemotecontenttypename?view=visualstudiosdk-2017).

Après avoir ajouté une définition de type de contenu, vous pouvez alors définir quand charger l’extension de votre client linguistique dans la classe client de langue :

```csharp
    [ContentType("bar")]
    [Export(typeof(ILanguageClient))]
    public class BarLanguageClient : ILanguageClient
    {
    }
```

L’ajout de support pour les serveurs linguistiques LSP ne vous oblige pas à implémenter votre propre système de projet dans Visual Studio. Les clients peuvent ouvrir un seul fichier ou un dossier dans Visual Studio pour commencer à utiliser votre service linguistique. En fait, la prise en charge des serveurs linguistiques LSP est conçue pour fonctionner uniquement dans des scénarios de dossier/fichier ouverts. Si un système de projet personnalisé est implémenté, certaines fonctionnalités (comme les paramètres) ne fonctionneront pas.

## <a name="advanced-features"></a>Fonctionnalités avancées

### <a name="settings"></a>Paramètres

La prise en charge des paramètres personnalisés spécifiques au serveur de langue est disponible, mais elle est toujours en cours d’amélioration. Les paramètres sont spécifiques à ce que le serveur de langue prend en charge et contrôlent généralement la façon dont le serveur de langue émet des données. Par exemple, un serveur de langue peut avoir un paramètre pour le nombre maximum d’erreurs signalées. Les auteurs d’extension définiraient une valeur par défaut, qui peut être modifiée par les utilisateurs pour des projets spécifiques.

Suivez ces étapes ci-dessous pour ajouter la prise en charge des paramètres de votre extension de service linguistique LSP :

1. Ajoutez un fichier JSON (par exemple, *MockLanguageExtensionSettings.json*) à votre projet qui contient les paramètres et leurs valeurs par défaut. Par exemple :

    ```json
    {
        "foo.maxNumberOfProblems": -1
    }
    ```

2. Cliquez à droite sur le fichier JSON et sélectionnez **propriétés**. Modifier l’action **Build** en "Contenu" et le "Inclure dans la propriété vsIX à **vrai**.

3. Implémentez configurationSections et retournez la liste des préfixes pour les paramètres définis dans le fichier JSON (Dans le code visual studio, cela serait la carte du nom de la section de configuration dans package.json):

    ```csharp
    public IEnumerable<string> ConfigurationSections
    {
        get
        {
            yield return "foo";
        }
    }
    ```

4. Ajoutez un fichier .pkgdef au projet (ajouter un nouveau fichier texte et modifier l’extension du fichier en .pkgdef). Le fichier pkgdef doit contenir cette information :

    ```
    [$RootKey$\OpenFolder\Settings\VSWorkspaceSettings\[settings-name]]
    @="$PackageFolder$\[settings-file-name].json"
    ```

    Exemple :

    ```
    [$RootKey$\OpenFolder\Settings\VSWorkspaceSettings\MockLanguageExtension]
    @="$PackageFolder$\MockLanguageExtensionSettings.json"
    ```

5. Cliquez à droite sur le fichier .pkgdef et sélectionnez **propriétés**. Modifier l’action **Build** en **contenu** et **l’inclure dans la** propriété VSIX à **vrai**.

6. Ouvrez le fichier *source.extension.vsixmanifest* et ajoutez un actif dans **l’onglet Asset** :

   ![modifier l’actif vspackage](media/lsp-add-vspackage-asset.png)

   * **Type**: Microsoft.VisualStudio.VsPackage
   * **Source**: Fichier sur le système de fichiers
   * **Chemin**: [Chemin vers votre fichier *.pkgdef]*

### <a name="user-editing-of-settings-for-a-workspace"></a>Modification des paramètres par l’utilisateur pour un espace de travail

1. L’utilisateur ouvre un espace de travail contenant des fichiers que possède votre serveur.
2. L’utilisateur ajoute un fichier dans le dossier *.vs* appelé *VSWorkspaceSettings.json*.
3. L’utilisateur ajoute une ligne au fichier *VSWorkspaceSettings.json* pour un paramètre que le serveur fournit. Par exemple :

    ```json
    {
        "foo.maxNumberOfProblems": 10
    }
    ```

### <a name="enable-diagnostics-tracing"></a>Activer le traçage des diagnostics

Le traçage des diagnostics peut être activé pour produire tous les messages entre le client et le serveur, ce qui peut être utile lors de la débogage des problèmes. Pour permettre le traçage diagnostique, faites ce qui suit :

1. Ouvrez ou créez les paramètres de l’espace de travail fichier *VSWorkspaceSettings.json* (voir "Édition utilisateur des paramètres pour un espace de travail").
2. Ajouter la ligne suivante dans le fichier json paramètres :

```json
{
    "foo.trace.server": "Off"
}
```

Il existe trois valeurs possibles pour la verbosité des traces :

* "Off": traçage éteint complètement
* "Messages": traçage activé, mais seul le nom de la méthode et id de réponse sont tracés.
* "Verbose": traçage allumé; l’ensemble du message rpc est tracé.

Lorsque le traçage est activé, le contenu est écrit sur un fichier dans *l’annuaire %temp%-VisualStudio-LSP.* Le journal suit le format de nommage *[LanguageClientName]-[Datetime Stamp].log*. À l’heure actuelle, le traçage ne peut être activé que pour les scénarios de dossiers ouverts. L’ouverture d’un seul fichier pour activer un serveur linguistique n’a pas de support de traçage de diagnostics.

### <a name="custom-messages"></a>Messages personnalisés

Des API sont en place pour faciliter la transmission de messages et la réception de messages du serveur linguistique qui ne font pas partie du protocole standard du serveur de langue. Pour gérer les messages [personnalisés, implémentez l’interface ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017) dans votre classe de clients linguistiques. La bibliothèque [VS-StreamJsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/doc/index.md) est utilisée pour transmettre des messages personnalisés entre votre client linguistique et votre serveur linguistique. Étant donné que votre extension de client en langue LSP est comme n’importe quelle autre extension Visual Studio, vous pouvez décider d’ajouter des fonctionnalités supplémentaires (qui ne sont pas prises en charge par le LSP) à Visual Studio (en utilisant d’autres API Visual Studio) dans votre extension par le biais de messages personnalisés.

#### <a name="receive-custom-messages"></a>Recevez des messages personnalisés

Pour recevoir des messages personnalisés du serveur linguistique, implémentez la propriété [CustomMessageTarget](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.custommessagetarget?view=visualstudiosdk-2017) sur [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017) et retournez un objet qui sait gérer vos messages personnalisés. Exemple ci-dessous :

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

#### <a name="send-custom-messages"></a>Envoyer des messages personnalisés

Pour envoyer des messages personnalisés au serveur de langue, implémentez la méthode [AttachForCustomMessageAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.attachforcustommessageasync?view=visualstudiosdk-2017) sur [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017). Cette méthode est invoquée lorsque votre serveur linguistique est démarré et prêt à recevoir des messages. Un objet [JsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/src/StreamJsonRpc/JsonRpc.cs) est passé comme un paramètre, que vous pouvez ensuite conserver pour envoyer des messages au serveur de langue à l’aide d’API [VS-StreamJsonRpc.](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/doc/index.md) Exemple ci-dessous :

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

### <a name="middle-layer"></a>Couche moyenne

Parfois, un développeur d’extension peut vouloir intercepter les messages LSP envoyés et reçus du serveur de langue. Par exemple, un développeur d’extension peut vouloir modifier le paramètre de message envoyé pour un message LSP particulier, ou modifier les résultats retournés à partir du serveur de langue pour une fonctionnalité LSP (par exemple les achèvements). Lorsque cela est nécessaire, les développeurs d’extension peuvent utiliser l’API MiddleLayer pour intercepter les messages LSP.

Chaque message LSP a sa propre interface de couche moyenne pour l’interception. Pour intercepter un message particulier, créez une classe qui implémente l’interface de la couche centrale pour ce message. Ensuite, implémentez l’interface [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017) dans votre classe de client de langue et retournez une instance de votre objet dans la propriété [MiddleLayer.](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.middlelayer?view=visualstudiosdk-2017) Exemple ci-dessous :

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

La fonction de couche moyenne est encore en cours de développement et n’est pas encore complète.

## <a name="sample-lsp-language-server-extension"></a>Exemple d’extension du serveur linguistique LSP

Pour voir le code source d’une extension d’échantillon à l’aide de l’API client LSP dans Visual Studio, consultez l’échantillon VSSDK-Extensibility-Samples [LSP](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/LanguageServerProtocol).

## <a name="faq"></a>Questions fréquentes (FAQ)

**Je voudrais construire un système de projet personnalisé pour compléter mon serveur de langue LSP pour fournir un support de fonctionnalité plus riche dans Visual Studio, comment puis-je faire cela?**

La prise en charge des serveurs linguistiques basés sur le LSP dans Visual Studio repose sur la [fonction de dossier ouvert](https://devblogs.microsoft.com/visualstudio/open-any-folder-with-visual-studio-15-preview/) et est conçue pour ne pas nécessiter un système de projet personnalisé. Vous pouvez construire votre propre système de projet personnalisé en suivant les instructions [ici,](https://github.com/Microsoft/VSProjectSystem)mais certaines fonctionnalités, telles que les paramètres, peuvent ne pas fonctionner. La logique d’initialisation par défaut pour les serveurs linguistiques LSP est de passer dans l’emplacement du dossier racine du dossier actuellement ouvert, donc si vous utilisez un système de projet personnalisé, vous devrez peut-être fournir une logique personnalisée lors de l’initialisation pour s’assurer que votre serveur de langue peut démarrer correctement.

**Comment ajouter un support de débbugger ?**

Nous fournirons un soutien pour le [protocole commun de débogage](https://code.visualstudio.com/docs/extensionAPI/api-debugging) dans une prochaine version.

**S’il existe déjà un service de langue supporté VS installé (par exemple, JavaScript), puis-je encore installer une extension de serveur de langue LSP qui offre des fonctionnalités supplémentaires (comme le linting)?**

Oui, mais toutes les fonctionnalités ne fonctionneront pas correctement. L’objectif ultime pour les extensions de serveur en langue LSP est de permettre aux services linguistiques non pris en charge par Visual Studio. Vous pouvez créer des extensions qui offrent un support supplémentaire à l’aide de serveurs en langage LSP, mais certaines fonctionnalités (comme IntelliSense) ne seront pas une expérience en douceur. En général, il est conseillé d’utiliser des extensions de serveur de langue LSP pour fournir de nouvelles expériences linguistiques, et non pour étendre celles existantes.

**Où puis-je publier mon serveur de langue LSP rempli VSIX ?**

Voir les instructions Marketplace [ici](walkthrough-publishing-a-visual-studio-extension.md).

## <a name="see-also"></a>Voir aussi

- [Ajouter la prise en charge de l’éditeur Visual Studio pour d’autres langages](../ide/adding-visual-studio-editor-support-for-other-languages.md)
