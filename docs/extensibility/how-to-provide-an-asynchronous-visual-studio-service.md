---
title: 'Comment : fournir un service Visual Studio asynchrone | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0448274c-d3d2-4e12-9d11-8aca78a1f3f5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d486aac8e990fef6b139bca989a51d74146ecb67
ms.sourcegitcommit: 8cbced0fb46959a3a2494852df1e41db1177a26c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76826404"
---
# <a name="how-to-provide-an-asynchronous-visual-studio-service"></a>Comment : fournir un service Visual Studio asynchrone
Si vous souhaitez obtenir un service sans bloquer le thread d’interface utilisateur, vous devez créer un service asynchrone et charger le package sur un thread d’arrière-plan. À cet effet, vous pouvez utiliser un <xref:Microsoft.VisualStudio.Shell.AsyncPackage> plutôt qu’un <xref:Microsoft.VisualStudio.Shell.Package>, et ajouter le service avec les méthodes asynchrones spéciales du package asynchrone.

 Pour plus d’informations sur la fourniture de services Visual Studio synchrones, consultez Guide pratique [pour fournir un service](../extensibility/how-to-provide-a-service.md).

## <a name="implement-an-asynchronous-service"></a>Implémenter un service asynchrone

1. Créez un projet VSIX (**fichier** > **nouveau** **projet** >  > **Visual C#**  > **extensibilité** > **projet VSIX**). Nommez le projet **TestAsync**.

2. Ajoutez un VSPackage au projet. Sélectionnez le nœud de projet dans la **Explorateur de solutions** , puis cliquez sur **Ajouter** > **nouvel élément** > **éléments visuels C#**  > **extensibilité** > **package Visual Studio**. Nommez ce fichier *TestAsyncPackage.cs*.

3. Dans *TestAsyncPackage.cs*, modifiez le package de sorte qu’il hérite de `AsyncPackage` plutôt que `Package`:

    ```csharp
    public sealed class TestAsyncPackage : AsyncPackage
    ```

4. Pour implémenter un service, vous devez créer trois types :

    - Interface qui identifie le service. La plupart de ces interfaces sont vides, c’est-à-dire qu’elles n’ont aucune méthode, car elles ne sont utilisées que pour l’interrogation du service.

    - Interface qui décrit l’interface de service. Cette interface comprend les méthodes à implémenter.

    - Classe qui implémente à la fois le service et l’interface de service.

5. L’exemple suivant montre une implémentation très basique des trois types. Le constructeur de la classe de service doit définir le fournisseur de services. Dans cet exemple, nous allons simplement ajouter le service au fichier de code du package.

6. Ajoutez les directives using suivantes au fichier de package :

    ```csharp
    using System.Threading;
    using System.Threading.Tasks;
    using System.Runtime.CompilerServices;
    using System.IO;
    using Microsoft.VisualStudio.Threading;
    using IAsyncServiceProvider = Microsoft.VisualStudio.Shell.IAsyncServiceProvider;
    using Task = System.Threading.Tasks.Task;
    ```

7. Voici l’implémentation de service asynchrone. Notez que vous devez définir le fournisseur de services asynchrone plutôt que le fournisseur de services synchrones dans le constructeur :

    ```csharp
    public class TextWriterService : STextWriterService, ITextWriterService
    {
        private IAsyncServiceProvider asyncServiceProvider;

        public TextWriterService(IAsyncServiceProvider provider)
        {
            // constructor should only be used for simple initialization
            // any usage of Visual Studio service, expensive background operations should happen in the
            // asynchronous InitializeAsync method for best performance
            asyncServiceProvider = provider;
        }

        public async Task InitializeAsync(CancellationToken cancellationToken)
        {
            await TaskScheduler.Default;
            // do background operations that involve IO or other async methods

            await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync(cancellationToken);
            // query Visual Studio services on main thread unless they are documented as free threaded explicitly.
            // The reason for this is the final cast to service interface (such as IVsShell) may involve COM operations to add/release references.

            IVsShell vsShell = this.asyncServiceProvider.GetServiceAsync(typeof(SVsShell)) as IVsShell;
            // use Visual Studio services to continue initialization
        }

        public async Task WriteLineAsync(string path, string line)
        {
            StreamWriter writer = new StreamWriter(path);
            await writer.WriteLineAsync(line);
            writer.Close();
        }
    }

    public interface STextWriterService
    {
    }

    public interface ITextWriterService
    {
        System.Threading.Tasks.Task WriteLineAsync(string path, string line);
    }
    ```

## <a name="register-a-service"></a>Inscrire un service
 Pour inscrire un service, ajoutez le <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> au package qui fournit le service. Différent de l’enregistrement d’un service synchrone, vous devez vous assurer que le package et le service prennent en charge le chargement asynchrone :

- Vous devez ajouter le champ **AllowsBackgroundLoading = true** à la <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> pour vous assurer que le package peut être initialisé de manière asynchrone pour plus d’informations sur PackageRegistrationAttribute, consultez [inscrire et désinscrire des VSPackages](../extensibility/registering-and-unregistering-vspackages.md).

- Vous devez ajouter le champ **IsAsyncQueryable = true** à la <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> pour vous assurer que l’instance de service peut être initialisée de façon asynchrone.

  Voici un exemple de `AsyncPackage` avec une inscription de service asynchrone :

```csharp
[ProvideService((typeof(STextWriterService)), IsAsyncQueryable = true)]
[ProvideAutoLoad(UIContextGuids80.SolutionExists, PackageAutoLoadFlags.BackgroundLoad)]
[PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]
[Guid(TestAsyncPackage.PackageGuidString)]
public sealed class TestAsyncPackage : AsyncPackage
{. . . }
```

## <a name="add-a-service"></a>Ajouter un service

1. Dans *TestAsyncPackage.cs*, supprimez la méthode `Initialize()` et substituez la méthode `InitializeAsync()`. Ajoutez le service et ajoutez une méthode de rappel pour créer les services. Voici un exemple de l’initialiseur asynchrone qui ajoute un service :

    ```csharp
    protected override async Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        await base.InitializeAsync(cancellationToken, progress);
        this.AddService(typeof(STextWriterService), CreateTextWriterService);
    }

    ```
    Pour rendre ce service visible en dehors de ce package, définissez la valeur de l’indicateur promote sur *true* comme dernier paramètre : `this.AddService(typeof(STextWriterService), CreateTextWriterService, true);`

2. Ajoutez une référence à *Microsoft. VisualStudio. Shell. Interop. 14.0. designtime. dll*.

3. Implémentez la méthode de rappel comme une méthode asynchrone qui crée et retourne le service.

    ```csharp
    public async Task<object> CreateTextWriterService(IAsyncServiceContainer container, CancellationToken cancellationToken, Type serviceType)
    {
        TextWriterService service = new TextWriterService(this);
        await service.InitializeAsync(cancellationToken);
        return service;
    }

    ```

## <a name="use-a-service"></a>Utiliser un service
 Vous pouvez désormais accéder au service et utiliser ses méthodes.

1. Nous allons l’afficher dans l’initialiseur, mais vous pouvez obtenir le service partout où vous souhaitez utiliser le service.

    ```csharp
    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        await base.InitializeAsync(cancellationToken, progress);
        this.AddService(typeof(STextWriterService), CreateTextWriterService);

        ITextWriterService textService = await this.GetServiceAsync(typeof(STextWriterService)) as ITextWriterService;
        string userpath = @"C:\MyDir\MyFile.txt";
        await textService.WriteLineAsync(userpath, "this is a test");
    }

    ```

     N’oubliez pas de remplacer `userpath` par un nom de fichier et un chemin d’accès qui ont un sens sur votre ordinateur !

2. Générez et exécutez le code. Lorsque l’instance expérimentale de Visual Studio s’affiche, ouvrez une solution. Cela provoque le chargement du `AsyncPackage`. Lorsque l’initialiseur est exécuté, vous devez trouver un fichier à l’emplacement que vous avez spécifié.

## <a name="use-an-asynchronous-service-in-a-command-handler"></a>Utiliser un service asynchrone dans un gestionnaire de commandes
 Voici un exemple d’utilisation d’un service asynchrone dans une commande de menu. Vous pouvez utiliser la procédure indiquée ici pour utiliser le service dans d’autres méthodes non asynchrones.

1. Ajoutez une commande de menu à votre projet. (Dans le **Explorateur de solutions**, sélectionnez le nœud du projet, cliquez avec le bouton droit, puis sélectionnez **Ajouter** > **nouvel élément** > **extensibilité** > **commande personnalisée**.) Nommez le fichier de commande *TestAsyncCommand.cs*.

2. Le modèle de commande personnalisé ajoute à nouveau la méthode `Initialize()` au fichier *TestAsyncPackage.cs* pour initialiser la commande. Dans la méthode `Initialize()`, copiez la ligne qui initialise la commande. Le résultat doit être semblable à ce qui suit :

    ```csharp
    TestAsyncCommand.Initialize(this);
    ```

     Déplacez cette ligne vers la méthode `InitializeAsync()` dans le fichier *AsyncPackageForService.cs* . Étant donné qu’il s’agit d’une initialisation asynchrone, vous devez basculer vers le thread principal avant d’initialiser la commande à l’aide de <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>. Elle doit maintenant ressembler à ceci :

    ```csharp

    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        await base.InitializeAsync(cancellationToken, progress);
        this.AddService(typeof(STextWriterService), CreateTextWriterService);

        ITextWriterService textService =
           await this.GetServiceAsync(typeof(STextWriterService)) as ITextWriterService;
        
        string userpath = @"C:\MyDir\MyFile.txt";
        await textService.WriteLineAsync(userpath, "this is a test");

        await this.JoinableTaskFactory.SwitchToMainThreadAsync(cancellationToken);
        TestAsyncCommand.Initialize(this);
    }

    ```

3. Supprimez la méthode `Initialize()`.

4. Dans le fichier *TestAsyncCommand.cs* , recherchez la méthode `MenuItemCallback()`. Supprimez le corps de la méthode.

5. Ajoutez une directive using :

    ```csharp
    using System.IO;
    ```

6. Ajoutez une méthode asynchrone nommée `UseTextWriterAsync()`, qui obtient le service et utilise ses méthodes :

    ```csharp
    private async System.Threading.Tasks.Task UseTextWriterAsync()
    {
        // Query text writer service asynchronously to avoid a blocking call.
        ITextWriterService textService =
           await AsyncServiceProvider.GlobalProvider.GetServiceAsync(typeof(STextWriterService))
              as ITextWriterService;

        string userpath = @"C:\MyDir\MyFile.txt";
        await textService.WriteLineAsync(userpath, "this is a test");
       }

    ```

7. Appelez cette méthode à partir de la méthode `MenuItemCallback()` :

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        UseTextWriterAsync();
    }

    ```

8. Générez la solution et commencez le débogage. Lorsque l’instance expérimentale de Visual Studio s’affiche, accédez au menu **Outils** et recherchez l’élément de menu **appeler TestAsyncCommand** . Lorsque vous cliquez dessus, le TextWriterService écrit dans le fichier que vous avez spécifié. (Vous n’avez pas besoin d’ouvrir une solution, car l’appel de la commande entraîne également le chargement du package.)

## <a name="see-also"></a>Voir aussi
- [Utilisez et fournissez des services](../extensibility/using-and-providing-services.md)
