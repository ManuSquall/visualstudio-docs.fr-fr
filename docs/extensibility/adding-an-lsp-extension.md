---
title: Ajout d’une extension de protocole de serveur de langage | Microsoft Docs
description: Découvrez comment créer une extension Visual Studio qui intègre un serveur de langage basé sur le protocole de serveur de langue (LSP).
ms.custom: SEO-VS-2020
ms.date: 11/14/2017
ms.topic: conceptual
ms.assetid: 52f12785-1c51-4c2c-8228-c8e10316cd83
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: accf054cbf0b58066568124a3f35e064ce3cba78
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105094989"
---
# <a name="add-a-language-server-protocol-extension"></a>Ajouter une extension du protocole de serveur de langage

Le protocole de serveur de langage (LSP) est un protocole courant, sous la forme de JSON RPC v 2.0, utilisé pour fournir des fonctionnalités de service de langage à différents éditeurs de code. À l’aide du protocole, les développeurs peuvent écrire un serveur de langage unique pour fournir des fonctionnalités de service de langage comme IntelliSense, les diagnostics d’erreur, rechercher toutes les références, etc., à différents éditeurs de code qui prennent en charge LSP. Traditionnellement, les services de langage dans Visual Studio peuvent être ajoutés à l’aide des fichiers de grammaire TextMate pour fournir des fonctionnalités de base telles que la mise en surbrillance de la syntaxe ou l’écriture de services de langage personnalisés qui utilisent l’ensemble des API d’extensibilité Visual Studio pour fournir des données plus riches. Avec la prise en charge de Visual Studio pour LSP, il existe une troisième option.

![Language Server Protocol service dans Visual Studio](media/lsp-service-in-VS.png)

## <a name="language-server-protocol"></a>Protocole de serveur de langage

![implémentation du protocole de serveur de langage](media/lsp-implementation.png)

Cet article explique comment créer une extension Visual Studio qui utilise un serveur de langage basé sur LSP. Il part du principe que vous avez déjà développé un serveur de langage LSP et que vous souhaitez simplement l’intégrer dans Visual Studio.

Pour la prise en charge dans Visual Studio, les serveurs de langage peuvent communiquer avec le client (Visual Studio) via un mécanisme de transmission basé sur le flux, par exemple :

* Flux d’entrée/sortie standard
* Canaux nommés
* Sockets (TCP uniquement)

L’objectif du LSP et sa prise en charge dans Visual Studio sont les services de langage intégrés qui ne font pas partie du produit Visual Studio. Elle n’est pas destinée à étendre les services de langage existants (tels que C#) dans Visual Studio. Pour étendre les langages existants, reportez-vous au Guide d’extensibilité du service de langage (par exemple, le [.NET Compiler Platform « Roslyn »](../extensibility/dotnet-compiler-platform-roslyn-extensibility.md)) ou consultez [étendre l’éditeur et les services de langage](../extensibility/extending-the-editor-and-language-services.md).

Pour plus d’informations sur le protocole lui-même, consultez la documentation [ici](https://github.com/Microsoft/language-server-protocol).

Pour plus d’informations sur la création d’un exemple de serveur de langage ou sur l’intégration d’un serveur de langage existant dans Visual Studio Code, consultez la documentation [ici](https://code.visualstudio.com/docs/extensions/example-language-server).

## <a name="language-server-protocol-supported-features"></a>Fonctionnalités prises en charge par le protocole de serveur de langage

Les tableaux suivants indiquent les fonctionnalités LSP prises en charge dans Visual Studio :

Message | Prend en charge dans Visual Studio
--- | ---
initialize | Oui
initialisé | Oui
shutdown | Oui
exit | Oui
$/cancelRequest | Oui
Window/showMessage | Oui
fenêtre/showMessageRequest | Oui
fenêtre/logMessage | Oui
télémétrie/événement |
client/registerCapability |
client/unregisterCapability |
espace de travail/didChangeConfiguration | Oui
espace de travail/didChangeWatchedFiles | Oui
espace de travail/symbole | Oui
espace de travail/executeCommand | Oui
espace de travail/applyEdit | Oui
textDocument/publishDiagnostics | Oui
textDocument/didOpen | Oui
textDocument/didChange | Oui
textDocument/willSave |
textDocument/willSaveWaitUntil |
textDocument/didSave | Oui
textDocument/didClose | Oui
textDocument/achèvement | Oui
achèvement/résolution | Oui
textDocument/pointage | Oui
textDocument/signatureHelp | Oui
textDocument/références | Oui
textDocument/documentHighlight | Oui
textDocument/documentSymbol | Oui
textDocument/mise en forme | Oui
textDocument/rangeFormatting | Oui
textDocument/onTypeFormatting |
textDocument/définition | Oui
textDocument/codeAction | Oui
textDocument/codeLens |
codeLens/résoudre |
textDocument/documentLink |
documentLink/résoudre |
textDocument/renommer | Oui

## <a name="get-started"></a>Bien démarrer

> [!NOTE]
> À compter de Visual Studio 2017 version 15,8, la prise en charge du protocole du serveur de langage commun est intégrée à Visual Studio. Si vous avez créé des extensions LSP à l’aide de la version [VSIX du client du serveur de langue](https://marketplace.visualstudio.com/items?itemName=vsext.LanguageServerClientPreview) préliminaire, elles cessent de fonctionner après la mise à niveau vers la version 15,8 ou une version ultérieure. Vous devrez effectuer les opérations suivantes pour réutiliser les extensions LSP :
>
> 1. Désinstallez la version préliminaire VSIX du protocole Microsoft Visual Studio Language Server.
>
>    À partir de la version 15,8, chaque fois que vous effectuez une mise à niveau dans Visual Studio, la préversion VSIX est automatiquement détectée et supprimée.
>
> 2. Mettez à jour votre référence NuGet vers la dernière version non Preview pour les [packages LSP](https://www.nuget.org/packages/Microsoft.VisualStudio.LanguageServer.Client).
>
> 3. Supprimez la dépendance à la version préliminaire VSIX du protocole Microsoft Visual Studio Language Server dans votre manifeste VSIX.
>
> 4. Assurez-vous que votre extension VSIX spécifie Visual Studio 2017 version 15,8 Preview 3 comme limite inférieure pour la cible d’installation.
>
> 5. Procédez maintenant à la régénération et au redéploiement.

### <a name="create-a-vsix-project"></a>Créer un projet VSIX

Pour créer une extension de service de langage à l’aide d’un serveur de langage LSP, commencez par vérifier que la charge de travail **développement d’extension Visual Studio** est installée pour votre instance de vs.

Ensuite, créez un projet VSIX en accédant à **fichier**  >  **nouveau projet**  >  **extension Visual C#**  >    >  **projet VSIX**:

![créer un projet VSIX](media/lsp-vsix-project.png)

### <a name="language-server-and-runtime-installation"></a>Installation du serveur de langage et du Runtime

Par défaut, les extensions créées pour prendre en charge les serveurs de langues LSP dans Visual Studio ne contiennent pas les serveurs de langue eux-mêmes ou les runtimes nécessaires pour les exécuter. Les développeurs d’extensions sont responsables de la distribution des serveurs de langage et des runtimes nécessaires. Il existe plusieurs façons de procéder :

* Les serveurs de langage peuvent être incorporés dans le VSIX en tant que fichiers de contenu.
* Créez un MSI pour installer le serveur de langage et/ou les runtimes nécessaires.
* Fournissez des instructions sur la place de marché informant les utilisateurs sur la façon d’obtenir des runtimes et des serveurs de langage.

### <a name="textmate-grammar-files"></a>Fichiers de grammaire TextMate

Le LSP n’inclut pas de spécification sur la manière de fournir la coloration du texte pour les langues. Pour fournir une colorisation personnalisée pour les langages dans Visual Studio, les développeurs d’extensions peuvent utiliser un fichier de grammaire TextMate. Pour ajouter des fichiers de TextMate ou de grammaire personnalisés, procédez comme suit :

1. Créez un dossier nommé « Grammars » dans votre extension (ou le nom que vous choisissez).

2. Dans le dossier *Grammars* , incluez tous les fichiers *\* . tmlanguage*, *\* . plist*, *\* . tmtheme* ou *\* . JSON* souhaités pour fournir une colorisation personnalisée.

   > [!TIP]
   > Un fichier *. tmtheme* définit la manière dont les étendues sont mappées aux classifications Visual Studio (clés de couleur nommées). Pour obtenir de l’aide, vous pouvez référencer le fichier global *. tmtheme* dans le répertoire *% ProgramFiles (x86)% \ Microsoft Visual Studio \\ \<version> \\ \<SKU> \Common7\IDE\CommonExtensions\Microsoft\TextMate\Starterkit\Themesg*

3. Créez un fichier *. pkgdef* et ajoutez une ligne semblable à celle-ci :

    ```
    [$RootKey$\TextMate\Repositories]
    "MyLang"="$PackageFolder$\Grammars"
    ```

4. Cliquez avec le bouton droit sur les fichiers et sélectionnez **Propriétés**. Modifiez l’action de **génération** en **contenu** et remplacez la propriété **inclure dans VSIX** par **true**.

Une fois les étapes précédentes terminées, un dossier de *grammaires* est ajouté au répertoire d’installation du package sous la forme d’une source de référentiel nommée « MyLang » (« MyLang » est simplement un nom pour la désambiguïsation et peut être toute chaîne unique). Toutes les grammaires (fichiers *. tmlanguage* ) et les fichiers de thème (fichiers *. tmtheme* ) de ce répertoire sont récupérés comme des potentiels et ils remplacent les grammaires intégrées fournies avec TextMate. Si les extensions déclarées du fichier de grammaire correspondent à l’extension du fichier en cours d’ouverture, TextMate effectue un pas à pas détaillé.

## <a name="create-a-simple-language-client"></a>Créer un client de langage simple

### <a name="main-interface---ilanguageclient"></a>Interface principale- [ILanguageClient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017&preserve-view=true)

Après avoir créé votre projet VSIX, ajoutez le ou les packages NuGet suivants à votre projet :

* [Microsoft. VisualStudio. LanguageServer. client](https://www.nuget.org/packages/Microsoft.VisualStudio.LanguageServer.Client)

> [!NOTE]
> Lorsque vous prenez une dépendance sur le package NuGet une fois que vous avez effectué les étapes précédentes, les packages Newtonsoft.Jssur et StreamJsonRpc sont également ajoutés à votre projet. **Ne mettez pas à jour ces packages, sauf si vous êtes certain que ces nouvelles versions seront installées sur la version de Visual Studio que votre extension cible**. Les assemblys ne sont pas inclus dans votre VSIX ; au lieu de cela, ils sont récupérés dans le répertoire d’installation de Visual Studio. Si vous référencez une version plus récente des assemblys que celle qui est installée sur l’ordinateur d’un utilisateur, votre extension ne fonctionnera pas.

Vous pouvez ensuite créer une nouvelle classe qui implémente l’interface [ILanguageClient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017&preserve-view=true) , qui est l’interface principale requise pour les clients de langage se connectant à un serveur de langage basé sur LSP.

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

Les principales méthodes qui doivent être implémentées sont [OnLoadedAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.onloadedasync?view=visualstudiosdk-2017&preserve-view=true) et [ActivateAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.activateasync?view=visualstudiosdk-2017&preserve-view=true). [OnLoadedAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.onloadedasync?view=visualstudiosdk-2017&preserve-view=true) est appelé lorsque Visual Studio a chargé votre extension et que votre serveur de langage est prêt à être démarré. Dans cette méthode, vous pouvez appeler le délégué [StartAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017&preserve-view=true) immédiatement pour signaler que le serveur de langage doit être démarré, ou vous pouvez effectuer une logique supplémentaire et appeler [StartAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017&preserve-view=true) ultérieurement. **Pour activer votre serveur de langue, vous devez appeler StartAsync à un moment donné.**

[ActivateAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.activateasync?view=visualstudiosdk-2017&preserve-view=true) est la méthode éventuellement appelée en appelant le délégué [StartAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017&preserve-view=true) . Il contient la logique permettant de démarrer le serveur de langage et d’établir une connexion à celui-ci. Un objet de connexion qui contient des flux pour l’écriture sur le serveur et la lecture à partir du serveur doivent être retournés. Toutes les exceptions levées ici sont interceptées et affichées à l’utilisateur via un message de la barre d’informations dans Visual Studio.

### <a name="activation"></a>Activation

Une fois que votre classe de client de langage est implémentée, vous devez définir deux attributs pour lui afin de définir la façon dont il sera chargé dans Visual Studio et activé :

```csharp
  [Export(typeof(ILanguageClient))]
  [ContentType("bar")]
```

### <a name="mef"></a>MEF

Visual Studio utilise [MEF](https://github.com/Microsoft/vs-mef/blob/master/doc/index.md) (Managed Extensibility Framework) pour gérer ses points d’extensibilité. L’attribut [Export](/dotnet/api/system.componentmodel.composition.exportattribute) indique à Visual Studio que cette classe doit être récupérée en tant que point d’extension et chargée à l’heure appropriée.

Pour utiliser MEF, vous devez également définir MEF en tant que ressource dans le manifeste VSIX.

Ouvrez votre concepteur de manifeste VSIX et accédez à l’onglet **ressources** :

![Ajouter un élément multimédia MEF](media/lsp-add-asset.png)

Cliquez sur **nouveau** pour créer un élément multimédia :

![définir la ressource MEF](media/lsp-define-asset.png)

* **Type**: Microsoft. VisualStudio. MEFComponent
* **Source**: projet dans la solution actuelle
* **Projet**: [votre projet]

### <a name="content-type-definition"></a>Définition du type de contenu

Actuellement, la seule façon de charger votre extension de serveur de langage LSP est par type de contenu de fichier. Autrement dit, lors de la définition de la classe de votre client de langage (qui implémente [ILanguageClient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017&preserve-view=true)), vous devez définir les types de fichiers qui, une fois ouverts, provoquent le chargement de votre extension. Si aucun fichier correspondant à votre type de contenu défini n’est ouvert, votre extension ne sera pas chargée.

Pour ce faire, vous définissez une ou plusieurs `ContentTypeDefinition` classes :

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

Dans l’exemple précédent, une définition de type de contenu est créée pour les fichiers qui se terminent par l’extension de fichier *. bar* . La définition du type de contenu reçoit le nom « bar » et doit dériver de [CodeRemoteContentTypeName](/dotnet/api/microsoft.visualstudio.languageserver.client.coderemotecontentdefinition.coderemotecontenttypename?view=visualstudiosdk-2017&preserve-view=true).

Après avoir ajouté une définition de type de contenu, vous pouvez définir à quel moment charger votre extension de client de langage dans la classe de langage client :

```csharp
    [ContentType("bar")]
    [Export(typeof(ILanguageClient))]
    public class BarLanguageClient : ILanguageClient
    {
    }
```

L’ajout de la prise en charge des serveurs de langues LSP ne vous oblige pas à implémenter votre propre système de projet dans Visual Studio. Les clients peuvent ouvrir un seul fichier ou dossier dans Visual Studio pour commencer à utiliser votre service de langage. En fait, la prise en charge des serveurs de langues LSP est conçue pour fonctionner uniquement dans les scénarios ouverts de dossiers/fichiers. Si un système de projet personnalisé est implémenté, certaines fonctionnalités (telles que les paramètres) ne fonctionneront pas.

## <a name="advanced-features"></a>Fonctionnalités avancées

### <a name="settings"></a>Paramètres

La prise en charge des paramètres spécifiques au serveur de langage personnalisé est disponible, mais elle est toujours en cours d’amélioration. Les paramètres sont spécifiques à ce que le serveur de langage prend en charge et contrôlent généralement la manière dont le serveur de langage émet les données. Par exemple, un serveur de langage peut avoir un paramètre pour le nombre maximal d’erreurs signalées. Les auteurs d’extensions définissent une valeur par défaut, qui peut être modifiée par les utilisateurs pour des projets spécifiques.

Suivez les étapes ci-dessous pour ajouter la prise en charge des paramètres à votre extension de service de langage LSP :

1. Ajoutez un fichier JSON (par exemple, *MockLanguageExtensionSettings.js*) à votre projet qui contient les paramètres et leurs valeurs par défaut. Par exemple :

    ```json
    {
        "foo.maxNumberOfProblems": -1
    }
    ```

2. Cliquez avec le bouton droit sur le fichier JSON et sélectionnez **Propriétés**. Définissez l’action de **génération** sur « contenu » et la propriété « inclure dans VSIX » sur **true**.

3. Implémentez ConfigurationSections et retournez la liste des préfixes pour les paramètres définis dans le fichier JSON (dans Visual Studio Code, cette valeur est mappée au nom de la section de configuration dans package.jssur) :

    ```csharp
    public IEnumerable<string> ConfigurationSections
    {
        get
        {
            yield return "foo";
        }
    }
    ```

4. Ajoutez un fichier. pkgdef au projet (ajoutez un nouveau fichier texte et remplacez l’extension de fichier par. pkgdef). Le fichier pkgdef doit contenir les informations suivantes :

    ```
    [$RootKey$\OpenFolder\Settings\VSWorkspaceSettings\[settings-name]]
    @="$PackageFolder$\[settings-file-name].json"
    ```

    Exemple :

    ```
    [$RootKey$\OpenFolder\Settings\VSWorkspaceSettings\MockLanguageExtension]
    @="$PackageFolder$\MockLanguageExtensionSettings.json"
    ```

5. Cliquez avec le bouton droit sur le fichier. pkgdef et sélectionnez **Propriétés**. Remplacez l’action de **génération** par **contenu** et la propriété **inclure dans VSIX** par **true**.

6. Ouvrez le fichier *source. extension. vsixmanifest* et ajoutez un élément multimédia dans l’onglet **ressource** :

   ![modifier un élément multimédia VSPackage](media/lsp-add-vspackage-asset.png)

   * **Type**: Microsoft. VisualStudio. VSPackage
   * **Source**: fichier sur le système de fichiers
   * **Chemin d’accès**: [chemin d’accès à votre fichier *. pkgdef* ]

### <a name="user-editing-of-settings-for-a-workspace"></a>Modification par l’utilisateur des paramètres d’un espace de travail

1. L’utilisateur ouvre un espace de travail contenant les fichiers détenus par votre serveur.
2. L’utilisateur ajoute un fichier dans le dossier *. vs* appelé *VSWorkspaceSettings.jssur*.
3. L’utilisateur ajoute une ligne au fichier *VSWorkspaceSettings.js* pour un paramètre fourni par le serveur. Par exemple :

    ```json
    {
        "foo.maxNumberOfProblems": 10
    }
    ```

### <a name="enable-diagnostics-tracing"></a>Activer le suivi des diagnostics

Le suivi des diagnostics peut être activé pour la sortie de tous les messages entre le client et le serveur, ce qui peut être utile lors du débogage de problèmes. Pour activer le suivi de diagnostic, procédez comme suit :

1. Ouvrez ou créez le fichier de paramètres de l’espace de travail *VSWorkspaceSettings.js* (voir « modification par l’utilisateur des paramètres d’un espace de travail »).
2. Ajoutez la ligne suivante dans le fichier JSON des paramètres :

```json
{
    "foo.trace.server": "Off"
}
```

Il existe trois valeurs possibles pour les commentaires de suivi :

* "OFF" : le suivi est désactivé complètement
* « Messages » : le suivi est activé, mais seuls le nom de la méthode et l’ID de réponse sont suivis.
* « Verbose » : le traçage est activé ; le message RPC entier est suivi.

Lorsque le traçage est activé, le contenu est écrit dans un fichier dans le répertoire *%temp%\VisualStudio\LSP* Le journal suit le format d’affectation *de noms [LanguageClientName]-[horodatage DateTime]. log*. Actuellement, le suivi ne peut être activé que pour les scénarios de dossiers ouverts. L’ouverture d’un seul fichier pour activer un serveur de langue ne prend pas en charge le suivi des Diagnostics.

### <a name="custom-messages"></a>Messages personnalisés

Des API sont en place pour faciliter le transfert de messages vers et la réception de messages à partir du serveur de langue qui ne font pas partie du protocole de serveur de langage standard. Pour gérer les messages personnalisés, implémentez l’interface [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017&preserve-view=true) dans votre classe de client de langage. La bibliothèque [vs-StreamJsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/doc/index.md) est utilisée pour transmettre des messages personnalisés entre votre client de langage et le serveur de langage. Étant donné que l’extension de votre client de langue LSP est identique à toute autre extension Visual Studio, vous pouvez décider d’ajouter des fonctionnalités supplémentaires (qui ne sont pas prises en charge par le LSP) à Visual Studio (à l’aide d’autres API Visual Studio) dans votre extension par le biais de messages personnalisés.

#### <a name="receive-custom-messages"></a>Recevoir des messages personnalisés

Pour recevoir des messages personnalisés du serveur de langage, implémentez la propriété [CustomMessageTarget](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.custommessagetarget?view=visualstudiosdk-2017&preserve-view=true) sur [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017&preserve-view=true) et retournez un objet qui sait comment gérer vos messages personnalisés. Voici un exemple ci-dessous :

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

Pour envoyer des messages personnalisés au serveur de langage, implémentez la méthode [AttachForCustomMessageAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.attachforcustommessageasync?view=visualstudiosdk-2017&preserve-view=true) sur [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017&preserve-view=true). Cette méthode est appelée lorsque votre serveur de langage est démarré et prêt à recevoir des messages. Un objet [JsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/src/StreamJsonRpc/JsonRpc.cs) est passé en tant que paramètre, que vous pouvez ensuite conserver pour envoyer des messages au serveur de langage à l’aide des API [vs-StreamJsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/doc/index.md) . Voici un exemple ci-dessous :

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

Parfois, un développeur d’extensions peut vouloir intercepter les messages LSP envoyés et reçus par le serveur de langage. Par exemple, un développeur d’extensions peut vouloir modifier le paramètre de message envoyé pour un message LSP particulier, ou modifier les résultats retournés par le serveur de langue pour une fonctionnalité LSP (par exemple, les saisies semi-automatiques). Lorsque cela est nécessaire, les développeurs d’extensions peuvent utiliser l’API MiddleLayer pour intercepter les messages LSP.

Chaque message LSP possède sa propre interface de couche intermédiaire pour l’interception. Pour intercepter un message particulier, créez une classe qui implémente l’interface de couche intermédiaire pour ce message. Ensuite, implémentez l’interface [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017&preserve-view=true) dans la classe de votre langage client et retournez une instance de votre objet dans la propriété [MiddleLayer](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.middlelayer?view=visualstudiosdk-2017&preserve-view=true) . Voici un exemple ci-dessous :

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

La fonctionnalité de couche intermédiaire est toujours en cours de développement et n’est pas encore complète.

## <a name="sample-lsp-language-server-extension"></a>Exemple d’extension de serveur de langage LSP

Pour afficher le code source d’un exemple d’extension à l’aide de l’API cliente LSP dans Visual Studio, consultez l’exemple VSSDK-Extensibility-Samples [LSP](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/LanguageServerProtocol).

## <a name="faq"></a>Forum aux questions

**Je souhaite créer un système de projet personnalisé pour compléter mon serveur de langage LSP afin d’offrir une prise en charge plus riche des fonctionnalités dans Visual Studio. Comment faire ?**

La prise en charge des serveurs de langues LSP dans Visual Studio s’appuie sur la [fonctionnalité ouvrir le dossier](https://devblogs.microsoft.com/visualstudio/open-any-folder-with-visual-studio-15-preview/) et est conçue pour ne pas nécessiter de système de projet personnalisé. Vous pouvez créer votre propre système de projet [personnalisé en suivant les instructions ci](https://github.com/Microsoft/VSProjectSystem)-dessous, mais certaines fonctionnalités, telles que les paramètres, peuvent ne pas fonctionner. La logique d’initialisation par défaut pour les serveurs de langues LSP consiste à passer à l’emplacement du dossier racine du dossier en cours d’ouverture. par conséquent, si vous utilisez un système de projet personnalisé, vous devrez peut-être fournir une logique personnalisée pendant l’initialisation pour garantir le bon fonctionnement du serveur de langue.

**Comment faire ajouter la prise en charge du débogueur ?**

Nous fournirons la prise en charge du [protocole de débogage commun](https://code.visualstudio.com/docs/extensionAPI/api-debugging) dans une prochaine version.

**Si un service de langage VS pris en charge est déjà installé (par exemple, JavaScript), puis-je continuer à installer une extension de serveur de langue LSP qui offre des fonctionnalités supplémentaires (telles que le non-type de tissu) ?**

Oui, mais toutes les fonctionnalités ne fonctionneront pas correctement. L’objectif ultime pour les extensions de serveur de langage LSP est d’activer les services de langage qui ne sont pas pris en charge en mode natif par Visual Studio. Vous pouvez créer des extensions qui offrent une prise en charge supplémentaire à l’aide de serveurs de langue LSP, mais certaines fonctionnalités (telles qu’IntelliSense) ne seront pas une expérience sans heurts. En général, il est recommandé d’utiliser les extensions du serveur de langue LSP pour fournir de nouvelles fonctionnalités de langage et ne pas étendre celles qui existent déjà.

**Où puis-je publier mon extension de serveur de langue LSP terminée ?**

Consultez les instructions de la place de marché [ici](walkthrough-publishing-a-visual-studio-extension.md).

## <a name="see-also"></a>Voir aussi

- [Ajouter la prise en charge de l’éditeur Visual Studio pour d’autres langages](../ide/adding-visual-studio-editor-support-for-other-languages.md)
