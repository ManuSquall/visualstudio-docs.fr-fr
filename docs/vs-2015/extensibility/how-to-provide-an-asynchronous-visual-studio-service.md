---
title: 'Comment : fournir un service asynchrone | Microsoft Docs'
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 0448274c-d3d2-4e12-9d11-8aca78a1f3f5
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0c58b0be10bf10a21b783a48d52806bf769381ee
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204104"
---
# <a name="how-to-provide-an-asynchronous-visual-studio-service"></a>Guide pratique pour fournir un service Visual Studio asynchrone
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Si vous souhaitez obtenir un service sans bloquer le thread d’interface utilisateur, vous devez créer un service asynchrone et charger le package sur un thread d’arrière-plan. À cet effet, vous pouvez utiliser un <xref:Microsoft.VisualStudio.Shell.AsyncPackage> plutôt qu’un <xref:Microsoft.VisualStudio.Shell.Package> et ajouter le service avec les méthodes asynchrones spéciales du package asynchrone

 Pour plus d’informations sur la fourniture de services Visual Studio synchrones, consultez Guide pratique [pour fournir un service](../extensibility/how-to-provide-a-service.md).

## <a name="implementing-an-asynchronous-service"></a>Implémentation d’un service asynchrone

1. Créez un projet VSIX (**fichier/nouveau/projet/Visual C#/extensibilité/projet VSIX**). Nommez le projet **TestAsync**.

2. Ajoutez un VSPackage au projet. Sélectionnez le nœud du projet dans le **Explorateur de solutions** puis cliquez sur **Ajouter/nouvel élément/éléments Visual C#/extensibilité/package Visual Studio**. Nommez ce fichier **TestAsyncPackage.cs**.

3. Dans TestAsyncPackage.cs, modifiez le package de sorte qu’il hérite de AsyncPackage plutôt que package :

    ```csharp
    public sealed class TestAsyncPackage : AsyncPackage
    ```

4. Pour implémenter un service, vous devez créer trois types :

    - Interface qui décrit le service. La plupart de ces interfaces sont vides, c’est-à-dire qu’elles n’ont aucune méthode.

    - Interface qui décrit l’interface de service. Cette interface comprend les méthodes à implémenter.

    - Classe qui implémente à la fois le service et l’interface de service.

5. L’exemple suivant montre une implémentation très basique des trois types. Le constructeur de la classe de service doit définir le fournisseur de services. Dans cet exemple, nous allons simplement ajouter le service au fichier de code du package.

6. Ajoutez les instructions using suivantes au fichier de package :

    ```csharp
    using System.Threading;
    using System.Threading.Tasks;
    using System.Runtime.CompilerServices;
    using System.IO;
    ```

7. Voici l’implémentation de service asynchrone. Notez que vous devez définir le fournisseur de services asynchrone plutôt que le fournisseur de services synchrones dans le constructeur :

    ```
    public class TextWriterService : STextWriterService, ITextWriterService
    {
        private Microsoft.VisualStudio.Shell.IAsyncServiceProvider serviceProvider;
        public TextWriterService(Microsoft.VisualStudio.Shell.IAsyncServiceProvider provider)
        {
            serviceProvider = provider;
        }
        public async System.Threading.Tasks.Task WriteLineAsync(string path, string line)
        {
            StreamWriter writer = new StreamWriter(path);
            await writer.WriteLineAsync(line);
            writer.Close();
        }
        public TaskAwaiter GetAwaiter()
        {
            return new TaskAwaiter();
        }
    }
    public interface STextWriterService
    {
    }
    public interface ITextWriterService
    {
        System.Threading.Tasks.Task WriteLineAsync(string path, string line);
        TaskAwaiter GetAwaiter();
    }
    ```

## <a name="registering-a-service"></a>Inscription d’un service
 Pour inscrire un service, ajoutez au <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> package qui fournit le service. Il existe deux différences avec l’inscription d’un service synchrone :

- Si vous chargez le package, vous devez ajouter la <xref:Microsoft.VisualStudio.Shell.PackageAutoLoadFlags> valeur BackgroundLoad à l’attribut. Pour plus d’informations sur le chargement automatique des VSPackages, consultez [chargement des VSPackages](../extensibility/loading-vspackages.md).

- Vous devez ajouter le champ **AllowsBackgroundLoading = true** à <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> . Pour plus d’informations sur PackageRegistrationAttribute, consultez [inscription et annulation de l’inscription de VSPackages](../extensibility/registering-and-unregistering-vspackages.md).

  Voici un exemple de AsyncPackage avec une inscription de service asynchrone :

```csharp
[ProvideService((typeof(STextWriterService)), IsAsyncQueryable = true)]
[ProvideAutoLoad(UIContextGuids80.SolutionExists, PackageAutoLoadFlags.BackgroundLoad)]
[PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]
[Guid(TestAsyncPackage.PackageGuidString)]
public sealed class TestAsyncPackage : AsyncPackage
{. . . }
```

## <a name="adding-a-service"></a>Ajout d’un service

1. Dans TestAsyncPackage.cs, supprimez la `Initialize()` méthode et substituez la `InitializeAsync()` méthode. Ajoutez le service et ajoutez une méthode de rappel pour créer les services. Voici un exemple de l’initialiseur asynchrone qui ajoute un service :

    ```
    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        this.AddService(typeof(STextWriterService), CreateService);

        await base.InitializeAsync(cancellationToken, progress);
    }

    ```

2. Ajoutez une référence à Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime.dll.

3. Implémentez la méthode de rappel comme une méthode asynchrone qui crée et retourne le service.

    ```csharp
    public async System.Threading.Tasks.Task<object> CreateService(IAsyncServiceContainer container, CancellationToken cancellationToken, Type serviceType)
    {
        STextWriterService service = null;
        await System.Threading.Tasks.Task.Run(() => {
                    service = new TextWriterService(this);
             });

        return service;
    }

    ```

## <a name="using-a-service"></a>Utilisation d’un service
 Vous pouvez désormais accéder au service et utiliser ses méthodes.

1. Nous allons l’afficher dans l’initialiseur, mais vous pouvez obtenir le service partout où vous souhaitez utiliser le service.

    ```csharp
    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        this.AddService(typeof(STextWriterService), CreateService);

        ITextWriterService textService = await this.GetServiceAsync(typeof(STextWriterService)) as ITextWriterService;

        await writer.WriteLineAsync(<userpath>), "this is a test");

        await base.InitializeAsync(cancellationToken, progress);
    }

    ```

     N’oubliez pas de remplacer *\<userpath>* par un nom de fichier et un chemin d’accès qui ont un sens sur votre ordinateur !

2. Générez et exécutez le code. Lorsque l’instance expérimentale de Visual Studio s’affiche, ouvrez une solution. Cela entraîne le chargement automatique de AsyncPackage. Lorsque l’initialiseur est exécuté, vous devez trouver un fichier à l’emplacement que vous avez spécifié.

## <a name="using-an-asynchronous-service-in-a-command-handler"></a>Utilisation d’un service asynchrone dans un gestionnaire de commandes
 Voici un exemple d’utilisation d’un service asynchrone dans une commande de menu. Vous pouvez utiliser la procédure indiquée ici pour utiliser le service dans d’autres méthodes non asynchrones.

1. Ajoutez une commande de menu à votre projet. (Dans le **Explorateur de solutions**, sélectionnez le nœud du projet, cliquez avec le bouton droit, puis sélectionnez **Ajouter/nouvel élément/extensibilité/commande personnalisée**.) Nommez le fichier de commande **TestAsyncCommand.cs.**

2. Le modèle de commande personnalisé rajoute la `Initialize()` méthode au fichier TestAsyncPackage.cs pour initialiser la commande. Dans la méthode Initialize (), copiez la ligne qui initialise la commande. Il doit se présenter comme suit :

    ```
    TestAsyncCommand.Initialize(this);
    ```

     Déplacez cette ligne vers la `InitializeAsync()` méthode dans le fichier AsyncPackageForService.cs. Étant donné qu’il s’agit d’une initialisation asynchrone, vous devez basculer vers le thread principal avant d’initialiser la commande à l’aide de <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> . Elle doit maintenant ressembler à ceci :

    ```csharp

    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();
        TestAsyncCommand.Initialize(this);

        this.AddService(typeof(STextWriterService), CreateService);

        ITextWriterService textService =
           await this.GetServiceAsync(typeof(STextWriterService)) as ITextWriterService;

        await writer.WriteLineAsync((<userpath>, "this is a test");

        await base.InitializeAsync(cancellationToken, progress);
    }

    ```

3. Supprimez la `Initialize()` méthode.

4. Dans le fichier TestAsyncCommand.cs, recherchez la `MenuItemCallback()` méthode. Supprimez le corps de la méthode.

5. Ajoutez une instruction using :

    ```
    using System.IO;
    ```

6. Ajoutez une méthode asynchrone nommée `GetAsyncService()` , qui obtient le service et utilise ses méthodes :

    ```csharp
    private async System.Threading.Tasks.Task GetAsyncService()
    {
        ITextWriterService textService =
           this.ServiceProvider.GetService(typeof(STextWriterService))
              as ITextWriterService;
        // don’t forget to change <userpath> to a local path
        await writer.WriteLineAsync((<userpath>),"this is a test");
       }

    ```

7. Appelez cette méthode à partir de la `MenuItemCallback()` méthode :

    ```
    private void MenuItemCallback(object sender, EventArgs e)
    {
        GetAsyncService();
    }

    ```

8. Générez la solution et commencez le débogage. Lorsque l’instance expérimentale de Visual Studio s’affiche, accédez au menu **Outils** et recherchez l’élément de menu **appeler TestAsyncCommand** . Lorsque vous cliquez dessus, le TextWriterService écrit dans le fichier que vous avez spécifié. (Vous n’avez pas besoin d’ouvrir une solution, car l’appel de la commande entraîne également le chargement du package.)

## <a name="see-also"></a>Voir aussi
 [Utilisation et fourniture de services](../extensibility/using-and-providing-services.md)
